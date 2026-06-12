---
title: "Help with Xauth"
date: 2006-10-30
forum: General Help
---

### Post by rappazzo on 2006-10-30
Hi, I just started working with linux/ubuntu (v6.06) recently, and I am starting to get the hang of things.  But now I am getting a problem running the admin modules of the GUI (like the user-admin or package manager apps).  The Error I a getting is that something cannot copy the user's Xauthorization file.  Rebooting did not help.

I did a little searching around on the web and in this forum, and I think that the problem somehow stems from a file in my home dir, the .Xauthority file.  I did an 'ls -a', and there is not a file by that name.  there are a few files in the /tmp heirarchy (from: 'find / -print | grep .Xauth'), but I don't think they are useable.

So I think I need to run 'xauth', but I am not sure how, or what key to use (or even what a key should be in this case).  Any help would be greatly appreciated.

---

### Post by Doppelbock on 2006-12-10
I'm having the same issue now myself. I had no issues for several weeks after my install of Dapper but now whenever I try to open a GUI admin tool I get the same error. The only directory permissions changes I've made have been on a separate drive from where the OS is located so I'm stumped as to why this error seems to have come up out of the blue.

---

