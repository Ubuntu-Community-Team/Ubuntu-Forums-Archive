---
title: "Asus zenbook:  hotkeys not working"
date: 2014-06-23
forum: General Help
---

### Post by Michele_Tettamanzi on 2014-06-23
Ciao a tutti, 

just managed to get a new zenbook, pushed by the fact that it should have worked quite perfectly, without too much fixing, once ubuntu had been installed. 

BUT, as a matter of fact, i do have an issue..obvioulsy!

None of the hotkeys is working, neither pressed alone or in combination with cterl, alt, ...does anybody have some clue on how i can solve this issue?

I am happy lubuntu user, but if someone tells me that i'll be fine under other ubuntu distributions, i can change easily.

Thank you in advance, 
michi

---

### Post by jeremy31 on 2014-06-23
Hello
```
lsmod | grep asus
```
If asus_nb_wmi is in the list do
```
sudo modprobe -rv asus_nb_wmi
```  wait a bit and try hotkeys

If no change in hotkeys ```
sudo modprobe asus_nb_wmi
```

---

### Post by Michele_Tettamanzi on 2014-06-25
Unfortunately nothing changed using both the commands!

Anyway, 
what I obtained using lsmod was:


```

michele@miche-UX32LN:~$ lsmod | grep asus
asus_nb_wmi            16990  0 
asus_wmi               24191  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
wmi                    19177  3 mxm_wmi,nouveau,asus_wmi
video                  19476  3 i915,nouveau,asus_wmi


```

more ideas? maybe i can try by modifing openbox config file....you think it might be working?


grazie

---

### Post by jeremy31 on 2014-06-25
Can check some other things first ```
acpi_listen
``` and try the hotkeys- CTRL+C to stop.

---

### Post by Michele_Tettamanzi on 2014-07-10
here's the output:
```
The program 'acpi_listen' is currently not installed. You can install it by typing:sudo apt-get install acpid

```

I guess you want me to install it...

---

### Post by Michele_Tettamanzi on 2014-07-10
Ok, 
installed...nothing happened!

---

### Post by jeremy31 on 2014-07-10
> **Michele_Tettamanzi said:**
> Ok, 
installed...nothing happened!
That means trying some grub options for booting then
Do you see a grub menu at boot?  If you do, when you restart press e when the grub menu is displayed, use arrow keys to scroll to just after "quiet splash" is on the display and enter ```
acpi_osi=
``` and press F10 to boot.  There are more options like ```
acpi_osi="Linux"
``` or ="Windows 2012"  ="Windows 2006"  Hopefully one of them will get those keys to work

---

### Post by Michele_Tettamanzi on 2014-07-10
Not seeing any grub at booting, since i got rid of windows, so my computer starts directly on Linux.
Shall i install a GRUB?

---

### Post by jeremy31 on 2014-07-10
Grub is installed it is just hidden ```
cat /etc/default/grub
```
The results from that should show how to get it to display at boot

---

### Post by jeremy31 on 2014-07-10
Going to have to search google

---

### Post by Michele_Tettamanzi on 2014-07-11
Ok, 

i managed to make the GRUB appear, to enter the "e-menu" and to edit acpi_osi= ...
Nothing happend, actually, but  I noticed that ifI reboot the computer, and than re-press e during bootin, after quite splash still seeing the default command, that is ```
 $vt_handoff
```.

is that right?

---

### Post by jeremy31 on 2014-07-11
> **Michele_Tettamanzi said:**
> Ok, 

i managed to make the GRUB appear, to enter the "e-menu" and to edit acpi_osi= ...
Nothing happend, actually, but  I noticed that ifI reboot the computer, and than re-press e during bootin, after quite splash still seeing the default command, that is ```
 $vt_handoff
```.

is that right?

Seeing the $vt_handoff is normal, and I prefer to test commands in grub by editing when booting, just add the acpi_osi= before the $vt_handoff

If you do find a acpi_osi that works and forget which one you tried you can check the command line with ```
cat /proc/cmdline
```

Are there any OS options in BIOS?  Is the BIOS the latest version?  I did find a bug report that indicates the ```
acpi_osi=
``` does make the hotkeys work on some Asus models

---

### Post by Michele_Tettamanzi on 2014-07-26
i have tried all the options you suggested me in the e-menu, but the not showed any improvement!  on the contrary..it stopped working also the brightness and the wifi key which i managed to make work!

what do you mean "[COLOR=#000000]Are there any OS options in BIOS? Is the BIOS the latest version? [/COLOR]"?


Thanks

---

