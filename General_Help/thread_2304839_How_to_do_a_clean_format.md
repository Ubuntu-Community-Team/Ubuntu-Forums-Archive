---
title: "How to do a clean format?"
date: 2015-11-30
forum: General Help
---

### Post by michael-piziak on 2015-11-30
I'm sending back a Notebook computer.

How can I do a clean format of the computer, leaving nothing on it, not even Ubuntu.

---

### Post by Bucky Ball on 2015-11-30
Perhaps you could mark [this]("http://ubuntuforums.org/showthread.php?t=2304743&p=13399367#post13399367") thread as 'solved' to save others from spending time helping there if you are sending it back. :) 

I have used DBan in the past. Your machine didn't come with Windows and a method to recover it to the state it was in when you got it? Check the manual. Think there's a key you can press at boot, or a combination.

Depending how completely you want to delete the data, an easy way is to simply boot to a Ubuntu live session, launch Gparted, delete everything on the drive.

---

### Post by michael-piziak on 2015-11-30
> **Bucky Ball said:**
> Perhaps you could mark [this]("http://ubuntuforums.org/showthread.php?t=2304743&p=13399367#post13399367") thread as 'solved' to save others from spending time helping there if you are sending it back. :) 

I have used DBan in the past. It didn't come with Windows and a method to recover it to the state it was in when you got it? Check the manual. Think there's a key you can press at boot, or a combination.

Depending how completely you want to delete the data, an easy way is to simply boot to a Ubuntu live session, launch Gparted, delete everything on the drive.

ok, I boot from a usb ubuntu installer thumb drive and choose try out ubuntu

please give me the exact terminal code to launch this gparted, or is it an app that doesn't need terminal

---

### Post by Bucky Ball on 2015-11-30
Doesn't need a terminal. You'll find it in the applications menu. It's there by default in a live session.

---

### Post by michael-piziak on 2015-11-30
> **Bucky Ball said:**
> Doesn't need a terminal. You'll find it in the applications menu. It's there by default in a live session.

ok I formatted it and then went and deleted the HD too

On boot, it does tell a version of GNU Grub upon "trying to boot."

I was hoping I could make it look like Ubuntu was never installed. 

I could care less about putting Windows back on it - just want it to look like it's been formatted and leave no clue what I put on it, so the seller can't blame Ubuntu

---

### Post by oldfred on 2015-11-30
Was it BIOS/MBR or UEFI/gpt?
You can zero out MBR if BIOS/MBR.

       Zero out MBR only of sda Use 440 if windows as serial number is between 440 & 446. Using 512 deletes MBR boot code & partition table info.
sudo dd if=/dev/zero of=/dev/sdX bs=512 count=1

If system is newer and UEFI, UEFI has its own NVRAM and saves entries there.
to see if you have entries you must boot in UEFI mode
sudo efibootmgr -v
If that show entries we can delete those also.

Unless you run a program like dban, data is still on drive. You can use testdisk to restore the partitions you deleted and see the data.
      
 Entire Drive - May take a long time, where sdX is your correct drive:
sudo dd if=/dev/zero of=/dev/sdX
sudo shred -n2 -v /dev/sdX
[http://www.dban.org/](http://www.dban.org/)

Make absolute sure you use correct drive sda, sdb etc for the sdX. 
dd's nickname is Data Destroyer as any typo using wrong drive is not recoverable.

---

### Post by Bucky Ball on 2015-11-30
As per your other thread. If the dealer said there was 4Gb in the machine and there is physically 2Gb it is irrelevant what you installed on it. The OS can't replace RAM sticks. :)

---

### Post by michael-piziak on 2015-11-30
Much of that is above my head.

Is there an option in Bios that I can zero out/format.  I went through all the bios menus and didn't see an option

---

### Post by michael-piziak on 2015-11-30
> **Bucky Ball said:**
> As per your other thread. If the dealer said there was 4Gb in the machine and there is physically 2Gb it is irrelevant what you installed on it. The OS can't replace RAM sticks. :)

True,

But the Notebook had a Windows sticker on the bottom, and I removed it and it left an extremely hard leave behind pattern that I got most off with a razor blade.

I Just wan'ted to send back an entirely blank system with no clue if Windows was taken off

---

### Post by Bucky Ball on 2015-11-30
> **michael-piziak said:**
> I Just wan'ted to send back an entirely blank system with no clue if Windows was taken off

That is going to be difficult if you've wiped the drive, as you say, and Windows is no longer on it. If you press F11 repeatedly at boot, does it take you to a Windows System Recovery? That will put the machine back to the state it was when you bought it, as I've mentioned. Looks like that's what you want.

---

### Post by michael-piziak on 2015-11-30
I'll try that, but I have my doubts.
I already put Ubuntu 12.04 lts on the entire system several times, formatted it with Gparted a few time.

I'll try, but I doubt anything Windows is even remotely left on it.

It's not big deal - it's going back regardless.  The guy that sells them on Amazon sells oodles of them, so I'm sure he can put Windows back on it and list it correctly - even though it won't have the windows sticker on it.

---

### Post by michael-piziak on 2015-11-30
> **Bucky Ball said:**
> That is going to be difficult if you've wiped the drive, as you say, and Windows is no longer on it. If you press F11 repeatedly at boot, does it take you to a Windows System Recovery? That will put the machine back to the state it was when you bought it, as I've mentioned. Looks like that's what you want.


Tried it, & it quickly acted like it was going to go into a recovery mode, but just as quickly went to a GNU GRUB message.

No big deal - it's going back regardless.  Nothing to really concern myself with.  It didn't have the right ram, and even though it wouldn't cost much for me to make it right, I later learned that the same HP Notebook 2000 comes in Intel Core 2 Duo, which I'm told is better than AMD, as AMD is not keeping up.   So I'll get the HP notebook 2000 intel one and I think I'll be happier - and I'll make sure it has what it is suppose to have when I get it.   Amazon has already authorized, via the vendor, to have this sent back and sent me a shipping label this morning.

Cheers

Michael

thread solved

---

