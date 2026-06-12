---
title: "Does running Ubuntu from a flash drive provide full functionality?"
date: 2014-05-21
forum: General Help
---

### Post by ejroberts on 2014-05-21
I am new to Linux and Ubuntu, and have seen a lot of posts about problems installing Linux on Windows 8.1 PCs.  I am running from a 32G USB 3.0 flash drive and find that the boot time is fast enough for me.  Is there any functionality lost by not installing on a hard drive partition?  

Cheers!

---

### Post by LastDino on 2014-05-21
Considering your PC is new, as far as I know, as long as it is a persistent install it will be as good as installing on HD. Of course, you need to have good flashdrive/ssd to get good read/write speeds of the drive used.

I could be wrong about technicality issues involved as I'm not technical person my self.

---

### Post by Harsh_Parikh on 2014-05-21
If you have a new and ubuntu requirements' satisfactual computer,then you should install it on your HDD,or if not more use of it,you should run it in virtual machine....

And I think that 32 GB pen drive is very big,if you only want to test ubuntu....

---

### Post by monkeybrain20122 on 2014-05-21
> **LastDino said:**
> Considering your PC is new, as far as I know, as long as it is a persistent install it will be as good as installing on HD. Of course, you need to have good flashdrive/ssd to get good read/write speeds of the drive used.

I could be wrong about technicality issues involved as I'm not technical person my self.

Of course not. You can't upgrade kernel or install proprietary driver and your file system is limited to 4 G (FAT) for a live usb with persistence. Installing into the usb would the same as a 'real' install except for the speed.

---

### Post by sudodus on 2014-05-21
> **monkeybrain20122 said:**
> Of course not. You can't upgrade kernel or install proprietary driver and your file system is limited to 4 G (FAT) for a live usb with persistence. Installing into the usb would the same as a 'real' install except for the speed.

+1

So it is very important to get a fast USB 3 pendrive to ge satisfactory results with an installed system. See these links

[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

[Link to USB 2 and USB 3 speed tests for installers]("http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085")

[Portable installed system booting from UEFI & BIOS]("https://help.ubuntu.com/community/Installation/UEFI-and-BIOS")

---

### Post by LastDino on 2014-05-21
As monkybrain and Sudodus pointed out, you should consider that as important factor if your system doesn't work with pre-installed ubuntu non-free drivers. Kernel update would become a problem in long run too. I've personally never found myself using any file above 4gb on linux but that might be different for you, so you should consider that as well.

---

### Post by ejroberts on 2014-05-21
Thanks all for insights!  I do have USB 3.0, and it's 32G only because that's the one that I had.  I'm using Linux mostly for scientific applications (lot's of great and *free* apps out there).  I'll probably end up doing an install, but not until it becomes necessary. 

Cheers!

---

### Post by ejroberts on 2014-05-21
Thanks for links.  Very helpful!

---

### Post by sudodus on 2014-05-22
You are welcome and good luck :-)

If your problem is solved, please click on** Thread Tools** at the top of the page and mark this thread as SOLVED.

You are welcome back to create a new thread with a good descriptive title, when you have another question or problem.

---

### Post by C.S.Cameron on 2014-05-22
If you are satisfied with the speed, a Full* install to flash drive should give full functionality.
If you make the first partition FAT32 or NTFS, the drive can be used to transfer data to a Windows machine.
ie first partition FAT32, second partition / and third partition swap.

* Full install, not Persistent install.

---

