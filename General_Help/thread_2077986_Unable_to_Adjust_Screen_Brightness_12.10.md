---
title: "Unable to Adjust Screen Brightness 12.10"
date: 2012-10-29
forum: General Help
---

### Post by mathiasbrownjr on 2012-10-29
Hello! I have just installed Ubuntu 12.10 on my Acer Aspire One 725 but I cannot seem to adjust my screen brightness and it is stuck on maxmimum draining my battery quickly. I have searched through every thread but nothing seems to work for my specific laptop. I have tried editing my ```
/etc/default/grub

``` as tried in many other threads but it has not worked for me. I might also add that I have tried using both Fn + L and R arrow keys, as well as going to the system settings and adjusting the screen brightness (although after I messed with the /etc/default/grub the brightness slider has disappeared for some reason). If anyone could provide some insight into the issue that would be great. Also let me know if you need any more information regarding my system.

Thanks in advance,

matt

---

### Post by JakeXsV on 2012-11-01
I have the same issue. I also tried installing xblacklight and that failed. I successfully installed it and set my brightness to different things but the actual screen brightness never changed.

Hopefully someone has a solution?

Dell XPS 13 (64 bit)

---

### Post by mathiasbrownjr on 2012-11-07
bump

---

### Post by mathiasbrownjr on 2012-11-24
bump

---

### Post by ohmy28 on 2012-11-24
I wrote my self a little guide cause i had this problem a while ago.


Be in sudo:

Open /etc/default/grub with your favorite text editor, ie gedit

    gksudo gedit /etc/default/grub

Look for the line

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

and add acpi_backlight=vendor to it so that it reads

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"

Update grub to include the changes done

sudo update-grub

Reboot

sudo reboot


Source: [http://www.techjail.net/solved-brightness-problem-in-ubuntu-12-04-precise-pangolin.html](http://www.techjail.net/solved-brightness-problem-in-ubuntu-12-04-precise-pangolin.html)

---

### Post by mathiasbrownjr on 2012-11-24
Thanks for the response ohmy28 but that did not work for me. This issue has been a problem in almost every linux distro I have tried including Linux Mint, Peppermint, and Ubuntu 12.04 and 12.10 It is frustrating because it limits my battery life to about an 1.5 hours.

---

### Post by ohmy28 on 2012-11-24
Have you tried looking at this post both Acer so it might help
[http://ubuntuforums.org/showthread.php?t=1864513](http://ubuntuforums.org/showthread.php?t=1864513)

---

### Post by mathiasbrownjr on 2012-11-24
I have tried this before and it still does not work for my netbook. One interesting note I might add is that after I did the grub update the screen brightness slider(under Settings and then under Brightness and Lock) has completely disappeared.

---

### Post by ohmy28 on 2012-11-24
holy crap! Well I truly don't know then...

---

### Post by mathiasbrownjr on 2012-11-24
Thanks for your help ohmy28. I have even tried reinstalling but this has not helped either. I am hoping someone out there has some sort of solution for this! Anybody?!?

---

### Post by ohmy28 on 2012-11-24
I'd also post this question at askubuntu.com see if the folks over there can help you out

---

### Post by mathiasbrownjr on 2012-11-24
Thanks! I think someone out there has to have a solution to the problem. I might just be looking in the wrong place.

---

### Post by smalss on 2012-11-27
Are you guys using 64 bit or 32 bit? Don't know if that would make a difference, but stranger things have happened out there.

---

### Post by speedwlk on 2012-11-27
Each different vendor measures brightness is different scales. For your machine, find out the value of max-brightness by running the following command in terminal:

```

/usr/lib/gnome-settings-daemon/gsd-backlight-helper --get-max-brightness 

```

Say that it is 10. Then to set the brightness at half, run this command:

```

pkexec /usr/lib/gnome-settings-daemon/gsd-backlight-helper --set-brightness 5

```

Hope this works for your machine.

---

