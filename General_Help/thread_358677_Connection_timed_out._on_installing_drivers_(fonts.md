---
title: "Connection timed out. on installing drivers (fonts?)"
date: 2007-02-11
forum: General Help
---

### Post by TailorMade on 2007-02-11
Hey everyone

Yes, im new to this forum, please spare the flames, anyhow, here goes.

While installing Drivers, for example, in this case, Nvidia's Drivers for Edgy 6.10
> 
aki@aki-desktop:~$ sudo apt-get install nvidia-glx nvidia-kernel-common
Reading package lists... Done
Building dependency tree
Reading state information... Done
nvidia-glx is already the newest version.
nvidia-kernel-common is already the newest version.
The following packages were automatically installed and are no longer required:
  libjack0.100.0-0 libfluidsynth1 ladcca2 scummvm
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up msttcorefonts (1.2ubuntu3) ...
warning: /usr/share/fonts/X11/truetype does not exist or is not a directory
warning: /usr/lib/X11/fonts/truetype does not exist or is not a directory
These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

---**THIS IS THE ERROR AREA**---
You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.
--12:31:32--  [http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving belnet.dl.sourceforge.net... failed: Connection timed out.
--12:31:42--  [http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving easynews.dl.sourceforge.net... failed: Connection timed out.
--12:31:52--  [http://twtelecom.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://twtelecom.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving twtelecom.dl.sourceforge.net... failed: Connection timed out.
--12:32:02--  [http://aleron.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://aleron.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving aleron.dl.sourceforge.net... failed: Connection timed out.
--12:32:12--  [http://cesnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://cesnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving cesnet.dl.sourceforge.net... failed: Connection timed out.
--12:32:22--  [http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving switch.dl.sourceforge.net... failed: Connection timed out.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)
aki@aki-desktop:~$ apt-cache policy msttcorefonts
msttcorefonts:
  Installed: 1.2ubuntu3
  Candidate: 1.2ubuntu3
  Version table:
 *** 1.2ubuntu3 0
        500 [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) edgy/multiverse Packages
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages
        100 /var/lib/dpkg/status

I been searching for an answer to my problem for hours and hours, this is what i got so far.

One page suggested me to use Automatix, nope, same error on that one

, the command 'aki@aki-desktop:~$ apt-cache policy msttcorefonts' gave me this
>   Installed: 1.2ubuntu3
  Candidate: 1.2ubuntu3
  Version table:
 *** 1.2ubuntu3 0
        500 [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) edgy/multiverse Packages
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages
        100 /var/lib/dpkg/status


I also got this error , for example when i tried installing a dc++ trough Automatix (not that i need one, so i dont need help on installing the dc++)   (i found wine ;) )
,
Heres a screenshot of my automatix report page
[Img]http://img302.imageshack.us/img302/8646/errormsg2uf7.jpg[/IMG]

So please! Community of Linux ;> save me! i dont want to go back to Windows to play games

(ill add more info if i get any, also, ill try to answer ur questions as well as i can)

---

