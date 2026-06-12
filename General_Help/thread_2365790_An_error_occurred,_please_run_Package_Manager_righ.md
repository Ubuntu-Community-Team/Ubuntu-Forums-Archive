---
title: "An error occurred, please run Package Manager right click-menu..."
date: 2017-07-10
forum: General Help
---

### Post by Nuitblanche on 2017-07-10
I turned my computer on this morning and there's a red icon with white bar on top panel with message:

*An error occurred, please run Package Manager right click-menu or apt-get in a terminal to see what is wrong. The error message was: 'Unknown Error: '<class KeyError'>' "The cache has no package named 'wine1.6-i386'")'. This usually means that your installed packages have unmet dependencies*

When I turned my computer off last night there was no such message. And I didn't do any updates.

Is this a known problem? How can I fix it?

---

### Post by cheesy-potato on 2017-07-11
I am having the same problem. I'm an Ubuntu noob. I don't really have any experience trying to fix something like this.
If some one has some advice before I delve in to this swinging commands I don't fully understand...
That would be amazing.

---

### Post by kbeets68 on 2017-07-11
What's the complete error message? You can try the following for now. i) start a terminal window by pressing ctrl+alt+T, ii) type sudo apt-get update + enter and after that finishes iii) sudo apt-get upgrade.

---

### Post by Nuitblanche on 2017-07-11
Thanks kbeets68. 
I did as you say. That fixed the problem.

---

