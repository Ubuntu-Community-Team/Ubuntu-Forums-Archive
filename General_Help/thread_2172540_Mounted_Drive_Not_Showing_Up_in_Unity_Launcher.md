---
title: "Mounted Drive Not Showing Up in Unity Launcher"
date: 2013-09-05
forum: General Help
---

### Post by ChochiWpg on 2013-09-05
[COLOR=#333333][FONT=UbuntuRegular]I am currently using Ubuntu 13.04 and I tried to update the kernel today to 3.11. After doing so I was having issues with Unity where I could log into my user account but it would only display the wallpaper. I couldn't see the Unity launcher or menu bar.
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]So I rebooted my system and through GRUB I booted using the previous kernel. Same thing happened and I only had wallpaper. Was able to get everything back again by performing the below tasks.
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]dconf reset -f /org/compiz/[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]unity --reset-icons &disown
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]So now I am back to the 3.8.0.30 kernel, I have purged the 3.11 kernel and my Unity Launcher and menu bars are back and things are functioning as normal.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]The issue I am having now though is when I go to files and mount my Windows Drive (to access the files located in the drive) it doesn't show up as being mounted on the Unity Launcher. It does show as mounted in Files and I can navigate and open all my files as normal, but nothing shows up on the launcher indicating it is mounted. Usually it shows a harddrive icon on the launcher and you can right click and unmount from there. I have to go back into Files, right click on my Windows drive and unmount from there.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]It isn't a huge inconvenience, but I am just wondering why mounted drives are not displaying on the Unity Launcher and what I can do to get it back? Thanks.[/FONT][/COLOR]

---

### Post by ChochiWpg on 2013-09-08
I posted this question a few days ago, just curious if anyone happens to know the answer or knows what I could do to try and troubleshoot the issue?  Thanks.

---

