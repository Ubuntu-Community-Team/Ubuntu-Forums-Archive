---
title: "Monitor power saving"
date: 2006-07-03
forum: General Help
---

### Post by jeremy on 2006-07-03
I set my power saving to "switch off monitor after 2 minutes", and it works fine, but every time I reboot it resets itself to 30 minutes.
Any ideas as to how I can force it to remember?

---

### Post by Skrim on 2006-07-08
I have a similar problem. The power saving constantly reverts to 30 minutes. It also ignores being turned off, happily switching the screen off after 30 mins.

---

### Post by der_joachim on 2006-07-09
> **jeremy said:**
> I set my power saving to "switch off monitor after 2 minutes", and it works fine, but every time I reboot it resets itself to 30 minutes.
Any ideas as to how I can force it to remember?

Where did you set your power saving mode? The xorg.conf file or your Gnome/KDE/XFCE control panel? Maybe one overrides the other?

Just a thought...

---

### Post by Tulip on 2006-07-14
I have the same problem as Skrim - Id like to turn the power saving mode off, but my monitor stubbornly refuses to stay on. I have used System>Preferences>Power management. What am I missing?

---

### Post by Pyro MX on 2006-07-14
I have a similar problem too - I cannot turn on power saving for my monitor. Everytime I restart X, it turns back off. I try to set it from the System Settings pannel in Kubuntu 6.06.

---

### Post by Pyro MX on 2006-07-14
It seems it is a [KDE3.5.3]("http://bugs.kde.org/show_bug.cgi?id=128610").

Found the solution [in this thread]("http://www.ubuntuforums.org/showthread.php?t=188832"):
> **snowx1000 said:**
> Time for the bug fix! After running systemsettings through the console I discoverd that it uses xset for dpms which loses its effect after each reboot. I was also missing the DPMS option from my Xorg.conf. When I edited the monitor with systemsettings it put two monitors, which I do not have. That was confusing the screensaver.

So here is what to do:

First check for dual monitor entries in /etc/X11/xorg.conf.

Second make sure there is Option "DPMS" in the "Monitor" section.


Edit: Option "OffTime" "30" belongs in the ServerLayout section.
That will turn the monitor off after 30 mins, adjust accordingly.

Hope this helps!

It should work to turn on power saving, but try it to turn it off and set the offtime, maybe it'll work.

Edit: better write "offtime" "30" instead of "OffTime" "30". I don't know why, but with upper cases, it set the values to 5 hours.

---

