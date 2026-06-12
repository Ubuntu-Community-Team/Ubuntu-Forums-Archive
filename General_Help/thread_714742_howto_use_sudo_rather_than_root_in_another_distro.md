---
title: "howto use sudo rather than root in another distro"
date: 2008-03-04
forum: General Help
---

### Post by ingo on 2008-03-04
Hello, 
 
I've got a Debian Etch install (with KDE) running fine with proper root, i.e. no sudo. Now I'd quite like to change that to the way Ubuntu behaves but have run into problems. 
 
Here is what I have done: 
 
1) did "visudo" and added "my_username  ALL=(ALL) ALL" under the "User privilege specification" line. 
 
This worked a treat and I can do a sudo on the command line. However, it does not work when I call up adept from the menu - anything from the menu which requires root privileges accepts the root password only. 
 

I am aware that KDESU is the app which runs these menu items, but am not sure how to tell KDESU that the sudo user is to be accepted instead of the root user.

Any help is greatly appreciated!

---

### Post by mali2297 on 2008-03-04
Hi.

Out of curiousity, I searched the web for your problem. I think that I have found a solution.

Create a file **~/.kde/share/config/kdesurc** with the contents:
```

[super-user-command]
super-user-command=sudo

```

Let us know whether it works.

---

### Post by ingo on 2008-03-04
It worked it worked it worked it worked!!! Great!

Where did you find this? I googled but to no avail! 

Also I wonder how this will work when I remaster my system, i.e. how it behaves once it gets dumped in /etc/skel... Hm, only one way to find out :)

---

