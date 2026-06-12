---
title: "ubuntu 6.06 so slooooow!"
date: 2006-12-22
forum: General Help
---

### Post by kerius on 2006-12-22
I've had Dapper Drake loaded on my machine for the past 9 months and I'm committed to learning as much about linux as possible (even the command line) in hope that I can totally abandon the Windows platform.  

There is, however, one thing I've been dealing with ever since I loaded it onto my machine.  It seems the performance is slower that I would have hoped it to be.  I was hoping there was someone who could troubleshoot this slowness issue with me.

_Here's what I know:_

System Hardware - Not exactly sure.  All components are about 8 years old.  I've added some RAM (probably about 500 megs total)

All software opens and performs slowly:
Firefox - 10+ seconds to open (I have DSL but it literally seems like dial-up)
Thunderbird - 10+ second to open
Open Office - 15+ second to open and very slow while saving
Games - anything that requires moderate animated graphics I can't run.

I've heard Kubuntu was faster but thought I would troubleshoot ubuntu first.

Some other posts mentioned the swap partition not mounting causing performance issues but that's beyond my expertise.  I'm willing to learn though.  Any help appreciated.

---

### Post by taurus on 2006-12-22
Need to know the spec of your machine especially your RAM and the amount of swap partition that you set aside!!!

```
free
```

---

### Post by kerius on 2006-12-22
Upgraded Ram to 512

             total       used       free     shared    buffers     cached
Mem:        646012     522876     123136          0      67852     278084
-/+ buffers/cache:     176940     469072
Swap:       939760          0     939760

---

### Post by jml on 2006-12-22
An eight year old computer, even with 512 megs of ram may not be robust enough for Ubuntu.  Gnome and the other applications you list are very resource intensive.  You might want to download and try Xubuntu.  It is both a live and install cd.  Its designed to run on machines with more modest specifications.

Joe

---

