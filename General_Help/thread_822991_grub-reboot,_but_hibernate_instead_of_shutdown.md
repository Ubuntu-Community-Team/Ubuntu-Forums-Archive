---
title: "grub-reboot, but hibernate instead of shutdown?"
date: 2008-06-08
forum: General Help
---

### Post by Izkata on 2008-06-08
Right now, I don't see why it wouldn't be possible, but I haven't a clue how I could go about making it work myself.

Right now, I'm using 'pm-hibernate', then pressing the power button and selecting Windows from grub's menu.

So I'm hoping there's a way to have grub-reboot do a hibernate instead of a shutdown, so that I don't have to return to my computer midway between the switch.  Anyone know of one?

---

### Post by meierfra. on 2008-06-09
grub-reboot is just a shell script (/usr/sbin/grub-reboot). 

The second to last line contains the command "reboot". I guess you just need to change that command.  But I haven't tried it myself.

---

### Post by geopearl on 2008-06-09
provide some more details for the wide knowledge of this site..........
=====================
geopearl
Suffering from an addiction. This website has a lot of great resources and treatment centers. 
[http://www.treatmentcenters.org](http://www.treatmentcenters.org)

---

### Post by meierfra. on 2008-06-09
> provide some more details for the wide knowledge of this site....

Here is  all I know:

"sudo grub-reboot 4" will automatically reboot  the computer into the  5th  title on the Grub Menu.

More precisely  "grub-reboot 4" does two things:

#1  Writes the number "4" into the file  "/boot/grub/default"

#2  reboots

(For #1 to have any effect, you need to use "default saved" in /boot/grub/menu.lst instead of "default 0".
Also "grub-reboot 4" has the side effect that  the 5th title is the default  boot from now on, until you pick a different title at the Grub Menu. You can avoid this by adding "savedefault=0" to the windows item in menu.lst. 
Of course, the numbers "4" and "0" need to be replaced by the appropriate numbers for your setup)

If you open the script "grub-reboot" via

```
 gksudo gedit /usr/sbin/grub-reboot
```
you see that grub-reboot spends all its time on #1.
Only in the second to last line it works on #2.

So I suggest to add   a command, before "reboot" in the second to last line of "/usr/sbin/grub-reboot", which hibernates the computer. Also you can create a icon on the desktop which automatically runs "sudo grub-reboot 4" and you should be able to hibernate and reboot into Windows  with just one click of the mouse.

(I don't know what the correct command for hibernation is and I never created an icon  to  run a command.)

---

### Post by Izkata on 2008-06-09
> **meierfra. said:**
> grub-reboot is just a shell script (/usr/sbin/grub-reboot). 

The second to last line contains the command "reboot". I guess you just need to change that command.  But I haven't tried it myself.

Eh, not quite..  Maybe I didn't explain it quite right.  I know I can get a similar effect there with "echo n > grub-reboot 6".

Hibernate saves the RAM to hard disk.  Reboot does a full shutdown and automatically restarts the computer.  Those are the two steps I want to combine - save the RAM to the swap, and do a full reboot instead of a shutdown.  I don't know of any command that does such a thing.

> **meierfra. said:**
> (I don't know what the correct command for hibernation is and I never created an icon  to  run a command.)
The only command for hibernate that I know of is "pm-hibernate", which includes the shutdown step.

---

### Post by meierfra. on 2008-06-09
Sorry for solving the part of the problem, which your already solved yourself. Sorry again, I have no idea  how to combine "hibernate and reboot".

---

