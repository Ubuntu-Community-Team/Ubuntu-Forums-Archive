---
title: "Ubuntu is killing my laptop's batteriES. What to do?"
date: 2013-02-08
forum: General Help
---

### Post by mercmobily on 2013-02-08
Hi,

After 3 years of using Ubuntu on my laptops, I noticed that after less than 1 year the battery capacity is only 50% of what it was when I first used it.

I use my laptop in a pretty standard way: it's connected as much as possible, with the laptop leaving the recharger every now and ten for a few hours (or a few minutes at times).

I have a Thinkpad Edge E320.

Now... the first odd thing is that I don't have the usual files in /proc:

# ls /proc/acpi
button  event  ibm  wakeup
#

No battery or anything. OK...

I found this post that seems to suggest that the best way not to kill your battery is to only start recharging when it's more than 50% drained, and stop charging at 97%:

[http://leadorg.wordpress.com/technology/thinkvantage-power-manager/how-to-tpm-to-prolong-your-battery-life/](http://leadorg.wordpress.com/technology/thinkvantage-power-manager/how-to-tpm-to-prolong-your-battery-life/)

I saw this thread that seems to confirm that:

[http://ubuntuforums.org/showthread.php?t=546537](http://ubuntuforums.org/showthread.php?t=546537)

I remember reading on the Lenovo web site itself that for thinkpads their Windows driver has a special mode for laptops that are often attached to the recharger (such as mine). I cannot find it anywhere though -- sorry.

I already have tp_smapi, and can get to the battery information through smapi:

# /sys/devices/platform/smapi/BAT0# cat last_full_capacity 
28040
# /sys/devices/platform/smapi/BAT0# cat design_capacity
62160

Gosh, worse than I thought.

So, questions:

* How come I don't have anything in /proc?

* What values shall I set, in start_charge_thresh and stop_charge_thresh, in order to keep my battery from dying?

* Is there a GUI somewhere where I can set these values and make them stick? (If not, OK no biggie

* Is there a way to "recover" this battery so that it goes back to something acceptable?

Any other info would be super-welcome.

Merc.

---

### Post by mercmobily on 2013-02-08
Sorry, subscribing...

---

### Post by offgridguy on 2013-02-08
I haven't tried this but it looks interesting.

[http://ubuntuforums.org/showthread.php?t=1607911](http://ubuntuforums.org/showthread.php?t=1607911)

A lot of reading but maybe worth a look regarding undervolting.

[http://ubuntuforums.org/showthread.php?t=786402](http://ubuntuforums.org/showthread.php?t=786402)

---

### Post by mercmobily on 2013-02-08
Hi,

Alright, first answer down:

> **mercmobily said:**
> Hi,
* How come I don't have anything in /proc?


Easy one: /proc/acpi/battery is now gone. The new one is sys/class/power_supply/ 

The important ones, that I really feel need to get an answer to before I stick the new battery in:

* What values shall I set, in start_charge_thresh and stop_charge_thresh, in order to keep my battery from dying?

* Is there a way to "recover" this battery so that it goes back to something acceptable?

Thank you,

Merc.

---

