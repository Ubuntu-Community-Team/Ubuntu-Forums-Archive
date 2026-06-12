---
title: "Newbie here. Ubuntu 21.10. Which Gnome extension creating my taskbar?"
date: 2022-02-08
forum: General Help
---

### Post by Advait on 2022-02-08
[COLOR=#000000][FONT=Arial]See pic here [/FONT][/COLOR][COLOR=#1155cc]_[https://imgur.com/lj2DHrq.png](https://imgur.com/lj2DHrq.png)_[/COLOR][COLOR=#000000][FONT=Arial] for details.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Here&#8217;s the list of my Gnome extensions. Is Dash to Panel installed and active? I can&#8217;t tell.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]```
advait@advait-Bravo-15-A4DDR:~$ dpkg --list 'gnome-shell-extension*'[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Desired=Unknown/Install/Remove/Purge/Hold[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]||/ Name                                     Version       Architecture Description[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]+++-========================================-=============-============-==================================================================[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]ii  gnome-shell-extension-appindicator       40-1          all          AppIndicator, KStatusNotifierItem and tray support for GNOME Shell[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]un  gnome-shell-extension-autohidetopbar     <none>        <none>       (no description available)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]un  gnome-shell-extension-caffeine           <none>        <none>       (no description available)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]un  gnome-shell-extension-dash-to-panel      <none>        <none>       (no description available)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]un  gnome-shell-extension-dashtodock         <none>        <none>       (no description available)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]un  gnome-shell-extension-desktop-icons      <none>        <none>       (no description available)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]ii  gnome-shell-extension-desktop-icons-ng   20-0ubuntu3   all          desktop icon support for GNOME Shell[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]un  gnome-shell-extension-gamemode           <none>        <none>       (no description available)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]un  gnome-shell-extension-multi-monitors     <none>        <none>       (no description available)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]un  gnome-shell-extension-pixelsaver         <none>        <none>       (no description available)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]ii  gnome-shell-extension-prefs              40.5-1ubuntu2 amd64        tool to enable / disable GNOME Shell extensions[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]un  gnome-shell-extension-taskbar            <none>        <none>       (no description available)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]un  gnome-shell-extension-top-icons-plus     <none>        <none>       (no description available)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]ii  gnome-shell-extension-ubuntu-dock        70~ubuntu3    all          Ubuntu Dock for GNOME Shell[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]un  gnome-shell-extension-workspaces-to-dock <none>        <none>       (no description available)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]un  gnome-shell-extensions                   <none>        <none>       (no description available)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]advait@advait-Bravo-15-A4DDR:~$ 
```[/FONT][/COLOR]

---

### Post by KBar on 2022-02-08
You already had an active thread.

No, you don't have it installed via APT. You probably installed them from GNOME Shell extensions website, which was mentioned in [my reply]("https://ubuntuforums.org/showthread.php?t=2471635&p=14079724#post14079724") to you in the other thread.

I guess I'll paste it here…
[QUOTE=KBar]Unfortunately, I don't use GNOME so I can't really tell what it is. On  the GNOME Shell extensions website, there is a tab called *Installed extensions*.  Depending on your web browser, you need a dedicated extension (i.e.  browser add-on) to access it. Check whether you have it installed and  also get the list of extensions if you can. There is also a separate app  for extensions on your desktop named *Extensions*. Check there.                 [/QUOTE]

---

### Post by dragonfly41 on 2022-02-08
Hit the SuperKey (windows icon) and in the popup query type Extensions.
Hit the green button.

---

### Post by Advait on 2022-02-08
> **dragonfly41 said:**
> Hit the SuperKey (windows icon) and in the popup query type Extensions.
Hit the green button.

Perfect. Thanks. It says Dash to Panel is activated.

---

### Post by Advait on 2022-02-08
> **KBar said:**
> You already had an active thread.

No, you don't have it installed via APT. You probably installed them from GNOME Shell extensions website, which was mentioned in [my reply]("https://ubuntuforums.org/showthread.php?t=2471635&p=14079724#post14079724") to you in the other thread.

I guess I'll paste it here…

[COLOR=#000000][FONT=Arial]My feeling right now is to just live with the issue. Nautilus still works even though the icon doesn't work right. Dash to Panel is very important for me and I'm nervous about uninstalling it and installing from apt. On a few occasions I've tried fixes like that and they subsequently badly messed up my system. So I don't want to take any chances. Perhaps I'll try your suggestion when I'm able to get 2 good backup images of my system drive.

And when I get some time I'll switch to BTRFS and (if I understand it correctly) I'll be able to effortlessly restore a previous system state.[/FONT][/COLOR]

---

