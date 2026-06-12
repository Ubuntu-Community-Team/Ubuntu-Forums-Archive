---
title: "reopen STDERR STDIN STDOUT in switched workspace"
date: 2024-07-30
forum: General Help
---

### Post by Skaperen on 2024-07-30
i'm running a script or program that starts in one workspace in the display.  it switches to a different workspace.  i need for this script/program to work with the console in the new workspace.  it needs to re-open STDERR STDIN and STDOUT to the console of the new workspace.  it turn out that "/dev/tty" is still the console of the old workspace.  how do i get "/dev/tty" updated to the new workspace so i can re-open STDERR STDIN and STDOUT?  i may end up with a similar issue with virtual text consoles in the next related project.

---

### Post by currentshaft on 2024-07-30
What exactly is meant by "workspace" in this context?

---

### Post by Skaperen on 2024-08-07
do "man wmctrl" and scroll down to the "-s" option.  it is called many things.  my program will run "wmctrl -s NN" to switch the display (being seen) to display number NN.  these are virtual displays that operate like separate virtual desktops.  the window manager manages this by making everything in the current workspace invisible (unexposed) then making everything in the target (NN) workspace visible and exposes everything.  there may be other details about doing this that i am unaware of.

i wonder how many Ubuntu users are aware of virtual workspaces.

most of my actual X desktops (i usually run 12 to 18 of them) have 20 virtual workspaces.  most are empty but a great many run an X terminal program with a near full screen (and its own shell).

---

### Post by currentshaft on 2024-08-07
.

---

### Post by Skaperen on 2024-08-08
i already use screen for some cases.  a solution for those cases might also be useful in the future, but the first need is for this particular need involving a jump to a different xterm.

---

