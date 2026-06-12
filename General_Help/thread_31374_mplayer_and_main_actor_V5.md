---
title: "mplayer and main actor V5"
date: 2005-05-02
forum: General Help
---

### Post by ptesone on 2005-05-02
I was tirlessley going down the unofficial ubuntu starter page installing everything on there and tweaking all that could be tweaked when I got to mplayer and this is what I got:

ptesone@ubuntu:~$ sudo apt-get -t hoary install mplayer-386
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mplayer-386: Depends: libavcodeccvs (>= 2:20050417-0.0) but it is not going to be installed
               Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
               Depends: libfontconfig1 (>= 2.3.0) but 2.2.3-4ubuntu7 is to be installed
               Depends: libpostproc0 (>= 2:20050417-0.0) but it is not going to be installed
               Depends: libvorbis0a (>= 1.1.0) but 1.0.1-1 is to be installed
               Depends: libxvidcore4 (>= 1:1.0.0-0.0) but it is not going to be installed
               Depends: xmms (>= 1.2.10+cvs20050209) but 1.2.10-2ubuntu1 is to be installed
E: Broken packages

but the freaky thing is is I copied my mplayer and gmplayer binary from my suse install /usr/bin and /etc/mplayer, etc and installed the missing libs, (there were 4) I think, and BOOM it works perfectly. . .

Now I had gotten an RPM of Main Actor V5 demo and aliened it and it installed fine but got a segment fault whenever I ran it so I removed it completley with synaptic and copied it from my suse install and now it works in ubuntu  \\:D/

---

