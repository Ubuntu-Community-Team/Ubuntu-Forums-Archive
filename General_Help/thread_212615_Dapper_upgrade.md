---
title: "Dapper upgrade"
date: 2006-07-10
forum: General Help
---

### Post by kriding on 2006-07-10
As yet, I do not have my dapper install CD's so I tried to update from breezy using the 'dist-upgrade' command, and also the upgrade option in synaptic.

I have had dapper on my system before and it works great on my setup, however, for some reason it will no longer install.

I have the live CD that I burned, but even that will not load up the GUI. The install will take place as should (in all circumstances) and show no errors, however, when it comes to bringing up the login screen the system hangs at a black screen.

My current Breezy install is working great now I have set it up, but I have a nagging itch to get back up to dapper.

Can anyone help me with this one?

---

### Post by raldz on 2006-07-10
You mean you were able to install Dapper? The install finished? but when it rebooted, no xserver?

---

### Post by kriding on 2006-07-10
> **raldz said:**
> You mean you were able to install Dapper? The install finished? but when it rebooted, no xserver?

Yes, The install completes, it does it's final restart, I get the graphical interface which has 'Ubuntu' displayed and then shows a list of the services it is running, then the screen goes blank as normal, but instead of the login screen appearing, it remains blank

---

### Post by raldz on 2006-07-10
there could be different reasons for this, but one primary is the xserver configuration.. try to boot in Recovery Mode then execute this code in the terminal if you were able to login in the terminal:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by kriding on 2006-07-10
nothing...It wont even let me boot up the live CD

---

### Post by raldz on 2006-07-10
Mmmm.. I'm on a bump here, I don't know how to fix this if you couldn't even boot on the recovery console.. could you please post your hardware specs here so that if somebody else reads this and has similar problem like yours may help us out.. could be a hardware issue.. sorry, but don't lose hope, maybe someone else here could help after reading this..

---

### Post by raldz on 2006-07-10
ok, I remember it could be an acpi issue, I have this similar problem with a KM-400 motherboard.. here is what I did, when GRUB loads press "c" to boot manually then execute this codes:


Specify the location of your installation:
```
root (hd0,1)
```

Specify your kernel version and partition where it is installed (note that acpi=off):
```
kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro noapic nolapic quiet splash acpi=off 
```
Edit the numbers so that it corresponds to your kernel version:
```
initrd /boot/initrd.img-2.6.12-9-386
```

Finally:
```
boot
```

in essence, you will just add "acpi=off" on your boot commands

---

