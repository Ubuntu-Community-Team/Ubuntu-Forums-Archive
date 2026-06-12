---
title: "Applications menu troubles"
date: 2007-12-05
forum: General Help
---

### Post by eipi1 on 2007-12-05
I have an installed application: /share/applications/monodevelop.desktop
I can navigate to it and run it OK.

It appears in my Applications-Programming menu but when I select it I get:

Failed to execute child process "/share/applications/monodevelop.desktop" (Permission denied).

Now this is weird:
If I goto Applications- Add/Remove, it doesn't appear in the list???

Any direction would be appreciated.

---

### Post by pjman on 2007-12-05
How was it installed? 

You might need to chown the files so you are the owner. It's a guess..

---

### Post by oeolycus on 2007-12-05
It does sound like you installed it manually, in which case it wouldn't show up in Add/Remove Applications. You can find the MENU ITEM if you edit the menus (under system > preferences, and other ways).

You should check its permissions either through Nautilus or at the command line. I can offer a little more help when I get home, but try these options first. Good luck!

---

### Post by eipi1 on 2007-12-05
Hi,

I think this chown is a hot lead but I'm still in trouble.

To install I followed the instructions at 

[http://www.howtogeek.com/howto/linux/installing-monodevelop-from-source-on-ubuntu/](http://www.howtogeek.com/howto/linux/installing-monodevelop-from-source-on-ubuntu/)

pretty much to the letter except I installed monodevelop-0.17 and I corrected

./configure –prefix=`pkg-config –variable=prefix mono`

to

./configure --prefix=`pkg-config –variable=prefix mono`

I'm pretty green at this and don't know about chown. Executing ls -l at /share/applications gives:
-rw-r--r-- 1 root root 538 2007-12-04 20:19 monodevelop.desktop (which I think meens the owner is root)

and chown mark monodevelop.desktop gives:

chown: changing ownership of `monodevelop.desktop': Operation not permitted

---

### Post by diplo on 2007-12-05
> **eipi1 said:**
> Hi,

I think this chown is a hot lead but I'm still in trouble.

To install I followed the instructions at 

[http://www.howtogeek.com/howto/linux/installing-monodevelop-from-source-on-ubuntu/](http://www.howtogeek.com/howto/linux/installing-monodevelop-from-source-on-ubuntu/)

pretty much to the letter except I installed monodevelop-0.17 and I corrected

./configure –prefix=`pkg-config –variable=prefix mono`

to

./configure --prefix=`pkg-config –variable=prefix mono`

I'm pretty green at this and don't know about chown. Executing ls -l at /share/applications gives:
-rw-r--r-- 1 root root 538 2007-12-04 20:19 monodevelop.desktop (which I think meens the owner is root)

and chown mark monodevelop.desktop gives:

chown: changing ownership of `monodevelop.desktop': Operation not permitted

Because the item is owned by root you need to chown it by using sudo as your normal user doesn't have the privileges to do this so just append sudo 'sudo chown mark monodevelop.desktop'

---

### Post by eipi1 on 2007-12-06
OK, I executed 'sudo chown mark monodevelop.desktop'

and now ls -l gives: -rw-r--r-- 1 mark root 538 2007-12-04 20:19 monodevelop.desktop

so, I believe I now own the file.

Using system > preferences > Main Menu, I removed the item then added it again.

When I try to run it from Applications I still get "Failed to execute child process "/share/applications/monodevelop.desktop" (Permission denied)"

the actual file is /share/applications/monodevelop.desktop not user/share/applications/monodevelop.desktop 

echo $PATH gives /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

could this be related to my troubles??

---

