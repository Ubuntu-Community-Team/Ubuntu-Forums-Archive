---
title: "Because of low graphic mode CANT install ubuntu."
date: 2014-04-21
forum: General Help
---

### Post by shivam_lakhotia on 2014-04-21
i have been trying to dual boot ubuntu in my hp 15 n-004tx notebook alongside windows 8.1 but due to low graphic mode cant even run ubuntu without installing. also windows 8.1 is running without any problem. have installed all the drivers of display and graphic in windows. I formatted my laptop deleting the recovery partition which acc. to me had the drivers for display. so without having ubuntu how to solve the low graphic mode problem.
PS- there are similar threads but the say to write some command such as sudo apt -get install/update in termnal but since i **dont** have the terminal where to write those. commands 
please help me dual boot my laptop.

---

### Post by oscarivera9 on 2014-04-21
> **shivam_lakhotia said:**
> i have been trying to dual boot ubuntu in my hp 15 n-004tx notebook alongside windows 8.1 but due to low graphic mode cant even run ubuntu without installing. also windows 8.1 is running without any problem. have installed all the drivers of display and graphic in windows. I formatted my laptop deleting the recovery partition which acc. to me had the drivers for display. so without having ubuntu how to solve the low graphic mode problem.
PS- there are similar threads but the say to write some command such as sudo apt -get install/update in termnal but since i **dont** have the terminal where to write those. commands 
please help me dual boot my laptop.

It's just a thought, but try running Lubuntu or Xubuntu instead.  Those two distributions are compatible with more hardware than the regular Ubuntu.  Not knowing which version you're running, but I'm assuming you're trying to use 14.04, you may want to try using an older version of Ubuntu like 12.04 because at this point it's more stable than the newest version.

---

### Post by Bashing-om on 2014-04-21
shivam_lakhotia; Hi !

My thought:
A graphics driver problem is a reasonable assumption.

Try this: Boot up ubuntu from cold boot, soon as the bios screen clears, depress the shift key -> grub menu>
Insure a "non recovery" kernel option is highlighted and press the "e"key for edit mode -> boot parameters; arrow down to the line similar to this "linux /boot/vmlinuz-3.2.0-24-generic root=UUID=dbd69ed2-530c-4409-8f5a-a3f1ea41fc67 ro quiet splash"
; arrow across to the term "quiet splash" and insert the term "nomodeset" -without the quotes-; ctl+x to continue the boot process. GUI login -> user name and password -> desktop. Left side of screen is the launcher ->ubuntu Software Center ->Software Sources(edit menu option on top task bar) ->Additional Drivers (tab in Software Sources) [must have 'net connectivity ]//assumes that 3rd party software sources have been enabled// Install the recommended driver.

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by shivam_lakhotia on 2014-09-10
Well, my laptop came with ubuntu 12.04 bt then i formatted it with windows 8....Before, ubuntu was working fyn bt after installing windows i am unable to run ubuntu. i tried 14.04...not working!!

---

### Post by shivam_lakhotia on 2014-09-10
Bashing-om...nw it works!!!thnx a ton man!!!!

---

### Post by Bashing-om on 2014-09-10
shivam_lakhotia; Hey hey ,

Pleased it has worked out for you, after all this time.

as this situation is now under control.
Please mark this thread solved : top of post -> thread tools.

and _>

[INDENT][INDENT]happy trails to you
[/INDENT][/INDENT]

---

### Post by shivam_lakhotia on 2014-10-26
The solution I got only helped me to run the ubuntu in the live mode...still cant install Ubuntu...Help!

---

### Post by Bashing-om on 2014-10-26
shivam_lakhotia; Hi !

Still here am I .

Before I am comfortable to offer any advise, I want you aware of a fixed bug, that may still apply to your situation:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

Before proceeding I need to know what version of ubiquity is available in that liveDVD.

From the liveDVD post back the output of terminal command:
```

dpkg -l ubiquity

```

ELSE; one would have to pre-partition the hard drive to accept installing ubuntu - jumping through Window's UEFI booting parameters to enable this.
Out of my sphere of experience -> then install with the install option "something else" .

[INDENT][INDENT]but hey, we can struggle through this
[/INDENT][/INDENT]

---

### Post by dragonfly41 on 2014-10-26
> 
.. also windows 8.1 is running without any problem. have installed all the drivers of display and graphic in windows.


There is another option you could consider instead of dual boot. You could try installing VirtualBox on Windows (if you're still using windows) and then install Ubuntu 14.04 as a virtual machine on VirtualBox-Windows.

Depends on your plans for using Ubuntu since you must have plenty of RAM for this approach to be effective.   

The advantage of using VirtualBox is you can experiment with different versions of Ubuntu.

---

### Post by shivam_lakhotia on 2014-11-03
Bashing-om I tried your previous solution again....I don't know how but it worked...once Ubuntu started working I changed the display drivers to proprietary...and its working.
Thnx a lot!

---

### Post by Bashing-om on 2014-11-03
shivam_lakhotia; Great !

Pleased it had worked out for you.

> **shivam_lakhotia said:**
> Bashing-om I tried your previous solution again....I don't know how but it worked...once Ubuntu started working I changed the display drivers to proprietary...and its working.
Thnx a lot!

[INDENT][INDENT]I wish
[INDENT][INDENT][INDENT]happy trails to you
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

