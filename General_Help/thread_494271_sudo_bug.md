---
title: "sudo bug?"
date: 2007-07-06
forum: General Help
---

### Post by namelessone on 2007-07-06
I am suddenly not able to use sudo...(syntax error in sudoers file) I've noticed a couple of other people have had this problem too. Is this some kind of bug?

I first noticed it's lack of workingness when I typed sudo dhclient eth0. Things I have changed since I had last successfully used sudo: added a .gtkrc-2.0 file that tells gtk applications to use emacs keybindings, made a .bash-aliases file with some useful aliases, and added a line into my .bashrc file that expands ! history commands into full commands when I press space.

Those seem like pretty harmless things to do...did one of those things break sudo, or did it just happen randomly? I didn't touch the sudoers file...

EDIT: okay... so maybe I did edit it and I just forgot... problem solved

---

### Post by ubuntu.daemon on 2007-07-06
I had an issue with that,  it was when i installed smb4k, and for some reason it just totally messed with it, there is a lil prevention you can do b4 it happens being, have a root user.  I dont have any advice for you how to fix it, but look up smb4k, bc i think there is a work around, i just reinstalled into a new feisty b4 it came out.

gl:popcorn:

---

### Post by namelessone on 2007-07-07
wow. i feel stupid... i guess i forgot that I did actually edit my sudoers file... should've used visudo so I wouldn't have made that stupid typo...

---

