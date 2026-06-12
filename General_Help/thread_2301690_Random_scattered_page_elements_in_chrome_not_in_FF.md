---
title: "Random scattered page elements in chrome not in FF"
date: 2015-11-04
forum: General Help
---

### Post by Ace..... on 2015-11-04
[SIZE=3]**Random scattered page elements in chrome not in FF**[/SIZE]
It's almost like as if bits were breaking out of their containers
The image below presents a good example.

The top image is in place, a space, then the bottom image.
However, in the middle, we can see part of the navbar in red on the left.
To its right, another section of the page, followed by a small section of another image.

[ATTACH=CONFIG]265358[/ATTACH]

There is no repeating pattern.
Any parts of the page can appear..... in different places.

**Note:**
[LIST]
[*]If I adjust the browser window (even a miniscule amount) the display errors disappear, until page is re-loaded.
[*]The page may load without any errors.
[*]Re-loading the page causes a different pattern of errors, or none at all.
[*]Any change to the browser clears the errors.
[/LIST]

**When the problem occurs:**

It only occurs at pixel widths lower than 992px.

This is when the rows auto-change to columns.
I presume that this is being controlled by bootstrap.
I haven't spent much time checking bootstrap, because I don't want to be editing it anyway.

@992px I made a few padding type mods, to get the display correct, and changed the float of one lower container from none to left.

This display glitch can then appear at all lower resolutions.

I thought that I'd cracked it, by re-loading the page and counting to 5, before scrolling down.
About 8 times in a row, it displayed perfectly........ and then it didn't.

The display is rock solid in FF.

In chrome console..... if I uncheck _any_ struck through element..... the display corrects.
In effect.... any change to the page or window, corrects the problem.


[LIST]
[*]Has anybody experienced this before?
[*]Also...... how might I verify the code?
[*]Does the random nature of the display fault, provide a clue as to the cause?
[/LIST]

**My Next step:**
Is to begin removing containers, to see if one is causing the problem.

---

### Post by slickymaster on 2015-11-04
Not a Programming Talk topic.
[I]
Moved to the [/I]**General Help*** sub-forum*

---

