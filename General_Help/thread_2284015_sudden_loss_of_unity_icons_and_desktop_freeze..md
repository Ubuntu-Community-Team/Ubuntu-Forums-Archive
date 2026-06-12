---
title: "sudden loss of unity icons and desktop freeze."
date: 2015-06-26
forum: General Help
---

### Post by Sbarton on 2015-06-26
Hi everybody! it's been sometime since I posted here, just shows how things have been going well. Anyway, I have looked at various similar posts but have not helped.
What has been happening on a fairly regular basis is that I have been logged on the internet via either Opera/Seamonkey when for no particular reason the desktop looses unity icons, the browser disappears, and it is frozen. It may be a browser link? but it is not the same each time, in fact I was looking at the forums just 5 minutes ago and it happened again. unity icons were no longer and desktop froze so it was a matter of pressing the shut down button to reboot. I have done a memory test and hard disk check and it seems fine. Ubuntu is installed on a usb hard drive which is fairly new and seems fine. The laptop I am using has win 7 installed and I have to say this experience does not happen with windows. It has never happened with other incarnations of ubuntu which I have had since 'Hoary' It has happened with ver 14.04 LTS. Any suggestions of help appreciated.
Regards
Sbarton

---

### Post by steveo314 on 2015-06-26
reboot your pc and boot into ubuntu. when you get to the login in screen hit ctrl + alt + f1 and then login there. follow these steps and see if it works:
sudo apt-get update
sudo apt-get install --reinstall ubuntu-desktop
sudo apt-get install unity
sudo shutdown -r now

Unity was having issues in Trusty from what I've found on Google.

---

### Post by kostkon on 2015-06-26
Well, Unity stopped working for some reason. You could drop to TTY and do a:
```
setsid unity
```
to restart it.

In case of that failing you could restart your X with:
```
sudo service lightdm restart
```

And, as a final resort you could try the [REISUB]("https://en.wikipedia.org/wiki/Magic_SysRq_key") key combo instead of powering down your system, which is pretty a unsafe thing to do in general, regardless of the OS and hardware.

---

### Post by Sbarton on 2015-06-28
OK! thanks kostkon, and stevo314 for your replies. Stevo, I had performed your suggestion before, it worked but has not solved the incidences of it happening. Kostkon thanks for reminding me of that. Actually I was preparing to answer the replies yesterday when same thing happened, browser disappears and no icons available and it is frozen. I am up and running again and am actually typing this from my windows drive so that it does not happen again. I am ok! now with restarting ubuntu but I am not confident it is not going to happen again which is a pain in the rear when it does. So just maybe it is to do with a browser on linux drive, maybe a script or something? I favourite browser is Opera which I know is not fully supported now by the Opera people. I suppose the google browser (which seems to have bits of Opera in it) can be tried but to be honest I am not particularly happy with the Big Brother Google. OH! well I'll plug away with it.
All the best and thanks again!
sbarton

---

