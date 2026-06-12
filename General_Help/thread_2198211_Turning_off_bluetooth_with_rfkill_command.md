---
title: "Turning off bluetooth with rfkill command"
date: 2014-01-07
forum: General Help
---

### Post by CaptainMark on 2014-01-07
I use bluetooth once in a blue moon (no puns) so leaving on all the time is a waste of my laptops battery which has no hardware switch for it so I looked online for a way to have bluetooth switched of (apparently xfce doesn't retain its previous on/off state like gnome based DE's do) and found this post [http://tacticalvim.wordpress.com/2012/08/10/disable-bluetooth-by-default-in-xfce-and-gnome/](http://tacticalvim.wordpress.com/2012/08/10/disable-bluetooth-by-default-in-xfce-and-gnome/) 

I have two questions:
1. Is this still the best method to disable bluetooth permanently or has it been superseeded by another method I don't know of?
2. Is it safe(ish) to use sudoers to remove the password from the rkfill command as this command needs root to work


Regards
Mark

---

### Post by varunendra on 2014-01-10
Doesn't the bluetooth applet in Xubuntu give you the option to turn it on/off? It is the same thing that "rfkill block/unblock" command does. And as far as I know, the soft block is same as hard block (using a hardware switch) in terms power saving on radio devices like wifi or bluetooth. So whether blocked by the command or the applet, you shouldn't need to worry about its power consumption as long as it is kept off by these.

But if you want to keep it permanently off, just blacklisting the "btusb" driver should do the job -
```
echo "blacklist btusb" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Since next boot, it should be turned off. To enable it again either remove or comment out the blacklist line. To remove it via commandline -
```
sudo sed -i '/blacklist btusb/ d' /etc/modprobe.d/blacklist.conf
```

> **CaptainMark said:**
> 2. Is it safe(ish) to use sudoers to remove the password from the rkfill command as this command needs root to work

Doesn't need sudo here on my Ubuntu 12.04.

---

### Post by CaptainMark on 2014-01-10
I dont want to permanently kill it with no chance to use it at all just start with a soft block, and XFCE has had a bluetooth problem for a long time, basically you can disable bluetooth with the applet but it will turn on again when you log back in

---

