---
title: "Ubuntu 18.10 after period of time wont open windows"
date: 2019-01-21
forum: General Help
---

### Post by cheltgar on 2019-01-21
Hi

I have recently upgraded to ubuntu 18.10.

When I boot, everything works correctly, however after a period of time - say 30 mins, I loose all windows. I can see that the programs are still running (if i right click on the favourites bar, and show all windows, there is an accurate image of the running window (although i cant see it). Also if i click a new icon, then the red blob indicates it has been launched, but i dont see a window. (again, right clicking on the icon and showing all windows, indicates there is a window).

Also, after the period when I loose windows, if I go to the top right hand Icon to reboot, then only the volume and Wired Connection are shown, the restart / users eg are gone (they are there when i first boot.

I am just running a single monitor (not sure if Ubuntu thinks there are two monitors connected all of a sudden). I have installed a Dummy monitor as generally dont have a monitor connected, but had exactly the same problem when this was not installed and had a monitor connected.

First time this occurred I wondered if the upgrade had not been successful, so I have done a full fresh install, and have the same problem.

Should also say, I am getting a crash reported from Plymouthd. Didnt have this before 18.10.
This is probably related, I guess. 

Message- plymouthd assert failure: plymouthd: ./plugin.c:1244: set_handler_for_input_sourece: Assertion 'has_inout_source (backend, input_source)' failed.
Not sure if that means anything to anyone?

Thanks

Gareth

---

### Post by cheltgar on 2019-01-21
Have found a report of the Plymothd error as a bug [https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/1802993](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/1802993) .. so maybe its unrelated, as cant find any other people finding issues with windows they cant get to

---

