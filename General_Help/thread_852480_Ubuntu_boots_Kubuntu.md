---
title: "Ubuntu boots Kubuntu"
date: 2008-07-07
forum: General Help
---

### Post by ernesto55 on 2008-07-07
I am running Kubuntu 8.04 Hardy Herron
Last nite I downloaded KDE and now when I boot up Ubuntu it shows the Kubuntu loading screen it almost boots up but freezes up at the very end and I cannot get into Ubuntu 
When I boot to recovery mode the process stops after 

Please Help I am a noob who is trying to learn Ubuntu and Linux but I am not a total noob to computers.

Thanks

---

### Post by Zill on 2008-07-07
I am slightly puzzled.  Ubuntu uses the Gnome desktop environment, whereas Kubuntu uses KDE.  Although both Ubuntu and Kubuntu use the same base software, each desktop environment has its own applications.

If you used a Kubuntu install disk then you already have KDE - it is not necessary to "download" it.

Can you please clarify if your install disk was Ubuntu **or** Kubuntu.

How did you "download" KDE?  Note that it is not normally necessary to specifically download Linux software - this is usually handled by package management software, such as Synaptic.

---

### Post by ernesto55 on 2008-07-07
Hello guys I had an emergency and had to leave.
This is for Zill
I think I might have made a mistake in my posting I didn't download kde I downloaded the Kubuntu desktop.
Here is some other information 
I had to run fsck because Ubuntu wouldn't load yesterday.
I was able to make it work by pressing esc during step 2 while Ubuntu was checking drivers, but later ran fsck and fixed the boot problem.
Then I had a problem with my synpatic package and fixed that problem but when I restarted my computer under Ubuntu it took me to Kubuntu boot screen and froze near the end.
I hope this will help you help me.

---

### Post by Zill on 2008-07-08
ernesto55:  Just to clarify:

1)  Did you use an Ubuntu CD for the initial installation?
2)  If so, did Ubuntu then run correctly, including after a reboot?
3)  Did you then install the kubuntu-desktop metapackage?
4)  If so, how did you install it (with Synaptic or from the terminal)?
5)  Did Kubuntu initially run correctly, including after a reboot?
6)  Can you now select *both* Ubuntu and Kubuntu from the login screen menu?
7)  Do either Ubuntu or Kubuntu now run correctly?

ps.  Your references to "downloading" worries me as this implies that only certain parts of the software may be installed.  The package manager (Synaptic, apt-get or aptitude) will automatically download everything required, including all dependencies, and will then install these programs in the right sequence.  Manual downloading can break things ;-)

---

### Post by ernesto55 on 2008-07-08
1) I used wubi and a Ubuntu ISO
2) Yes it ran correctly for about three days until I tried to use Java 6.o
3) I am not sure about this one
4) I used the terminal to install Kubuntu desktop
   That is where I had a problem by me being stupid I stopped the                  
   terminal
   and then installed Kubuntu-desktop again. 
5) Kubuntu desktop did run correctly
6) I could see Ubuntu and Kubuntu at the Login Screen Menu 
7) No I cannot get into Ubuntu or Kubuntu

My use of download was incorrect i used apt-get to install sorry for incorrect terms.

---

### Post by Zill on 2008-07-08
I have never used Wubi so please take my comments with a pinch of salt :-)

According to the [Wubi website]("http://wubi-installer.org/") it seems that Wubi allows you to install Ubuntu as just another Windows application, within the existing filesystem.  It does not appear to modify partitions, as with a "normal" installation, so I cannot understand how your file system got corrupted and then repaired using fsck!

There may be a clue to your problem in the following website faq:
> Hibernation is not supported under Wubi, moreover Wubi filesystem is more vulnerable to hard-reboots (turning off the power) and power outages than a normal filesystem, so try to avoid unplugging the power. An Ubuntu installation to a dedicated partition provides a filesystem that is more robust and can better tolerate such events.

Maybe someone who has used Wubi could help further on this but you may find things easier if you use your Ubuntu iso to do a "normal" install.  I dumped Windows years ago and find things much simpler and more reliable without it :-)

---

### Post by ernesto55 on 2008-07-08
Thanks for the help I am going to look and try to find someone who has used Wubi.

---

