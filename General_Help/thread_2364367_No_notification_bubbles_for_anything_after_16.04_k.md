---
title: "No notification bubbles for anything after 16.04 kernel upgrade"
date: 2017-06-22
forum: General Help
---

### Post by Roy_Gardiner on 2017-06-22
Two days ago I updated my Ubuntu 16.04.02 OS. The major part of the upgrade was to the kernel. I am using the Unity 7 Desktop environment.
After this change I am not having any notification bubbles at all e.g. for wireless connection, Rhythmbox, Myweather indicator. I am not sure where all the settings are located and Ubuntu Help does not help. I think a "universal" notifications setting must have been affected by the change. In desperation I have installed an app called NotifyOSD but that just seems to be a tool for configuring the notification bubbles. I have read online that there is a notifications "daemon" that is used by the Gnome Desktop Environment but that is not used for Unity. Maybe I am misunderstanding that.
Can anyone advise me of a fix for this issue?

---

### Post by #&amp;thj^% on 2017-06-22
I'm not seeing that myself...everything works as expected here. (And I'm running kernel 4.11 **not advised though**)
But maybe have a read here: [https://askubuntu.com/questions/128474/how-to-customize-on-screen-notifications](https://askubuntu.com/questions/128474/how-to-customize-on-screen-notifications)
I know by your post you have seen this, but maybe overlooked something?

---

### Post by Roy_Gardiner on 2017-06-22
> **1fallen said:**
> I'm not seeing that myself...everything works as expected here. (And I'm running kernel 4.11 **not advised though**)
But maybe have a read here: [https://askubuntu.com/questions/128474/how-to-customize-on-screen-notifications](https://askubuntu.com/questions/128474/how-to-customize-on-screen-notifications)
I know by your post you have seen this, but maybe overlooked something?

Thanks for your reply. You are correct:I have seen this before. However, as I stated in my post, this application seems only to configure notifications, not to enable or disable them.

---

### Post by #&amp;thj^% on 2017-06-22
Give this a try then from the terminal:
```
gsettings set org.gnome.desktop.notifications enable true
```
To reverse this:
```
gsettings set org.gnome.desktop.notifications enable false
```
Fingers crossed.

---

### Post by Roy_Gardiner on 2017-06-22
Thanks for the suggestion. However, in the terminal I got the message: No such key 'enable'

---

### Post by #&amp;thj^% on 2017-06-22
Odd?
What dose this return from the terminal:
```
apt policy libappindicator1
```

---

### Post by Roy_Gardiner on 2017-06-22
> **1fallen said:**
> Give this a try then from the terminal:
```
gsettings set org.gnome.desktop.notifications enable true
```
To reverse this:
```
gsettings set org.gnome.desktop.notifications enable false
```
Fingers crossed.

Thanks. I found online that I might need to use instead: 
gsettings set org.gnome.desktop.notifications show-banners true

I tried that and got no error message. So now I wait with bated breath, to see if I get any notifications :p

---

### Post by Roy_Gardiner on 2017-06-22
> **1fallen said:**
> Odd?
What dose this return from the terminal:
```
apt policy libappindicator1
```
This is what I got:
```
libappindicator1:
  Installed: 12.10.1+16.04.20170215-0ubuntu1
  Candidate: 12.10.1+16.04.20170215-0ubuntu1
  Version table:
 *** 12.10.1+16.04.20170215-0ubuntu1 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     12.10.1+15.04.20141110-0ubuntu1 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/main amd64 Packages
```

---

### Post by #&amp;thj^% on 2017-06-22
You may also need to log out and back in again to see the change.
Also waiting here with  bated breath. ;)

---

### Post by Roy_Gardiner on 2017-06-22
> **1fallen said:**
> You may also need to log out and back in again to see the change.
Also waiting here with  bated breath. ;)

Hi, sorry for the delay...other events took me away.
Well, I have rebooted but so far no notifications received. If everything was back to normal I would have expected MyWeatherIndicator app thing to have shown a notification.:(

---

### Post by #&amp;thj^% on 2017-06-22
By chance do you have dual monitors (Screens) hooked up?
I do and when second one is active...the notifications show on that monitor. (Just a thought)

---

### Post by Roy_Gardiner on 2017-06-22
No, I am just on my laptop.
This problem is quite a mystery. I have posted my problem on several online fora and I seem to be the only one with the problem. There was one user who said he had had the same issue but he fixed his problem just by manually opening the applications that he normally opened automatically at Start Up. However, I am not sure that our problems were the same.

---

### Post by vasa1 on 2017-06-22
Do you have libnotify-bin installed?

If so, running the following in a terminal should give you a notification bubble showing the time and date:
  ```
notify-send --app-name="" "$(date)"
```

---

### Post by #&amp;thj^% on 2017-06-22
Yep probably not the same problem.
>  However, I am not sure that our problems were the same. 
But your right this is quite the mystery??
I'll try to rack my brain here (whats left of it anyway) and will post back here if any relevant solutions come to me.
Sorry not much help here. :(

---

### Post by Roy_Gardiner on 2017-06-22
> **vasa1 said:**
> Do you have libnotify-bin installed?

If so, running the following in a terminal should give you a notification bubble showing the time and date:
  ```
notify-send --app-name="" "$(date)"
```

I ran it but, alas, there was no notification. How can i find out if libnotify-bin is installed? (Sorry, I'm new to all this "in the weeds with Linux" stuff:(.

---

### Post by #&amp;thj^% on 2017-06-22
> **Roy_Gardiner said:**
> I ran it but, alas, there was no notification. How can i find out if libnotify-bin is installed? (Sorry, I'm new to all this "in the weeds with Linux" stuff:(.

Run this and paste back
```
apt policy libnotify-bin
```

I would also be interested if booting to a older kernel now shows your notifications again?

EDIT: Just for fun run this in the terminal:
```
sudo apt-get --reinstall install libnotify-bin notify-osd
```
If any errors from this paste them back here.
If there is no errors>>>Reboot or Log out and back in again.
I've got to go for a bit... will check back in a while.

---

### Post by Roy_Gardiner on 2017-06-22
> **1fallen said:**
> Run this and paste back
```
apt policy libnotify-bin
```

I would also be interested if booting to a older kernel now shows your notifications again?

EDIT: Just for fun run this in the terminal:
```
sudo apt-get --reinstall install libnotify-bin notify-osd
```
If any errors from this paste them back here.
If there is no errors>>>Reboot or Log out and back in again.
I've got to go for a bit... will check back in a while.

Many thanks for your help.....
Here is the first paste:
```
libnotify-bin:
  Installed: 0.7.6-2svn1
  Candidate: 0.7.6-2svn1
  Version table:
 *** 0.7.6-2svn1 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/main amd64 Packages
        100 /var/lib/dpkg/status
```

---

### Post by Roy_Gardiner on 2017-06-22
> **1fallen said:**
> Run this and paste back
```
apt policy libnotify-bin
```

I would also be interested if booting to a older kernel now shows your notifications again?

EDIT: Just for fun run this in the terminal:
```
sudo apt-get --reinstall install libnotify-bin notify-osd
```
If any errors from this paste them back here.
If there is no errors>>>Reboot or Log out and back in again.
I've got to go for a bit... will check back in a while.

Here is the second paste: there were no errors.

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 2 reinstalled, 0 to remove and 1 not upgraded.
Need to get 125 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/main amd64 libnotify-bin amd64 0.7.6-2svn1 [6,584 B]
Get:2 [http://ppa.launchpad.net/leolik/leolik/ubuntu](http://ppa.launchpad.net/leolik/leolik/ubuntu) xenial/main amd64 notify-osd amd64 0.9.35+16.04.20160415-0ubuntu1-leolik~ppa0 [119 kB]
Fetched 125 kB in 1s (85.2 kB/s)                                               
(Reading database ... 325913 files and directories currently installed.)
Preparing to unpack .../libnotify-bin_0.7.6-2svn1_amd64.deb ...
Unpacking libnotify-bin (0.7.6-2svn1) over (0.7.6-2svn1) ...
Preparing to unpack .../notify-osd_0.9.35+16.04.20160415-0ubuntu1-leolik~ppa0_amd64.deb ...
Unpacking notify-osd (0.9.35+16.04.20160415-0ubuntu1-leolik~ppa0) over (0.9.35+16.04.20160415-0ubuntu1-leolik~ppa0) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for gconf2 (3.2.6-3ubuntu6) ...
Processing triggers for libglib2.0-0:amd64 (2.48.2-0ubuntu1) ...
Processing triggers for libglib2.0-0:i386 (2.48.2-0ubuntu1) ...
Setting up libnotify-bin (0.7.6-2svn1) ...
Setting up notify-osd (0.9.35+16.04.20160415-0ubuntu1-leolik~ppa0) ...
```

---

### Post by #&amp;thj^% on 2017-06-22
Well i guess by a lack of joy here this was merely an exercise in re-installing.
And have you yet tried booting to the previous kernel (By way of Grub Advanced Options selecting the kernel below the top one) before the update? (as this is the only thing left in my bag of tricks)

---

### Post by Roy_Gardiner on 2017-06-22
Thanks for your efforts anyway. I don't really want to go back to the previous kernel because it has susceptibilities that the new kernel fixed.
Thanks again!

---

### Post by #&amp;thj^% on 2017-06-22
That was not the idea to stay on the older kernel, but perhaps find a bug in the newer kernel.
But as you wish.
Best Regards

---

