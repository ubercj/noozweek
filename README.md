# Noozweek

See the site live [here](https://ubercj.github.io/noozweek/).

This is a project from The Odin Project's full-stack web development curriculum, read more about the assignment [here](https://www.theodinproject.com/paths/full-stack-ruby-on-rails/courses/html-and-css/lessons/using-bootstrap). In short, the goal is to use [Bootstrap](https://getbootstrap.com/) to imitate the layout of the Newsweek [front page](http://www.newsweek.com/).

## Notes and Reflections

### Navbar

The hardest part of this project was definitely configuring the navbar at the top. The Bootstrap [docs](https://getbootstrap.com/docs/5.0/components/navbar/#toggler) actually do a pretty good job of explaining how to make a responsive "disappearing" navbar, and putting the toggler in an element other than the navbar itself. (In this case, the hamburger menu is in the header element, not the navbar itself). It just took me a little while and a few failed attempts before I found the winning combination.

One note: I couldn't get the little hamburger menu to show up, even though I was using the exact same code from the docs:

```
<span class="navbar-toggler-icon"></span>
```

It turns out, you need to have the `.navbar-light` or `.navbar-dark` class on the __parent element of the span__ in order for it to render properly. Even though the parent element in this case was the header element, it still needed a class of `.navbar-dark`, and that kind of threw me off.

### Scrolling and Y-Overflow

I had a difficult time figuring out how to make the independently-scrolling columns at the top of the page in the desktop layout. Even though I figured out an approximation, I still never came across a solution that _doesn't_ make the shortest column scroll like in the actual Newsweek site. Check out their site to see what I mean.

I found out how to hide the scrollbars from this [Stack Overflow answer](https://stackoverflow.com/a/49278385/15316848). So I ended up adding a CSS called "scrollable" to make it work:

```
  .scrollable {
    height: 100%;
    overflow: scroll;
    scrollbar-width: none;
    -ms-overflow-style: none;
  }

  .scrollable::-webkit-scrollbar {
    width: 0;
    height: 0;
  }
}
```

### Responsive design and screen widths

I was fairly impressed with how easy Bootstrap made it to design for multiple devices. There was one aspect of the actual Newsweek site design that I failed to include, which is the drastic reordering of elements for the mobile layout. Elements from the 3 columns at the top have their order mixed up - for example the Top Story from the middle column comes first, then some of the Latest Stories from the left column, then the Debate section from the right column, etc. I imagine the actual site just uses a completely separate stylesheet for the mobile layout, so I just went with an approximation of the layout that followed the order of my elements in the html I had already written.