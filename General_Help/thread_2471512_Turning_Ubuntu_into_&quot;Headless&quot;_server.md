---
title: "Turning Ubuntu into &quot;Headless&quot; server"
date: 2022-02-01
forum: General Help
---

### Post by couzin2000 on 2022-02-01
So I run this Ubuntu machine at home, it operates as my home server. I leave the GUI on so I can tunnel into it using Teamviewer. Samba gives me all the rest of the access I need from within Windows 10 or my macOS Monterey. I'm able to download movies, shows, songs, and games from my Windows machine and copy them over to the Ubuntu home server, and then play them off my Plex player on my Mac.

The Ubuntu machine was an old Compaq computer, it has been replaced by a home-built Intel machine. Lots more ram, space to keep drives, and so on. 

The old machine had 18.06 LTS. Never upgraded. For it to work continuously, I had to connect a dummy plug into the DisplayPort for it to continue on. Otherwise, Teamviewer would establish a connection, but I would get a black screen. So that worked for a few years. 

Now I am installing 20.04 LTS on the new machine. It also has a DisplayPort. Will this all work the same? I have no recollection of having done anything other than just connectiong the dummy plug, no software mod.

I tried doing it, but the machine crashed because of something else... so I am left with questions unanswered. Should I be doing anything when I reinstall?


EDIT: I tried installing Focal but ran into major issues with it detecting my RAID1 array. So I destroyed the RAID array and created a RAID0 instead (they're SSDs so I should get some reliability out of them), and went for Beaver instead. As of now I am running 18.06 LTS again. Hopefully the dummyplug will work again, but we'll see. I still need some answers.

---

### Post by HermanAB on 2022-02-02
I would use SSH instead of Teamviewer.  

When using OpenSSH, a server doesn't need a GUI running.  SSH has a limited X server and client built in and therefore you can launch X programs remotely on a server using "ssh -X user@server programname", without actually having Xorg running on the server.

---

### Post by couzin2000 on 2022-02-03
> **HermanAB said:**
> I would use SSH instead of Teamviewer.  

When using OpenSSH, a server doesn't need a GUI running.  SSH has a limited X server and client built in and therefore you can launch X programs remotely on a server using "ssh -X user@server programname", without actually having Xorg running on the server.

I understand that. But my goal is not to use SSH. I need to be able to Teamviewer in. Which requires the GUI. But thanks for the good try.

---

### Post by naxal on 2022-02-04
Hello,

Have you tried using XRDP option of remote desktop?

I have one Ubuntu 20 LTS Computer within my local home network and xrdp works fine with headless mode.

Thanks.

---

### Post by couzin2000 on 2022-02-17
> **naxal said:**
> Hello,

Have you tried using XRDP option of remote desktop?

I have one Ubuntu 20 LTS Computer within my local home network and xrdp works fine with headless mode.

Thanks.

No, I haven't. BUt I'll be frank, I don't intend to. I prefer using the Teamviewer interface I already have. 

SO - I have to find info about removing the mouse, keyboard and monitor while this server functions, reboots and auto logs-in. I do have a Display port dummy plug, perhaps this can help? I do have to tell my BIOS I'll be using the DP output from this point on, though. Otherwise it'll register through the VGA that no monitor is detected. 

Anybody have links to point me to?

---

### Post by couzin2000 on 2022-02-17
Well, as it turns out, I was unable to run the PC with the dummy plug because the Display Port output had never been used before. I pulled a DP-connected monitor from work to plug it into the server. It turned on, worked, so I had the server reboot. Before the turn-off cycle ended, I pulled out the DP connector from the PC, and instead put in the dummy plug. That did it - the BIOS seemed to remember it was supposed to boot to that output, and the dummy plug did its job and let the server think it had a monitor in. 

For the mouse and keyboard, I used this little USB wireless connector for a wireless keyboard I own, which I don't use. I serves the function of the dummy plug as well - even when the keyboard isn't turned on.

All works! Thanks all!

---

### Post by HermanAB on 2022-02-18
It looks like you found neat solutions to 
make it work.  I am wondering about some edge cases: What if there was a power failure and  reboot which wants to run fsck requiring a Press Any Key to Continue kind of thing?

---

