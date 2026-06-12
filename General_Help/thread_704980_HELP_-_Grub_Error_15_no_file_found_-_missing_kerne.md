---
title: "HELP - Grub Error 15 no file found - missing kernel?"
date: 2008-02-22
forum: General Help
---

### Post by vanndrage on 2008-02-22
hello, i am having a problem on my desktop machine running 6.10. i rebooted my machine and it gave me the error 15: no file found press any key to continue.

i know this has been posted many a time on the forums but i have tried some things that i found on there w/ no luck at all. here is the low down on what i have tried:

i hit c to go to command then typed "find /boot/grub/stage1" and this said (hd0,0)
i then entered "root (hd0,0)" and hit enter
i then put "kernel (hd0,0)/boot/  hit TAB" to display the kernel and when doing this it said something like possible files = grub and memtest....  and that is it, nothing about any kernel

i also tried just hitting e to edit the lines and changing my (hd0,0) to something like (hd0,1) or (hd1,0)

i do have a 6.10 live cd so is there anything i can do from within that cd?

how do i know if the (hd0,0) is correct?

Any help is GREATLY appreciated as i need my machine back up ASAP. Thanks!

---

### Post by vanndrage on 2008-02-22
excuse me, i am using 7.10 not 6.10

---

### Post by vanndrage on 2008-02-23
ok, i am now able to boot my system but i no longer have gnome...... i do not know how all this stuff is just gone?

in order to boot into my system i copied files from my laptop, from the boot folder and then i also had to copy the /lib/modules folder as everything was missing from that also. now i get to the login and i enter my username and password and hit enter, it accepts this info but then just sits at an orange background w/ a cursor. if i try to select a login session at the login screen gnome is not an option, failsafe gnome is but i tried that and it says gnome not found.

any ideas?

---

### Post by vanndrage on 2008-02-25
ok, got booted back into gnome. i had to go to the command line and then type sudo apt-get install gnome and it downloaded and installed gnome again, after doing this i was then able to log into gnome and all my stuff is just as i left it. really not sure how this happened.

---

