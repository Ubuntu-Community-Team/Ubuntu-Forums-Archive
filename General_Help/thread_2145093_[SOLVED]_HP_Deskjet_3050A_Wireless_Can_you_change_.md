---
title: "[SOLVED] HP Deskjet 3050A Wireless: Can you change the IP address once configured?"
date: 2013-05-14
forum: General Help
---

### Post by cforput on 2013-05-14
I've set up my HP Deksjet 3050A to print wirelessly. The trouble I have it I get power failures at my home and when the printer resets, the IP address takes the next IP address when the power comes back up. Most of the time, that means it doesn't grab the same IP address as was originally configured. This causes a problem with printing because when you set up the printer in Ubuntu, you have to list the IP address so the computer can connect to the printer. 

The only way I have figured out on how to solve this problem is to delete the printer in Ubuntu and set it up all over again. Is there a way to change the IP address in Ubuntu or on the Printer so they match again and I don't have to remove and reinstall the printer each time? I know during the printer setup you can put in your own IP address so I could put something in at the end of the IP addresses but I'm not sure if the power failure will reset that option as well and still cause me the same problem.

---

### Post by MartyBuntu on 2013-05-14
Does the printer have a webGUI where you can set up a static IP address in the settings. My Samsung network printer does, yours should as well.

---

### Post by cforput on 2013-05-14
It does. The only thing I have found is an option called settings but it is grayed out. If I try to open the gui through the terminal with a sudo command it doesn't open. If I try to open the gui via the terminal without sudo, it opens fine but the option is grayed out. Since I can't get into the settings option, I'm not sure if there is a place to change the IP address.

---

### Post by coffeecat on 2013-05-14
> **MartyBuntu said:**
> Does the printer have a webGUI where you can set up a static IP address in the settings. My Samsung network printer does, yours should as well.

My old ethernet only HP network printer and my newer HP Deskjet wireless 3520 both do.

@cforput, check your router to see what local IP address it has assigned to your HP printer, enter that address into the address bar of your browser and you should see the webGUI configuration for your printer. It's straightforward to set a static address. It seems to be an undocumented feature of HP network printers. Neither of my printers' manuals mention the existence of the webGUI, but it's there nonetheless.

---

### Post by cforput on 2013-05-14
Wow, nice utility! If I put in my own IP address, what do I use for the Default Gateway and Subnet Mask?

---

### Post by AgentZ86 on 2013-05-14
are you printing wirelessly through
 a router ? if so you can set the mac address or reserve the IP address in the router for that device
then when it cycles on power, it will retreive the same exact ip from the dhcp server built into the router etc 

If not on a router then you have to use the printer static IP or you have to use a device naming scheme etc.

---

### Post by cforput on 2013-05-14
I'm on a router but I have no idea how to do that. I have a Belkin router. I can get into the Belkin Router conf page through Firefox but I don't know where to manually (and permanently) assign the printer an IP address.

---

### Post by ajgreeny on 2013-05-14
It may also be worth looking in your router setup in a browser. I have a Netgear router and using its own configuration page it is possible to reserve specific IP addresses for all the connected devices (computers and HP printer) that are attached to the router.  It means that even if the router loses power, all connected devices are at the same address when power returns, very handy for all my ssh bookmarks to other computers, and for printer use.

---

### Post by cforput on 2013-05-14
I'm going to make this a solved. I ran a test. I frist used Firefox to hit my printer and used the utility to force the IP address of the printer to one at the end of the range (xxx.xxx.xxx.99). That took. I then unplugged the printer awited for 15 seconds and plugged it back in. I then checked the IP address and it stayed at 99. Next time the power goes, all our computers will grab IP addresses at the lower end and the printer should stay at 99 which means I shouldn't have to reconfig the printer any more.

---

### Post by cforput on 2013-05-14
I'm going to make this a solved. I ran a test. I frist used Firefox to hit my printer and used the utility to force the IP address of the printer to one at the end of the range (xxx.xxx.xxx.99). That took. I then unplugged the printer awited for 15 seconds and plugged it back in. I then checked the IP address and it stayed at 99. Next time the power goes, all our computers will grab IP addresses at the lower end and the printer should stay at 99 which means I shouldn't have to reconfig the printer any more.

---

