---
title: "Disable Browsing Of Entire System / SSH"
date: 2006-12-08
forum: General Help
---

### Post by shanepardue on 2006-12-08
Is there a way to restrict an ssh client from browsing anywhere outside the home folder that is created for him? I'd rather not have these users be able to see all of the files on my machine. Thanks!

---

### Post by lloyd_b on 2006-12-08
It can be done, via a "chroot" command in the user's login, but it's not easy.  The issue is that the user *needs* to be able to see most of the system, in order to actually do anything.  For instance, if they don't have access to the "/bin" directory, then they won't be able to run the most basic commands (such as "ls").  Even with the chroot you'll still need to make most of those directories available, but you can limit them to being able to see ONLY what they need to be able to see.

Setting up a working chroot environment means determining exactly what the user needs, and hard-linking/copying/remounting those programs/files to a point within the user's limited environment.  A heck of a lot of work (though if you set up a script, after you have it properly configured it's fairly easy to maintain).

Generally, the fact that the user can "browse" the system is not an issue, since the default permissions prevent him/her from *changing* anything.

You may want to change the permissions on user's home directories to 700, so that one user can't browse into another user's home directory.

Lloyd B.

---

### Post by technodigifreak on 2006-12-08
Agrees: chrooting is a PITA, but well worth it.  I have not attempted a chroot on Ubuntu, but I should be very similar to the process on Debian.

The following are 2 links for setting up a chroot environment for ssh access.

The first one is a very long read, but quite detailed.  The second is quick and dirty, but both of them should work.  It will help if you've got practice setting up a chroot for other services (like BIND), but these tutorials should put you in the right direction.

[http://debian.chains.ch/chroot/chroot.html](http://debian.chains.ch/chroot/chroot.html)
[http://www.howtoforge.com/chrooted_ssh_howto_debian](http://www.howtoforge.com/chrooted_ssh_howto_debian)

---

### Post by shanepardue on 2006-12-08
After reading there very informative posts, I've decided if I'm wanting to share files with encryption, I may just set up a webserver instead with https. That seems to make more sense if I'm only wanting it to work as a file  server.

---

