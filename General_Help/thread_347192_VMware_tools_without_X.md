---
title: "VMware tools without X"
date: 2007-01-26
forum: General Help
---

### Post by tfunky on 2007-01-26
Hello,

I could use some pointers on getting VMware tools running.

I've installed ubuntu 6.10 (server)  in vmware 5.53 on winXP pro.  

I've got to point where you've ran through the vmware-toolsconfig.pl file and accepted the defaults.

This is my first experience with Edgy, so please forgive me is this is a dumb noob question, but...

How do I start vmtools (and then have it stat at boot) without xwindows installed?

all the directions I find state to run vmware-toolbox and change you settings, etc from there :(

Can someone point me in the right direction to make this work on a server install without xwindows?

Thanks so much (in advance) for your help!!!!!

Tfunky

---

### Post by f0rmula on 2007-03-05
1. Click VM -> Install VMware tools from the server console, which will seemingly do nothing.  It hasn't done nothing.  It's effectively put the VMtools CD in the cdrom drive.  

2. As root run "mount /cdrom".

3. cd /cdrom

4. Then untar and install the tar.gz file you find on the cdrom.

This isn't obvious.  It seems like clicking "Install VMWare tools" does nothing, when infact it does work.  What they don't say is if you're not in xwindows, you'll have to manually mount the cdrom drive.

James

---

