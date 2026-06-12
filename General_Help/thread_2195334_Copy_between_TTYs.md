---
title: "Copy between TTYs"
date: 2013-12-23
forum: General Help
---

### Post by Tristan_Williams on 2013-12-23
How can I copy text from one tty to another?

Example:
I have a terminal open in tty7 (graphical interface) and I want to copy some of its contents to tty1 (where I have nano open).

---

### Post by bapoumba on 2013-12-23
[https://answers.launchpad.net/ubuntu/+source/gnome-desktop/+question/212118](https://answers.launchpad.net/ubuntu/+source/gnome-desktop/+question/212118)

I used to use that a lot.. The buffer is lost when you exit the desktop to enter a tty.

---

### Post by ian-weisser on 2013-12-24
bapoumba is right. The system considers ttys to be separate terminal machines, sitting side by side. They are multiplexed onto a single keyboard/display as a convenience - they could as easily be in different rooms.

GUI cut/paste buffers don't work in a non-GUI terminal.
The terminal windows you create and use within the GUI can use cut/paste buffers because they are within that environment.

In a non-GUI environment you usually transmit data between ttys as a saved file. Applications transmit data between ttys using files, pipes, or sockets.

---

