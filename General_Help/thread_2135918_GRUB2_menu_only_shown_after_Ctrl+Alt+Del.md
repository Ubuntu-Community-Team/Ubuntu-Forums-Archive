---
title: "GRUB2 menu only shown after Ctrl+Alt+Del"
date: 2013-04-15
forum: General Help
---

### Post by furlopunk on 2013-04-15
After finally getting GRUB to see my win8 installment, I decided to tackle my other GRUB2 issue. The GRUB menu only comes up if i press CAD during a blank magenta splash screen that appears during boot where the GRUB menu should be. After I press CAD my computer reboots and then I can see the GRUB menu. How can I set it so that the GRUB menu always shows up?

---

### Post by nerdtron on 2013-04-15
> **furlopunk said:**
> After finally getting GRUB to see my win8 installment, I decided to tackle my other GRUB2 issue. The GRUB menu only comes up if i press CAD during a blank magenta splash screen that appears during boot where the GRUB menu should be. After I press CAD my computer reboots and then I can see the GRUB menu. How can I set it so that the GRUB menu always shows up?

Alright let's try this:
1. Boot into Ubuntu and run ```
gksu gedit /etc/default/grub
```
2. Now on gedit, locate the GRUB_TIMEOUT line. Here is the sample:

> [COLOR=#0000cd]GRUB_DEFAULT=0[/COLOR]
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
[COLOR=#ff0000]GRUB_TIMEOUT=8[/COLOR]
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

3. Put there 10 secs if you like. While you are there, you can also change the default choice of operating system in the line GRUB_DEFAULT. If Windows 8 is listed as the 7th choice in the GRUB choice screen, put 6 on that line. (because counting starts from zero)

4. Now save your changes and close gedit.

5. Open the terminal and run ```
sudo update-grub
```
This is to make sure GRUB knows your changes.

Goodluck and keep us posted.

---

### Post by furlopunk on 2013-04-16
> **nerdtron said:**
> Alright let's try this:
1. Boot into Ubuntu and run ```
gksu gedit /etc/default/grub
```
2. Now on gedit, locate the GRUB_TIMEOUT line. Here is the sample:



3. Put there 10 secs if you like. While you are there, you can also change the default choice of operating system in the line GRUB_DEFAULT. If Windows 8 is listed as the 7th choice in the GRUB choice screen, put 6 on that line. (because counting starts from zero)

4. Now save your changes and close gedit.

5. Open the terminal and run ```
sudo update-grub
```
This is to make sure GRUB knows your changes.

Goodluck and keep us posted.

Thanks nerdtron! It worked. I had already commented out "[COLOR=#000000]*GRUB_HIDDEN_TIMEOUT" and "GRUB_HIDDEN_TIMEOUT_QUIET", but I had forgoten to update grub. Thanks again!*[/COLOR]

---

