---
title: "Running Wine from existing Windows partition?"
date: 2006-11-08
forum: General Help
---

### Post by temcat on 2006-11-08
Hi folks,

several years ago I could run some Windows programs in Linux using Wine **from an existing Windows partition**. Wine has undergone a lot of changes since that time, and I can't see this method mentioned in any recent Wine HOWTO. Is it still possible? If it is, how do I set it up? (I plan to have a separate FAT32 partition with Win98SE specifically for that purpose.) The reason I want to do that is that the app I need for my work, namely Trados computer aided translation program, won't work properly when installed under Wine.

---

### Post by YokoZar on 2006-11-10
It's not really something that is done anymore.  However, you can still use individual windows DLLs - perhaps running the program and seeing what errors the terminal spits out can help guide you to picking the native ones you still need.

---

### Post by CatKiller on 2006-11-10
As I understand it, it's not a method that will work well. If a program has written stuff that it needs to the Windows registry, it won't be included in the pretend Wine registry. So then the program will complain, not work, or not work properly. There may be ways round it, but it's probably best to either use native .dlls as needed, as YokoZar suggests, to get the program working after it is installed through Wine, or use some kind of Virtual Machine environment like all the cool kids are doing these days, or just boot Windows if you want to run a Windows application.

Or find a different application that does a similar thing.

---

### Post by the8thstar on 2007-10-07
Can you actually copy your Windows registry on the Windows partition and paste it into Wine's on the Ubuntu partition?

---

### Post by kellemes on 2007-10-07
Maybe your app. will work in a vm?
[VirtualBox]("http://www.virtualbox.org/")

---

