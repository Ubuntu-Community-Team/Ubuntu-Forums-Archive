---
title: "Ubuntu Crashing for no apparent reason - Please Help"
date: 2007-06-02
forum: General Help
---

### Post by sibot on 2007-06-02
Hey,
My ubuntu seems to crash for no apparent reason, it'll all be working fine and suddenly the whole system would freeze, nothing seems to work, the only resort is to restart. I cant seem to put my finger on anything. Can anyone please help me out with what could be wrong or how i can find out what is wrong? 

Thanks in advance
sibot

---

### Post by Haegin on 2007-06-02
Make notes of what programs are running when it crashes (including those you aren't using and that are in the system tray). See if you can work out if there is one program that always is running. If you are using beryl (the pretty desktop effects) try disabling it and see if you still get crashes.
Unfortunately tracking down something like this is normally a combination of experience and trial and error. Also check the error logs in /var/log using the System Log Viewer in System>Administration to see if there is anything written to the various logs after each crash.
Good luck!

---

### Post by jjacobs2 on 2007-06-02
Stick the ubuntu install cd in and run memtest for a few hours.  If you have bad memory it can cause random crashes.  Also you can try cntrl + alt + backspace when it crashes to avoid a reboot.

---

### Post by sibot on 2007-06-02
Well, the crash occurs at anytime. I dont think with any programs running or anything. I am using desktop effects now, but the system was crashing before hand too, with the desktop effects turned off. I did run a memtest, and it went on for 2 or 3 hrs, without error, after which I rebooted, i dont think theres a problem with RAM though, I tried Ctrl + Alt + Backspace for relief, but sadly that didnt work either. The system comes to a total freeze. Although i have noticed, everytime my system crashes, i get this message in system log:-

Maybe this could be of any help.
> 
Jun  2 18:56:45 sibot NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 

I dont have any wireless cards, I am on normal wired lan, really confused, not sure what to do. Please help!
thanks!

---

### Post by sibot on 2007-06-02
Here is a screenshot of my syslog from the system crash time.

[[IMG]http://img458.imageshack.us/img458/2899/screenshotvarlogsyslogmgt5.th.png[/IMG]](http://img458.imageshack.us/my.php?image=screenshotvarlogsyslogmgt5.png)

---

### Post by jjacobs2 on 2007-06-02
Are you using any restricted drivers like the ati or nvidia graphics driver?  If you aren't sure it should say in system > preferences > hardware information what hardware is detected.

---

### Post by sibot on 2007-06-02
yes, im using restricted drivers for nvidia 6200 PCI-E

---

### Post by sibot on 2007-06-02
but the system seemed to crash even before i installed the drivers.

---

### Post by Haegin on 2007-06-02
I would try removing network manager as its not that much use on wired networks and see if that helps anything but before you un-install it rashly just stop it running on startup.

To do this go to System>Administration>Sessions and untick it. Now reboot your PC and see if it crashes. If it does check the sys log to see if there is the same entry there again. If so it may be the network manager service is still running.

Let us know how you get on.

---

### Post by sibot on 2007-06-02
Someone suggested that to me before also. Ill try it and let you know! thanks!

---

### Post by sibot on 2007-06-02
Well, I tried it again, and it crashed...again.....anyother way?

---

### Post by Haegin on 2007-06-02
I reckon the network manager service may still be running (the thing in Session is probably just for the tray applet). Can you check to see if there is anything in the syslog after that last crash?

If there is you probably need to disable to service so it doesn't run on startup. The easiest way to do this is explained here:
[https://help.ubuntu.com/community/WifiDocs/NetworkManager#head-1de145d05f957ff659f5fdb58974ec3e5864def5](https://help.ubuntu.com/community/WifiDocs/NetworkManager#head-1de145d05f957ff659f5fdb58974ec3e5864def5)

I hope this sorts the problem - if not it can't be network manager and we will have to look elsewhere.

---

