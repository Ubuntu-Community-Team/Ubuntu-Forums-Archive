---
title: "Somethings not visible in Lubuntu Software Center"
date: 2014-11-23
forum: General Help
---

### Post by jim1944 on 2014-11-23
Just installed Lubuntu 14.04 LTS on some older hardware. The main problem is that when I run some apps, like Lubuntu Software Center, some of what is trying to be displayed is not visible. For example, in the first attachment screen shot none of the icons are visible except that the icon for Universal Access has a sliver that is visible. I can get the icons to become visible, although sometimes only briefly, by moving my mouse over the app (Screen shot 2). Another example is in the third screen shot where the list of Office apps is invisible (or almost invisible - you can see a very, very light list of apps. Again, I can get them to be visible briefly by scrolling the list.

I also saw similar behavior with the installer. I could not see the list of languages until I touched the scroll bar. I also could not see whether check boxes had been checked or toggle buttons toggled.

Not seeing this in other apps like Firefox but, then, I haven't done a whole lot of poking around yet to see what apps are/are not affected.

Any ideas about what is causing this and how to fix it?

Thanks
Jim[ATTACH=CONFIG]258149[/ATTACH][ATTACH=CONFIG]258150[/ATTACH][ATTACH=CONFIG]258151[/ATTACH]

---

### Post by mörgæs on 2014-11-23
Could you check if it's the same in a live boot of 15.04, please?

---

### Post by ajgreeny on 2014-11-23
Assuming you did the install with either a DVD or USB, did you check the iso file's md5sum before burning.
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

If you've already done that, tell us more about the hardware, particularly the graphic card.

---

### Post by vasa1 on 2014-11-23
> **jim1944 said:**
> Just installed Lubuntu 14.04 LTS on some older hardware. ...

Not seeing this in other apps like Firefox but, then, I haven't done a whole lot of poking around yet to see what apps are/are not affected.

Any ideas about what is causing this and how to fix it?
...
Even though the Lubuntu devs do their best to provide for old hardware, some people still have difficulties. 
You'd get a better picture by trying out a lot of GUI-based programs and seeing if similar things happen.

And giving details of the older hardware would help as well: graphics card, RAM, CPU would be good starters.

---

### Post by jim1944 on 2014-11-24
Replying to a couple of things:

I verified the md5sum.

This is the output of the hardware checking suggested by the "Old hardware brought back to life" thread:

jim@jim-desktop:~$ sudo lshw -C cpu | grep sse2
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pebs bts
jim@jim-desktop:~$ sudo lshw -C cpu | grep -i width
       width: 32 bits
jim@jim-desktop:~$ sudo lshw -short -C memory | grep -i system
/0/1c                       memory      768MiB System Memory
jim@jim-desktop:~$ lspci | grep -i vga
01:00.0 VGA compatible controller: NVIDIA Corporation NV20 [GeForce3] (rev a3)
jim@jim-desktop:~$ 

I know my motherboard will not support any more memory.

Still need to do more poking around to see what other apps are affected. Will try 15.04.

I tried running the CD on newer hardware and did not see the problem. 

Thanks Jim

Thanks
Jim

---

### Post by mörgæs on 2014-11-25
Thanks. A faulty CD and/or ISO is almost never the explanation. If it's faulty it does not run, the problem is not that it displays a partly working GUI.

My guess is that you will see the same for 15.04, but please confirm when you have done the test. It's likely a problem with drivers for the old Nvidia as mentioned in the thread.

---

### Post by jim1944 on 2014-11-25
I ran 15.04 and did _**not**_ experience the problem using Ubuntu Software Center (does not appear to be an Lubuntu 15.04 available yet). So I tried Ubuntu 14.04 and ran its Ubuntu Software Center and did experience the problem. Have not tried any 14.10 yet.

But now I am having a more serious problem: can't boot after the latest updates. But that's a subject for another thread.

Thanks
Jim

---

### Post by jim1944 on 2014-11-25
I am seeing this invisibility problem in Firefox. In particular note the invisible icons above where I am typing in the screen shot attached.

Will try same with 15.04.

Thanks
Jim[ATTACH=CONFIG]258203[/ATTACH]

---

### Post by mörgæs on 2014-11-25
Lubuntu (development version) is here: 
[http://cdimage.ubuntu.com/lubuntu/daily-live/current/](http://cdimage.ubuntu.com/lubuntu/daily-live/current/)

---

### Post by vasa1 on 2014-11-25
> **jim1944 said:**
> I am seeing this invisibility problem in Firefox. In particular note the invisible icons above where I am typing in the screen shot attached.
...
I see something very similar when I have Adblock Plus and a stylesheet applied. If I disable both, all images appear. I've been seeing this ever since the forums upgraded their forum software. So it's not Lubuntu 14.04 but at least two previous versions of Lubuntu. Firefox isn't a good example to help examine your case. Please try some other program. What about Abiword or gnumeric?

---

### Post by jim1944 on 2014-11-25
I do not see the problem in either the software centers or on this formum in either Lubuntu 14.10 or 15.04. So I have only seen this invisibility problem in Lubuntu and Ubuntu 14.04.

In Ubuntu 14.04 I also see the problem in the live CD welcome screen where you can either install or try: the list of available languages is invisible until you do some scrolling. Lubuntu uses a different sort of display to select a language and there is no problem with it in any version I have tried.

Probably won't get much time to poke at what apps I see the problem in until next week - what with Thanksgiving.

One additional item: in 14.04, viewing this forum in Firefox, when you go to press the "Submit Reply" button (you just have to hover the mouse over the button), it disapears (becomes white) and the "Submit Reply" text becomes some kind of faint aqua. Does not happen with the other versions.

Thanks
Jim

---

### Post by mörgæs on 2014-11-26
It's a pleasant surprise that the developers have already fixed the bug.
Time for marking the thread 'solved'?

---

### Post by jim1944 on 2014-11-26
> **mörgæs said:**
> It's a pleasant surprise that the developers have already fixed the bug.
Time for marking the thread 'solved'?

Do we know what fixed it? If we don't know, how can we be assured that it won't be inadvertently reintroduced? Shouldn't whatever did fix it be applied to 14.04 LTS? Am I the only one who has experienced this problem?

Thanks
Jim

---

### Post by mörgæs on 2014-11-26
What fixed it was likely changes to the kernel introduced in 3.16 which is used in 14.10. The changes are passed on to 3.18 used in 15.04.

Some day 3.16 could be transferred into 14.04, and if it happens it will be interesting to see the results.

---

### Post by vasa1 on 2014-11-26
> **jim1944 said:**
> ... Am I the only one who has experienced this problem?
...
I try to keep up with Lubuntu stuff and haven't come across others with this issue.

---

### Post by jim1944 on 2014-11-27
OK, I'll mark this one solved because it is no longer a problem in 14.10. Since no one else is seeing this, there would not be anyway to regression test to make sure that it hasn't recurred unless I donated my machine to the cause. It's a machine my son and I built around 2001.

Jim

---

