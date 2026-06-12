---
title: "Ubuntu File Recovery"
date: 2006-07-23
forum: General Help
---

### Post by mike2587 on 2006-07-23
Hello-

I was speaking to a friend of mine in regards as to how to setup ubuntu on my computer using it as a livecd so that i can transfer my important files from my computer with the windows system error (which won't allow me to access the desktop), however, he couldn't figure it out because the samba file isn't in the directory, so this kind of got thrown on me, which is fine because it was a favor anyway.  Unfortunately, he kind of left me hanging with this and i really need some files that are on my computer as soon as humanly possible, hopefully by tomorrow i can get access to these.  Both computers are on the same network i just have to figure out how to set up so that the terminal will set up access or something??  Basically i'm stuck, if someone out there could please try and walk me through just setting it up so i can transfer all my documents over i would greatly appreciate it..  I'd even offer some money for some help, i'm pretty desparate.

Thank you in advance,

[email]mike2587@msn.com[/email]

---

### Post by aysiu on 2006-07-23
I don't know much about samba, but if you're booting the Ubuntu live CD on your Windows copmuter, you don't need samba.

All you need to do is mount your Windows partition and then get your files onto a USB key, an iPod, or some other storage device.

First thing you should do is go to Applications > Accessories > Terminal.

Paste (Shift-Insert) this command into the terminal ```
sudo fdisk -l
``` That's a lowercase L, not the number one. This will give you your partition table. Find the appropriate NTFS partition--we'll assume, for this example, that it's /dev/hda1.

Then, paste these commands in: ```
sudo mkdir /recovery
sudo mount -t ntfs /dev/hda1 /recovery -o nls=utf8,umask=0222
``` Finally, go to Places > Computer > Filesystem > recovery, and you'll see your Windows files.

---

### Post by mike2587 on 2006-07-24
ok i have my files awesome!!  but how can i transfer them over to another computer that's on the same network????????

---

### Post by aysiu on 2006-07-24
> **mike2587 said:**
> ok i have my files awesome!!  but how can i transfer them over to another computer that's on the same network????????
Ah, there I cannot help you. I know virtually nothing about networking computers--in Ubuntu or Windows. You don't have any external media--USB drives, iPods, external hard drives, zip drives?

Have you tried going to Places > Network Servers?

---

### Post by mike2587 on 2006-07-24
or how do i get the ubuntu to recognize my mp3 player??  so that i can put stuff on it??  or ipod??

---

### Post by aysiu on 2006-07-24
> **mike2587 said:**
> or how do i get the ubuntu to recognize my mp3 player??  so that i can put stuff on it??  or ipod??
It should automatically recognize it. Just plug it in...

---

### Post by JoWilly on 2006-07-24
> **mike2587 said:**
> ok i have my files awesome!!  but how can i transfer them over to another computer that's on the same network????????

system/admin/shared folders and set it up with samba.

---

### Post by wieman01 on 2006-07-24
> **JoWilly said:**
> system/admin/shared folders and set it up with samba.

Yes, you need to use Samba for it. Plus - if you are trying to share files with Windows machines, you'll need to configure a workgroup (which is also fairly simple). 

I did it before but after eliminating my Windows clients, this is as much as I can say. But there are many posts out there that will guide you through Samba, Windows file sharing, and the "shared folder" tool in Gnome/KDE (which uses Samba as an option).

---

### Post by Herman on 2006-07-24
I have never had any trouble accessing Windows computers from a Ubuntu System, if a Windows Network is established, and the IP address for the Ubuntu System is allowed in both the SP2 firewall and the third party firewall in Windows. 
All I do is go 'Places' --> 'Network Servers' --> 'Windows Network'.
Ubuntu has that ability 'out of the box', you don't need Samba.
Ubuntu will be able to 'See' all the Windows boxes, and read and write to any shared folders just fine! :D

However, the Windows boxes will  not be able to 'see' the Ubuntu System on the Network.
That's fine as long as you are happy to use your Ubuntu system as your master system and do most of your  work from Ubuntu. (Which suits me).
The only reasons I know of for installing Samba are when someone might want to share printers on a mixed network or if they want to be able to access their Ubuntu System from Windows. I never did feel comfortable with opening my security that much personally. Maybe I'm just being superstitious though, I really don't know very much about networking to be honest, or about IPTables.
Regards, Herman :D

---

