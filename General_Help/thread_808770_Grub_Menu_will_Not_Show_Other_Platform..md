---
title: "Grub Menu will Not Show Other Platform."
date: 2008-05-26
forum: General Help
---

### Post by fossilfiction on 2008-05-26
I started my Linux+ Course last week. I have to be at home a lot but I need to run labs. So I thought "Well a dual boot would work." I was wrong. Once I installed Ubuntu 7.04 from a live CD my book provided. It went nice. I was able to boot into Windows and Linux. 
Two weeks later I noticed the little box in the right hand corner that was telling me of some available updates. No harm no foul in preforming updates. Then I saw where a new dist was available. 7.10! Neat! 
The installtion failed to complete after a while. Then when I tried to go and reboot to check on windows the grub showed me the something like the following....
[I]
Ubuntu 7.10
Unbuntu 7.10 (recovery console 
Ubuntu 7.10
Unbuntu 7.10 (recovery console 
Ubuntu 7.10
Unbuntu 7.10 (recovery console 
mem test 84
Other 
Windows Longhorn (loader)
Windows Longhorn (loader)
Windwos Vista[/I]

Before attempting to upgrade it went something like this....

[I]Windwos Vista Beta
Ubuntu 7.10
Unbuntu 7.10 (recovery console 
Ubuntu 7.10
Unbuntu 7.10 (recovery console 
Ubuntu 7.10
Unbuntu 7.10 (recovery console 
mem test 84
Other 
Windows Longhorn (loader)[/I]
*Windows Longhorn (loader)*

   Now the issue. The current grub menu will only take me to the built in recovery tools of Vista.I cannot access Windows at all. I need to gain access to both platforms. If anyone on here to could help me to enter windows again that would be great. 
The Recovery Partition is on sda 01, The NTFS(Windows) is sda 02 with Linux on sda 3 and 4.

I no longer have the Live CD nor do I have access to Windows Recovery Console( way to go Vista)  The only tools availble in the Windows recovery tools console are System Restore, Diagnositics, Restore C(this means I lose all data), and rescue data.

    Any help?

---

### Post by unutbu on 2008-05-26
What happens when you try to boot to Ubuntu Recovery mode? Don't assume just because the titles are the same that they do the same thing. Try each option.

---

### Post by Nameless Neko on 2008-05-26
Could you paste the contents of your menu.lst file?  I'll see if I can't work it out for ya.

---

### Post by scxtt on 2008-05-26
you most likely need to change the **hd(#,#)** entries for vista ... on my laptop the 1st entry was the recovery partition and the 2nd would boot vista ...

---

