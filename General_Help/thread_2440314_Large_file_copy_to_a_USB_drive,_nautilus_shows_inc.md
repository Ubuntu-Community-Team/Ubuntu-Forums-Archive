---
title: "Large file copy to a USB drive, nautilus shows incorrect progress status"
date: 2020-04-08
forum: General Help
---

### Post by jgwphd on 2020-04-08
I have Ubuntu 19.10 with all the latest updates installed. I noticed that when I copy a large file, using Files (1.34.1-stable), to an external USB thumb drive, the copy progress status will typically say 100% complete and 0" seconds" left when it's not finished being stored on the thumb drive! If I try to unmount or eject the drive I get a message that the drive is still busy. After some time 10 minutes to 30 minutes or more depending on the file size I will get the message that it is ok to remove the drive. **All this time Files/Nautilus is showing 100% done with "0 seconds" left.** Clearly the file is still being written to the USB thumb drive, with some drives I can see the activity light flashing until completion. I don't mind waiting for the file copy to complete but I find the incorrect nautilus copy status to be confusing/wrong. Why say 100% and "0 seconds left" when clearly it is nowhere near finished and this does not provide any of the valuable information that I want which is information regarding how long I am likely to wait for completion. I suspect that most users like me are interested in how much of the file has been actually stored on the thumb drive and how long it will be until it is safe to remove the thumb drive. Is there a configuration "switch" that I can adjust somewhere to get more realistic information of copy status. Thank-you!

Best Regards
John

---

### Post by sudodus on 2020-04-08
Nautilus has done its job, but it has copied to a buffer in RAM. After that a slow writing process will continue, 'flushing the buffer' until everything is written. The terminal window command [FONT=Courier New]**sync**[/FONT] will tell the system to give some priority to the flushing process. The terminal window will not return to prompt until [FONT=Courier New]**sync**[/FONT] has finished.

If you [try to] unmount/eject the USB drive, it will first start [FONT=Courier New]**sync**[/FONT], and then finish unmounting the mounted partitions on the drive.

You may want to watch the process (flushing the buffers). Some time ago I made a shellscript for that purpose. If you are interested, see  [this link](https://unix.stackexchange.com/questions/554265/how-can-i-estimate-the-whole-time-of-a-write-process-including-sync).

---

### Post by jgwphd on 2020-04-08
I understand your work around (I'll probably try it). But I see a significant usability issue. Ubuntu is providing to a novice user (not a developer but someone who wants to get work done using Ubuntu) bogus information about the true status of a **copy task** to a thumb drive. You can say nautilus has done it's job ...but in reality it is reporting that the "copy task" is at 100% with 0 seconds left ...leaving the expectation that the thumb drive can be removed at any time (and I suspect that many users would just yank it out at that time). **This copy task status is simply not true.** Any user who plugs in a thumb drive to transfer some files is usually interested in when the thumb drive can be removed so he can transport the files away. The typical user is really not interested in system internals such that "nautilus has done its job". A user trying to accomplish a **task** such as copying a file to a thumb drive should be given accurate information about the status and progress of the **task**. Giving incorrect or caveat ridden geek-friendly status is a questionable practice. Besides your shell script, is there a configuration "switch" that I can adjust somewhere to get more realistic information of copy status. Thank-you again!

---

### Post by TheFu on 2020-04-08
We can watch the disk and RAM buffers being used with the **vmstat** and **free** commands.

---

### Post by jgwphd on 2020-04-08
I appreciate the answers. But giving caveat ridden geek-friendly status to novice users is a questionable practice (they will probably just yank the thumb drive out and later on complain about corrupted files). I think this usability issue makes Ubuntu look bad and provides ammunition to those who would say other systems are better! This should be changed/fixed.

---

### Post by TheFu on 2020-04-08
> **jgwphd said:**
> I appreciate the answers. But giving caveat ridden geek-friendly status to novice users is a questionable practice (they will probably just yank the thumb drive out and later on complain about corrupted files). I think this usability issue makes Ubuntu look bad and provides ammunition to those who would say other systems are better! This should be changed/fixed.

Sometimes, other systems are better, for some people.  This isn't an Ubuntu-specific thing.  it is a Unix thing.
Feel free to open a bug about it with the "Files" tool.

BTW, nobody here works for Canonical.  Everyone is a volunteer.

---

### Post by jgwphd on 2020-04-08
I sincerely appreciate the efforts of all the volunteers. One more question ...maybe my memory is bad but I don't remember this being an issue till recently. I have been an Ubuntu user for over 10 years and I am just noticing his now. Maybe files are bigger these days, but everything else is getting faster. Did something change in nautilus recently that exposed or more clearly reveal this usability issue? ....the amount of time that Nautilus sits there at 100% with 0 seconds left is truly remarkable. It must by 95% of the entire copy task time.

---

### Post by sudodus on 2020-04-09
Your observation is correct and I have seen it too. RAM is bigger and processes are buffering in RAM more aggressively in recent computers with recent versions of linux operating systems. Be aware that also Windows uses this feature and for that reason you must 'remove the USB drive safely' or your data on it might get corrupted also in Windows.

For this reason I check flushing the buffers in the new tool to create USB boot drives, [mkusb-plug](https://help.ubuntu.com/community/mkusb/plug). If you install mkusb-plug, it will bring the shellscript **watch-flush**, that you can use as a stand-alone program, or use it via the zenity GUI as I use it in mkusb-plug. **watch-flush** is a slightly improved version of the script in the link in post #2.

It would certainly be possible to do it also in Files alias nautilus, but unless you want to unplug the drive at once it is better to detach nautilus from the write process when it has done its job, so that you can do other things with it, and the write process can continue in the background. So there are pros and cons.

I see your point about newbies and **if you take the time to write a bug report at Launchpad, please link to it from here, and I will confirm it by marking that it 'affects me too'**. (Bug reports are the way for us to communicate with the developers - not only to report bugs but also to ask for new or improved features).

---

### Post by jgwphd on 2020-04-09
Thanks for the information, sudodus. I have never done a bug report before, maybe its time to get more involved. Can you please  give me a pointer to the correct web page for this problem (that way I'll know I am in the right place for the correct developers to see the report) and I'll do the bug report and post/link to it here. Many Many Thanks!

---

### Post by sudodus on 2020-04-09
You are very welcome to join us as an active member :-)

[help.launchpad.net](https://help.launchpad.net/) should be a good starting point.

You need a user ID at Launchpad and I think it helps to read and sign the Ubuntu [code of conduct](https://ubuntuforums.org/misc.php?do=showrules).

It may seem overwhelming in the beginning, but there are people here that can help you.

[hr][/hr]
To start reporting a bug when Ubuntu works but there is a program package that fails or needs improvements:

Start a terminal window and type

```

ubuntu-bug package-name

```

if you know the name of the affected package. See [FONT=Courier New]**man ubuntu-bug**[/FONT] for more details.

In your current case I think 'nautilus' is the name of the program that is started by the desktop file 'Files' and also the name of the package. Sometimes the name of the package is different from that of the program. You can ask here if you need help with that later on. So

```

ubuntu-bug nautilus

```

and follow the instructions ...

The more details you provide the better. But the first description should be rather short, like a summary, and you can add details in comments later on.

You can tell people here (and the next bug in a new thread) at the Ubuntu Forums (via a link) that you have created a bug report (and why you want us to confirm it and/or write comments).

---

### Post by jgwphd on 2020-04-09
Bug report created: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1871869](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1871869)  Please confirm the bug report that you also find this behavior confusing to novices users and agree this is a serious usability issue. Thank-you!

---

