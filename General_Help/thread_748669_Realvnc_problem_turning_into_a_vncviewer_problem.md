---
title: "Realvnc problem turning into a vncviewer problem"
date: 2008-04-07
forum: General Help
---

### Post by Valyander on 2008-04-07
I am fairly new to Ubuntu and the Linux environment so I might very well get served the most basic palm-to-face solution here, but I'm stuck nontheless so here goes.

I am using VNC to connect to the computers of our clients when helping them with various problems. Up until a few months ago we were using Windows XP and thus using the Realvnc client without any problems.

When I transferred to Ubuntu I originally used the Terminal Server Client software included in the distro. Basically a good and simple multipurpose remote connector software, though I became increasingly annoyed with a small issue. Whenever I had connected to the remote computer and was prompted for the password I had problems selecting the password field. I was unable to TAB to it, and it took me several clicks with the mouse for the text marker to appear in the field. My coworker does not have this problem, and none of the other Ubuntu machines have either, and after searching around for a solution I thought I might as well use the Realvnc client.

So, I started using the standalone Realvnc Enterprise Edition viewer. It seemed to work pretty smoothly but at random intervals I would get disconnected with error messages like "rect too big", or simply with no error at all. I could use it flawlessly for five minutes, or I could get disconnected after 15 seconds.

After lots of google'ing, searching the realvnc forums,  and searching the forums here I tried to use the vncviewer command from the terminal window. That resulted in this error:

~$ vncviewer
vncviewer: error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory

I have now spent the better part of a work day looking for somewhere I could get this library, but to no avail. The problem now also arises because the Terminal Server Client used the vncviewer command to launch the vnc part of the program, so I am now stuck with only the standalone viewer with random disconnects.

So, my question is twofold:
1) Does anyone have any solution to the issues with the standalone realvnc viewer? (Other than the one they post on the realvnc website, which basically says it might be fixed in a later version)
2) Does anyone know where I might be able to retrieve a package containing the missing library? (Have searched with the Synaptics Package Manager as well, but no luck)


And ofcourse, as I said, this might have the simplest solution ever. If so, feel free to serve me like the noob I am :)

---

