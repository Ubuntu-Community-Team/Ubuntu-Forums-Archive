---
title: "i want to pre-cache every file ..."
date: 2019-12-01
forum: General Help
---

### Post by Skaperen on 2019-12-01
i want to pre-cache every file in [COLOR=#0000cd][FONT=courier new]**/etc**[/FONT][/COLOR] and [COLOR=#0000cd][FONT=courier new]**/usr**[/FONT][/COLOR] into RAM, on systems with more than enough to do so (8GB and more), and lock it in to stay there.  i can read every file and that will get them into cache, but a lot of I/O buffering activity can bump a lot of that out.  another idea was to copy them to a ramdisk, but that is just duplication and using a file means 2 copies of it will be in RAM.  the goal is to have all the content of all these files to be in RAM, with a valid backing store to reload from in the rare event that a page gets modified by one process (the kernel reads in a new copy for all the other processes that have it mapped).  i also want to prevent these pages from being discarded (being unmodified makes them easy to "steal" since no swapout is required) when buffering demand gets high. **any suggestions?**  a reserved block of RAM might do this if there is a way to load mapped pages into it and make use of them there.

---

### Post by gnusci on 2019-12-01
You may need to create the directories etc and usr in RAM every time you system run, then copy the files and mount them before the system boot.

---

### Post by Skaperen on 2019-12-02
like i mentioned in my original post, that would be duplication.  there would be the copy in ramdisk,and the active cache copy when it gets run.

---

### Post by SeijiSensei on 2019-12-02
I think this would be difficult for /etc since it has to be available in single-user mode during boot. You'd probably have to create a custom initrd image as well. /usr might be more manageable since it is only mounted when the system goes multi-user.

I doubt you'd see enormous performance improvements over using an SSD drive.

---

### Post by #&amp;thj^% on 2019-12-02
All though I have not used this for a long time no,[ vmtouch]("https://hoytech.com/vmtouch/") seems like a good tool for the job.
Usage:
```
vmtouch -dl /whatever/directory/
```

---

### Post by Skaperen on 2019-12-02
vmtouch looks like a nice simple tool that will save one component of development.

what i am making may be booted from external media that i want to be able to remove or detach, ranging from an SD card to an AWS EC2 EBS virtual storage device.

---

