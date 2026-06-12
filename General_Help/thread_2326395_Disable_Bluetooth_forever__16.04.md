---
title: "Disable Bluetooth forever?  16.04"
date: 2016-05-31
forum: General Help
---

### Post by TheFu on 2016-05-31
[https://help.ubuntu.com/16.04/ubuntu-help/bluetooth-turn-on-off.html](https://help.ubuntu.com/16.04/ubuntu-help/bluetooth-turn-on-off.html)

Explains how to disable it manually in the GUI.  I´m seeking a way to disable it forever since being hacked through an unused bluetooth connection previously. I don´t and have never used bluetooth. To me, seems like an added security risk.

Would be nice if the documentation covered this scenario too, BTW.

I suspect the answer will be related to systemd.  Tried 
```

  sudo systemctl stop bluetooth
  sudo systemctl disable bluetooth

```

status returns:```

$ sudo systemctl status bluetooth
&#65533;&#65533; bluetooth.service - Bluetooth service
   Loaded: loaded (/lib/systemd/system/bluetooth.service; disabled; vendor preset: enabled)
   Active: active (running) since Tue 2016-05-31 13:01:13 EDT; 5min ago
     Docs: man:bluetoothd(8)
 Main PID: 8548 (bluetoothd)
   Status: "Running"
   CGroup: /system.slice/bluetooth.service
           &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;8548 /usr/lib/bluetooth/bluetoothd

May 31 13:01:13 cc3550 bluetoothd[8548]: Not enough free handles to register service
May 31 13:01:13 cc3550 bluetoothd[8548]: Not enough free handles to register service
May 31 13:01:13 cc3550 bluetoothd[8548]: Current Time Service could not be registered
May 31 13:01:13 cc3550 bluetoothd[8548]: gatt-time-server: Input/output error (5)
May 31 13:01:13 cc3550 bluetoothd[8548]: Not enough free handles to register service
May 31 13:01:13 cc3550 bluetoothd[8548]: Not enough free handles to register service
May 31 13:01:13 cc3550 bluetoothd[8548]: Sap driver initialization failed.
May 31 13:01:13 cc3550 bluetoothd[8548]: sap-server: Operation not permitted (1)
May 31 13:01:13 cc3550 bluetoothd[8548]: Endpoint registered: sender=:1.47 path=/MediaEndpoint/A2DPSource
May 31 13:01:13 cc3550 bluetoothd[8548]: Endpoint registered: sender=:1.47 path=/MediaEndpoint/A2DPSink

```

and the service is still running.


TIA.

---

### Post by yoshii on 2016-05-31
What you can do is use gedit or mousepad or leafpad or geany or whatnot to edit and create an .override file.  
Use the terminal console:  

sudo gedit /etc/init/bluetooth.override

when the blank document opens up, just type on one line:

manual

...and then save the file.  
The file should be "/etc/init/bluetooth.override" and it should simply contain one line with the word "manual" in it.  
Then log out and restart the computer and bluetooth should be disabled.  

If you later want to get bluetooth back, just "sudo rm /etc/init/bluetooth.override" from a terminal console.  

In the "/etc/init/" folder, you can find lots of .conf configuration files.  If you want to disable something else, the procedure is pretty much the same...
create an .override file (containing just the word "manual") corresponding to the .conf file and service you want to disable.  For example, apport.override

Also, check in "/etc/xdg/autostart/" to see if anything about bluetooth is in there too.  If it is, create a folder "/etc/xdg/autostart-disabled" and move the 
bluetooth-related .desktop file into that to disable it from autostarting.  

I hope this is helpful.

---

### Post by QDR06VV9 on 2016-05-31
I have always just edited /etc/rc.local
Like this
```
sudo nano /etc/rc.local
```

add this line before exit 0

```
rfkill block bluetooth
```
Screens Before and After and it works for Xenial also.
```
$ sudo systemctl status bluetooth
&#9679; bluetooth.service - Bluetooth service
   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset
   Active: inactive (dead)
Condition: start condition failed at Tue 2016-05-31 11:39:12 MDT; 1h 17min ago
           ConditionPathIsDirectory=/sys/class/bluetooth was not met
```

Hope this helpful
Kind Regards

---

### Post by ajgreeny on 2016-05-31
I am not yet using 16.04 but in the past I have used bum (Boot Up Manager) to remove services at boot and stop them running.

You could also remove bluetooth from the machine, but take care as some of the bluetooth libraries are dependencies of other packages that you probably do want to keep.

---

### Post by QDR06VV9 on 2016-05-31
> I´m seeking a way to disable it forever since being hacked through an  unused bluetooth connection previously. I don´t and have never used  bluetooth. To me, seems like an added security risk.

Would be nice if the documentation covered this scenario too, BTW.
I just stopped it by editing "/lib/systemd/system/bluetooth.service"
```
sudo nano /lib/systemd/system/bluetooth.service

```
Then I commented out **"ExecStart=/usr/lib/bluetooth/bluetoothd "**
So it now looks like this

```
[Unit]
Description=Bluetooth service
Documentation=man:bluetoothd(8)
ConditionPathIsDirectory=/sys/class/bluetooth

[Service]
Type=dbus
BusName=org.bluez
# ExecStart=/usr/lib/bluetooth/bluetoothd
NotifyAccess=main
#WatchdogSec=10
#Restart=on-failure
CapabilityBoundingSet=CAP_NET_ADMIN CAP_NET_BIND_SERVICE
LimitNPROC=1

[Install]
WantedBy=bluetooth.target
Alias=dbus-org.bluez.service



```

Now it shows in the terminal
```
~$ sudo systemctl status bluetooth
[sudo] password for me: 
&#9679; bluetooth.service - Bluetooth service
   Loaded: error (Reason: Invalid argument)
   Active: inactive (dead)
```
Maybe more what you are after
I have an old friend tell me that this works also but i had already made my changes so I duno for sure...check it out if you want or just to verify.
```
sudo "echo 'manual' > /etc/init/bluetooth.override"
```
I'll be curious.

---

### Post by TheFu on 2016-05-31
Thanks guys!

The override - assuming it works - is the way to go.  Already had that w/ the ¨manual¨ inside, but I hadn´t rebooted. Generally only reboot when a new kernel requires it.

Had a number of things setup by the installer (mate as the GUI) that I don´t want - set those to manual and removed them from the autostart.  Is the **autostart-disabled** a special directory or just a smart name?  For example, could I use a autostart/disabled/ instead and would that work equally well?

I was under the impression that rc.local wasn´t being called with systemd ... haven´t migrated any of my servers over to 16.04 or created any new servers yet to know.  There isn´t any reference to it inside /etc/init/, but there is in the old /etc/init.d/ - hopefully that is all backwards compatible.

Will someone be able to update the documentation to reflect the /etc/init/ and xdg/autostart stuff? Would be nice to have that solved for this release.

BTW, **sudo gedit** (or more GUI editors) can have undesirable side effects. There was an entire discussion in these forums about a year ago.  **sudoedit** was proposed as a solution. The other was to use policy-kit.  

Anyway - thanks for the pointers.  I´ll reboot in a sec and post back.

---

### Post by jeremy31 on 2016-05-31
Another option would be to blacklist the btusb module as it is used in one way or another with any bluetooth chip I have ever used
```
echo "blacklist btusb" | sudo tee -a /etc/modprobe.d/bluetooth-blacklist.conf
```

---

### Post by TheFu on 2016-05-31
Just to confirm that the  /etc/init/bluetooth.override worked.

---

### Post by QDR06VV9 on 2016-05-31
Nice and thanks for the conformation. And also pointing out [B]using "sudo" with any GUI is highly discouraged.
[/B]Cheers

---

### Post by cbraxton on 2016-05-31
> **TheFu said:**
> 
I was under the impression that rc.local wasn´t being called with systemd ... haven´t migrated any of my servers over to 16.04 or created any new servers yet to know.


I've been using rc.local in my 16.04 system and it appears to be working OK.

---

