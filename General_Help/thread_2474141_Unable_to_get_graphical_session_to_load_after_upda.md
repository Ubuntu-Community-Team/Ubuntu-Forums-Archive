---
title: "Unable to get graphical session to load after updates"
date: 2022-04-22
forum: General Help
---

### Post by challdns on 2022-04-22
lsmod shows I have properly loaded nvidia
logs show XORG -EE no screen found
restarting GDM3 does the same

I know the hardware is good because I can boot livecds and it works fine


any ideas?

---

### Post by challdns on 2022-04-22
I will also add that startx works as root, while running it under a normal says no screens found

---

### Post by #&amp;thj^% on 2022-04-22
running X as root makes the **.Xauthority **and **.ICEauthority **files owned by root>> Not a good practice.
Nvidia drivers can cause this as well:
Remove all the Nvidia drivers

```
sudo apt remove --purge '^nvidia-.*'

```
see if we can fix this as well
```
sudo rm .Xauthority
sudo rm .ICEauthority
```
reboot we can deal with the nvidia driver after

---

### Post by challdns on 2022-04-22
I've purged nvidia everything and removed .Xauthority,

 .ICEauthority seemed not to exist

This booted into gdm, so its got to be something to do with nvidia

---

### Post by #&amp;thj^% on 2022-04-22
If you still want the nvidia driver.
Software Updates&#8674;Additional Drivers&#8674;**_select recommended _**&#8674;Apply Changes &#8674;reboot

---

### Post by challdns on 2022-04-22
I was using the dkms version since I was using an odd kernel, the FIPS kernel

After reinstalling the nvidia 470 driver through the gui, It gets hung at a screen that says fips check done and has a blinking cusor under it

systemctl status gdm3 says modprobe FATAL module nvidia not found in directory /lib/modules/5.4.0-1037-fips

---

### Post by #&amp;thj^% on 2022-04-22
I guess purge again, don't know how to advise you on that FIPS kernel.
sorry about that, and good luck.
here's what a developer had told me.
> we have not yet verify FIPS kernel cryptography,
could you please contact with nvidia sales team if you need further supports.
thanks
looks like rough sailing with drivers and that kernel. :(

---

### Post by challdns on 2022-04-22
Thats silly because a lot of classified workloads will want to use cuda in a linux dev environment

I ran 
update-initramfs - u - k all 
update-grub
when it said it couldnt find the module

That got it booting into gdm3 again

Im not sure why it broke in the first place though, the one the gui installed is the same dkms version that I had installed earlier :lolflag:

Whats even weirder is I rebooted the machine a good 8 times yesterday testing for reliable booting, and then did it again this morning and that's when it started failing to load, the thing was off network throughout the night. So the whole situation is just strange. 

Im going to just keep rebooting it over and over add see if it stays working

---

