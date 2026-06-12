---
title: "DELL Vostro 3460 Wi-Fi not working"
date: 2012-10-29
forum: General Help
---

### Post by khurtsiya on 2012-10-29
Just bought new DELL Vostro 3460 with preinstalled Ubuntu - Wi-Fi worked out of the box. But that was 11.04.

After I made fresh install of 12.04 my - Wi-Fi card was not recognized.

I tried to install 11.04 and 12.10 with no  luck. I guess Wi-Fi driver is only on preinstalled 11.04. 

I already looked here

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/927782](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/927782)

here

[http://askubuntu.com/questions/125529/wireless-doesnt-work-on-a-broadcom-bcm4312](http://askubuntu.com/questions/125529/wireless-doesnt-work-on-a-broadcom-bcm4312)

here

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/701259](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/701259)

here

[http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560](http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560)

here

[https://bbs.archlinux.org/viewtopic.php?id=145884](https://bbs.archlinux.org/viewtopic.php?id=145884)

and finally here

[http://ubuntuforums.org/showthread.php?t=1928241](http://ubuntuforums.org/showthread.php?t=1928241)

No luck!

If anybody have any idea - will glad to check it.

---

### Post by Androzani1 on 2012-10-29
You did enable the driver right?

---

### Post by khurtsiya on 2012-10-29
What do you mean? It is not working.

---

### Post by Androzani1 on 2012-10-29
> **khurtsiya said:**
> What do you mean? It is not working.

This may sound thick, but is the wifi switch turned on?

If not, you need to go to your hardware menu and check all of the drivers are enabled.

---

### Post by khurtsiya on 2012-10-29
There are no hardware switch.

When I go System settings -> Additional drivers - there are nothing to acitvate there because it is empty.

---

### Post by Androzani1 on 2012-10-29
> **khurtsiya said:**
> There are no hardware switch.

When I go System settings -> Additional drivers - there are nothing to acitvate there because it is empty.

Go to the update manager and check all the updates are installed. If they are, I'm afraid I can't help you as I'm not a user of Linux.

---

### Post by khurtsiya on 2012-10-29
Software Up to date.

---

### Post by Androzani1 on 2012-10-29
> **khurtsiya said:**
> Software Up to date.

Well, I'm all out of ideas I'm afraid. :(

---

### Post by khurtsiya on 2012-10-29
Thank you anyway. May be someone help me.

---

### Post by wildmanne39 on 2012-10-29
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by khurtsiya on 2012-10-29
Here is the file.

---

### Post by wildmanne39 on 2012-10-29
Hi, are you currently connected with an usb adapter? is it your internal card that does not work? you do know that both will not work at the same time?

Read post 18 in this link for the solution.
[https://answers.launchpad.net/ubuntu-certification/+question/200767](https://answers.launchpad.net/ubuntu-certification/+question/200767)
Thanks

---

### Post by khurtsiya on 2012-10-29
Yes, I use USB-Wi-Fi. Yes, my internal card does not work. Yes I know they will not work at the same time. But: (1) my internal card does not even shows connections (as it always was even if I plugin USB-adapter and (2) if I eject USB-adapter my internal card still not work.

Running file from link outputs next:

Conflicts wit the installed package 'bcmwl-kernel-source'

---

### Post by khurtsiya on 2012-10-29
Removed that package. Installed one by the link. Nothing happened. Should I restart?

---

### Post by wildmanne39 on 2012-10-29
Hi, ```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```then try again.
Thanks

---

### Post by wildmanne39 on 2012-10-29
Run the command I gave you and reboot.
If it still does not work repost the info from the wireless script but delete the old one first.
Thanks

---

### Post by khurtsiya on 2012-10-29
I now have my internal Wi-Wi working! Thank you! Will mark SOLVED.

---

### Post by wildmanne39 on 2012-10-29
Your welcome! Glad it is working.
Enjoy

---

