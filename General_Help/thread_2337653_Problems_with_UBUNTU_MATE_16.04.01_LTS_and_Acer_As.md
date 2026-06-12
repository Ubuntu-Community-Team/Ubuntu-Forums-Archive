---
title: "Problems with UBUNTU MATE 16.04.01 LTS and Acer Aspire ONE D150-1 Bk"
date: 2016-09-20
forum: General Help
---

### Post by mate1 on 2016-09-20
I installed Ubuntu MATE 16.04.01 LTS on a netbook, Acer Aspire ONE D150-1 Bk and I have two issues:

  1) when I turn off my netbook, the netbook doesn't turn off, but it  goes to standby mode, so I need to press the ON button, the pc restarts  and again click on the icon to turn off the pc, and my netbook goes OFF,  same thing when i turn it ON, i press the On button, and after the bios  message, the PC goes to standby mode, I need to press again the ON  button and only after this procedure, the PC turns ON, so what's the  problem?
I also noticed that when I turn off my PC, the screen goes all black and  it appears only a line that says something like " dev/sda1 clean ,  xxxxxx bytes, xxxx bytes " something like this .. This wording is a  result of a "fsck"?, ... can be reconnected to my problem?

  For this Problem I try this "fix" :

  
[LIST]
[*]I try with a "shutdown -h now" command and the PC turns OFF normally ; 
[*]also checked my power management settings in System ->  Preferences -> Hardware -> Power Management and set all the  options to " Never " or " Do Nothing ", but I have the same problem; 
[*]In System -> Preferences -> Hardware -> Power Management  -> General I set " When press the ON button -> " Turn OFF the PC "  and when i press the ON button, my PC goes OFF normally,.... but why  the PC behaves this way?..what's the problem? 
[/LIST]
  
2) Sometimes when I turn on my PC the Wi-Fi card doesn't show any  wireless network, so I need to open a terminal and issue the following  comand: " sudo service network-manager restart " ,after this command the  Wi-Fi starts to work well, why I need to do this, why the Wi-Fi card  sometimes doesn't show any wireless network?

  For this Problem I try this "fix" :

  
[LIST]
[*]here is the output of the command " sudo systemctl status  network-manager ", performed after switching on the PC and before  restarting the "service network-manager" ---> [https://thepb.in/p/76hErQzXPk1HV](https://thepb.in/p/76hErQzXPk1HV) 
[/LIST]
  
Thanks.

---

### Post by #&amp;thj^% on 2016-09-20
There was one bug discovered early in development where the network-manager was stopping the shut down process.
Try this before you shut down...disconnect from the network by way of network-manager see if that helps.

---

### Post by mate1 on 2016-09-20
> **1fallen said:**
> There one bug discovered early in development where the network-manager was stopping the shut down process.
Try this before you shut down...disconnect from the network by way of network-manager see if that helps.

Thanks, how I can disconnect from the network by way of network-manager, what is the command for do that?...and what is the command for reconnect from the network by way of network-manager?

---

### Post by #&amp;thj^% on 2016-09-20
You would just right click the Network-Manager from the panel..and un-tick the Enable Networking.
And to re-enable it after a reboot do the same but tick the box Enable Networking.

---

### Post by mate1 on 2016-09-20
> **1fallen said:**
> You would just right click the Network-Manager from the panel..and un-tick the Enable Networking.
And to re-enable it after a reboot do the same but tick the box Enable Networking.

Thanks, I tried this, but doesn't work, Same problems on the start of the PC and same problems when turn OFF the PC...

---

### Post by mate1.2 on 2016-10-12
Hello,
I'm " mate1 ", I solved these problems by updating the BIOS of my netbook to the latest version.
I ask the moderators to add " [SOLVED] " in the title of the thread.
Thanks.

---

