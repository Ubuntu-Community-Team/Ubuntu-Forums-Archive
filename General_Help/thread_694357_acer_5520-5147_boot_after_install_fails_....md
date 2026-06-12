---
title: "acer 5520-5147 boot after install fails ..."
date: 2008-02-11
forum: General Help
---

### Post by pupEOkami on 2008-02-11
this is not cool
i just purchased this new acer 5520-5147 that came standard with vista home junk
this is the 5th time ive gone threw a re-install and not getting any luck after the install completes . 
start out with safe graphic's mode live up boot .
go threw the step by steps . every thing seems to configure smooth and security updates download . install .
then the restart window shows . after the (press enter to remove disk an reboot shows ) i do so

then the re boot shows the load . 
at load screen only a small portion of load bar shows . about 4 min pass an it shows this strange text mode to do something that i have no clue on how to tamper with 

any one have some advice on how to make this thing work the way it should or at least have this at a stable state to run? 

any thing helps . 
thanks guys 

~pup

---

### Post by Pelham123 on 2008-02-12
Have you done a dual boot with Vista/Ubuntu? What happens when you start your PC up now - without any install CD in the CD drive - do you get a "Loading GRUB..." stage? What is the 'strange text mode' that you mention - what is displayed on the screen?

---

### Post by pupEOkami on 2008-02-13
Vista has been totoaly removed from the physical HDD . when GRUB loads it shows the boot status bar but only a short bit of orange displays for 5 min then text mode as if it was ubuntu failsafe mode . which im positive its something other than failsafe mode . any suggestions on kernel mods or something that i may be doing wrong or something that i could try different ?

---

### Post by Pelham123 on 2008-02-14
At initial boot-up press 'esc' to enter GRUB menu. This should bring up boot choices, highlight first option which should look something like this:

**Ubuntu 7.10, kernel 2.6.22-14-generic**

and press the 'e' key to edit boot parameters. This will bring up a second menu. Highlight the 'kernel' line, which will look a little like this:

**kernel     /boot/vmlinuz-2.6.22-14-generic boot=UUID=5a9e8f79-40ed-4897-a16e-3d8b4b21d3d7 ro quiet splash**

Again press 'e' to edit. Scroll along to the end and delete the word 'splash' and hit <return>

Press 'b' to boot OS

The above option will remove the 'splash' screen temporarily...make a note of where the boot up process stalls - ie the last text entry on the screen. Post reply.

---

