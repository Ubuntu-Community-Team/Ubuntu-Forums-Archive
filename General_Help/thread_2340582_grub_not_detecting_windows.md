---
title: "grub not detecting windows"
date: 2016-10-19
forum: General Help
---

### Post by Josey on 2016-10-19
I tried to set up a dual boot for my friend, but apparently windows 8 has a fastboot option by default which makes it look like it wasn't shut down properly, thus, ubuntu can't mount it, and totally ignored it when setting up grub.  

So first I need to remove hibernation status on the ntfs drive, and then add it to grub.  One thing at a time though so if you know how to remove the hibernation thing please help.

---

### Post by colmax on 2016-10-19
Try booting into windows then restart (not shutdown) & boot into linux
The restart seems to keep the windows voume accessible
Hope that helps

---

### Post by Josey on 2016-10-20
I can not boot into windows.

---

### Post by Bucky Ball on 2016-10-20
If Windows was in hibernation mode you would not have been able to install Ubuntu in the first place. It locks the drive and partitions on it.

It helps greatly if you tell us how you installed, what you tried to fix it and the exact problem now, what you can and can't do. You also give no indication of the Ubuntu release or flavour you have installed. The more info you can give to start with the less time we need to waste asking basic questions. :)

Bottom line: you need hibernation off in Windows, faststart and secureboot off in the BIOS and you need to install in EFI mode if Windows is installed in EFI, which it probably is. Your problem may be that you've installed in Legacy and Windows is in EFI. Please see the Boot Repair link in the signature at the bottom of my post, launch Boot Repair and create a bootinfo report (DO NOT do a recommended repair) and post the link to the output here (you will be provided with a weblink once the file is created).

* Also, try this. Open a terminal, paste this in and hit enter:

```
sudo update-grub
```

Reboot. Do you see Windows on the list now? Are you even getting a list of operating systems at boot? If not, hit the shift key after boot and it should come up.

---

### Post by Josey on 2016-10-20
Appreciate the reply .  Here is log created by boot repair.  [http://paste2.org/Mx00E7GJ](http://paste2.org/Mx00E7GJ)  
The partition with windows is /dev/sda2  

Windows was definately installed with bios on legacy, as it is a circa 2006 PC.  Also, I am attempting to fix it remotely, so I have no access to bios.  

Grub sees and boots to linux partitions just fine, but ignores windows on /dev/sda2

My best guess is I really just need to get it back into a good state.  ie get that hibernation flag / file off it from linux.

---

### Post by colmax on 2016-10-20
If you can get it to boot off LAN may work but i do think thats in bios
Otherwise maybe treat it as a dumb terminal to mount then see if you can drop system files on it
I'm outta ideas

---

### Post by Josey on 2016-10-20
Somehow I must have got the hibernation flag off it, because I can mount it now.  I just need to get it into grub now.  grub-update isn't seeing it

---

### Post by Josey on 2016-10-20
Trying to boot to windows but I can't get grub to spot it with a simple update-grub

it's dev/sda2  

Boot repair info log  [http://paste2.org/kNIY80dP](http://paste2.org/kNIY80dP)  

Here is a rundown on the problem.
I installed windows xp on /dev/sda1 just for the hell of it.
Then I installed windows 8 on /dev/sda2
then in installed linux mint on /dev/sda3

all was working at this point.  when you loaded windows 8 I would have to select load older version of windows and it would reboot into windows xp.
This is where it gets tricky.

I then wiped windows xp and formatted /dev/sda1 to ext4 and slapped ubuntu on there
ubuntu did not setup windows 8 on dev/sda2
I assumed this was due to windows 8 not shutting down properly as it was flagged as in some sort of hibernation.
I removed the hibernation file so now I can mount it and see all my windows 8 files in /dev/sda2, but update-grub still fails to set it up

My guess is windows 8 got setup with it's own dualboot file on /dev/sda1 which is no longer there
The solution to this is likely to pop in the windows 8 disk and let it fix it's boot problems.  The problem here is that I am trying to do this remotely.
any ideas?

---

### Post by sisco311 on 2016-10-20
Threads merged. Please don't start multiple threads on the same topic.

---

### Post by Josey on 2016-10-20
Except now my title is not at all what I need help with.  I had two problems, this one was fixed.  mods >.>

---

### Post by Bucky Ball on 2016-10-20
> **Josey said:**
> Except now my title is not at all what I need help with.

Then change the title of this thread by editing the first post, Go Advanced.

> **Josey said:**
>   I had two problems, this one was fixed.  mods >.> 

You actually have one problem with several parts. You've fixed one part but all you ever wanted was to get Windows in the grub, yes? Also, it is best to let us know all the details right at the start for the best support, not wait until a few posts in to reveal you are actually accessing this machine remotely and can't access the BIOS. That is quite a different matter and should possibly be in ***Server Platforms*** for better support.

---

### Post by oldfred on 2016-10-20
It does not matter how many Windows you install, it always installs its boot files into one NTFS partition with the boot flag. Normally the first NTFS or first Windows install.
So if you erased the first install, you erased all boot files from all installs.

       To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html](http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html)
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by Josey on 2016-10-20
I appreciate all that good info.  So as far as anyone knows, there is no way to do this remotely?  I need to get a windows 8 disk into the machine and let it repair it's boot?

---

