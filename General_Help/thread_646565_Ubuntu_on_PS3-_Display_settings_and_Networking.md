---
title: "Ubuntu on PS3- Display settings and Networking"
date: 2007-12-21
forum: General Help
---

### Post by Dio V. Telmo on 2007-12-21
1) I installed Ubuntu (linux OS) but I cannot see the whole window. How do you change the display settings.
 
2) Ubuntu also is not able to connect to my network.
 
Merry Christmas to all!!!

---

### Post by cgm12mgc on 2007-12-27
i just put gusty on my ps3 and am having the same issues, my wifi does not work, my display settings are all off (and i have an hdtv) and i do not believe its running on all of its cores, any input would be great

Thanks,
Charlie


--EDIT-- it is running on 2 of the cores

---

### Post by cgm12mgc on 2007-12-27
--bump--

---

### Post by raj727 on 2007-12-27
Same problems here.  Installed 7.10 and have resolution problems with no wifi.

---

### Post by gyrene2083 on 2007-12-28
Well regarding the wifi, if you updated the firmware of the PS3, your pretty much screwed with wifi. The update messed up the kernal, or at least that is what has been posted in psubuntu
read this [http://psubuntu.com/2007/11/10/ps3-firmware-20-breaks-wifi/]("http://psubuntu.com/2007/11/10/ps3-firmware-20-breaks-wifi/")

I did the update, and now my ps3 is stuck at the booting system, part in kboot. 
Regarding fixing the resolution, you have to edit kboot.conf, from the terminal I think it's
sudo nano /etc/kboot.conf
Then change "video=ps3fb:mode:x to 3", that will give you 720p. Here is a link that could help better than I can.
[http://psubuntu.com/forum/viewtopic.php?t=1566]("http://psubuntu.com/forum/viewtopic.php?t=1566")

If any of you know how to get me back into Gutsy, without rebooting, I would greatly appreciate it.

---

### Post by god0fgod on 2008-01-05
When I instlled ubuntu on my PS3 and got to the reolution selections I thought enter was select but it wasn't and it continued installation. How can I redo this step? I've found a command somewhere else but I need to know the graphics chip or something.

Please help!

---

### Post by god0fgod on 2008-01-05
I've managed to change the resolution settings but my TV says mode not supported when the xsever starts. What do I do now?

---

