---
title: "sudo dpkg-reconfigure keyboard-configuration"
date: 2016-03-10
forum: General Help
---

### Post by dirk-lehmann on 2016-03-10
Unfortunately the change of my keyboard layout does not has any effect with the command "sudo dpkg-reconfigure  keyboard-configuration" on my ubuntu 14.04.4 LTS server running in a virtual box. ](*,)Even if I change with the help of this command to the German keyboard the layout still is English.:confused: I must change my keyboard layout to the German keyboard layout. I have no graphical interface installed. How to change the keyboard layout if the change with "sudo dpkg-reconfigure  keyboard-configuration" has no effect? :confused: How to force to German keyboard layout? :confused:

Dirk Lehmann

---

### Post by papibe on 2016-03-10
Hi dirk-lehmann.

Try this:
```
sudo apt-get install console-data

sudo dpkg-reconfigure console-data

sudo dpkg-reconfigure keyboard-configuration
```
Hope it helps. Let us know how that goes.
Regards.

---

### Post by dirk-lehmann on 2016-05-19
Hi papibe,

I executed all the commands your wrote. I chose 105 key, latin1 and german keyboard settings in the dialog. Still my keyboard setting is english. The commands did not fix my problem!

Also I did a sudo shutdown -r now after the commands you wrote. But the english keyboard is still active.

Is it that much complicated to change from english keyboard layout to german keyboard layout?

I am thinking about to buy a support contract from canonical. But will they be able to fix my problem with the keyboard layout?

Please send me further more ideas to change my keyboard laylout from englisch to german on my ubuntu 14.04.4 virtual maschine.

Best regards,

Dirk Lehmann

---

### Post by dirk-lehmann on 2016-06-14
I need to change the keyboard layout for the terminal console. There is no GUI running at the virtual machines. 

Other commands?

Other things to change somewhere in some configuration files?

The keyboard layout on the virtual box host (also running ubuntu) is correct, but the virtual machines running Ubuntu show the english keyboard layout even after execution of the commands (and correct configuration in the dialogs shown by those commands) which are allready thill now written in this thread.

Hopeing getting this problem solved.

Best regards 

Dirk

---

### Post by dirk-lehmann on 2016-06-14
bump

---

