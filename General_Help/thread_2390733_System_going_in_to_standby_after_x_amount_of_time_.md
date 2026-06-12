---
title: "System going in to standby after x amount of time inactive."
date: 2018-05-01
forum: General Help
---

### Post by computer0freek on 2018-05-01
Hello!

I did look for this issue a little bit but I didn't see anything under the newest version. I believe I have found a bug. Every time I leave the system - 15 mins or 30 mins the system "MAY" go in to sleep mode. I have to press the keyboard a couple of times to get the system online or press the power button. The POWER LED will simply flash stating it is in standby mode. This system was running 17.xx and then i upgraded it to 18.04. Everything else seems to be working find except for this random sleep issue. Under power management - the setting: Put computer to sleep when inactive for: is set to  "Never". Any idea how to stop this would be helpful. 

Release: 
root@SGC:~# uname -a
Linux SGC 4.15.0-20-generic #21-Ubuntu SMP Tue Apr 24 06:16:15 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Thanks for any input. 
Kyle

---

### Post by Xian on 2018-05-01
It does sound like a possible bug. There are various other methods. 

Let's try this. Edit the acpi-support configuration file in a terminal:

```
sudo nano -w /etc/default/acpi-support
```

Scroll down .... and set the SUSPEND_METHODS="none"

Then restart the daemon:

```
sudo /etc/init.d/acpid restart
```

---

### Post by computer0freek on 2018-05-01
> **Xian said:**
> It does sound like a possible bug. There are various other methods. 

Let's try this. Edit the acpi-support configuration file in a terminal:

```
sudo nano -w /etc/default/acpi-support
```

Scroll down .... and set the SUSPEND_METHODS="none"

Then restart the daemon:

```
sudo /etc/init.d/acpid restart
```

Thanks for the reply. 
I just entered that. We will give that a try. 

Kyle

---

### Post by computer0freek on 2018-05-01
> **computer0freek said:**
> Thanks for the reply. 
I just entered that. We will give that a try. 

Kyle


Sorry to report that fix did not fix the issue. 

It still is going in to standby after about 10 min of inactivity. Even after a reboot.

---

### Post by computer0freek on 2018-05-01
I just changed ACPI_SLEEP from TRUE TO FALSE. Testing to see if that works.

---

### Post by computer0freek on 2018-05-01
> **computer0freek said:**
> I just changed ACPI_SLEEP from TRUE TO FALSE. Testing to see if that works.

This also failed.

---

### Post by computer0freek on 2018-05-02
Quick Update: 

System is going to sleep after 10 minutes of inactivity from the Desktop itself. However, the system will also go in to standby after 10 minutes even if I'm using an RDP/VNC session from XRDP or using Putty to SSH in to the box. I would be moving the mouse or opening an app within XRDP and it will just go to sleep. Sending a WAKE ON LAN Packet wakes the system back up. Funny note as well- I have an older Acer laptop that I just upgraded to 18.04. I have it set not to shutdown or go in to standby - it still does after 10 minutes and 10 seconds. I also have the lid set to leave the system on - meaning don't go to sleep when the lid is shut. The machine goes to sleep each time the lid shut down. It appears that at least in Mate- the power management is not working. 

Thanks,
Kyle

---

### Post by Xian on 2018-05-02
Assuming you have the gconf2 package installed .... 

Issue this command in a terminal [as non-root and no sudo]:

```
[COLOR=#111111][FONT=Ubuntu]gsettings set org.gnome.desktop.session idle-delay 0[/FONT][/COLOR]
```

Any change?

---

### Post by computer0freek on 2018-05-03
> **Xian said:**
> Assuming you have the gconf2 package installed .... 

Issue this command in a terminal [as non-root and no sudo]:

```
[COLOR=#111111][FONT=Ubuntu]gsettings set org.gnome.desktop.session idle-delay 0[/FONT][/COLOR]
```

Any change?


I'm sorry to report that this did not fix the issue on either my desktop or the acer laptop. The acer laptop is near clean install. The only thing installed on it is the nvidia graphics driver and Steam - the game client. The craziest thing on the desktop is the use of ZFS.

---

### Post by computer0freek on 2018-05-03
Is there any log that I can pull that would show the standby action? Is there a way to disable standby completely?

---

### Post by Xian on 2018-05-03
Well .... if we're going nuclear --- use a systemctl command to close all the doors.

```
sudo systemctl mask sleep.target suspend.target hibernate.target hybrid-sleep.target
```

Output should be like this:

```
$)&#9472;> sudo systemctl mask sleep.target suspend.target hibernate.target hybrid-sleep.target
Created symlink /etc/systemd/system/sleep.target &#8594; /dev/null.
Created symlink /etc/systemd/system/suspend.target &#8594; /dev/null.
Created symlink /etc/systemd/system/hibernate.target &#8594; /dev/null.
Created symlink /etc/systemd/system/hybrid-sleep.target &#8594; /dev/null.
```

To re-enable just substitute 'unmask' for 'mask'.

---

### Post by computer0freek on 2018-05-04
> **Xian said:**
> Well .... if we're going nuclear --- use a systemctl command to close all the doors.

```
sudo systemctl mask sleep.target suspend.target hibernate.target hybrid-sleep.target
```

Output should be like this:

```
$)&#9472;> sudo systemctl mask sleep.target suspend.target hibernate.target hybrid-sleep.target
Created symlink /etc/systemd/system/sleep.target &#8594; /dev/null.
Created symlink /etc/systemd/system/suspend.target &#8594; /dev/null.
Created symlink /etc/systemd/system/hibernate.target &#8594; /dev/null.
Created symlink /etc/systemd/system/hybrid-sleep.target &#8594; /dev/null.
```

To re-enable just substitute 'unmask' for 'mask'.

Thanks Man! I will try this out tomorrow :) The Desktop Runs almost like a server... Not running server like functions but act like a general storage device.

---

