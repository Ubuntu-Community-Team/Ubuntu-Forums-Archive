---
title: "Upgrade Problem"
date: 2007-01-22
forum: General Help
---

### Post by reb68 on 2007-01-22
I upgraded to 6.10 and all went well. I did it with a cd I burned from the downloaded .iso.
Yesterday the font was enlarged and when I went to monitor settings there was no way to reduce it. Then the 6.10 would not boot up. It goes as far as the Kubuntu screen and then blacks out. It leaves a flashing curser that will take typeing but I do not know how to proceed.
I tried /cdrom/cdromupgrade with the cd inserted but this did not work.
Please help as I do not want to lose my documents. (it is tax time)
I did the recovery mode but when it ends at a /root-dekstop# prompt I do not know what to do.
Thanks.

---

### Post by renzokuken on 2007-01-22
may be there was some grafix jiggery pokery going on when you upgraded and your xorg.conf has been reverted to an unrecognised driver.

what grafix card do you have?

when u get to the flashing cursor, press Ctrl+Alt+F1 and login at the CLI. then type

```
sudo nano /etc/X11/xorg.conf
```

and scroll down to Devices section and see what is listed opposite "Driver"

post it here, (posting your whole xorg.conf would be preferable but thats alot of typing

---

### Post by reb68 on 2007-01-23
I followed your instructions and this is the result. 
driver    kbd
driver    mouse
driver    wacom   (stylus)
driver    wacom   (eraser)
driver    wacom   (curser)
driver    ati
driver    ATI Technologies
---------------
Does this information help?
Is this what you wanted?
I tried to copy/paste but I have to close and boot Windows to get to the internet and this forum.
Hope you can help.
Dick

---

### Post by renzokuken on 2007-01-23
ok, sounds like its screwed around with the drivers.

go back to your xorg.conf

```
sudo nano /etc/X11/xorg.conf
```

and change the line

Driver  "ati"

to

Driver "vesa"

Ctrl+X and follow options to save and exit.

now reboot, this should give you basic grafic functionality, and from here, you should be able to install the proper ati driver (search for "fglrx howto") using some of the superb guides here ...... i'm obviously assuming you actually DO have an ATI card in your machine

---

