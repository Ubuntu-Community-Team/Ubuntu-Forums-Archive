---
title: "OS Help"
date: 2016-02-19
forum: General Help
---

### Post by yonatan4 on 2016-02-19
So I tell you my story I have 3 os on my computer :
- Windows 10
- Windows 7
- Ubuntu

Windows 7 and Ubuntu are on the same hard drive and windows 10 on the second.i was reformating my computer on  ( Windows 10 ) it didnt work . I had at the end of the a HDD WITH windows 7 and ubuntu and The Other nothing.
Now I want to boot windows 7 its boot me  on &#8203;&#8203;grub with 2 choice  (Windows 7 and Ubuntu) I chose Windows 7 its put me a Error Message and put me on on grub! So I click ubuntu im in ubuntu after thanks to the terminal I copy the Windows 7 partition and i put it on the second hard drive. When I boot Windows on the second hard drive its putting me grub with the same options I click Windows and  ...its put me some me  code and its restarting e the computer. I need Windows 7 help me plz

---

### Post by yonatan4 on 2016-02-19
here is my boot info : [http://paste.ubuntu.com/15132176/](http://paste.ubuntu.com/15132176/)

---

### Post by ajgreeny on 2016-02-19
You appear to have formatted your Win 10 partition as it now has a Linux ext4 filesystem on it.
```
sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe
```
There is no reference at all to an installation of Win 10 but I believe Windows will not always describe the boot files with the OS name.

I think you may have to try to recover the old Win 10 partition using something like testdisk, but I do not have experience of that at all and I have not used Windows since WinXP so I'm a long way out of date.

Wait for other responses, hopefully from oldfred in particular who is the real guru on these sort of problems.

---

### Post by yancek on 2016-02-19
What were you reformatting, which system or partition and what does "didn't work" mean.  That's a little vague.
You indicate that when you select windows 7 from the boot menu, you get an error message.  You didn't post the error message so there's no way for anyone to make a suggestion on how to correct that unknown message.

You seem to have two windows installs, on the second partition of the first drive and the only partition of the second drive.  The problem with the second drive is that it is formatted ext4 as pointed out above and that won't work with windows.  If you look at the grub.cfg file from boot repair, there is an entry for windows on the second drive but the UUID in the grub.cfg menu is not the same as the actual UUID since you changed the filesystem to a Linux ext4 which also changed the UUID.

You could try running sudo update-grub to see if you get an entry for windows on the first drive which does not exist now.

---

### Post by yonatan4 on 2016-02-19
k so i was reformating windows 10 from windows 10 when is restarted windows 10 it told me unaccesebele boot device and its restarting . so i go to my other HDD to go on Ubuntu and i copied the windows 7 partitions (ntfs) into the second hdd then is discovered it put ext4 so i deleted the partition and put ntfs im gonna restart the computer when the copy is finished .

---

### Post by ajgreeny on 2016-02-20
I am pretty sure you can't just copy a partition in that manner and still get it to boot, but best of luck!

---

