---
title: "Chrome Web Store Crashes Ubuntu 14.04"
date: 2014-10-08
forum: General Help
---

### Post by trip4 on 2014-10-08
Hello all,

I'm new to this Forum, so if I mistakenly post incorrectly please redirect me.

I have installed Ubuntu 14.04 on an old Dell Inspiron 1420.  All seems to be working quite well.

However, when using the Chrome browser to navigate to the Chrome Web Store Ubuntu completely freezes for about 10 seconds, and then the screen goes blank and the entire system is 100% unresponsive.  The only way back to the desktop is via a hard shutdown and reboot.

Not sure what to do to try to fix this.  As for now, I am unable to add any extensions to Chrome.  I'm quite new to unix and bash in general, so please feel free to be padantic :-)

Thank you for your kind help,

Trip

---

### Post by vasa1 on 2014-10-08
The Chrome Webstore is quite heavy on resources. Could you tell people a little more about your system? CPU? RAM? Graphics?

---

### Post by sammiev on 2014-10-09
This would likely help with your system info if you can run the below in Terminal.

```
lshw
```

---

### Post by trip4 on 2014-10-09
Thanks Vasa and Sammiev[[COLOR=#000000][/COLOR]]("http://ubuntuforums.org/member.php?u=628319"),

Yes, it's an 8 year old laptap running an Intel Core 2 duo at 1.5 GHz with 2 GB of memory and an Intel GM965/GL960 graphics card.  I'm using the standard Unity desktop.

This behvior is exhibited even if Chrome is the only application running at the time.

Any thoughts would be greatly appreciated.

Thanks again,

Trip

---

### Post by vasa1 on 2014-10-09
Please type **chrome://settings** in Chrome's address bar and hit **enter**.

Then go to the bottom of that page and click on **Show Advanced Settings**.

Then go to nearly the bottom of the new page and see if "Use hardware acceleration when available" is ticked. If it is, try the Web Store after you untick that setting and restart Chrome.

Also, do you have some sort of RAM and CPU monitor to let you see what is happening? What about other heavy sites like YouTube or Gmail Google Drive? Do they behave properly?

---

### Post by trip4 on 2014-10-09
Thanks Vasa!

Yes, hardware acceleration was the issue.  It's working fine now.  On a side note, CPU was running about 3.5% prior to loading the page.  With hardware acceleration on, the system froze so quickly that the monitor never changed.  With hardware acceleration off, CPU topped-out at about 80% for a few seconds and memory useage grew to about 50%.

Thanks again!

Trip

---

### Post by vasa1 on 2014-10-09
Great! If you're sure your problem is solved please see how you can mark it "solved": [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by tracejm on 2014-12-25
Just a quick note of thanks for vasa1.  This also solved my issue on very similar hardware.  (Acer Core 2 Duo system.)  A note for others experiencing this issue - in addition to Chrome webstore crashing, you may also observe Youtube crashing (or at least I did).

---

### Post by Blasman on 2014-12-29
Thanks for this.  This was the fix that was needed for my Dell Inspiron 1525.  Youtube would freeze my computer for about 5-10 seconds and then the display would go black, forcing me to hard reboot.

---

### Post by FRAGnat on 2015-01-04
Hello. I have some problem within two month. Previously I had Ubuntu 14.04 and my chromium crashed when the video in youtube is over. Also i have 100% crash when try to open some link in chromium webstore. Two days ago I bought new hard disk (SSD) and install new distributive linux (Linux Mint) but problem is not solved. I didn't copy any files from old system. Also I check my RAM and try to change strap. But it is not solved my problem again. Please help me 

Result lshw

[ATTACH]258992[/ATTACH]

---

### Post by nicomagliaro on 2015-01-29
Just to add, it's works for me as well as the GDM crash when attemp to view a youtube or access to chrome webstore.
After i disabled [COLOR=#000000]"Use hardware acceleration when available" in Settings, my Ubuntu stop crashing. I thinks it's a memory leak when trying to use graphic acceleration with dual core CPUs.

Br,[/COLOR]

---

