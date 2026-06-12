---
title: "Buttons not working for T60p"
date: 2008-01-09
forum: General Help
---

### Post by eTronicGaming on 2008-01-09
Hey, I've got a Lenovo Thinkpad (T60p), and when installing ubuntu 7.10, every button used to work.. all function keys, brightness, volume, and thinkvantage (which I assigned to open a terminal window when pressed).

However, I was following some tutorial on getting better battery lifetime use on laptops, and I think I changed an acpi setting or something, because now the volume, thinkvantage, and most function keys don't work (like brightness).  Do you know what I can do to fix this?  I tried reinstalling the kernel, and reundoing my steps I did following the tutorial... but I'm not sure.  Here are some of the commands I used during that time:

acpi
acpi -V
sudo vim /etc/default/acpi-support
sudo apt-get install ubuntu-laptop-mode
sudo apt-get install laptop-mode-tools
sudo apt-get install laptop-detect
sudo apt-get install cpuf reqd
sudo apt-get install cpufreqd
sudo apt-get install cpufrequtils
sudo apt-get install uswsusp
sudo s2disk
cat /proc/cpuinfo

I "apt-get remove"d all of those, and changed the acpi-support file back to normal, but I can't figure out what went wrong and why my buttons don't work anymore.  I even tried rmmod/modprobe thinkpad_acpi and ibm_acpi thinking that might help but it didn't work.

Please if anyone can help, thanks!

-Josh

---

### Post by eTronicGaming on 2008-01-10
Please... anyone?

---

### Post by Gotterdammerung on 2008-04-26
try configuring your keyboard. it solved my problem.

---

### Post by Dougie187 on 2008-07-23
Not sure if your prolem is solved or not.

But bascially, there are directions here.
[http://www.thinkwiki.org/wiki/How_to_get_special_keys_to_work#acpi_fakekey](http://www.thinkwiki.org/wiki/How_to_get_special_keys_to_work#acpi_fakekey)

You have to read the walkthrough on it, and your buttons *should* already be set up. Mine were at least, however my thinkvantage button was set to a keycode that for some reason didn't generate an event.

Where the directions say to use $KEY_MACRO mine was defaulted to using $KEY_PROG1. This for somereason didn't work.  I changed to $KEY_MACRO (key 112) and it generated an event then. There are proabably other keys that you can set it to as well, but this is just how I did it in my case.

---

