---
title: "Connecting to Windows PC's"
date: 2007-09-04
forum: General Help
---

### Post by bschuteker on 2007-09-04
I have used Ubuntu in the past but always revert back to being a Windows user because I find something that doesn't work or work as well. I am trying to move to Ubuntu completely and stay there this time. I am a system engineer and maintain many different systems. I have to log in remotely to them. Gnome-RDP seems to work well but I can't find a way to ninimize it from full screen to get back to my desktop. I know that there is a key shortcut that will do it but I cant find it. 

Next issue is in windows I can just open a window and type \\server\share and it will prompt for a password and let me in. How can I acomplish the same thing in Ubuntu?

last thing, what is the best way to maintain all of my different wireless connections? Windows stores the info and automatically connects to which ever one is present and then switches to wired when it is present.

If I can solve these 3 main issues I think I can be a Linux user for life.

Thanks in advance for any help.

Edit Running Feisty on a Dell 1501

---

### Post by svtfmook on 2007-09-04
for connecting to a windows machine, just go to places > connect to server, select "windows share"

enter in the IP for the host and login (if needed) and it should mount the shared folders from the windows machine.

---

### Post by cwaldbieser on 2007-09-05
I use rdesktop for RDP, and the shortcut is CTRL+ALT+Enter.  Not sure if it is the same for the program you are using.

I use Kubuntu, so I open shares with the smb:/ URL.  E.g. "smb:/jupiter/d$".

---

### Post by expatal on 2007-09-13
To bschuteker about switching wireless networks:

Have you tried using the "Location" facility in the "Network Settings" tool (System >> Administration >> Network)? I know it's not automatic as in Windows, but it works fine for me - at least you can save as many network configs as you like.

---

### Post by Gas_Man on 2007-10-28
i use nautilus. or at least i think i do!

Places -> Home Folder

then in the address bar, i put

```
smb://192.168.1.141
```

this gives me all of my shares on my xp pro box

good luck

---

