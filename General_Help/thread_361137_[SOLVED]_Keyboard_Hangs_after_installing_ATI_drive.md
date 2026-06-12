---
title: "[SOLVED] Keyboard Hangs after installing ATI driver Dell Inspiron 6400"
date: 2007-02-14
forum: General Help
---

### Post by prince_niceguy on 2007-02-14
I installed ATI propriety driver using the following link

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

After doing this I am no longer able to login into my Kubuntu Edgy system. The login screen does not display me any text box to fill in the user name and password, mouse moves but it does not click anything, keyboard shortcut to restart xserver does not work... I am stuck... please help...](*,)

---

### Post by prince_niceguy on 2007-08-30
included napci in my kernel option and it fixed the issue...

---

### Post by xoltrix2000 on 2008-05-24
Hi there, i'm very new to this, would you mind posting how you included that to the kernel options, pweeeese!


Thanks in advance!

X

---

### Post by prince_niceguy on 2008-05-25
when you boot up, in the grub OS selection screen press e, then again press e. Now, at the last put acpi. press b, and the system would boot up.

if it works and you want to make the change permanent, then edit the /boot/grub/menu.lst using sudo.

```
sudo gedit /boot/grub/menu.lst
```.

find a line

#DEFOPTION=

add acpi at the last with space.

save and exit. 

```
sudo update-grub
```

---

### Post by xoltrix2000 on 2008-05-25
at defoptinos, this is what I have now:

#defoptions=quiet splash

Do i add it after the word "splash" or do I make a new line like this:  

#defoptions=quiet splash
acpi

Thanks!

---

### Post by prince_niceguy on 2008-05-25
add it after the splash. ensure you keep a space between splash and acpi.

but before you do...has this resolved your issue?

---

