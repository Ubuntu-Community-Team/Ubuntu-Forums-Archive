---
title: "Strange screen full of text post update, please help"
date: 2021-08-20
forum: General Help
---

### Post by MibunoOokami on 2021-08-20
Hi all,


A friend has emailed me a picture of their screen after doing an update, which allegedly took some 45 minutes to an hour to complete.


I have tried to do a Duckduckgo search to find what the problem could be. Most information says the problem is either linked to X11 or lightdm. I Skyped my friend and walked them through the process of getting into a tty screen and running ```
sudo systemctl restart display-manager
``` which seemed not to work. I got them to do ```
ctrl + alt+ prtsc, r,e,i,s,u,b
```, also to no effect. Finally, I got them to go back to tty and type in ```
sudo reboot now
```, still they are getting the exact same message.


Again I used Duckduckgo to search the last line of text on their screen, which resulted in a lot of ambiguous talk, and no potential solutions.


I have attached the photo I was sent, in the hopes someone here can tell me what the situation is and how to rectify it. I have seen this type of screen on the odd occasion at a boot up, but it usually vanishes a few moments later.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289009&stc=1[/IMG]

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289011&stc=1[/IMG]

The machine is said to be running Ubuntu 18.04, has 4 GB RAM, and a 2.50Ghz processor. 


Please help if you can.

Edited to add a better photo.

---

### Post by tea for one on 2021-08-20
In the second image, all the lines have the prefix [COLOR="#008000"]OK[/COLOR].

Can you see if your friend can reach the Grub menu > Advanced Options > Recovery

---

### Post by grahammechanical on 2021-08-20
What your friend is seeing are normal Linux messages which are being "echoed" (technical term) to the screen. At some point a display driver will be loaded and it will load a splash screen and those messages will be hidden. I understand that Linux loads on one tty and the desktop environment loads on a second tty. So, these messages remain on that first tty but we no longer see them. When we shutdown the system the desktop environment shuts down on its tty and the system switches back to the first tty where Linux then shuts down. We may see some of those messages still on the screen and new ones related to Linux shutting down or we may only see a splash screen.

We assume that after the update/upgrade the desktop is not loading. As advised above your friend could try loading another kernel from the Grub menu Advanced options for Ubuntu. If we run a kernel with recovery mode we get a recovery menu. Selecting Resume should load a desktop with a low resolution open source video driver. It is a method of overcoming problems with proprietary video drivers and getting a working desktop where we can try to fix things.

Regards

---

### Post by MibunoOokami on 2021-08-21
Thanks for the replies. Following your advice to go into recovery mode, the same message was present in the most recent kernel, and the older kernel. 


After rebooting again, they are now getting just a black screen with a white blinking dash. I searched a solution to that problem which was to do ```
sudo dpkg –configure -a
``` then ```
sudo apt-get update
``` which went well, but once they tried ```
sudo apt-get upgrade -y
``` they were presented with a dpkg error and a message which said ```
errors encountered while processing: grub-efi-amd64-signed
``` and ```
shim-signed
```


Searched this problem, ran ```
sudo apt-get purge grub\*
``` ```
sudo apt-get install grub-efi
``` ```
sudo apt-get autoremove
``` ```
sudo update-grub
``` 
All looked to be well, but the black screen now says ```
/dev/sda1: clean 271868/193312 files, 4859107/7719680 blocks
``` and won’t change. 
Walked them through the first lot of instructions I mentioned, upgrade went without a hitch this time, but still arriving at the exact same screen mentioned just now.

---

### Post by tea for one on 2021-08-21
> **MibunoOokami said:**
>  Most information says the problem is either linked to X11 or lightdm.

Do you still think lightdm is misbehaving?
You could try:-
```
sudo dpkg-reconfigure lightdm
```

---

### Post by MibunoOokami on 2021-08-22
> **tea for one said:**
> Do you still think lightdm is misbehaving?
You could try:-
```
sudo dpkg-reconfigure lightdm
```

I have just walked my friend through that command, and it has returned them to the same screen as first pictured in this post, then walked them through recovery mode again, which has given them the black screen with blinking cursor again. 


Another restart resulted in a brief pause ```
unattended upgrade in progress during shutdown, please don&#8217;t turn off the computer
``` after about 30 mins the machine rebooted to black screen with white cursor. That message made me think that the update may have been incomplete when they encountered the original problem in this thread, so I suggested they go through the update/upgrade/autoremove process via tty. Now they got this message after running update. ```
(appstreamcli:2318): Glib-CRITICAL **: 15:42:44.068: g_atomic_ref_count_dec: assertion &#8216;g_atomic_int_get (arc) > o&#8217; failed
```

I&#8217;m not 100% that output is verbatim, the camera my friend was using to Skype on made it quite blurry, and there was some frustration during communications. Forgot to say, I searched the Glib critical error, and the info I came across was too advanced for me, I couldn&#8217;t understand probably 90+% of what I was reading. 


The reason for so much detail is, if during the process of trying to fix this problem, something is made worse, it hopefully will be easier to troubleshoot.

---

### Post by tea for one on 2021-08-22
Troubleshooting via Skype – that adds another dimension to the communication channels ;)

Anyway, I found a bit of info about appstream which seems to be an application linked to upgrades. As your friend is using a 2018 version (18.04), it may be relevant.

[https://www.suramya.com/blog/2018/08/fixing-the-appstreamcli-error-when-running-apt-get-update/](https://www.suramya.com/blog/2018/08/fixing-the-appstreamcli-error-when-running-apt-get-update/)

Can you check the version of appstream?

In Ubuntu 20.04, I have 0.12.10-2.

```
sudo apt update
```

```
sudo apt install appstream
```

The last command should install a later version if available.

After 2/3 days of trying to fix a problem without success, I would seriously consider  a fresh installation and followed by restoring a backup.

The beauty of Ubuntu is that it takes very little time to start from scratch and then add your data. Xubuntu 20.04 LTS for 4GB RAM would be my suggestion.

---

### Post by MibunoOokami on 2021-08-26
> **tea for one said:**
> Troubleshooting via Skype – that adds another dimension to the communication channels ;)

Anyway, I found a bit of info about appstream which seems to be an application linked to upgrades. As your friend is using a 2018 version (18.04), it may be relevant.

[https://www.suramya.com/blog/2018/08/fixing-the-appstreamcli-error-when-running-apt-get-update/](https://www.suramya.com/blog/2018/08/fixing-the-appstreamcli-error-when-running-apt-get-update/)

Can you check the version of appstream?

In Ubuntu 20.04, I have 0.12.10-2.

```
sudo apt update
```

```
sudo apt install appstream
```

The last command should install a later version if available.

After 2/3 days of trying to fix a problem without success, I would seriously consider  a fresh installation and followed by restoring a backup.

The beauty of Ubuntu is that it takes very little time to start from scratch and then add your data. Xubuntu 20.04 LTS for 4GB RAM would be my suggestion.

A challenging dimension to communications, that's for sure.


In the end, I was able to help my friend back up the PC, then create a live USB and install Lubuntu. And that was a mission in and of itself, because Xubuntu and a couple of other light weight distros just would not install for one error or another. I forget what the outcome of appstream was, it didn't give a version number though...


Thanks for your help, it’s a shame we couldn’t solve the problem without a fresh install, but it is what it is.

---

