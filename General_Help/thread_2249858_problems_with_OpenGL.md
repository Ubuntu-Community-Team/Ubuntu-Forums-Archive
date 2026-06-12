---
title: "problems with OpenGL"
date: 2014-10-25
forum: General Help
---

### Post by fabiani on 2014-10-25
Dear community,

I was having some graphical  problems (OpenGL not working), so I decided to upgrade my Dell Optiplex  9010 to ubuntu 14.04 (from 13.10) and installed the intel graphics  drivers. gnome was giving problems, so I uninstalled gnome-session (that  was the desktop manager I was used to) and I'm using lightdm at the  moment.

That didn't seem to solve the problem, OpenGL is still not working:

$ glxinfo -v
name of display: localhost:10.0
Segmentation fault (core dumped)



It seems that the GL libraries are where they're supposed to be, I guess:

$ find /usr/lib -name libGL.so.1 -exec ls -al {} \;
lrwxrwxrwx 1 root root 14 Jul 18 04:40 /usr/lib/x86_64-linux-gnu/libGL.so.1 -> libGL.so.1.2.0
lrwxrwxrwx 1 root root 14 Jul 18 04:59 /usr/lib/i386-linux-gnu/libGL.so.1 -> libGL.so.1.2.0




I followed the instructions in 

[http://ubuntuforums.org/showthread.php?t=1931696](http://ubuntuforums.org/showthread.php?t=1931696)


and, after restarting, I still get the same error.



Maybe there might be a conflict between different libraries, as in this case?

[http://unix.stackexchange.com/questions/79701/opengl-glx-core-dumps-generic-intel-linux-drivers-rhel6](http://unix.stackexchange.com/questions/79701/opengl-glx-core-dumps-generic-intel-linux-drivers-rhel6)


Thank you in advance for any feedback.

---

