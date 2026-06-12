---
title: "The search in Nautilus does not work"
date: 2007-09-13
forum: General Help
---

### Post by goldtech on 2007-09-13
The search in Nautilus does not work. 
Will it ever be fixed?

---

### Post by aysiu on 2007-09-13
Can you be more specific?

---

### Post by goldtech on 2007-09-13
Open Nautilus. Enter a know file in the field. Hit the search button - it finds nothing.

---

### Post by aysiu on 2007-09-13
Works for me. I'm using Ubuntu 7.04 (Feisty Fawn).

How recently was this "know[n] file" created?

---

### Post by FuturePilot on 2007-09-13
I think it only searches the current directory that you are in.

---

### Post by shoaibi on 2007-11-25
i agreed with FuturePilot and goldtech. I am using Gutsy and same bug is being faced, I can serach anything using nautilus, but the shell commands like locate and find works fine even without a updatedb command...

---

### Post by mikepee on 2007-11-28
Yeah Gutsy 7.10 does not search on mine either.  It's maybe the most annoying thing.  I plugged in a windows drive to take a file off to put into my Qemu Win2k install.  But NO!  the damn search tool is about as worthless as is "peace of mind." (if you need peace of mind go get your self a drill)

Other than that I'm pretty much in love with my Ubuntu.

Mike

---

### Post by LenardKoen on 2008-02-02
It doesn't work. It's bug, and same in Hardy alpha too. I can not believe that such important function isn't working.  
Link:
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/148701](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/148701)

---

### Post by _godbout_ on 2008-03-09
Same problem here.
I thought for a while that I was a bit stupid and didn't know how to use the function :D

Notice that if you search using the 'Search in Files' from the Places menu, it works. At least for me...

---

### Post by Oldsoldier2003 on 2008-03-09
> **_godbout_ said:**
> Same problem here.
I thought for a while that I was a bit stupid and didn't know how to use the function :D

Notice that if you search using the 'Search in Files' from the Places menu, it works. At least for me...
use find   or locate or the tracker search tool

---

### Post by ryanhaigh on 2008-03-16
There are workarounds for this such as the previously mentioned places > find files. You can also install nautilus-search-tool which provides a right click option to search the directory using the places>find files search application. I have also written a howto on recompiling nautilus without tracker support, it is not as hard as it may sound. 
[http://ubuntuforums.org/showthread.php?p=4524522](http://ubuntuforums.org/showthread.php?p=4524522)

---

### Post by mukarakaplan on 2008-04-10
> **_godbout_ said:**
> Same problem here.
I thought for a while that I was a bit stupid and didn't know how to use the function :D

Notice that if you search using the 'Search in Files' from the Places menu, it works. At least for me...

The same here.

---

### Post by bwang on 2008-04-12
Same here. This really should be fixed.

---

### Post by ryanhaigh on 2008-04-12
The method I have posted in the above mentioned thread is working great for me and a few others [http://ubuntuforums.org/showthread.php?p=4524522](http://ubuntuforums.org/showthread.php?p=4524522)

---

### Post by imtheguru on 2008-04-13
Disable tracker from Sessions.
Install beagle daemon and optionally the beagle search tool.
Run the daemon. Let beagle index your files for a bit.
Now you can search using Nautilus or the beagle search tool.

For a grand finale, install catfish and conduct searches using find, slocate or beagle.

Cheers.

---

