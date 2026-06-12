---
title: "Mouse problem in Xubuntu"
date: 2007-05-18
forum: General Help
---

### Post by jSepia on 2007-05-18
I recently installed Xubuntu (using the alternate install CD because I only have 128MB RAM). So far, it's the best distribution I've ever tried since I met Linux 10 years ago, but I only have one problem: my mouse doesn't work at all. No movement, no clicks. I had to enable "mouse emulation" in Xfce to be able to do stuff.

My mouse is a generic optical PS/2 mouse. It has worked flawlessly on countless other distributions (including the Ubuntu 6 LiveCD). Other distros detect it as /dev/psmouse, /dev/mouse or /dev/mouse0, so I tried putting that in xorg.conf (xubuntu originally detected the mouse as /dev/input/mice). I also tried both "PS/2" and "ImPS/2" as the protocol. No result. :( Do you think the problem could be somewhere else?

I tried using a normal (non-optical) PS/2 mouse, and then a Serial mouse, but they didn't work either. Any help is appreciated.

---

### Post by kvonb on 2007-05-20
Hi,

I will be installing Ubuntu 7.04 server edition on an old system later today which has a serial mouse, I will post back with the answer if I have any useful info for you :)

---

### Post by kvonb on 2007-05-22
OK, here is the solution, well it worked for me anyway :).

This is for a serial mouse on com1, for com2 simply substitute ttyS0 for ttyS1 and so on.

Also be careful with the "S", it is an uppercase "S", not lowercase!!!  That caused me many hours of headaches :S.

```
sudo ln -S /dev/ttyS0 /dev/input/sermouse
```

Now edit your xorg.conf and change a few lines.  I'm assuming that you are using a terminal (text mode) seeing as your mouse isn't working anyway.  Simply substitute "nano" in the line below for "gedit" if you would rather do it from the desktop.

sudo nano /etc/X11/xorg.conf

Look for the following lines in the first "Section InputDevice" line:

```
Option         "Protocol" "auto"
Option         "Device" "/dev/psaux"
```

I don't know if you can leave the Protocol as auto as it didn't have that option on the xorg.conf that I was using, Try it and see what happens, otherwise change protocol to "Microsoft" as shown below:

```
Option         "Protocol" "Microsoft"
Option         "Device" "/dev/input/sermouse"
```

Save and exit the editor, now either restart the computer or logout of the desktop then restart X like so:

sudo /etc/init.d/gdm restart

Hope that worked for you.

Regards, Kev :)

---

### Post by jSepia on 2007-05-23
Thank you _a lot_ for taking the time to help me. :) I'll try it at home and see if it works.

---

### Post by kvonb on 2007-05-23
> **jSepia said:**
> Thank you _a lot_ for taking the time to help me. :) I'll try it at home and see if it works.

You are most welcome :)

Regarding your PS/2 mouse, all I can suggest is make sure that you have all the updates, I really see no reason why your mouse won't work :confused:.

If you boot from a standard Ubuntu CD on the same computer does it work?  I know you said you tried that, but I'm not sure if it was on the same machine.

Do you have a PS/2 to USB mouse adaptor?  Maybe give that a try.

Also make sure that IRQ 12 is enabled in the computers BIOS, it might say something about Mouse or PS/2 you will have to search as BIOS are all different.

Good luck!

Regards, Kev :)

---

### Post by Shinoda on 2007-11-02
> **kvonb said:**
> I don't know if you can leave the Protocol as auto as it didn't have that option on the xorg.conf that I was using, Try it and see what happens, otherwise change protocol to "Microsoft"
```
Option "Device" "/dev/ttyS0"
Option "Protocol" "Microsoft"
```did it for me. [FONT=Courier New]Auto[/FONT] didn't work, and the symbolic link seems to vanish after rebooting. Thank you so much, kvonb. ;)

Edit: I later found an older [thread]("http://ubuntuforums.org/showthread.php?t=202972#post1176847") with the above solution. Guess I didn't lurk enough the first time.

---

