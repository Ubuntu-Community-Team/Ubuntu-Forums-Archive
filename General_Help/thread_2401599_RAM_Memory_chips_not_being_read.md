---
title: "RAM Memory chips not being read"
date: 2018-09-20
forum: General Help
---

### Post by tmichaelglass on 2018-09-20
Greetings,
I am running Ubuntu 14.04 on a Dell Inspiron 530. I had been running with 2 x 1 Gig chips and 2 x 512 Mb chip and it was shown in the "About this computer" as having the expected 3 Gb memory (or 2.9 Gb )

I recently replaced the 2 x 512 Mb chips with 2 x 1 Gb chips. When Ubuntu boots up, the "About this computer" tells me I have 3.2 Gb. I tried swapping the chips in the slots and got no difference. When I boot into the computer setup from the splash screens before Ubuntu boots, It says I have 4 GB memory installed.

What's going on?

---

### Post by Claus7 on 2018-09-20
Hello,

have you checked the output of the top command or check what is the result of task manager about your memory? Check also this link:
[https://www.binarytides.com/linux-command-check-memory-usage/](https://www.binarytides.com/linux-command-check-memory-usage/)

which shows more ways to monitor your memory.

Just some simple ideas,
Regards!

---

### Post by Impavidus on 2018-09-20
Is that a 32 bit or 64 bit Ubuntu install? To effectively use 4GiB of memory, you need 64 bit.

---

### Post by Yellow Pasque on 2018-09-20
> **Impavidus said:**
> To effectively use 4GiB of memory, you need 64 bit.

You also need BIOS 1.0.12 or later to support memory remapping.
```
BIOS Release Notes
===================================================================
===================================================================

Systems: Dell Insprion 530/530s
Version: 1.0.12
Build Date: 03/01/2008

Fixes/Enhancements:
1. Add support for new Intel CPU.
2. Update to latest microcodes.
3. Improve POST time with internal USB Card Reader & Buffalo USB HDD combination.
4. Correct Memory Map for => 4GB configurations.
```

---

### Post by ajgreeny on 2018-09-20
What does command ```
free -mw
``` show as output.
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by tmichaelglass on 2018-09-22
It looks like the problem is the BIOS version. I have version 1.0.10.
I'll have a go at updating the BIOS in a couple of minutes and report back.
It is a 64bit version.
free -mw tells me that w is an invalid option. I presume that was a typo.
free - m displays the following:

```

michael@michael-Inspiron-530:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3249       2429        820        373        103       1450
-/+ buffers/cache:        874       2374
Swap:         3059          0       3059
michael@michael-Inspiron-530:



```

---

### Post by ajgreeny on 2018-09-22
The command **free -mw** works fine on 16.04 and 18.04 so perhaps it is your older OS version that does not support that command.

---

### Post by tmichaelglass on 2018-09-23
I have successfully upgraded BIOS (from 1.0.10 to 1.0..18) and the memory problem appears to be fixed.

I had issues with**3. Creating a USB Bootable Storage Device Using FreeDOS (Legacy Systems)**

from [https://www.dell.com/support/article/us/en/19/sln171755/updating-the-dell-bios-in-linux-and-ubuntu-environments?lang=en](https://www.dell.com/support/article/us/en/19/sln171755/updating-the-dell-bios-in-linux-and-ubuntu-environments?lang=en).
Some reviews of UNetbootin said it didn't work with Ubuntu 14.04. Maybe that was the problem.
Eventually I downloaded the BIOS update file to a Windows Vista machine desktop and swapped the harddrives and ran the update from the windows desktop.
 It seems to have worked.

```

michael@michael-Inspiron-530:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3941       1586       2354        246         99        845
-/+ buffers/cache:        641       3299
Swap:         3059          0       3059
michael@michael-Inspiron-530:~$ 
```

---

### Post by Yellow Pasque on 2018-09-24
It looks good. Please mark the thread solved if you're satisfied (thread tools menu above first post).

---

