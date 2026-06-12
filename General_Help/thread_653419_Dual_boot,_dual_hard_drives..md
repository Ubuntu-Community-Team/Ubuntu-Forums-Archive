---
title: "Dual boot, dual hard drives."
date: 2007-12-29
forum: General Help
---

### Post by kelasia on 2007-12-29
I, before I start, have read other posts on this subject, but they don't seem to answer my problem.

I just recently bought a 750gb hard drive, SATA. It is currently hard drive number two, at least that's how my BIOS sees it. It's what I have Ubuntu on (7.10). No partitions. I want Windows XP on my old 150gb hard drive, which is being read as hard drive 1. I formatted both hard drives via "delete" in Gparted from Ubuntu's live cd. Loaded XP just fine, booted into it and loaded my Nvidia drivers. I then loaded Ubuntu onto my 750, and that loads beautifully, no problems. I have the boot order set to look at the 750, with Ubuntu on it, THEN XP. I have yet to set up the Grub to see XP (I'd like a little help with that as well, if it isn't too much trouble.). But now that Ubuntu is loaded, whenever I select XP from my one time boot manager, XP gives me a "Error loading operating system." error and just stops there.

I can set up a dual boot on one hard drive with ease, but throw another hard drive in the mix and I'm gone.

For those who "tl;dr"'d this post, the gist is: I need some help getting Ubuntu 7.10 and Windows XP to dual boot, via grub, on two hard drives.

---

### Post by meierfra on 2007-12-29
To help you  I need some information. Open a terminal (Applications->Accessories->Terminal) and post the output of

```
sudo fdisk -l
```
and

```
 cat /boot/grub/menu.lst
```
(both "l" are lowercase L)

Just to make sure that  I  understand the situation correctly.
You are able to boot into ubuntu?
But neither picking Windows at the Grub Menu nor changing the  boot order lets you boot into Windows?
Or  does Windows not even appear on the Grub menu?

---

### Post by kelasia on 2007-12-29
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19456   156280288+   7  HPFS/NTFS

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe3c71a0b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       90444   726491398+  83  Linux
/dev/sdb2           90445       91201     6080602+   5  Extended
/dev/sdb5           90445       91201     6080571   82  Linux swap / Solaris

```

Is the output of the first command you gave me.

And, 
[http://rafb.net/p/pggiTE36.nln.html](http://rafb.net/p/pggiTE36.nln.html) 
is the output of the second. (It was just, in my experience, much too long to post to a forum, eye rape, etc.)

I am able to boot into Ubuntu easily, I'm in it at the moment.
I don't have my grub set up to boot windows, but changing windows to the first boot gives me the aforementioned error, as does picking it as a one time boot.

---

### Post by meierfra on 2007-12-29
To add Windows to the grub menu:

```
gksudo gedit /boot/grub/menu.lst 
```

add this to the end of the file:

title Windows  XP
root (hd0,0)
chainloader +1

Save the file, reboot and see whether you can boot into XP.

But it seems that grub is actually installed on the Windows drive.
Let me know  if you would like reinstall grub to the Ubuntu drive.

---

### Post by kelasia on 2007-12-29
I see the windows XP entry and am able to select it, but:

"NTLDR Missing.
Press Ctrl+Alt+Delete to restart."

happens to me.

I installed Ubuntu second, and grub loads from my ubuntu drive, so I don't see how it got into windows...
If that is the case, then yes, I would like to reinstall grub to my ubuntu drive.

---

### Post by meierfra on 2007-12-29
Well, your menu.lst says  "root (hd1,0)" under the Ubuntu title. Grub starts counting at zero.   and (hd1,0) means first partition on second hard drive. For Grub the first hard drive is always the one you are booting from. So this means that Ubuntu is not on the drive you are booting from.

This of course contradicts that you have been telling me.  But I believe you, so I would guess that  your hard drives are somehow   plugged  in  wrongly, or that some setting in your bios are messed up.  (but I'm not an expert in such matters)


Try this:

title Windows XP
rootnoverify (hd0,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1


This really is not supposed to work, but I'm hoping that two wrongs give a right.
If this did not work,   remove the two map lines again.

Then I suggest that you look at the way your hard drives are plugged in.
And at the setting in your bios.
You might see what happens if  you remove one of the drives.

---

### Post by kelasia on 2007-12-30
It didn't work. It hung up on "Starting up...".
I'm sure however that my smaller hard drive, with windows on it, is hard drive one, and that I installed ubuntu second, cause XP wouldn't install because it wanted to add a file to my ubuntu drive, but couldn't because it's not a "windows compatible" drive. 

Perhaps if I switched where the two drives plugged in?

---

### Post by meierfra on 2007-12-30
> Perhaps if I switched where the two drives plugged in?

?????


Actually before you start messing with cables and bios setting it might be better to install grub to the ubuntu partition.  That will reduced the chances that you suddenly won't be able to boot into ubuntu. Give me a few minutes to write  up instructions.

---

### Post by kelasia on 2007-12-30
I think I understand what you mean now, how grub isn't on the actual ubuntu drive, seeing as how NTLDR, windows' boot loader is missing...
Reinstalling grub to the ubuntu drive would remedy this?

---

### Post by meierfra on 2007-12-30
> Reinstalling grub to the ubuntu drive would remedy this?

I don't know. But it will be easier to get Windows to boot, if Grub is not on the MBR of the Windows drive.  

Here are the Instructions:
(Do you have a Ubuntu LiveCD? If things go wrong, you might not be able to boot into Ubuntu after  you carried out these instructions)



Step 1 Edit menu.lst

```

cd /boot/grub

sudo cp menu.lst menu.lst.backup

gksudo gedit menu.lst
```

This creates a backup of "menu.lst" and  opens  "menu.lst"
Look for the line 

#groot (hd1,0)

change it to

#groot (hd0,0)

Change the Windows item to

title Windows XP
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

Save and close the file.

To complete Step 1, go back to the terminal and type
```
sudo update-grub 
```

Step 2:  Install Grub to the MBR of the Ubuntu drive

In the terminal type:
```
 sudo grub 
```

and at the "grub>" prompt

```
root (hd1,0)

setup (hd1)

quit
```


Step 3 Restore the MBR of the Windows Drive.

If you do not  have the "universe" repositories enabled:
Go to Systems-> Administration->Software Sources"
Click on the Box next to "Community-maintained Open Source Software (universe)
Click on Close (twice)

Next in a terminal type:

```

sudo apt-get update

sudo apt-get install ms-sys

sudo ms-sys -m /dev/sda 
```

Reboot  from the Ubuntu Drive and reboot  again from the Windows Drive. If the Grub Menu appears try Windows and Ubuntu.

---

### Post by kelasia on 2007-12-30
> **meierfra said:**
> Reboot  from the Ubuntu Drive and reboot  again from the Windows Drive. If the Grub Menu appears try Windows and Ubuntu.

You want me to let the bios boot take it's course, or try to boot both hard drives through the one-time boot manager?

---

### Post by meierfra on 2007-12-30
> You want me to let the bios boot take it's course, or try to boot both hard drives through the one-time boot manager?

try it all.

---

### Post by kelasia on 2007-12-30
I didn't try to let it boot in order, though number two was ubuntu anyways (CD drive is boot number 1.), which I'm back into. Windows was still complaining of NTLDR missing, but I am able to get back into Ubuntu.

Let the record show that I'm completely fine with formatting either drive and redoing everything in a different way than how I did it, so long as XP and ubuntu stay on the drives I want them on and will boot.

---

### Post by meierfra on 2007-12-30
You definitely don't have to reinstall Ubuntu. I don' t know whether reinstalling Windows would make a difference. So I'm hesitant to recommend that at this stage.


Let's see whether you can access the Windows partition from Ubuntu (just to make sure that there is nothing wrong with it)

```
mkdir XP
sudo mount -t ntfs /dev/sda1 XP
cd XP
ls 
```

That should  list all the files and directories on you Windows XP  C:\ drive

Try  booting from the Windows drive. (one time boot, change the boot order)


If you still can't  boot into Windows, I suggest to run "fixboot" from the recovery console of the Windows CD. If you don't have a Window CD, get Supergrub (see my signature)

---

### Post by meierfra on 2007-12-30
I fixed a typo in my previous post (it needs to be /dev/sda1)

---

### Post by kelasia on 2007-12-30
I got to:

```
sudo mount -t ntfs /dev/sda1 XP
```

and:

```
NTFS signature is missing.
Failed to mount '/dev/sda': Invalid argument
The device '/dev/sda' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
```


I can, however, see the 149.0gb disk when I go to Computer, and can access it and play around with it.


Edit while still posting: Alright, I got what you told me to do to work.

I am unable to reinstall XP, it doesn't like my ubuntu ext3 drive being there.

Maybe if I redid each drive one at a time, unplugging the one I'm not setting up, then set the ubuntu drive to be the first hard drive to boot and configured grub from there?
I'll try to run the fixboot from my CD, if I can find it. I'll let you know how that works out.

---

### Post by kelasia on 2007-12-30
Yeah, windows is really missing that NTLDR. I'll try fixboot.

---

### Post by meierfra on 2007-12-30
Don't reinstall Ubuntu.That is  an absolute waste of time.There is nothing wrong with Ubuntu. This is what I would do:


1) Try booting from the Window Drive.

If that did not work: Physically disconnect the Ubuntu Drive and

2) Try to boot windows.

if failed:

3)   Run fixboot and fixmbr from the Windows CD.  (or SuperGrub CD)

if failed

4)  Reinstall windows  (Still with the Ubuntu drive disconnect)

---

### Post by kelasia on 2007-12-30
Failed boot, tried fixboot and fixmbr and it still says NTLDR is missing.

I'll go ahead and disconnect my ubuntu drive and try reinstalling XP.

---

### Post by meierfra on 2007-12-30
Just   two steps 2 and 3 after disconnecting the Ubuntu drive and  before reinstalling.  (won't take  long)

---

### Post by kelasia on 2007-12-30
(On a different computer.)

Right now XP is reinstalling.
What I'm thinking I might end up having to do is let my bios handle what drive I boot from, try not to have either drive messing with eachother/loading one another.

But to do that I'll have to finish reinstalling XP, and correct all the lil modifications I've made to ubuntu, one drive at a time.

Edit: At least that's how I see it working in my mind; if neither drive is aware of the other when they are being set up, they shouldn't interfere with eachother and I'll be able to just select where to boot from the one time boot manager.

---

### Post by meierfra on 2007-12-30
Please do  not change anything on the Ubuntu drive.  You can plug in right now by it self and it will boot,  It will also boot if you add the Windows drive
And it is not interfering with Windows in anyway.

---

### Post by kelasia on 2007-12-30
Alright, I won't touch Ubuntu. But will the way I am describing it work?

In theory it should.

---

### Post by meierfra on 2007-12-30
> Alright, I won't touch Ubuntu

Sorry, for my plea. But we worked hard today to get Ubuntu to be independent from the Windows  drive. I didn't want you undo it.

> But will the way I am describing it work?

I think so,  And even better, you might be able to boot XP from the Grub Menu.

---

### Post by kelasia on 2007-12-30
That's alright, I understand.

Anyways, XP is still working on formatting the drive. In retrospect, I should have selected the quick format. 
Once I get that set up and get ubuntu plugged back in, I'll reconfigure grub to see XP, since after you had me update grub, the XP entry was deleted. Happened to me on my single HD dual boot. Grub kernel update, was it?

---

### Post by meierfra on 2007-12-30
The reason it got deleted is that you put it in the wrong place. It needs to be at the very end of the file. 

Use 

title Windows XP
root(hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

and make sure it is after the line:

### END DEBIAN AUTOMAGIC KERNELS LIST

Otherwise it will be deleted by "update-grub" as you already noticed. And every time Ubuntu updates the kernel, it runs "update-grub"

---

### Post by meierfra on 2007-12-30
Make sure that you successfully boot into   XP before you reconnect the Ubuntu drive.

---

### Post by kelasia on 2007-12-30
Oh it has to go after? Alright, that's good to know.

Ok, XP is done with it's thing, I'll plug ubuntu back in and reconfigure my boot order then test each drive. If XP will boot, I'll go back into Ubuntu and replace that entry and let you know how it goes.

---

### Post by kelasia on 2007-12-30
Alright! Windows boots with no problem, Ubuntu still boots with no problem, and grub sees and load up windows! Thank you very much for the help!

---

### Post by meierfra on 2007-12-30
> thank you very much for the help!

You are welcome, glad to be of help.

---

