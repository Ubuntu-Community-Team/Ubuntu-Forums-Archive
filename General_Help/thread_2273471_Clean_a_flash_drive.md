---
title: "Clean a flash drive"
date: 2015-04-13
forum: General Help
---

### Post by Camilia on 2015-04-13
I want to clean a flash drive which I formated ubuntu onto. It does not work though. So thought I would start over.

In gparted tried to reformat and got 2 partitions are currently active on device /dev/sda. 

I have tried these commands in the terminal
1. Type sudo blkid in the terminal.
2. sudo shred -fz /dev/sdb1 
3. sudo dd if=/dev/zero of=/dev/sdb1

What else can I do?

---

### Post by Vladlenin5000 on 2015-04-13
Why do you think you need to 'clean' it? Or even reformat it?

---

### Post by Camilia on 2015-04-13
Can't do anything with the flashdrive. Was the 1 I used put ubuntu on PC. I have started the process and now need to complete it. For originally it had 3 partitions. I deleted 1 with gpartion. Did Partion>Swapped>Delete. Same process won't work for the other 2.

Only options available are to unmount and resize. Resized it so 0 before and after partition. Did unmount and got message Could not unmount /dev/sda1

---

### Post by Vladlenin5000 on 2015-04-13
Of course you can't delete partitions that are being used. You're trying to do that to the same drive your system is running from...
You need to boot a live session with other drive (or DVD) and open GParted in that live session, then select the USB where you installed Ubuntu and remove away.

---

### Post by Camilia on 2015-04-13
> **Vladlenin5000 said:**
> Of course you can't delete partitions that are being used. You're trying to do that to the same drive your system is running from...
You need to boot a live session with other drive (or DVD) and open GParted in that live session, then select the USB where you installed Ubuntu and remove away.
No the system is not running off it. I uploaded the program from the usb. Now when it is in the tower and I start the PC it just starts normal.

All I understand of what you said is that I put a DVD in the tower. How do I boot a live session or do you mean download?

---

### Post by Vladlenin5000 on 2015-04-13
Yes, I'm aware there are lots of relevant things you don't understand. I tried to keep it simple but sometimes there are no other ways to explain certain things.
So...
Having the partitions in use is the main problem here. That could have happened as well with any USB drive but unless the partitions are system partitions you should always be able to unmout and then remove them as you tried to do. The error message informing the pertitions can't be unmounted suggests exactly what I explained before: Your running your Ubuntu FROM that same USB drive, ie, you installed A full desktop Ubuntu in it. It isn't a bootable drive intended to run a live session and eventually install the OS. It has or had a SWAP partition, the halmark of a full install...

Now... Do you really want to delete everything? As explained before, you can, but only from another computer or running a live session in the same one... The point being - again - you can't mess with partitions that are in use.

---

### Post by Camilia on 2015-04-13
Also I have an older form for ubuntu on a DVD-RW disk. I can't clear that 1 either. It is old and not on my PC but can't be cleared with GPartioner. Contrary to what you said about can't crear what is in use.

---

### Post by Topsiho on 2015-04-13
Maybe I don't get it.

I understand that Ubuntu is installed from the USB flashdrive (USB-stick? pendrive?) onto the hard disk, and after that the computer was rebooted from the hard disk (sda), with the flash drive still inserted (as sdb). Or the flash drive is inserted again after the reboot.

If so I think the flash drive is mounted and should be unmounted first before you can change anything on it using GParted (which should be installed using sudo). As Vladlenin5000 says you can't execute changes on a mounted drive, just as you can't cut a branch in a tree, that you are sitting on.

After the unmount (in GParted) you can remove the partitions on the flash drive and put new partitions on it  (also using GParted).

Topsiho

You can clear the DVD-RW disk using the application called brasero.

Easy, from the menu. Don't know what it says in English, something as "Clearing CD/DVD" I suppose. If it really is RW, of course.

Topsiho

---

### Post by Camilia on 2015-04-13
> **Topsiho said:**
> Maybe I don't get it.

I understand that Ubuntu is installed from the USB flashdrive (USB-stick? pendrive?) onto the hard disk, and after that the computer was rebooted from the hard disk (sda), with the flash drive still inserted (as sdb). Or the flash drive is inserted again after the reboot.

After the unmount (in GParted) you can remove the partitions on the flash drive and put new partitions on it  (also using GParted).

Flashdrive has not been since installed onto the hard disk.

Don't have the option unmount this time. 

Also why is then that an old old version of ubuntu, which is on a DVD-RW, that is not on the hard drive can not be cleared? Thus what say is not true for the DVD-RW.

---

### Post by Vladlenin5000 on 2015-04-13
If you weren't running Ubuntu from that drive you could easily unmount the partitions but you can't... Can you boot your PC without it? If so you have two Ubuntus but the good news is you should be able to do the aforementioned operations after inserting the pen, then unmount if needed. 
This is what you MUST understand...

CDs or DVDs are different. They do require specific software and usually you can just write/burn a new session, no need to delete/format, whatever.

---

### Post by Camilia on 2015-04-13
No option clean it with Brasero. You are wrong again

I have ubuntu 14.04. I have problems now with enlarged icons, which I can't undo. Thus want to reinstall ubuntu.

---

### Post by Topsiho on 2015-04-13
You need to insert the flash drive into the computer if you want to do anything with it using the computer. Inserting it doesn't mean it (or it's contents) is installed, only that the contents of it are made accessible to the computer. To make the contents inaccessible again, if you want to change the partitions, the contents should be made inaccessible, while the flash drive still remains in the computer, it should be unmounted first.

Clearing a DVD-RW is easy, independent from what is on the DVD-RW, using a program like brasero, which is available in Ubuntu.

Topsiho

What operating system are you using right now?

Topsiho

---

### Post by Camilia on 2015-04-13
As I already I have said I have ubuntu 14.04 on this computer. 

Also as I already said option to unmounted not available this time. I cleared it before using that option.

---

### Post by Vladlenin5000 on 2015-04-13
Once and for all... Can you boot you PC WITHOUT the USB? If not, there' s your answer: Your system has been installed on thata drive.

---

### Post by Topsiho on 2015-04-13
You haven't.
If you have Ubuntu on your computer, you have brasero.

I wish you good luck

Topsiho

---

### Post by QIII on 2015-04-13
Camilia -

Please eject the USB device and set it aside on your desk.  Turn off and reboot your machine without the USB device attached.

Let us know if you can boot to Ubuntu.

Everyone else please take a break until that answer is provided.

Thanks.

---

### Post by papibe on 2015-04-13
There's no need to get confrontational or rude.
> **Camilia said:**
> You are wrong again...
> **Vladlenin5000 said:**
> Once and for all... Can you boot you PC WITHOUT the USB? ...
@Camilia, we are all volunteers here. If a person responds to your thread is because s/he's trying to help.

@Vladlenin5000, please remember we all were newbies, not so long ago.

Best Regards.

---

### Post by Keith_Helms on 2015-04-13
> **Camilia said:**
> I want to clean a flash drive which I formated ubuntu onto. It does not work though. So thought I would start over.

In gparted tried to reformat and got 2 partitions are currently active on device /dev/sda. 

I have tried these commands in the terminal
1. Type sudo blkid in the terminal.
2. sudo shred -fz /dev/sdb1 
3. sudo dd if=/dev/zero of=/dev/sdb1

What else can I do?

When you say you formatted ubuntu onto, do you mean you downloaded it to the flash drive?  Can you open the flash drive and see a file on it that is named something like **ubuntu-14.04.2-desktop-amd64.iso**?  Downloading a file onto a flash drive is not the same thing as making the flash drive bootable.  When you say it does not work, did you mean it won't boot?

You have another thread going about burning Ubuntu to a DVD.   You just need to open a disc burning application and select "burn image" or "burn iso".  If you have the default disc burning application of Brasero installed, it would be "burn image".  When it prompts you for the image to burn, select that iso file you downloaded.  When that burn finishes, you should be able to restart your system and boot from the DVD you just burned.   You may have to go into your system's BIOS and change the boot options so that it tries the DVD drive before the hard drive.

Edit: I apologize for jumping in here.  I just got a strong feeling that different people had different understandings of some of the terminology being used.

---

### Post by Camilia on 2015-04-13
> **Vladlenin5000 said:**
> Once and for all... Can you boot you PC WITHOUT the USB? If not, there' s your answer: Your system has been installed on thata drive.
Yes!! I had put the usb up after installing ubuntu.

Jan using Universable USB Creator from PendriveLinux created a bootable drive. Then started PC with the USB saving it to hardrive. Then put the USB up.

So today when I put the USB back in the PC it just booted up as if it was not there.

> **Keith_Helms said:**
> 
You have another thread going about burning Ubuntu to a DVD.   You just need to open a disc burning application and select "burn image" or "burn iso".  If you have the default disc burning application of Brasero installed, it would be "burn image". 

I have Brasero installed. It burn it as a file though so I don't going to work. Guess try it again tomorrow. I've got to get ready for company coming in from Fla so it has to wait. Probably be clearer when I am not rushed.

Thanks everyone!!

I reinstalled ubuntu 14.10 using a CD that I bought. Thus I thought then I should be able to delete the partitions on a flash drive that I had made an ISO of ubuntu with GPartion. Now I get the option to unmount it. The message I get when I try to unmount is-
The partition could not be unmounted from the following mount points:
Most likely other partitions are also mounted on these mount points. You are advised to unmount them manually

How do I do it manually?

---

### Post by 1clue on 2015-05-04
[https://www.sdcard.org/downloads/formatter_4/](https://www.sdcard.org/downloads/formatter_4/)

The difference is the security function placed on many SD/flash cards by the manufacturer.  SD formatting software knows about this and won't trample on it.  Otherwise there's not really any difference AFAICT.

I don't think that code works on Linux anyway, so if you don't intend to use the flash drive on a Windows/Mac/Phone then you probably don't have to worry about it.

---

### Post by Vladlenin5000 on 2015-05-04
> **Camilia said:**
> I reinstalled ubuntu 14.10 using a CD that I bought. Thus I thought then I should be able to delete the partitions on a flash drive that I had made an ISO of ubuntu with GPartion. Now I get the option to unmount it. The message I get when I try to unmount is-
The partition could not be unmounted from the following mount points:
Most likely other partitions are also mounted on these mount points. You are advised to unmount them manually

How do I do it manually?

So you have reinstalled Ubuntu with a CD... Most likely a DVD, right? Ubuntu ISOs no longer fit into CDs, since a long time ago... Just sayin'... Moving on...

Your last reply regarding whether or not you're able to boot WITHOUT the USB is even more confusing, to say the least, but it doesn't matter now anyway, _assuming you reinstalled Ubuntu in an internal drive_. So, please correct me if I'm wrong:

[B]You start Ubuntu without any other media than the one where it's installed, supposedly an internal drive? And then you plug in the problematic USB flash drive? This is when you're unable to unmount it?
[/B]

---

### Post by Camilia on 2015-05-05
> **1clue said:**
> [https://www.sdcard.org/downloads/formatter_4/](https://www.sdcard.org/downloads/formatter_4/)

The difference is the security function placed on many SD/flash cards by the manufacturer.  SD formatting software knows about this and won't trample on it.  Otherwise there's not really any difference AFAICT.

I don't think that code works on Linux anyway, so if you don't intend to use the flash drive on a Windows/Mac/Phone then you probably don't have to worry about it.
I use my flash drives on pc with windows os and ubuntu os.

> **Vladlenin5000 said:**
> So you have reinstalled Ubuntu with a CD... Most likely a DVD, right? Ubuntu ISOs no longer fit into CDs, since a long time ago... Just sayin'... Moving on...

Your last reply regarding whether or not you're able to boot WITHOUT the USB is even more confusing, to say the least, but it doesn't matter now anyway, _assuming you reinstalled Ubuntu in an internal drive_. So, please correct me if I'm wrong:

[B]You start Ubuntu without any other media than the one where it's installed, supposedly an internal drive? And then you plug in the problematic USB flash drive? This is when you're unable to unmount it?
[/B]
I did not use an internal drive. I just put ubuntu disk and reinstalled it. Then tried to unmount the USB I had used in the past to burn ISO. Using the USB to intall ubuntu did not work. Thus I would like to clean it to save files.

---

### Post by 1clue on 2015-05-05
In that case you may want to reformat it using a Windows-based formatter, preferably one from the manufacturer of your flash drive.  That way, you may be able to resurrect/rebuild your security function as per original spec.

The way I understand it, if you used Linux to overwrite your flash card then that security function is gone.  Also I believe the generic SD formatters might not reinstall that security function, they may be different per manufacturer.

---

### Post by Camilia on 2015-05-05
> **1clue said:**
> In that case you may want to reformat it using a Windows-based formatter, preferably one from the manufacturer of your flash drive.  That way, you may be able to resurrect/rebuild your security function as per original spec.

The way I understand it, if you used Linux to overwrite your flash card then that security function is gone.  Also I believe the generic SD formatters might not reinstall that security function, they may be different per manufacturer.
I reformatted it with pc with windows os. Now when I put in pc with ubuntu I get 2 files. One has ubuntu and 1 is empty.

---

