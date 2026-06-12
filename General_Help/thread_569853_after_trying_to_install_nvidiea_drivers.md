---
title: "after trying to install nvidiea drivers"
date: 2007-10-07
forum: General Help
---

### Post by Mr.popo on 2007-10-07
after i installed them i rebooted went back on to ubuntu and i keep going to a black screen with a login
so i loggged in and its similar to terminal. all i can do is enter commands 
which commands wshould i use to sort this problem.


another thing is in the my boot up menu when i choose my os .


there are loads of options
there is 
ubuntu generic ( 2 of them)
and safe mode and mem test
should i have that many>

---

### Post by forestpixie on 2007-10-07
when you get to the command line enter this to reconfigure X, answer the questions as best as you can, how did you install the drivers - if you have problems try [envy]("http://albertomilone.com/nvidia_scripts1.html")

sudo dpkg-reconfigure xserver-xorg

as far as the boot options that's prettty normal - 1 new kernel, 1 previous and their safe modes and a memtest

---

