---
title: "Not Sure Where To Ask This"
date: 2007-04-02
forum: General Help
---

### Post by linuxwizard on 2007-04-02
Hello
I am using a dual boot system Ubuntu 6.10/Kubuntu 6.10 an was using Kubuntu at the time. I lost my internet connection so i needed to reboot. When i rebooted got my password in. It seemed like my hard drive was working more than usual and it took longer to get to my desktop. When at desktop my taskbar only showed up for maybe 5 seconds and than disappeared. I tried right clicking all over the desktop nothing happens. I tried restarting desktop same thing happened again. I have sound when i was at the blank desktop i can hear my mail notifier. I have not had any issues or problem till now. I booted into Ubuntu no problem there. Not sure what to do or look for or even search for an answer. This is a custom modd desktop computer and not using anything wireless.

---

### Post by mac.ryan on 2007-04-02
It might (or might not) be a problem with the configuration of your xserver. You might with to try to automatically reconfigure it. You can do that from the terminal (access it either via recovery mode, either pressing CTRL-ALT-F2, for example).

Make a backup copy of your present file (located in /etc/X11/xorg.conf). Issue the following command.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```Reboot.

Ideally, the system will be configured (for what concerns graphic settings and a few other things, but not software installation) as it was after you first installed ubuntu on it...

Best luck! :)

---

### Post by linuxwizard on 2007-04-05
I have tried everything i could find in my searching the last 2 days nothing worked. Could not get back my kicker what did work was adding a newuser as below states. I got back into my system everything works. Something happened when I lost my internet connection i don't know haven't found anything to explain the issue.




 aysiu
Ubuntu Master Roaster
 
	
Re: disappearing kicker (KDE)
Have you tried creating a new test user to see if that user runs into the same problem (you can always delete the test user later)?

If you both experience it, it's a systemwide problem. If only your current user experiences it, it may be a configuration file that's corrupt or something.

---

### Post by mac.ryan on 2007-04-05
> **linuxwizard said:**
> what did work was adding a newuser as below states.

Then is a user configuration problem. If you want to pin down the "incriminated file", you should probably move to a sub-directory all the hidden files in your user's home (/home/user), and then login again (at this point you should be able to do so).

You can then begin to bring them back a few at a time, until you will again fail to log-in... then you will understand what file is carrying the problem along....

Just be attentive when you move the files around, to leave them with the right (i.e. original) permissions.

---

