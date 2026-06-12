---
title: "Xubuntu Install Problem"
date: 2007-02-14
forum: General Help
---

### Post by xxl3w on 2007-02-14
I've been recently trying to install Xubuntu on some old AMD machines at work. The first machine's install went VERY smooth. I had no errors at all, and it's functioning fine now. Well, the second, third, and fourth are having BIG problems. The only thing different in them are the motherboards. I even used the cdrom from the other computer considering I'm not leaving cdroms in them. Well, the problem is when I run the install it gives me the following error: ```
ACPI Unable to locate RSDP
```This does not prevent the install from running though. The install loads fine and starts installing normally. On the second machine, it froze installing/loading the base system, and the others it's freezing while trying to Select and Install. Usually it will give me a CD read error. I've did the CD integrity check 3 times and it's passed each time. I've also re-burned the ISO on 2 other cds one at 4x and one at 2x. I'm running out of ideas. Are some motherboards unsupported? Another question... Why would the install be getting this far before it decides to act up?

---

### Post by gwm on 2007-02-15
Hi,
I found your thread because I too have this problem. ACPI refers to Advanced Computer Power Interface (or something) and refers to the mother board, not the CD. Older PCs, like the Pentium MMX that I'm trying to install on, were made before this thing was invented, hence the problem. From my scouting around with Google etc. it seems that all Linux Distributions have this problem on older machines. They have some way of telling their installer not to use the ACPI functionality. I understand that to refer to hibernating and so on.
What we need to find out, is how to turn the functions off in an Ubuntu install.
My release CD is Dapper Drake and I haven't found a way of telling it to turn the functions off, so X crashes on bootup and I never get as far as being able to install.
HTH

---

### Post by xxl3w on 2007-02-15
OK, so I finally have 2 errors on 2 of the same computers. The Select and Install gets a way through and it gives me an error when it's trying to install the Printer section. I believe it's just giving random errors, because of the ACPI. I did read an article on it last night and it said you had to pass a parameter at the beginning to disable ACPI. I tried the parameter and it really didn't work. Can any gurus give us some information on what to do? For a temporary fix, I'm going to pull some of the machines we have that have upgraded motherboards, because like I said, the install worked fine with one of our machines. It seems since Xubuntu is geared towards older machines they might make a fix for this?

---

### Post by xxl3w on 2007-02-15
Well, the installation failed when it hit the Printer install portion, but I was able to skip Select and Install and i just went to the next option which was "install remaining packages". Hopefully this will work out, but I'm having doubts. I guess my day will consists of finding the correct motherboard.

---

### Post by xxl3w on 2007-02-15
Well, I looked through 30 machines and all of them have the same motherboard type *sniff sniff*. So, I bucked up and now I'm trying to get this install to work. So far, I've tried the boot option 'noacpi' and now I'm trying "acpi=off". When i tried 'noacpi' the install went a lot faster but it still hung at 'select and install'. Where it usually gives me the printer error, it just had a '!' mark and that was it. I selected "go back" and went to 'select and install' again. Everything went OK, but when I got to installing a boot loader, GRUB gave me an error, so I tried LILO. LILO also gave me an error. Well, now i'm trying 'acpi=off' to see if I get anymore results. On a side note, am I entering in the boot option correctly? I'm just taking off the end part of it, where it says "quiet --" and putting 'noacpi' or 'acpi=off'

---

### Post by xxl3w on 2007-02-15
OK, so I've been entering every command I can think of in the boot options menu to see if I can get the installation to work. Well, I tried ```
-- linux noapic nolapic acpi=off
```The install installed the base system fine, then it went on to Select and install. Well, it was finished with file 541 of 541 at 5% and it jumped to 'Cleaning up files' and gave me an error that it did not install correctly. The only information I receive is a "!" in the titlebar. Well, i skipped the Select and Install and just tried to install GRUB. I had no luck, it just gave me an error and I was sent back to the menu where i can select other install options. I'm running out of ideas. I really don't want to try Fluxubuntu because it's still in development.

---

### Post by xxl3w on 2007-02-15
From the massive amount of feedback I've been getting, I know you guys are excited to know the outcome of my problems. Apparently the ACPI error really isn't a big deal and has been a bad lead. Today, I decided to check the harddrive settings in the BIOS. It seems they were user defined, so I put all the options on AUTO and booted up the install. Out of paranoia I still passed the 'acpi=off' option when i booted the install. Well, the install went great up until the "Select and Install" part (AS ALWAYS!). Well, it failed when it was loading the Ubuntu artwork. It took my back to a prompt where I could select "Select and Install" again, so I did. Well, it hit another big file (apparently) and it hung/exited again with another error. Well, I repeated the above step again, and it didn't give me any errors the last time. So, I went on to installing GRUB and finishing the install. Well, for some reason the bootloader isn't loading (I didn't mark the partition bootable, BUT I also didn't install the bootloader on the harddrive, i put it in the MBR). I think the MBR is still on the harddrive but I'm not sure if it's on the partition i dedicated to root. Well, I booted the harddrive from the CD and XuBuntu loaded fine. As soon as it started, I tried to run Firefox. I received an error. I tried to open one of the terminals, I recieved another error. Thankfully, the package manager had been installed correctly so now I'm downloading and installing packages. I hope when I get to work tommorrow everything is running fine. I have a big question though. Could it be, because i only dedicated like 400mb to SWAP and have 128 mb of ram, that's why it gets hung on big portions of the install? Also, do I have to mark the partition bootable for GRUB to boot?

---

### Post by xxl3w on 2007-02-15
I have a ton of machines to install Xubuntu on and I really don't want to do an install like this on all of them. If i dedicated 1 GB to swap, will the install still get hung on big packs, like artwork/etc? I wish I could have worked later today, because I'm really excited about getting linux on all of our machines. I've really enjoyed this experience, even though it's been a PAIN!

---

