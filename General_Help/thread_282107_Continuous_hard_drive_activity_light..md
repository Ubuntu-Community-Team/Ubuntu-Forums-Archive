---
title: "Continuous hard drive activity light."
date: 2006-10-22
forum: General Help
---

### Post by joemastro67 on 2006-10-22
On my IBM T40 the hard drive light shows continuous activity, even when the system should be idle. If I save a file or launch a program the light reacts normally. My problem is I don't think the drive is actually busy and I believe this is false reading. Is there a way in Ubuntu I can see what is actually being written or read to the drive? 

Thanks for your help.

---

### Post by MikeBenza on 2006-10-22
Does it happen all the time, or only once in a while for a few minutes?  If it's happens once in a while, that may be Ubuntu doing some tasks to keep itself running fine (i.e. checking the file system, updating aptitude sources, etc).

---

### Post by joemastro67 on 2006-10-22
The light is on steady all the time. The only time it blinks is when I'm saving or opening a file.

---

### Post by kent41 on 2006-10-22
> **joemastro67 said:**
> On my IBM T40 the hard drive light shows continuous activity, even when the system should be idle. If I save a file or launch a program the light reacts normally. My problem is I don't think the drive is actually busy and I believe this is false reading. Is there a way in Ubuntu I can see what is actually being written or read to the drive? 

Thanks for your help.

Right click on the **top panel**

Left click on **+add to panel**

Double click on **System monitor **in System & Hardware area
This will put a window on the top panel. You then can go into preferences and select hard drive and it will show you disk activity.

---

### Post by metalheart on 2006-10-22
Make backup of your important files and check your disk.

```
fsck -f
```

---

### Post by joemastro67 on 2006-10-22
Thanks Guys

I followed Kent41's advice and added a monitor, don't know why I didn't think of that. With the light on steady it reads 0% activity. If I move some files I get a reading, so at least I know the monitor is being truthful. Its not really a huge deal. With the light on steady I was a little concerned that it was writing to or reading from the drive continuously. It can't be good for it. 

I'll run file system check when I get good backup. The warning you get before you run it is pretty crazy.

---

