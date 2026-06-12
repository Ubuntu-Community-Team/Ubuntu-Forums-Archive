---
title: "dvd drive doesn't see Hollywood disk 16.04"
date: 2018-06-05
forum: General Help
---

### Post by Richard-S on 2018-06-05
In Ubuntu 16.04 I have installed and re-installed the following: 

sudo apt install libdvd-pkg
sudo dpkg-reconfigure libdvd-pkg

When I insert a Hollywood DVD, the machine doesn't recognize the drive. It works fine with data DVD's.

Richard

---

### Post by TheFu on 2018-06-05
> **Richard-S said:**
> In Ubuntu 16.04 I have installed and re-installed the following: 

sudo apt install libdvd-pkg
sudo dpkg-reconfigure libdvd-pkg

When I insert a Hollywood DVD, the machine doesn't recognize the drive. It works fine with data DVD's.

Richard

Commercial video DVDs have encryption.  Depending on your location, you may not want to break local laws.  [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs) is a how-to for this common question, assuming it is legal where you are.   

Note the troubleshooting section if there are issues. Not all DVDs will play because the makers add extra protections designed to break computer DVD drives, but not dedicated *dumb* DVD players.  Did you set the region?
I've had some luck using vobcopy to get an image, then work on that.

---

### Post by mc4man on 2018-06-06
Most likely your issue is hardware related. Commercial  DVD_VIDEO disks require drive to access the very inner ring area for dvd info, disk keys, ect. Some times drives that are  beginning to fail can't do this any more (particularly those cheap dvd drives found in laptops.

Structure protection found in some Commercial  DVD_VIDEO disks is mainly designed to prevent or imped dvd copying of those disks,  occasionally those protections make playback in unlicensed dvd playback players difficult to achieve.
Never heard or seen any protection that caused the dvd media  to be undiscoverable.

Edit: there is a very, very slight chance that if you have a Matshita dvd drive in a laptop & no or wrong region set that that's behind your problem. 
 This will show if the drive is matshita, look in *-cdrom section  for vendor:
```
sudo lshw -c disk
```

---

### Post by Richard-S on 2018-06-06
This problem occurs in both my machine and my wife's machine, both Ubuntu 16.04. Both were purchased here in Mexico. They are from different manufacturers.

I have looked into regionset. I can't quite get what they are saying in the readme.

Just unpack the package (you probably already did if you can read this file),
then call "make". ([COLOR=#ff0000]What does call "make" mean?) [/COLOR]After compiling, you'll find the binary "regionset" in the
directory which you should copy to /usr/sbin (as root, of course)([COLOR=#ff0000]All of the files in the extracted download are text files. There are no binary files.)[/COLOR]

How to use the programm
=======================
You need write access to the DVD drive, either by group or by being root. ([COLOR=#ff0000]What does this mean?)


[/COLOR]

---

### Post by TheFu on 2018-06-07
I doubt regionset will help.  It is most likely that the DVD disc has strong DRM on it and cannot be correctly read by any computer anywhere. It just depends on the title.  I keep a US$30 old DVD player around just to watch these discs.

The regionset is about DVD regions.  Different parts of the world have different regions, but you can set the region once or twice to be for a different location before it sticks usually.  The initial setting should be correct for where you purchased the DVD drive hardware. I have never used the regionset tool.

make is a tool to build code, usually C or C++.  On Unix-like systems, this used to be how software was delivered and we'd have to "make it" ourselves.  This [https://www.howtogeek.com/105413/how-to-compile-and-install-from-source-on-ubuntu/](https://www.howtogeek.com/105413/how-to-compile-and-install-from-source-on-ubuntu/) explains it better than I could.

There won't be any binary files until after you "make" it.

To modify hardware, the driver file connected to that hardware will need to allow the userid to "write" - normal Unix permissions is how Linux (and all unix-like OSes) handles that access.  That's what the last line is trying to say.  If you use sudo with the program, then that would provide "root" access and that should let the program write to the DVD player hardware.

---

