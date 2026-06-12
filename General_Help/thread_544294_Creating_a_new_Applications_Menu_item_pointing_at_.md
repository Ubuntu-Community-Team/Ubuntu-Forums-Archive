---
title: "Creating a new Applications Menu item pointing at a location containing spaces"
date: 2007-09-06
forum: General Help
---

### Post by rom1desboa on 2007-09-06
Hi there,

I am trying to create a new menu item in the Applications menu, pointing at "/home/<username>/path\ with\ spaces/binary"

It does not seem to cope very well with spaces, as they don't get escaped and I get an error saying:
  Could not launch menu item
  Failed to execute child process "/home/<username>/path"

I also tried to wrap the path between quotes but that did not work either.

Any ideas? (apart from creating a symbolic link or any such workaround)

Cheers

---

### Post by bettlebrox on 2007-09-06
U can try escaping the spaces with \ like so:

/home/me/directory\ with\ spaces/file

Or try surrounding it with double-quotes:
"/home/me/directory with spaces/file"

---

