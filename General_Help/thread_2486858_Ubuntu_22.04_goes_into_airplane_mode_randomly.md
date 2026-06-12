---
title: "Ubuntu 22.04 goes into airplane mode randomly"
date: 2023-05-14
forum: General Help
---

### Post by fahrbach on 2023-05-14
Sorry if this has been asked over and over but I did a suggested fix from the command line and it did not work.  Thought it did at first, but no.  There does not seem to be a knob in the Gnome GUI to stop this from happening.  Any help is greatly appreciated.  Thanks!

---

### Post by #&amp;thj^% on 2023-05-14
What are your computer specs?
```
sudo dmidecode | grep -A3 '^System Information'
```

---

### Post by fahrbach on 2023-05-14
Under wi-fi settings in Gnome you can turn off airplane mode.  But it will come back on.

---

### Post by #&amp;thj^% on 2023-05-14
> **fahrbach said:**
> Under wi-fi settings in Gnome you can turn off airplane mode.  But it will come back on.

Yes I'm aware of that, >> need to see what I asked for.

---

### Post by fahrbach on 2023-05-14
I receive:
Manufacturer: HP
Product Name: HP Pavilion Notebook
Version:

This is a clean from scratch install, was running 16.04 LTS.  Otherwise, the system runs flawlessly.

---

### Post by fahrbach on 2023-05-14
Tried this, did not work - or maybe I flubbed the edit.
[https://ubuntuhandbook.org/index.php/2022/04/disable-automatic-airplane-mode-ubuntu/](https://ubuntuhandbook.org/index.php/2022/04/disable-automatic-airplane-mode-ubuntu/)

---

### Post by #&amp;thj^% on 2023-05-14
"Airplane Mode" is automatically activated on boot for many HP laptops on Ubuntu?Debian
Here's a work around:
```
sudo nano /etc/systemd/system/hp-keycodes.service
```
Add this to that new file:
```
[Unit]
Description=HP setkeycodes fix

[Service]
Type=oneshot
Restart=no
RemainAfterExit=no
ExecStart=/usr/bin/setkeycodes e057 240 e058 240

[Install]
WantedBy=rescue.target
WantedBy=multi-user.target
WantedBy=graphical.target

```
Save and Exit, then run: 
```
sudo systemctl daemon-reload
sudo systemctl enable --now hp-keycodes.service
```
To revert back use:
```
 sudo rm -rf /etc/systemd/system/hp-keycodes.service
```
A reboot will be needed to see the changes.

---

### Post by fahrbach on 2023-05-14
Think I have it working...!!

---

### Post by #&amp;thj^% on 2023-05-14
Check with:
```
systemctl status hp-keycodes.service
```

---

### Post by fahrbach on 2023-05-14
Thank you.  I think I made the mistake of doing a reboot I would not need to enable the daemon.  Do you know if the service will go away with a reboot

---

### Post by fahrbach on 2023-05-14
Someone at Canonical needs to put in a knob in Gnome to either have this turned off and a timer setting.

---

### Post by #&amp;thj^% on 2023-05-14
> **fahrbach said:**
> Thank you.  I think I made the mistake of doing a reboot I would not need to enable the daemon.  Do you know if the service will go away with a reboot

Just so I'm clear here, **you do need the reboot **to see the change.
If you don't want that service any longer then use:
```
 sudo rm -rf /etc/systemd/system/hp-keycodes.service
```
Followed by:
```
sudo systemctl daemon-reload
sudo systemctl disable hp-keycodes.service
```
EDIT:
```
systemctl status hp-keycodes.service
&#9675; hp-keycodes.service - HP setkeycodes fix
     Loaded: loaded (/etc/systemd/system/hp-keycodes.service; enabled; preset: enabled)
     Active: inactive (dead) since Sun 2023-05-14 11:23:30 MDT; 1min 6s ago
    Process: 2216 ExecStart=/usr/bin/setkeycodes e057 240 e058 240 (code=exited, status=0/SUCCESS)
   Main PID: 2216 (code=exited, status=0/SUCCESS)
        CPU: 2ms

May 14 11:23:30 zfs-system systemd[1]: Starting hp-keycodes.service - HP setkeycodes fix...
May 14 11:23:30 zfs-system systemd[1]: hp-keycodes.service: Deactivated successfully.
May 14 11:23:30 zfs-system systemd[1]: **_Finished hp-keycodes.service - HP setkeycodes fix._**

```

---

### Post by #&amp;thj^% on 2023-05-14
> **fahrbach said:**
> Someone at Canonical needs to put in a knob in Gnome to either have this turned off and a timer setting.

This has nothing to do with Canonical but with HP themself.

---

### Post by fahrbach on 2023-05-14
I get:

hp-keycodes.service - HP setkeycodes fix
Loaded:  loaded (/etc/systemd/system/hp-keycodes.service; enabled; vendor p>
Active:  inactive (dead)

---

### Post by fahrbach on 2023-05-14
Guess that tells me that it's not working!  Who in the heck thought of this feature without tuning the parameters in Gnome? :-)

---

### Post by #&amp;thj^% on 2023-05-14
It's clearly not loaded, "Active: i**nactive (dead)** "

---

### Post by fahrbach on 2023-05-14
Action for closing lid should = "do nothing" if that is your choice.  But my HP will go into airplane mode when the lid is open!  Hey, Canonical is way better than MS at this so I hope they fix!. :-)

---

### Post by fahrbach on 2023-05-14
I get:

hp-keycodes.service - HP setkeycodes fix
Loaded:  loaded (/etc/systemd/system/hp-keycodes.service; enabled; vendor p>
Active:  inactive (dead)

---

### Post by fahrbach on 2023-05-14
Maybe so = HP, but there should still be a parameter setting in Gnome IMHO. Cheers

---

### Post by fahrbach on 2023-05-14
Would it be possible to have parameters = do not ever go into airplane mode or engage airplane mode after = certain amount of time. My HP Pavilion laptop randomly goes into airplane mode.  Someone suggested that this is an HP issue but I never had this happen running 16.04 LTS on the same machine. I did try the HP site suggestion about editing keycodes mapping at the command line but that did not work.  I can simply revert to 16.04 but I'd rather not.  Thank you!

---

### Post by fahrbach on 2023-05-14
Actually, there are no setting for airplane mode other than to turn it on under wi-fi settings.

---

### Post by #&amp;thj^% on 2023-05-14
The best I can offer you is this:
```

nmcli r wifi on 
```
turns airplane mode off, and the reverse sets it on.
You could write a script to toggle both.
Nothing personal, But I'll avoid Hp don't like their business model for Linux

---

### Post by coffeecat on 2023-05-14
@fahrbach, three points:

I've merged your two threads. The second thread is such a close follow-on from the first that splitting it in two may cause confusion and dilute community effort. Forum members need to know what has been said before.

Second point: you posted the second thread in the Ubuntu/Debian BASED sub-forum of the Other OS Support and Projects section of the forum, which is intended for operating systems which are not Ubuntu or the official flavours. You appear to be using Ubuntu. Your original choice of General Help is fine.

And thirdly: 

> **fahrbach said:**
> Would it be possible to have parameters = do not ever go into airplane mode or engage airplane mode after = certain amount of time.

This is a volunteer support forum whose membership consists of end-users such as yourself. We do not work for Canonical. This is not the place to request new features.

---

### Post by fahrbach on 2023-05-14
I did follow the steps from 1fallen but then looked to see if anything changed.  Command line reply was that it was not working but low and behold, the machine has not slipped into airplane mode.  Now this is an old HP Pavilion but it's got life left in it! :-)

---

