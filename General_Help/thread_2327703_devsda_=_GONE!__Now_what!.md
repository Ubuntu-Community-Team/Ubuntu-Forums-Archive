---
title: "/dev/sda = GONE!  Now what!?"
date: 2016-06-13
forum: General Help
---

### Post by wintry on 2016-06-13
My computer has been super glitchy recently, It started dropping me into an *initramfs* screen.  So I did a fsck on /dev/sda and it did it's thing, I clicked yes to ignore and fix accordingly.  It was a lot of yes-es.  Now, My partitions are gone.  all gone.  When I tried a reinstall from a disc (which is how I'm writing this now) it said I had 0.0b on this computer and /dev/sda1-2-5-6-7 were not usable. 
 I've done a couple of installs of different distros, and was running a lubuntu and ubuntu studio on this machine for a while.  

I should also mention an i/o error was occurring during the booting process. What does this mean?  Now, when I boot the computer "normally" it drops me into Grub rescue mode.

I know this post is all over the place...I'm sorry... I wish I had one thing to ask, but I want to know more, and I want to solve this and combat the planned obsolescence of our society/tech world.  

Thanks for fighting the good fight and helping me through this.  I haven't found anything quet like it on the forums..

Wintry

---

### Post by QIII on 2016-06-13
Was the device (well, a file system) mounted when you ran fsck?

---

### Post by wintry on 2016-06-13
I don't know.  I think so. What would it look like if it was or wasn't?  

 Thank you for your swift reply.

---

### Post by QIII on 2016-06-13
Were you running Ubuntu at the time?  That is, running from your installed Ubuntu?  Is it installed on sda?

---

### Post by wintry on 2016-06-13
yes I was.  Yes, It was installed on sda.

---

### Post by QIII on 2016-06-13
And the warning you ignored said something about how fsck would damage or destroy a mounted filesystem?

Did you have any files that were important to you?

---

### Post by wintry on 2016-06-13
Weellll. I don't recall it saying damage or destroy a mounted file system.  I feel like I wouldn't have gone beyond that.  but maybe I did.  It's all a blur. :confused:

No files that were important...no.

---

### Post by QIII on 2016-06-13
OK.  This is one of those hard-knock lessons about Linux.  Luckily you didn't lose all of your wedding pictures and all the pictures of the dogs at the beach.  :)

I don't usually like to suggest reinstalling as the first course of action, but this is one of those times.  To prepare for that, install gparted in a live session and remove all the partions from the sda.  That should leave the drive unallocated and allow you to install.

If you don't know how to use gparted, let us know.

---

### Post by wintry on 2016-06-13
does that mean I'm knocked up?  :-D  I see a pattern in my life that I have to destroy something to understand it... then rebuild.  such a human conundrum.

Fresh install sounds great...SO I have gparted in my live session now, and there are three partitions, none of which say sda.

They say the following:

/dev/sr0p1   unknown    4.00 KiB
unallocated  unallocated  2.56GiB
/dev/sr0p2  Unknown  2.31 MiB

I know for a fact that my hardrive has 250 GB. I'm pretty sure the above is referring to my CD drive correct?  So...now what?  gparted isn't talking to my computer?  My compu is mucked up from the hardware?

---

### Post by X-RED_Tech on 2016-06-13
GParted has a drop down menu to select the drive. You should find your 250GB HDD there.

---

### Post by QDR06VV9 on 2016-06-13
You just use the live installer to use the whole disk.
Which will make the necessary partitions.

---

### Post by wintry on 2016-06-13
nothing in the drop down but /dev/sr0  (2.56GiB).  :-(

I see the dropdown.  Nothing in it but /dev/sr0 (2.56Gib)  :-(

When I use the live installer, It says that I need 8GB of space and that I have 0.0KB.  So nothing to partition anywhere...

---

### Post by QDR06VV9 on 2016-06-13
Well now i would just download the Gparted iso from here: [http://gparted.org/download.php](http://gparted.org/download.php)
Boot to that and try again to find the hard drive && format the disk.
I would suggest using a ext4 format.

---

### Post by X-RED_Tech on 2016-06-13
well, unless something is wrong with the drive itself it should make no different running GParted from Ubuntu disk or directly with the Gparted boot CD/USB.

Have you by any chance changed or tried to change BIOS/UEFI settings? Does the drive show up in BIOS/UEFI now?

---

### Post by wintry on 2016-06-13
> **runrickus said:**
> Well now i would just download the Gparted iso from here: [http://gparted.org/download.php](http://gparted.org/download.php)
Boot to that and try again to find the hard drive && format the disk.
I would suggest using a ext4 format.

Still won't talk to my computer. Did I delete a /dev/SDA? IS that possible?

---

### Post by QIII on 2016-06-13
Have you used the drop-down (arrow towards the top right) to choose a different device?

---

### Post by wintry on 2016-06-13
> **X-RED_Tech said:**
> well, unless something is wrong with the drive itself it should make no different running GParted from Ubuntu disk or directly with the Gparted boot CD/USB.

Have you by any chance changed or tried to change BIOS/UEFI settings? Does the drive show up in BIOS/UEFI now?

Good Question!  

my boot menu has the following:
ATAPI CD-: Optiarc DVD RW etc...
ATA HDD0: ST9250410AS
PCI LAN: IBA GE Slot etc...

When I boot from HDD0, it drops me into:
Error: unknown filesystem.
Entering rescue mode...
Grub rescue>_

> **QIII said:**
> Have you used the drop-down (arrow towards the top right) to choose a different device?

Thank you.  Yes, it doesn't drop down.  It on't highlights the one thing there...which is /dev/sr0 etc...

---

### Post by X-RED_Tech on 2016-06-13
> **wintry said:**
> Good Question!

I know :P... I always try to ask good questions.
But the thing is, you should know the answer! BIOS/UEFI settings don't change themselves out of the blue. Users do it.

```
my boot menu has the following:
ATAPI CD-: Optiarc DVD RW etc...
[B]ATA HDD0: ST9250410AS
[/B]PCI LAN: IBA GE Slot etc...
```

In bold is your HDD so it's being recognized. How come it doesn't show up in GParted? Never saw that happening before...

---

### Post by wintry on 2016-06-13
> **X-RED_Tech said:**
> I know :P... I always try to ask good questions.
But the thing is, you should know the answer! BIOS/UEFI settings don't change themselves out of the blue. Users do it.

```
my boot menu has the following:
ATAPI CD-: Optiarc DVD RW etc...
[B]ATA HDD0: ST9250410AS
[/B]PCI LAN: IBA GE Slot etc...
```

In bold is your HDD so it's being recognized. How come it doesn't show up in GParted? Never saw that happening before...
Ha-ha sorry for not answering. No I didn't change anything in there. And when I boot from HDD0, it drops me into Grub rescue> with an error filesystem unknown message. :-(

Here's a new development.  I hit escape while booting up from the disc and this flashed on the screen (I took a pic) [ATTACH=CONFIG]269568[/ATTACH]  I've been toying around with things thinking it can't get any worse and I entered gparted again and got pop-up that said:

***Libparted error:***

[B][I]Error fsyncing/closing /dev/sda1:input/output error
      Retry      Ignore 
[/I][/B]
Retry did nothing so I went to ignore:

[B][I]Error fsyncing/closing /dev/sda2:input/output error
      Retry      Ignore[/I][/B]

same message but SDA 2....... ignore:   THEN the same box for each /dev/sda5-6-7 
 
and finally /dev/sda 

and it cycled around and around untill it dropped me on a cycle of 
[B][I]
Input/output error during read on /dev/sda [/I][/B]

I tried retrying a bunch of times.... but finally hit cancel on that last input/output error...
and now I see an unallocated 239GiB of space in GParted

What do I do now!?! :-o

---

### Post by X-RED_Tech on 2016-06-13
> **wintry said:**
> ****I tried retrying a bunch of times.... but finally hit cancel on that last input/output error...
and now I see an unallocated 239GiB of space in GParted

What do I do now!?! :-o

Perfect! :D \\:D/

Now make partition and format away or simply boot the Ubuntu installer and, as commented before, let it use the whole drive.

---

### Post by wintry on 2016-06-13
> **X-RED_Tech said:**
> Perfect! :D \\:D/

Now make partition and format away or simply boot the Ubuntu installer and, as commented before, let it use the whole drive.



The install keeps coming up with the error :

[I][B]Error fsyncing/closing /dev/sda1: Input/output error

[/B][/I]then cycling through all the sda numbers.  not installing.  


Same when I tried to create a table to partition:

finally it dropped me here:
[I][B]
Partition(s) 1, 2, 5, 6, 7 on /dev/sda have been written, but we have been unable to inform the kernel of the change, probably because it/they are in use.  As a result, the old partition(s) will remain in use.  You should reboot now before making further changes.

[/B][/I]And nothing is showing in Gparted anymore.    This is some wacky stuff.....

Going to reboot and see what happens...

good bye cruel world.

---

### Post by X-RED_Tech on 2016-06-13
That suggests hardware failure... Why where you error checking that drive again?

---

### Post by wintry on 2016-06-13
alright...so nothing on the install.  It just froze up.  

I'm thinking this is a hardware issue?  Should I replace my Hard Drive?  Is that easy?  will that fix this?

---

### Post by X-RED_Tech on 2016-06-13
I would try that because if it's not that it's the board itself.

---

