---
title: "Close lid on laptop, screen dies"
date: 2006-11-23
forum: General Help
---

### Post by gitargr8 on 2006-11-23
I've got an older Dell 8200 that I've installed Kubuntu on. The problem is that when I close the lid on the laptop, when I open it again, the screen is dead. Pressing keys and moving the mouse does nothing to bring it back. 

Seems as though the only thing I can do is hit the power button, then I see the Kubuntu shutting down screen and I have to restart. I checked the power settings, and it is set to do nothing on lid close.

I don't know if it is related, but I wasn't able to install the nvidia driver, threw an error about not being the correct kernal version... if it is relevant I can post the exact error. Anyway, x is running on the nv driver now.

Any help would be appreciated. 

~Ryan

---

### Post by awbassett on 2006-11-23
I also have an Inspiron 8200 and have this same issue.

First, make sure you're running the latest kernel before you try and install nvidia-glx.

sudo apt-get update
sudo apt-get upgrade (If you see the kernel being held back, use dist-upgrade, as it is a little more aggressive handling upgrades).

reboot

sudo apt-get install nvidia-glx

change nv to nvidia in /etc/X11/xorg.conf

As far as the screen issue, I generally have to hit ctrl+alt+F6 and then ctrl+alt+F7 and it will bring back up X.

---

### Post by gitargr8 on 2006-11-24
Wasn't able to get any updates:
```

root@worklaptop:~/Desktop/cpp# sudo apt-get update
...
Fetched 5B in 9s (1B/s)
Reading package lists... Done

root@worklaptop:~/Desktop/cpp# sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

root@worklaptop:~/Desktop/cpp# sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
I'll see what kernel, try to install the nvidia driver again, and we'll see what happens. Thanks for the key sequence tip.

~Ryan

---

### Post by awbassett on 2006-11-24
have you rebooted to make sure you're running the the latest installed kernel?

---

### Post by gitargr8 on 2006-11-24
Just checked Adept, I have Kernel 2.6.17-10 installed. I have rebooted since I did the update. I noticed on [kernel.org]("http://www.kernel.org") the newest stable kernel is 2.6.18.3, but it is not in the Ubuntu repositories. 

I'll try taking another stab at installing the nvidia driver and see how it goes. Pressing ctrl+alt+f6, ctrl+alt+f7 doesn't bring the screen back to life.

---

### Post by gitargr8 on 2006-11-25
Does it matter if I have the generic linux headers, and not the 386 headers?

---

### Post by gitargr8 on 2006-11-25
Found some more people with this problem, they have a fix posted [here]("https://launchpad.net/distros/ubuntu/+source/xorg-server/+bug/61746").

---

### Post by gitargr8 on 2006-11-26
Just a heads up, I found a [fix]("https://launchpad.net/distros/ubuntu/+source/xorg-server/+bug/61746") that seems to have worked for the time being.

Open up your xorg.conf file... 

```
sudo nano /etc/X11/xorg.conf
```

and add the following:

```

Section "ServerFlags"
        Option "NoPM"
EndSection

```

If you already have a Section "ServerFlags", then just add the NoPM option to that section.

Hit Ctrl+O to save, and Ctrl+X to exit nano.

~Ryan

---

### Post by stevoo on 2007-10-01
well i am having the same problem ....
on a dell insipron 6400 .... that wasnt there before

WHen i close the lid and  reopen it  it will not appear ( somethimes ) 
If i close and open it a few times perhpas i will get lucky and ill get the login screen again ! 

Else hard reboot..

I have tried your suggestion, but it seems i have to close the screen open it and then close it again in order for it to close. As the first time i close it the screen remain open (weird ) and by reopening  and reclosing it will close. 
Now the first time i tried it, the screen come back normally, the second time i had to do it three times to get the screen back ......

anything i can change on that ?
-----------------------------------------------------------------------------------------

it seems to be working just fine right know .... i believe this has solved my problme 
TY

---

### Post by Cyvros on 2007-10-01
Not really helpful, but I have a similar problem with my Inspiron 1501 - every so often, the screen won't turn on when I open it, but closing it and reopening it generally solves it. No idea why - happened with Windows as well, so I assume it's hardware-related...

---

