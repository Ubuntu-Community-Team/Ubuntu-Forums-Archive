---
title: "Kubuntu Updates Error"
date: 2019-08-13
forum: General Help
---

### Post by jbh54enwiler on 2019-08-13
I recently switched to Kubuntu from GNOME-based Ubuntu and until now everything has worked fine.  But now when I go to update my software through Discover, the update progress bars freeze about halfway through, then an error pops up.  After the error comes up, it will usually clear all the updates from the list as if the update completed successfully, which I'm not sure if it's actually updatijng my system.  See the attached image for a screenshot of the error message.  So far I've tried running sudo apt-get update and that didn't work.

---

### Post by Impavidus on 2019-08-14
I don't know Discover and I don't use Kubuntu. But I know the terminal. Try this:```
sudo apt update
sudo apt upgrade
```Error messages there will tell us what's going on.

---

### Post by SeijiSensei on 2019-08-14
Usually I have no issues with updating via Discover or from the command prompt as Impavidus recommends.  (Usually I choose the latter route.)

I checked, and I do have /lib/modules/5.0.0-23-generic/kernel/drivers/media/common/cx2341x.ko.  However it is the driver for an [obscure piece of video decoding hardware]("https://www.linuxtv.org/wiki/index.php/Conexant_CX2341x") that I doubt you have on your system.  I ran "lsmod" and that module is not loaded in my system.  The page at linuxtv.org dates back to 2012.

I suggest you try deleting the copy you have as root with sudo:

```
sudo rm -f /lib/modules/5.0.0-23-generic/kernel/drivers/media/common/cx2341x.ko
```

then try running Discover or update/upgrade again.  Maybe it will download the new copy and install it correctly.

---

### Post by jbh54enwiler on 2019-08-14
I ran sudo apt upgrade and it told me to run "apt --fix-broken install"
I ran that and it was unable to write to [FONT=monospace][COLOR=#000000]/var/lib/dpkg/info/linux-modules-5.0.0-25-generic.list-new' because the operation wasn't permitted.  Then it said "segmentation fault" and it stopped.[/COLOR]
[/FONT]

---

### Post by Impavidus on 2019-08-15
The complete output might help. There maybe something important in it that you skipped in your summary.

Also, what do you get from```
ls -ld /var/lib/dpkg/info
ls -ld /var/lib/dpkg/info/linux-modules-5.0.0-25*
```
Segfaults aren't supposed to happen. This means that something really unexpected occured.

---

### Post by SeijiSensei on 2019-08-15
> **jbh54enwiler said:**
> I ran sudo apt upgrade and it told me to run "apt --fix-broken install"
I ran that and it was unable to write to [FONT=monospace][COLOR=#000000]/var/lib/dpkg/info/linux-modules-5.0.0-25-generic.list-new' because the operation wasn't permitted.  Then it said "segmentation fault" and it stopped.[/COLOR]
[/FONT]

You ran that apt command with sudo, right?

---

