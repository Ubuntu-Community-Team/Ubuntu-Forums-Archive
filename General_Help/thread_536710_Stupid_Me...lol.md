---
title: "Stupid Me...lol"
date: 2007-08-28
forum: General Help
---

### Post by knopper67 on 2007-08-28
I Accidentally fried my system lol. I Tryed to disable all services except for GDM hopefully to spedd things up a bit. (Im a Speed Freak) But now when i try to turn them back on it says i don't have to permission to change the system configuration or something even though i entered my password. Any idea how to turn them back on using the terminal??

---

### Post by southernman on 2007-08-28
did you put sudo in front of the command?

sudo nano (or vi) <command>

---

### Post by knopper67 on 2007-08-28
What i did is i clicked -System >> Admin >> Services- and entered my password but then it gives me a message saying that i don't have permission.

When i try sudo services-admin it gives me these messages:

(services-admin:4757): Liboobs-WARNING **: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory

(services-admin:4757): Liboobs-WARNING **: OobsSession object hasn't connected to the bus, cannot register OobsObject

(services-admin:4757): Liboobs-CRITICAL **: run_message: assertion `oobs_session_get_connected (priv->session)' failed

(services-admin:4757): Liboobs-CRITICAL **: oobs_session_get_platform: assertion `priv->connection != NULL' failed

---

### Post by southernman on 2007-08-28
ah... Your probably going to have to do this from a livecd of your choosing.

I use SystemRescueCD but you can choose anything you have on hand or want to download.

Once booted into the livecd on SRCD type "startx" at the command prompt.

Then open a terminal window and enter the following commands...

mkdir /mnt/repair
fdisk -lsu (doing this to find your root partition for the next command)
mount /dev/hda? /mnt/repair - here replace ? with your root partiton number. you may also need to replace hda with sda if your running a sata or scsi drive.
nano /etc/passwd (which I think is the file needed to repair / reestablish the services you rendered useless.
shutdown -r now

remove the cd from the tray before it starts back up and see if your golden.

Hope that helps.

---

### Post by knopper67 on 2007-08-28
Okay i'll try that...be back in 15

---

### Post by kerry_s on 2007-08-28
> **knopper67 said:**
> I Accidentally fried my system lol. I Tryed to disable all services except for GDM hopefully to spedd things up a bit. (Im a Speed Freak) But now when i try to turn them back on it says i don't have to permission to change the system configuration or something even though i entered my password. Any idea how to turn them back on using the terminal??

if your a speed freak you need to go custom, ditch the slow a** DE & move to a light WM. build it to your needs with only what you use.

start here-> [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by knopper67 on 2007-08-28
Thanks for the help, i appreciate it. But i've decided i might need a fresh install anyways...I've customised my install a bit much.

Thanks

---

