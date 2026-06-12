---
title: "Files disappears from the launcher Ubuntu 16.04"
date: 2016-04-21
forum: General Help
---

### Post by gregurbo1 on 2016-04-21
Fresh install of Ubuntu 16.04. Nautilus (Files) will not stay in the unity launcher. I unpinned it now I can't pin it back. As soon as you open files from unity dash it disappears from the launcher after a split second. I put the usb I used to install Ubuntu back in to check if the same thing happens in the live iso and I can confirm the problem exits in the live iso also.&#65279;

---

### Post by sanislav on 2016-04-22
Can confirm Linux x1 4.4.0-21-generic #37-Ubuntu SMP Mon Apr 18 18:33:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by jonnylinuxnerd on 2016-04-24
I'm also having this issue! Looks like it's been reported here [https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/1565194](https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/1565194) . Click the affects me too button to let the developers know it's affecting multiple people :)

---

### Post by mc4man on 2016-04-24
Something similar happened here on fresh 16.04 install, seemed to be using wrong .desktop
Fixed here by 
Unlocking the icon from unity launcher if there.
Then - 
alt+f2
run this command, nautilus should open, lock that icon & see if better behaved
```
gtk-launch nautilus.desktop
```

Note that that's not actually the correct .desktop but it should produce the proper link in launcher

Or - 
unlock launcher if there.
Open a terminal & go 
nautilus
Lock that launcher

---

### Post by kd6ftr on 2016-04-24
> **mc4man said:**
> Something similar happened here on fresh 16.04 install, seemed to be using wrong .desktop
Fixed here by 
Unlocking the icon from unity launcher if there.
Then - 
alt+f2
run this command, nautilus should open, lock that icon & see if better behaved
```
gtk-launch nautilus.desktop
```

Note that that's not actually the correct .desktop but it should produce the proper link in launcher

Or - 
unlock launcher if there.
Open a terminal & go 
nautilus
Lock that launcher

Thanks for this. That is definitely a work-around for now.

---

### Post by jonnylinuxnerd on 2016-04-25
> **mc4man said:**
> Something similar happened here on fresh 16.04 install, seemed to be using wrong .desktop
Fixed here by 
Unlocking the icon from unity launcher if there.
Then - 
alt+f2
run this command, nautilus should open, lock that icon & see if better behaved
```
gtk-launch nautilus.desktop
```

Note that that's not actually the correct .desktop but it should produce the proper link in launcher

Or - 
unlock launcher if there.
Open a terminal & go 
nautilus
Lock that launcher

Thanks for the suggestion! :) Sadly for me, it only seems to work for the duration of that nautilus session before not working again! :( (Same as unlocking and re-dragging files back into the launcher) Anyone else experiencing that?

---

### Post by kunism14 on 2016-05-10
I went to **/usr/share/applications** and took a backup of **nautilus.desktop** and **org.gnome.Nautilus.desktop**

Then:

[LIST=1]
[*]In **nautilus.desktop**, removed "**NotShowIn=Unity**;"
[*]In **org.gnome.Nautilus.desktop**, added **"NotShowIn=Unity;**"
and removed "**OnlyShowIn=Unity;**"
[/LIST]

So now I use nautilus.desktop instead which works better. But I assume there's some disadvantage to this.

---

### Post by jonnylinuxnerd on 2016-06-30
I think I might have *finally* solved this one. Anyone still having trouble try reinstalling the '[FONT=Courier New]ubuntu-settings[/FONT]' package and ensure no other 'settings' packages are installed.

---

### Post by adlawren on 2016-07-16
> **jonnylinuxnerd said:**
> I think I might have *finally* solved this one. Anyone still having trouble try reinstalling the '[FONT=Courier New]ubuntu-settings[/FONT]' package and ensure no other 'settings' packages are installed.

Confirmed, ty!

---

### Post by warm-stegosaurus on 2017-01-06
> **jonnylinuxnerd said:**
> I think I might have *finally* solved this one. Anyone still having trouble try reinstalling the '[FONT=Courier New]ubuntu-settings[/FONT]' package and ensure no other 'settings' packages are installed.

This also worked for me. Thanks.

---

### Post by warm-stegosaurus on 2017-01-07
> **warm-stegosaurus said:**
> This also worked for me. Thanks.

Well it turns out the solution worked for me for a little while, but it's no longer working. It certainly is an annoying bug. When I installed Ubuntu 16.04 I did a fresh install, but I kept everything on my home partition and so I wonder if there is some setting file in my home directory that is messing things up.

---

### Post by warm-stegosaurus on 2017-01-07
Nautilus is currently working for me: it shows up in the launcher and in alt + tab. The way I got it to work was to delete a whole bunch of old configuration files and folders (the ones where the names start with a period) in my home directory. I'm not sure exactly what configuration file was causing the problem, but some of these were left over from Ubuntu 14.04 and probably even 12.04.

---

