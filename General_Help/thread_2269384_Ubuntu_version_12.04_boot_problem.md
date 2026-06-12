---
title: "Ubuntu version 12.04 boot problem"
date: 2015-03-15
forum: General Help
---

### Post by LukeSykpe on 2015-03-15
Hello everyone.

I recently ran into a problem with booting up my Linux Ubuntu instance on my hard drive. The Ubuntu instance has been installed on a partitioned part of my hard drive, for about a year and a half now, without any problem. A couple days ago, while I was playing a game on it, the computer froze, and I was forced to reboot. After that, whenever I try to boot up ubuntu, all day yesterday, it would simply hang and keep displaying a purple screen indefinetely. When I tried to boot it up earlier today, the same happened, but now, a few hours later, I tried it again, and it displayed a black screen with the following text on it: 

"GNU GRUB version 1.99-21ubuntu3

Minimal bash-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.

grub>"

Nothing I do after that has any effect. 

Additionally, the freezing and having been forced to reboot from said game has happened several times in the past, without problems. Note that I do know it's not healthy for the OS to hard reboot the computer, but there was no other option after it froze. 

Finally, there is nothing too important that I can't recreate within a few minutes of work in the Ubuntu instance, so I don't mind it too much to wipe and reinstall. The only reason I haven't done so yet, is because I would like to somehow get the few "important" stuff there is, if there is a way to do so that I don't know of.

Thanks in advance for your help, Luke Sykpe.

---

### Post by Bashing-om on 2015-03-15
LukeSykpe; Well ..

The good thing is that you can still boot to grub. As you can get a grtub > prompt means grub is at least partially loading.
Can you get the grub boot menu on reboot ?
IF ubuntu is the only operating system installed, by default the grub boot menu is not displayed. 
Can you boot to the grub boot menu ? Try ->
Reboot and as soon as the bios screen clears depress and hold the right -shift- key. In the grub boot menu is the 'recovery' kernel .
Select this and in the recovery console is an option to check the disk by running a file system check.

What results after the check is completed ?
Are you able to boot normally now ?

As to a graceful way to restart the system; remember the Elephants.
Magic SysRq key method: hold down the Alt+SysRq keys and slowly run through the sequence R,E,I,S,U,B (Raising (E)lephants Is Surely Utterly Boring) - after the B, your system will reboot (or if you want to shut it down, make the last letter o). For systems without a SysRq label on the key, it's the Prt Scr key.
[http://en.wikipedia.org/wiki/Magic_SysRq_key#Uses](http://en.wikipedia.org/wiki/Magic_SysRq_key#Uses)
[http://unix.stackexchange.com/questions/31818/what-to-do-when-a-linux-desktop-freezes](http://unix.stackexchange.com/questions/31818/what-to-do-when-a-linux-desktop-freezes)


[INDENT][INDENT]it's 'buntu
[INDENT][INDENT]it's fixable
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by egeezer on 2015-03-15
At the grub >, you mighht try entering ls

If it works like grub rescue > does, you might get access to further information, or even prompts.

---

### Post by LukeSykpe on 2015-03-15
> **Bashing-om said:**
> LukeSykpe; Well ..

The good thing is that you can still boot to grub. As you can get a grtub > prompt means grub is at least partially loading.
Can you get the grub boot menu on reboot ?
IF ubuntu is the only operating system installed, by default the grub boot menu is not displayed. 
Can you boot to the grub boot menu ? Try ->
Reboot and as soon as the bios screen clears depress and hold the right -shift- key. In the grub boot menu is the 'recovery' kernel .
Select this and in the recovery console is an option to check the disk by running a file system check.

What results after the check is completed ?
Are you able to boot normally now ?

As to a graceful way to restart the system; remember the Elephants.
Magic SysRq key method: hold down the Alt+SysRq keys and slowly run through the sequence R,E,I,S,U,B (Raising (E)lephants Is Surely Utterly Boring) - after the B, your system will reboot (or if you want to shut it down, make the last letter o). For systems without a SysRq label on the key, it's the Prt Scr key.
[http://en.wikipedia.org/wiki/Magic_SysRq_key#Uses](http://en.wikipedia.org/wiki/Magic_SysRq_key#Uses)
[http://unix.stackexchange.com/questions/31818/what-to-do-when-a-linux-desktop-freezes](http://unix.stackexchange.com/questions/31818/what-to-do-when-a-linux-desktop-freezes)

[INDENT][INDENT]it's 'buntu[INDENT][INDENT]it's fixable
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Ubuntu is not the only OS installed, I also have Windows 7. When I turn my computer on, after the bios screen, I get taken to the OS selection menu, where I have a choise between either Ubuntu or Windows. I tried holding down the key both right after the bios screen clears, and before I get taken to the OS menu, but that did nothing, and, after that, I selected Ubuntu to boot up, and tried to hold the right -shift- key again, with, again, no effect. Either I am doing something wrong, or I can't boot to the grub menu.

Also, thanks for the reboot tip. I'll keep that in mind for future use :)

> **egeezer said:**
> At the grub >, you mighht try entering ls

If it works like grub rescue > does, you might get access to further information, or even prompts.

I did enter ls, and it gave me a little bit of information. I didn't write it down, so I can't remember exactly what it was, but if it's anything important, I can run it once more. Other than that, it didn't do much.



Also, some further info that I just remembered. As I said, yesterday, Ubuntu was simply hanging on boot, and was displaying a purple screen, while, today, I get the GNU GRUB screen. What happened was, when I booted up windows, the system ran an automated disk check on the partition I have Ubuntu on. While, before said check, I was getting the boot hang, after it, I get the GRUB screen. That disk check didn't display its results though, even after I rebooted, so I couldn't tell you much more about it.

---

### Post by Bashing-om on 2015-03-15
LukeSykpe; Well ..

Let's back up a bit, now I think it is best to 1st run a file system check on ubuntu.
To do that from terminal we need to know where on the hard disk ubuntu is installed to.
To do that the easiest way is to boot a liveDVD(USB) and provide the outputs of terminal commands:
```

sudo fdisk -lu
sudo parted -l

```
Between code tags please.

Once we have run the file system check/repair, we see what it will take to boot ubuntu and IF a (RE-)install of ubuntu's boot code is in order.

[INDENT][INDENT]it be a process
[/INDENT][/INDENT]

---

### Post by LukeSykpe on 2015-03-16
Is there not any other way to do that? 

Because I currently don't own either a flash drive, or any blank DVDs to burn Ubuntu into for a liveCD. If there's not another way, it'll just have to wait a few days, until I'm back home to go buy some DVDs.

---

### Post by Bashing-om on 2015-03-17
LukeSykpe; Hi !

Sorry for the delay in responding. Life has a way of getting in the way. A minor crisis in that our submershable well pump burnt out.
The focus of my attention and effort had been to restore water. All better now.

Maybe we can restore your system from the grub > prompt, maybe.
We have to find the location of the file system, and where the boot files are.
As egeezer advised we start with the results of grub command ls -al.
This list the partitions on the hard drive, then we need to find which partition contains ubuntu, then once this partition is identified, where the boot files are located.
So in small steps, what returns;
From that grub > prompt:
```

ls -al

```

If I were aware of the partition holding ubuntu I could advise of the 'ls' command to see the files, that will be our next exercise.
To identify the ubuntu partition.

[INDENT][INDENT]we can do this
[/INDENT][/INDENT]

---

### Post by LukeSykpe on 2015-03-19
So, I ran ls -al, and I got this:
```
 error: bad filename. 
```

Then, I ran just ls, as egeezer had suggested at first, and here is the result:

```
 (memdisk1) (loop0) (hd0) (hd0,msdos2) (hd0,msdos1) 
```

---

### Post by Bashing-om on 2015-03-19
LukeSykpe; OK;

Let's go hunting where grub's boot files are located. Then we try and boot the operating system from the grub > prompt.
Next step up the ladder of isolation, what returns:
From the grub > prompt:
```

ls (hd0,msdos2)
ls (hd0,msdos1)

```

[INDENT][INDENT]small steps, all my litlle mind can deal with
[/INDENT][/INDENT]

---

### Post by LukeSykpe on 2015-03-19
Both commands output 
```
 grub> error: bad filename. 
```

---

### Post by Bashing-om on 2015-03-19
LukeSykpe; Yuk ...

That to me indicates a corrupted partition table. In order to proceed further will require a liveDVD.
From the liveDVD we can look at the hard drive, and the state of the file system.
Will require a liveDVD or USB - of the same same distribution and release as that of the installed system.

[INDENT][INDENT]too soon toooo tell more
[/INDENT][/INDENT]

---

### Post by LukeSykpe on 2015-03-19
I'm traveling back home tomorrow, so I'll have a liveDVD up soon.

---

### Post by Bashing-om on 2015-03-19
LukeSykpe; Great;

We continue when you have the tools at hand.
Those grub commands should have had outputs. 
a situation of:
> 
error: bad filename.

clearly indicates partition table problems. Now we must have an alternate means to look things over, and see what can be done.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

