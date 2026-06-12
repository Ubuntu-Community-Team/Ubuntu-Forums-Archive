---
title: "How to boot using device name vs UUID in Trusty?"
date: 2014-08-29
forum: General Help
---

### Post by Carl_Turney on 2014-08-29
Hi,

I've used this technique (in general) on earlier versions of Ubuntu for years, with no apparent problems.

But I want more knowledgeable folk to give me feedback, especially regarding any recent changes in Ubuntu's boot-up.

Yes, I know of the advantages of UUID, and the pitfalls of relying on device names, but UUIDs thwart my elegant backup system, and I have mediating human-based procedures in place.

[SIZE=1][FONT=Courier 10 Pitch]So, are the following steps correct, succinct, and complete?[/FONT][/SIZE]

  	 	 	 	   [SIZE=1][FONT=Courier 10 Pitch]***** STEP 1 [/FONT] 
[/SIZE]
[SIZE=1] [/SIZE][SIZE=1][FONT=Courier 10 Pitch]In[/FONT][FONT=Courier 10 Pitch]  /etc/default/grub  [/FONT][FONT=Courier 10 Pitch]un-comment[/FONT][FONT=Courier 10 Pitch] the line...  [/FONT] [/SIZE]

[SIZE=1] [/SIZE][SIZE=1][FONT=Courier 10 Pitch]#GRUB_DISABLE_LINUX_UUID=”true”[/FONT][/SIZE]

[SIZE=1] [/SIZE][SIZE=1]
[/SIZE]
[SIZE=1] [/SIZE][SIZE=1][FONT=Courier 10 Pitch]***** STEP 2 [/FONT] [/SIZE]

[SIZE=1] [/SIZE][SIZE=1][FONT=Courier 10 Pitch]In  /usr/share/grub/grub-mkconfig_lib  comment-out the (2) lines starting...[/FONT][/SIZE]

[SIZE=1] [/SIZE][SIZE=1][FONT=Courier 10 Pitch]if fs_uuid=[/FONT][/SIZE]

[SIZE=1] [/SIZE][SIZE=1][FONT=Courier 10 Pitch]WAIT! That leaves some loose “else” and “fi” lines still present.  That's OK??[/FONT][/SIZE]

[SIZE=1] [/SIZE][SIZE=1]
[/SIZE]
[SIZE=1] [/SIZE][SIZE=1][FONT=Courier 10 Pitch]***** STEP 3[/FONT][/SIZE]

[SIZE=1] [/SIZE][SIZE=1][FONT=Courier 10 Pitch]In  /etc/fstab  change every instance of UUID=(etc.)[/FONT][/SIZE]

[SIZE=1] [/SIZE][SIZE=1][FONT=Courier 10 Pitch]to the appropriate drive and partition (e.g. /dev/sda1)[/FONT][/SIZE]

[SIZE=1] [/SIZE][SIZE=1]
[/SIZE]
[SIZE=1] [/SIZE][SIZE=1][FONT=Courier 10 Pitch]***** STEP 4  [/FONT] [/SIZE]

[SIZE=1] [/SIZE][SIZE=1][FONT=Courier 10 Pitch]In  /etc/initramfs-tools/conf.d/resume  change RESUME=UUID=(etc.)[/FONT][/SIZE]

[SIZE=1] [/SIZE][SIZE=1][FONT=Courier 10 Pitch]into RESUME=(the appropriate drive and partition e.g. /dev/sda1)[/FONT][/SIZE]

[SIZE=1] [/SIZE][SIZE=1]
[/SIZE]
[SIZE=1] [/SIZE][SIZE=1][FONT=Courier 10 Pitch]***** STEP 5[/FONT][/SIZE]

[SIZE=1] [/SIZE][SIZE=1][FONT=Courier 10 Pitch]Run update-grub[/FONT][/SIZE]

[SIZE=1] [/SIZE][SIZE=1]
[/SIZE]
[SIZE=1] [/SIZE][SIZE=1][FONT=Courier 10 Pitch]***** STEP 6[/FONT][/SIZE]

[SIZE=1] [/SIZE][SIZE=1][FONT=Courier 10 Pitch]Repeat steps 1 through 5 every time there is a kernel upgrade.[/FONT][/SIZE]

[SIZE=1] [/SIZE][SIZE=1][FONT=Courier 10 Pitch]UNSURE:  Should I do those steps before or after an upgrade reboot?[/FONT][/SIZE]

[SIZE=1] [/SIZE][SIZE=1]
[/SIZE]
[SIZE=1][/SIZE]Thanks in advance for your comments, questions, and suggestions.

Carl
Melbourne, Australia

---

