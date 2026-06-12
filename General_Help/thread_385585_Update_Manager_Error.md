---
title: "Update Manager Error"
date: 2007-03-15
forum: General Help
---

### Post by jsnelli2 on 2007-03-15
Whenever I run Update Manager, it pops up an error saying "not all updates can be installed.  Run a distribution upgrade, to install as many updates as possible.  This can be caused by uncompleted upgrade, unofficial software packages or by running a developmental version."   Whenever I click upgrade, it gives me an error that says 

"Error authenticating some packages

It was not possible to authenticate some packages. This may be a transient network problem. You may want to try again later. See below for a list of unauthenticated packages."

faad
ffmpeg
libavcodeccvs51
libavformatcvs51
libavutilcvs49
libfaad0
libmjpegtools0
libpostproccvs51

It then closes update manager.  If I go back in and hit close and ignore the first message about the distribution upgrade, it shows me four updates:
faad
ffmpeg
mjpgeg tools
transcode

They are all greyed out.  What do I need to do to fix this?  I have no idea where to begin.  All help is appreciated...I'm running Edgy Eft 6.10. 

Thanks in advance.

---

### Post by Kateikyoushi on 2007-03-15
Run this from the terminal.

```
sudo aptitude update
sudo aptitude dist-upgrade
```

---

### Post by jsnelli2 on 2007-03-15
Alright, thanks.  That worked...but I still can't install updates to mjpegtools and transcode.  They are the only two left in the update list.  They aren't grayed out anymore.  When I try to update I get the error message:

"E: /var/cache/apt/archives/libmjpegtools0_1%3a1.8.0-0.4_i386.deb: trying to overwrite `/usr/lib/libmjpegutils-1.8.so.0.0.0', which is also in package libmjpegtools0c2a"

---

### Post by DougieFresh4U on 2007-03-15
Just a thought, try:: **sudo apt-get -f install ** then ** sudo dpkg --configure -a** Worth a shot!! Good luck  :)

---

### Post by jsnelli2 on 2007-03-15
josh@josh-laptop:~$ sudo apt-get -f install
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libdc1394-13 libsvga1 libavformat0d libpostproccvs51
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
josh@josh-laptop:~$ sudo dpkg --configure -a
josh@josh-laptop:~$

Do I want to go ahead and remove them?

---

### Post by DougieFresh4U on 2007-03-15
> **jsnelli2 said:**
> josh@josh-laptop:~$ sudo apt-get -f install
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libdc1394-13 libsvga1 libavformat0d libpostproccvs51
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
josh@josh-laptop:~$ sudo dpkg --configure -a
josh@josh-laptop:~$

Do I want to go ahead and remove them?

Those have been upgraded  and it's telling you you can remove the older versions. Also it looks as though your immediate problem has not been solved or has it???

---

### Post by jsnelli2 on 2007-03-15
Well, the first problem was there was a list of downloads that were telling me they were authenticated and would not let me attempt to download them.  Now when I run the update manager it just lists to updates, but when I attempt to update them, it tells me "E: /var/cache/apt/archives/libmjpegtools0_1%3a1.8.0-0.4_i386.deb: trying to overwrite `/usr/lib/libmjpegutils-1.8.so.0.0.0', which is also in package libmjpegtools0c2a" and doesn't update them...leaving them in the list.

---

### Post by jsnelli2 on 2007-03-16
When I look at details I find an error saying "subprocess paste killed by signal (Broke pipe)

---

### Post by DougieFresh4U on 2007-03-16
Sorry for your problem your having. I am no expert in the problem you have so I shall hope a "guru" will step in and help you out :)

---

### Post by jsnelli2 on 2007-03-16
Ha, that's ok man.  You got me past the initial (main) problem.  It's more than anything down to a minor annoyance now.  I really appreciate your help.  I too hope that a guru will help :)

---

### Post by jsnelli2 on 2007-03-16
I ended up going into the Synaptic Package Manager and just removed the two programs... The problem came when trying to install dvd::rip debian file.  Any idea around having this problem?

---

### Post by Kateikyoushi on 2007-03-16
So that's why you got these errors.
Things can get messy if you try to use not ubuntu debs, try to stay away from them if possible.

---

### Post by jsnelli2 on 2007-03-16
If I go back through and actually compile dvd::rip myself it should work without a problem?  I didn't realize that a deb file could be not ubuntu.  Thanks for the input!

---

