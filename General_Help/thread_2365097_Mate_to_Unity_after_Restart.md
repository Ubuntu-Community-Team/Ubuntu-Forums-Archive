---
title: "Mate to Unity after Restart?"
date: 2017-07-02
forum: General Help
---

### Post by Quarkrad on 2017-07-02
I have been playing around with different Desktops this afternoon - originally having Mate 16.04.  I installed ubuntu 16.04.2/gnome flashback - after a little time I decided to go back to Mate (I have separate / and /home).  I installed Mate 16.04.2, formating / but not formating /home and everything went OK.  I have sound problem (I had this with my original Mate 16.04 install) and went through the procedure I found to get sound working (the first three steps of *ubuntu sound troubleshooting* doc). At Step 3 you are asked to reboot before carrying out 2 diagnostic commands - I rebooted expecting to see my Mate 16.04.2 Desktop, but I was presented with the attached Unity Desktop. (Before I went through the sound trouble shooting doc I updated Mate and installed restricted-extras). This can only be a hangover from the ubuntu 16.04 install BUT I formatted / when I reinstalled Mate.  Do I have to reinstall Mate and can this be stopped happening again?  (If open Dash and type details I'm told I have ubuntu 16.04).

---

### Post by Quarkrad on 2017-07-02
I've just rebooted and I'm back in Unity.  Interestingly (I think) during the final stages of the shutdown process I saw the Mate logo as per normal.

---

### Post by Quarkrad on 2017-07-02
I dual boot win10 and on restart I get my normal Mate grub screen asking me to choose what OS I want - I hit Return (because Ubuntu is default) and see the normal Mate boot screens.  But I'm booting to a Unity Desktop.

```
dad@dadubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.2 LTS
Release:	16.04
Codename:	xenial

```

---

### Post by Quarkrad on 2017-07-02
If I launch the terminal via Dash and type caja then the caja file manager launches so my Mate16.04 is there 'under the bonnet'. How do I purge the Unity Desktop?

---

### Post by #&amp;thj^% on 2017-07-02
See post#6 here: [https://ubuntuforums.org/showthread.php?t=2364085](https://ubuntuforums.org/showthread.php?t=2364085)
Please read carefully and understand fully.

---

### Post by Quarkrad on 2017-07-03
That did not work very well - so I reinstalled.  But the same thing has happened again - I entered the commands below from h**ttps://help.ubuntu.com/community/SoundTroubleshootingProcedure** Step 1 and when I rebooted I was presented with a Unity Desktop.  This didn't happen originally when I used these commands to get over my sound problems.  Could it be the command sudo apt-get dist-upgrade - but why would the Desktop go from Mate 16.04 to Unity?



```
sudo apt-get update;sudo apt-get dist-upgrade; sudo apt-get install pavucontrol linux-sound-base alsa-base alsa-utils lightdm ubuntu-desktop  linux-image-`uname -r` libasound2; sudo apt-get -y --reinstall install linux-sound-base alsa-base alsa-utils lightdm ubuntu-desktop  linux-image-`uname -r` libasound2; killall pulseaudio; rm -r ~/.pulse*; ubuntu-support-status; sudo usermod -aG `cat /etc/group | grep -e '^pulse:' -e '^audio:' -e '^pulse-access:' -e '^pulse-rt:' -e '^video:' | awk -F: '{print $1}' | tr '\n' ',' | sed 's:,$::g'` `whoami`
```

---

### Post by vasa1 on 2017-07-03
I don't understand that code you posted.

Also, from what I understand, it's better to use "&&" to ensure that commands are executed sequentially and that the succeeding command will execute only upon the preceding command executing completely.

---

### Post by kc1di on 2017-07-03
> **Quarkrad said:**
> That did not work very well - so I reinstalled.  But the same thing has happened again - I entered the commands below from h**ttps://help.ubuntu.com/community/SoundTroubleshootingProcedure** Step 1 and when I rebooted I was presented with a Unity Desktop.  This didn't happen originally when I used these commands to get over my sound problems.  Could it be the command sudo apt-get dist-upgrade - but why would the Desktop go from Mate 16.04 to Unity?



```
sudo apt-get update;sudo apt-get dist-upgrade; sudo apt-get install pavucontrol linux-sound-base alsa-base alsa-utils lightdm ***ubuntu-desktop***  linux-image-`uname -r` libasound2; sudo apt-get -y --reinstall install linux-sound-base alsa-base alsa-utils lightdm ubuntu-desktop  linux-image-`uname -r` libasound2; killall pulseaudio; rm -r ~/.pulse*; ubuntu-support-status; sudo usermod -aG `cat /etc/group | grep -e '^pulse:' -e '^audio:' -e '^pulse-access:' -e '^pulse-rt:' -e '^video:' | awk -F: '{print $1}' | tr '\n' ',' | sed 's:,$::g'` `whoami`
```

According to the code you installed unity with the command ```
ubuntu-desktop
```. That command installs unity.  as to why you still get the mate logo on boot up, it's because you haven't changed grub , just added a desktop.  if you want to change the grub splash you need to issue this command ```
sudo update-grub
```

when ever you install multiple desk top system there will always be some interaction.  installing ubuntu-desktop (unity) does not remove any of Mates applications, it may change some of the defaults but applications like caja and pluma will still be there and usable by either desktop.  

Hope this helps.  If you want to try unity or mate or xfce or kde the best way is to do a fresh install or just run a live session until your satisfied as to the one you want then do the install. That way you will avoid the confusion.

If the problem is sound you should start a separate thread to address that problem, Sound issues are very rarely fixed by using different desktops.

---

### Post by Quarkrad on 2017-07-03
Thank you for your replies.  The code came from the official documentation mentioned in #6 - my problem seems to be have used Ubuntu Sound Troubleshooting for Ubuntu Mate.  My other problem was I was not trying to mixed Desktops - I did a fresh install of Mate and had no intention of installing Unity - but now  see why it happened.  I did have a different threat for my sound issue (ubuntuforums.org/showthread.php?t=2362604), that was resolved - what I have learn t is to be very careful following instructions across different flavours.  Thank you again.

---

