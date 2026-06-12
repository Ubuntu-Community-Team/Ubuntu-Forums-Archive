---
title: "CPU and GPU temp indicator 12.10?"
date: 2012-10-30
forum: General Help
---

### Post by Twilk73 on 2012-10-30
I am looking for a cpu and gpu temp indicator are there any available at the moment. I found a diffrnet system indicators for cpu speeds and the likes but thats not what I am interested in. Thanks in advance.

---

### Post by pqwoerituytrueiwoq on 2012-10-30
i know back in gnome2 i used sensors-applet (not sure if that works with unity)
i know conky can monitor temps
if you are using xfce i have some genmon scripts for temps

---

### Post by Twilk73 on 2012-10-31
xfce not sure. I am using 12.10 unitiy, forgive my newbiness.

can i search for the sensors applet?

sudo apt-get search sensors applet?

---

### Post by pqwoerituytrueiwoq on 2012-10-31
```
sudo apt-get install sensors-applet
```notice the dash (-)
if it wants to pull 20 to 100 packages it is not what you want
ubuntu uses unity
lubuntu uses lxde
xubuntu uses xfce
kubuntu uses kde
gnome-ubuntu uses gnome

psensor may be what you want for unity

---

### Post by Linuxisfast on 2012-10-31
Alex Murray's excellent indicator-sensors which has its own ppa at [https://launchpad.net/~alexmurray/+archive/indicator-sensors](https://launchpad.net/~alexmurray/+archive/indicator-sensors) wonder why this isn't included in USC or installed by default. You don't need hddtemp or lmsensors for this, it reads off the ACPI pool on supported hardware.

---

### Post by Mark Phelps on 2012-10-31
I believe that sensors-applet uses the info returned from lm-sensors, which is NOT installed by default.

You need to do the following:
1) install lm-sensors
2) once installed, enter "sudo sensors-detect" in a terminal and responde yes to all prompts
3) reboot
4) once rebooted, open a terminal and enter "sensors".

If you see a long list of temperature readings, it worked.

---

### Post by Rebelli0us on 2012-10-31
Another possibility is to [add Mint MATE desktop]("http://mate-desktop.org/") to Ubuntu 12.10. I've installed it and sensors work fine on the panel.

---

### Post by KegHead on 2013-01-01
> **Mark Phelps said:**
> I believe that sensors-applet uses the info returned from lm-sensors, which is NOT installed by default.

You need to do the following:
1) install lm-sensors
2) once installed, enter "sudo sensors-detect" in a terminal and responde yes to all prompts
3) reboot
4) once rebooted, open a terminal and enter "sensors".

If you see a long list of temperature readings, it worked.

Hi!

Thanks..this worked for me.

KegHead

---

### Post by Skoobs on 2013-02-03
> **Linuxisfast said:**
> Alex Murray's excellent indicator-sensors which has its own ppa at [https://launchpad.net/~alexmurray/+archive/indicator-sensors](https://launchpad.net/~alexmurray/+archive/indicator-sensors) wonder why this isn't included in USC or installed by default. You don't need hddtemp or lmsensors for this, it reads off the ACPI pool on supported hardware.

is there a way to get this program to display two temperatures at the same time? GPU and CPU? I can only seem to choose one or the other.

---

