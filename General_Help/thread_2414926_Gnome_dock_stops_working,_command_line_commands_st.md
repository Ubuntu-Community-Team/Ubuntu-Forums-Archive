---
title: "Gnome dock stops working, command line commands stop working, reboot hangs"
date: 2019-03-17
forum: General Help
---

### Post by jaygridley on 2019-03-17
**System Information:**
OS: Ubuntu 18.10 x86_64 
Host: HP ZBook 15 G2 A3009DD10303 
Kernel: 4.18.0-16-generic 
Uptime: 16 mins 
Packages: 1774 (dpkg), 3 (flatpak),  
Shell: bash 4.4.19 
Resolution: 1920x1080, 1920x1080, 19 
DE: GNOME 3.30.2 
WM: GNOME Shell 
WM Theme: Adwaita 
Theme: Yaru [GTK2/3] 
Icons: Yaru [GTK2/3] 
Terminal: gnome-terminal 
CPU: Intel i7-4810MQ (8) @ 3.800GHz 
GPU: NVIDIA Quadro K610M 
Memory: 933MiB / 32083MiB 

**Background:**
This is a work laptop that I'm using a USB 3.0 external hard drive on. Ubuntu boots and runs without too many issues. Before installing Ubuntu I had ran through Arch and then Manjaro i3 edition. What prompted me to switch over to Ubuntu was an issue I was encountering and thought maybe it was i3. Since I was extremely unfamiliar with Arch based linux and i3 I decided to move over to something I had used previously. It appears I'm running into the same issue on this Ubuntu set up as well and I'm not sure what it is or how to pin it down.

I have the laptop on a docking station. 
I cannot use the Nvidia drivers so I'm using the Nouveau drivers. If I install the Nvidia drivers and try to boot then all my text is is garbled and we never make it to a desktop.

**Issue: **
So far the issue seems to happen overnight. So basically I go to use the machine in the morning and I have the following symptoms.
[LIST]
[*]The Gnome bar on the left is shrunk, the icons are missing, and generally doesn't look to be there except if you look real close you can see the outline of the bar. 
[*]The drop down in the status bar at the top where the logout button is is gone. 
[*]I usually leave the Terminal open over night and when this issue presents itself, all command line commands fail. Usually with a note that the command is not found. Everything from 'ls' to 'reboot' doesn't work. 
[*]I have to hard reset the machine to get it booted back up. 
[/LIST]

I've set "Dim screen when inactive" to off.
"Blank Screen" is set to Never.
"Automatic suspend" is set to Off.

**Update:**
I just now had the first instance of this happening when I stepped away for 10 minutes. I ran out to the garage and had my .conkyrc1 file open in GEdit. I ran outside to the garage and spent about 10 minutes out there. I came back in and made an edit and then tried to save the file. GEdit gave me a 'Could not save the file {path}. Unexpected error: Error when getting information for file "{path}": Input/output error.'

Since everything pretty much stops working, I'm not sure if my drive is still technically mounted or not. Conky still seems to show that the Ubuntu partition is still being recognized so I don't think the drive disconnected.

**Update #2:**
I noticed something this time when rebooting. The shutdown text all seems to indicate that the drive is in a Read-only file system state. I'm wondering if this is somehow related.

systemd-journald[324]: Failed to write entry (9 items, 332 bytes), ignoring: Read-only file system

Pic of errors; 
[IMG]https://imgur.com/F3ofCmd[/IMG]

---

