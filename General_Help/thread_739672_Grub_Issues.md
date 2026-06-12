---
title: "Grub Issues"
date: 2008-03-29
forum: General Help
---

### Post by ChrisBatcho on 2008-03-29
I've read a couple of threads on this and didn't really find my answer so here we go:

I have two HD's and wasn't using one of them and decided to try Linux. I installed, had fun, and decided that it didn't support the apps and games that I like and that I didn't need it anymore. Stupidly, I cleaned D drive, the drive that linux was on. I did this from windows. So now when I boot up, grub tries to load but gets stuck, because linux aint there anymore.

I cannot do anything at this point. I'm not interested in loading linux back in. I DON'T have my windows restore cd. I cannot find it.

I tried to reinstall linux just to see if i could get past this and at least have windows back but for some reason when it boots up to reinstall,the screen resolution is 640x480 and i cannot see the menus to move forward through the installation.

I am very frustrated and I have zero access to my computer right now. I don't have access to a cd burner.

I get the error:

> GRUB Loading Stage1.5.

GRUB loading, please wait...
Error 22

Help me. I cannot even get into DOS and even if I did I wouldn't know what to do anyways.

---

### Post by smoker on 2008-03-30
ideally, you would insert your xp install disk (if it is xp you have), run the 'recovery console' and use the commands 'fixboot' and 'fixmbr' to get the machine booting windows.

as you don't have your windows disk, maybe you can borrow one,

---

### Post by Herman on 2008-03-30
:) Hello ChrisBatcho,
The reason you get GRUB error 22 is because you have the GRUB's stage1 file in your hard disk's MBR and it's trying to point to GRUB's stage2 file in Ubuntu, but when Ubuntu is gone there is nothing there to point to. The stage2 file is the important part of GRUB that does most of the complicated stuff.

Re-installing Ubuntu is one way to fix that, but I don't know how that can affect your screen resolution in Windows. Maybe Windows will come up with a 'Found new hardware' sign after a while and ask you to reboot and it will fix itself.

So you don't have access to a cd burner and you can't find your Windows Installation Disc.
Okay, what version of Windos do you have? 
If your PC has a working floppy disc drive you can go to [bootdisc.Com]("http://www.bootdisk.com/") (not bootdisc.com), and download a file for making a boot disc for Windows 98SE and boot your computer with that. 
Run the command 'fdisk /mbr' from your Windows 98 boot floppy and that will give you a Windows 98 MBR, which is good enough for Windows XP and maybe even Vista as well, I'm not sure about Vista, but it would be worth a try.

---

### Post by Herman on 2008-03-30
If all else fails and you are really stuck and even if Windows won't boot in the first place you can use a  Ubuntu LiveCD or a hard disk installed Ubuntu operating system to
download a small utility called MbrFix.exe here, [http://www.sysint.no/en/Download.aspx](http://www.sysint.no/en/Download.aspx)
     
    Read all about MbrFix.exe here, [http://www.sysint.no/nedlasting/mbrfix.htm](http://www.sysint.no/nedlasting/mbrfix.htm)

Just Paste the file to the root of drive C: from Ubuntu.

 [A Birds's eye view of Windows XP]("http://users.bigpond.net.au/hermanzone/p6.htm#A_Birdss_eye_view_of_Windows_XP").(showing the bootloader files).
If you have the FAT32 file system in Windows it is safe to do that from any Linux. 
If you have the Ubuntu Gutsy Gibbon or later it is safe to write to an NTFS file system.
It is not recommended to write to NTFS from Feisty or earlier versions of Ubuntu unless you have special software installed for that in Linux. 
[Windows NTFS Partitions Read/write support made easy in Ubuntu Feisty]("http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html") - UbuntuGeek

Then if you still have Ubuntu installed, use GRUB for the last time to reboot Windows with and  when Windows has booted you can run MbrFix.exe  from a Windows command prompt as follows,

Click 'Start'->'Run', type CMD (for a Command Prompt).
     The command prompt will at first be something like,
```
C:\ Documents and Settings \ ChrisBatcho >_
```Change it to just a C: prompt by typing: cd \ , then press 'Enter'.
     After that you should just have a plain C:\>_ prompt. 
                             ```
C:\>_
```Type this command after the C:\> prompt: MbrFix /drive 0 fixmbr /yes
   for example,
   
```
C:\> MbrFix /drive 0 fixmbr /yes
```     Nothing much will appear to happen, your monitor may blink slightly, that's all. You will see the plain C:\>_ prompt again. Type 'exit'.
   
  That's it! Reboot to see if it worked.

If you didn't have Ubuntu installed so you can't boot Windows with GRUB, you could still boot Windows if you go to this page and download a boot disk (CD, floppy disk or USB file),  with NTLDR, NTDetect.com and boot.ini on it, [http://tinyempire.com/notes/ntldr]("http://tinyempire.com/notes/ntldrismissing.htm") that will boot Windows for you almost no matter what!

Then delete Ubuntu again if you still have it.

Regards, Herman :)

---

### Post by ChrisBatcho on 2008-03-30
Thanks Herman.

Sorry I didn't supply more information.

The screen resolution problem is not a problem I have in windows but in Ubuntu. This is the only thing keeping me from just giving up and reinstalling ubuntu to my D drive so that I can at least get GRUB back to boot into XP.

Also, I have Windows XP, so I'm not sure if that bootdisk idea will work, you said it was something I can do with Windows 98SE.

I don't mind the GRUB. If it just has windows on it that would be fine.

I'll the bootdisk idea and the FIXMBR and see if that works.

Now I just have to go dig up a floppy, lol.

Thanks again for the help.

---

### Post by ChrisBatcho on 2008-03-30
I FOUND MY RESTORE CD! OH, HAPPY DAYS!

Thanks so much. That was such blind luck.

---

### Post by tad1073 on 2008-03-30
the screen resolution can be fixed by running:
```
sudo dpkg-reconfigure xserver-xorg
```

"Enter" through until you get to the area where you select your screen resolution. Use the arrow keys to navigate and the spacebare to select the desired resolutions.

---

