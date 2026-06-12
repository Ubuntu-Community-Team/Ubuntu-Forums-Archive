---
title: "Missing library on 14.04 after upgrade. I can't run stata now."
date: 2014-06-25
forum: General Help
---

### Post by jfca283 on 2014-06-25
Hi
I did an upgrade in ubuntu.
I'm running 14.04 version.
Before i could work with stata.
But now i can't load the mentioned software.
Here is the output when i try to load it

[I]
PC:/usr/local/stata12$ ./xstata
./xstata: error while loading shared libraries: libgnomeprint-2-2.so.0: cannot open shared object file: No such file or directory[/I]

I looked for the library libgnomeprint and it doesn't exist on ubuntu 14.04 trusty tahr.
So, what can i do?
Thanks for your time and interest.

---

### Post by monkeybrain20122 on 2014-07-06
The package has been removed upstream
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=707199](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=707199)

Install the saucy package from [http://packages.ubuntu.com/saucy/libgnomeprint2.2-0](http://packages.ubuntu.com/saucy/libgnomeprint2.2-0)
or use Arch/Fedora. Debian maintainers don't care if removing libraries upstreams break your applications.

---

### Post by cpl3043usmc on 2014-09-19
Thanks for posting up those links, monkeybrain20122.  I was able to get the two libraries I needed on my laptop (running KUbuntu 14.04) and load Stata12.  You just made my thesis project easier.

---

### Post by cpl3043usmc on 2014-09-20
> **jfca283 said:**
> Hi
I did an upgrade in ubuntu.
I'm running 14.04 version.
Before i could work with stata.
But now i can't load the mentioned software.
Here is the output when i try to load it

[I]
PC:/usr/local/stata12$ ./xstata
./xstata: error while loading shared libraries: libgnomeprint-2-2.so.0: cannot open shared object file: No such file or directory[/I]

I looked for the library libgnomeprint and it doesn't exist on ubuntu 14.04 trusty tahr.
So, what can i do?
Thanks for your time and interest.

Did a little homework and came up with this:

1. Follow this link in monkeybrain's reply: [http://packages.ubuntu.com/saucy/libgnomeprint2.2-0](http://packages.ubuntu.com/saucy/libgnomeprint2.2-0)  <--- THIS LINK IS BROKEN!!!  Use [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and then search from there!

Scroll to the bottom and chose the XX-bit version you need.  i.e.: amd64 for the 64-bit version or i386 for 32-bit version.

2. Open up your terminal and get root user access -- I usually use sudo -s

3. Open up terminal window and do the following:[INDENT]
gedit /etc/apt/sources.list[/INDENT]

4. When the editor opens, scroll to the bottom and paste in the following:
[INDENT]
## This is for downloading the library necessary to run Stata12
## on KUbuntu 14.04.1 LTS
deb [[MIRROR URL]]("http://mirror.mcs.anl.gov/ubuntu") saucy main universe  <--- NOTE: Original mirror listed (Argonne National Lab) no longer hosts public mirror.  
[/INDENT]
[B]
NOTE:[/B] The http: mirror URL address can be one that is "better" for you based on geographical location/preference.


5. Save and close the editor.  Leave the terminal open!

6. Go to this website and follow the instructions for getting Stata up and running:
[INDENT]
[http://eduardgrebe.net/2012/10/installing-stata-12-on-ubuntu-12-04/](http://eduardgrebe.net/2012/10/installing-stata-12-on-ubuntu-12-04/)[/INDENT]

This site was recently updated for Ubuntu 14.04 and Stata 13.

I followed these instructions for putting Stata 12 on my laptop.  I am running Kubuntu 14.04.1 LTS and can now use Stata 12 without too much trouble.  I did have to run Stata's update query from the terminal version, but it carries over to the "window" version.

I hope this helps you with getting Stata running, if you haven't figured it out already.  Good luck!

---

