---
title: "evince problem crashing the whole system"
date: 2008-06-03
forum: General Help
---

### Post by Santooka on 2008-06-03
well it simply crashes the system for me
as soon as i open a pdf file, the whole system freezes except the mouse cursor, and i have to reset and reboot the system.
well it happens after rolling down the pages, or selecting a link in the document.
help, please?

---

### Post by pytheas22 on 2008-06-03
Please provide a little more information:

Did this problem just start suddenly or has it always occurred since you installed Ubuntu?  Have you tried running evince from a terminal to see if any information related to the crash gets dumped there?  Could you take a look at your system log (you can view it by going to System>Administration>System Log) to see if there's any information there about what specifically is going wrong at the time that the system crashes?

---

### Post by Santooka on 2008-06-08
well after some days of experimenting , i figured out that it's not about evince at all.....
it's about compiz....
it freezes the system, i mean to be able to work right now i disabled the visual effects totally so it doesn't lock me hard
i tried several stuff to try to fix it
i changed the nvidia driver to nvidia-new-glx-envy, but nothing happened
i tried to install the xserver-xgl and it ruined my screen resolution.
i uninstalled and reinstalled compiz itself, but it still do the same action
which is freezeing for half a minute , and i have to move the mouse;s cursor to the close button so i close the program immediatley as soon as the freeze is over cause if i let it it will lock me hard.
ummm.. let's see what elese did i try....
i tried to remove the nvidia-new-glx and install the old nvidia-glx and it ruined my screen resolution too.

i installed a new kernel version with its restricted drivers and modules, and there was no progress here neither

i dunno if there's any solution for this
actually i am not happy without my screen effects

do u ppl have any idea what to do?

---

### Post by pytheas22 on 2008-06-08
What is the exact model of your graphics card?  If you don't know, post the output of the command:
```

lspci
```

It would also be helpful if you opened a terminal and from there typed:
```

compiz --replace
```

and post here the output that gets dumped to the terminal.

Also, have you always had this problem since installing Ubuntu, or did desktop effects used to work correctly?

---

### Post by Santooka on 2008-06-10
for the lspci code:
> 00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)
02:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


and for the compiz --replace command:
> Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0326 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x960) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

so have any ideas about this?
ahhh by the way , i have nvidia Geforce FX 5500

and i didn't have this problem since i got ubuntu , it happened recently , i upgraded to hardy and it was fine and suddelny it happened once a day , and later it happened several times a day , and now i shut the visual effects totally so it doesn't freeze or lock me hard

---

### Post by pytheas22 on 2008-06-10
The output of compiz in the terminal looks like everything's working alright, at least for the time you ran it.

When you uninstalled compiz, did you use the "remove completely" option?  If not, it might help to do:
```

sudo apt-get remove --purge compiz*
```

(be sure it doesn't uninstall anything else important as a dependency; it shouldn't, but don't forget to check) and then reinstall it again.  This should remove any configuration files that could be the source of the problem.  You could also try getting rid of the compiz settings for your user account:
```

mv ~/.compiz ~/.compiz-old
```

You might also try making a new user account and using that for a while to see if the freezes still occur.  This would tell you if the problem lies with some setting relevant to your current user account or a more globabl problem.

You could also check the system logs (/var/log/syslog) and the X logs (/var/log/Xorg*log) to see if anything useful gets recorded at the time of the crashes.

Finally, I found a thread [here]("http://ubuntuforums.org/showthread.php?p=4320931") started by someone with the same graphics card as you and issues that sound similar.  The solution mentioned there didn't work for him or her, but it's worth a shot.

Please post if you make any useful discoveries.

---

### Post by Santooka on 2008-06-12
well i tried what u told me to do and nothing happened :S

---

