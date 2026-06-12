---
title: "Unable to configure file sharing - 20.04"
date: 2020-05-01
forum: General Help
---

### Post by makem2 on 2020-05-01
I want to share folders across the LAN between two Linux machines but I get errors.

On the 20.04 machine I get the error, "Failed to open "XPS-13-9300 (File Sharing)".

From an 18.04 machine I get the error, "Failed to open "XPS-13-9300". Failed to receive share list from server: Connection refused.

I am able to browse the 18.04 machine from the 20.04 machine.

I configured the sharing on the 20.04 machine using this guide:

[URL="https://linuxconfig.org/how-to-configure-samba-server-share-on-ubuntu-20-04-focal-fossa-linux"]https://linuxconfig.org/how-to-configure-samba-server-share-on-ubuntu-20-04-focal-fossa-linux
[/URL]
/etc/smb.conf:

```

[global]
   workgroup = WORKGROUP
   server string = %h server (Samba, Ubuntu)
   log file = /var/log/samba/log.%m
   max log size = 1000
   logging = file
   panic action = /usr/share/samba/panic-action %d
   server role = standalone server
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user
   usershare allow guests = yes
[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
[homes]
   comment = Home Directories
   browseable = yes
   read only = no
   create mask = 0700
   directory mask = 0700
   valid users = %S
[public]
  comment = public anonymous access
  path = /var/samba/
  browsable =yes
  create mask = 0660
  directory mask = 0771
  writable = yes
  guest ok = yes

```

---

### Post by ActionParsnip on 2020-05-01
Why use samba if both systems are Linux? Install openssh-server on the server side and you can mouse SFTP using Nautilus. Use your Ubuntu username and password on the server side to connect. This is also a secure connection and traffic between the systems is encrypyed

---

### Post by makem2 on 2020-05-01
Thank you for your suggestion.

Neither machine is a server, just two machines used by two persons at the same time who want to send files either way whenever the need arises with the least possible hassle inside the LAN. Having to use passwords every time is a hassle and is it really needed inside the LAN?

---

### Post by Tadaen_Sylvermane on 2020-05-01
Just easier. Samba is more server oriented really, and mainly for sharing to Window's machines. Not that it's wrong of course. But an sftp is simpler and more direct.

---

### Post by makem2 on 2020-05-01
> **Tadaen_Sylvermane said:**
> Just easier. Samba is more server oriented really, and mainly for sharing to Window's machines. Not that it's wrong of course. But an sftp is simpler and more direct.

I follow you but I do have one windows machine on the LAN and the user is not computer savvy, wanting to copy/paste.

Is there a copy/paste sft facility available? I have never come across it. I use putty and terminal sftp at times.

Edit: Interesting comments for 18.04:

[URL="https://discourse.ubuntu.com/t/the-default-file-sharing-and-media-sharing-experience-in-18-04/3834"]https://discourse.ubuntu.com/t/the-default-file-sharing-and-media-sharing-experience-in-18-04/3834


[/URL][https://help.ubuntu.com/stable/ubuntu-help/sharing-personal.html.en](https://help.ubuntu.com/stable/ubuntu-help/sharing-personal.html.en)

But where have they hidden the Sharing Panel now?

[URL="https://help.ubuntu.com/stable/ubuntu-help/sharing-media.html.en"]https://help.ubuntu.com/stable/ubuntu-help/sharing-media.html.en
[/URL][URL="https://help.ubuntu.com/stable/ubuntu-help/sharing-media.html.en"]


[/URL][URL="https://help.ubuntu.com/stable/ubuntu-help/sharing-media.html.en"]


[/URL]

---

### Post by makem2 on 2020-05-01
Well. isn't this brilliant!

Official Ubuntu documents: Share your personal files.

"You must have the gnome-user-share package installed for      Personal File Sharing to be visible."

I am finally getting somewhere! Do as you are instructed and install gnome-user-share package, sounds good! 

No, to good to be true! Oh dear linux, linux why so hard for untrained users??

1. Open the [Activities]("https://help.ubuntu.com/stable/ubuntu-help/shell-introduction.html.en#activities") overview and       start typing Sharing.
2. Click on Sharing to open the panel.

No 'Sharing' to click on!

New user: No, I've had enough, goodbye.

I don't give up that easy but why is it so hard?

Edit: Well I found 'File Sharing' in /user/share/applications. Hurray!

Oh dear! Not another problem? Yep, clicking on the link File Sharing does nothing, absolutely nothing except change its coulour! Can play the game next to it by clicking though :)

Checking the launcher setting for it find, "Launch File Sharing if enabled" but we did enable it by installing gnome-user-share did we not? So, it must be enabled somehow, the switch! But that is in the Sharing Panel which we can't find! Hmm, now what?

Somebody, anybody? I'm in lockdown and can't run away!

---

### Post by ActionParsnip on 2020-05-01
The system sharing files is a server. It's a file server. You can send each other files using the SSH protocol and works around Samba

---

### Post by makem2 on 2020-05-01
> **ActionParsnip said:**
> The system sharing files is a server. It's a file server. You can send each other files using the SSH protocol and works around Samba

I believe you, both machines are servers in that respect,  but how?

Every way I go comes up with a dead end even using the instructions from official documents.

---

### Post by Dennis N on 2020-05-01
> **makem2 said:**
> I believe you, both machines are servers in that respect,  **but how**? Every way I go comes up with a dead end even using the instructions from official documents.

You could install **openssh-server** and **gigolo** on both computers. Gigolo is an application that helps you connect and manage your connections between Linux machines. All you need is the IP addresses. It bookmarks the details for repeated use. It can even connect to several other computers at once. And it's fairly easy to use with GUI. Then from either machine, you can open file manager windows to the other machine. Use copy and paste or drag and drop to move files between them.   

Have fun networking.

---

### Post by HermanAB on 2020-05-01
All Linux file browsers support sftp.  Enable ssh server on both machines and make a 'shortcut' on the desktop of each machine to connect to the other machine.

This is absolutely trivial compared to running the beast that is samba.

---

### Post by makem2 on 2020-05-01
Ubuntu says that 20.04 comes with Gnome Desktop. It did not. My install had Xfce. I have installed Gnome Desktop.

I now have a choice of:

Gnome
Gnome Classic
Gnome on Xorg
Gnome on Xorg
Ubuntu
Ubuntu on Wayland
Xfce Session
Xubuntu Session

I tried Gnome and switched file sharing to active.

Accessing 20.04 from 18.04 I find that there are now two connections available, both XPS-13-9300 (File Sharing). Both gave the original errors I have always had above.

I tried each of the other log-in option with the same result.

There is some setting in 20.04 which is preventing access although all settings appear correct.

---

### Post by coffeecat on 2020-05-01
> **makem2 said:**
> Ubuntu says that 20.04 comes with Gnome Desktop. It did not. My install had Xfce. 

Then you must have installed Xubuntu, not Ubuntu. Ubuntu 20.04 comes with Gnome Desktop. I'm posting from such a system at the moment which I installed from the Ubuntu 20.04 ISO.

---

### Post by makem2 on 2020-05-01
> **coffeecat said:**
> Then you must have installed Xubuntu, not Ubuntu. Ubuntu 20.04 comes with Gnome Desktop. I'm posting from such a system at the moment which I installed from the Ubuntu 20.04 ISO.

Yes, I did. :oops:

I assumed incorrectly that Ubuntu was the base and a variety of desktops were available, all having 'at the bottom' Ubuntu. Therefore the basic settings would be available.

I have always used Xfce and don't like any of the Desktops I have tried.

I would have thought something as basic and necessary to most, as file sharing should be easy to configure no matter what desktop is installed? Let those who know how remove it, disable it or whatever when they install a flavour of ubuntu. In my opinion there would be more users and less messed up, insecure systems if Linux catered for the novice user.

Anyway, regardless, I still have my problem: a 20.04 which can see windows, humax boxes and raspberry pi's but hides from 18.04. I have not tried from windows or the pi's yet.

When I try to access the shared folders in 20.04 from 20.04 I get the same error. It is even hiding from itself!

Edit: This what convinced me I was right to assume Gnome was installed as default:

"When you [install Ubuntu 20.04]("https://linuxconfig.org/how-to-install-ubuntu-20-04-focal-fossa-desktop")  it will come with the default GNOME 3.36 desktop. Gnome 3.36 is full of  improvements and results in better performance and a more aesthetically  pleasing graphical experience

[http://When you install Ubuntu 20.04 it will come with the default GNOME 3.36 desktop. Gnome 3.36 is full of improvements and results in better performance and a more aesthetically pleasing graphical experience](http://When you install Ubuntu 20.04 it will come with the default GNOME 3.36 desktop. Gnome 3.36 is full of improvements and results in better performance and a more aesthetically pleasing graphical experience)

---

### Post by HermanAB on 2020-05-01
The trouble is that Samba is total overkill.  The book is 2 inches thick.  You will always struggle with it.

---

### Post by makem2 on 2020-05-01
> **HermanAB said:**
> The trouble is that Samba is total overkill.  The book is 2 inches thick.  You will always struggle with it.

Then would you suggest how I get a simple file sharing going inside a LAN for someone who just wants copy/paste from folder to folder?

Windows is happy, Raspberry Pi's are happy, Two Linux Humax boxes are happy with samba.

---

### Post by makem2 on 2020-05-01
> **Dennis N said:**
> You could install **openssh-server** and **gigolo** on both computers. Gigolo is an application that helps you connect and manage your connections between Linux machines. All you need is the IP addresses. It bookmarks the details for repeated use. It can even connect to several other computers at once. And it's fairly easy to use with GUI. Then from either machine, you can open file manager windows to the other machine. Use copy and paste or drag and drop to move files between them.   

Have fun networking.

Sorry, I missed your post. I will check.

Bliddy hell!!!

Gigolo is already installed in xubuntu on both machines!

---

### Post by Morbius1 on 2020-05-01
There is a bug in gvfs that prevents any ubuntu system from accessing any server that disables SMB1 ( NT1 in samba-speak ). That means Win10 and now Ubuntu 20.04.

This means you cannot browse to then connect to a share through Thunar for those servers. 

But it doesn't mean you cannot access them at all - you just have to ask for it explicitly:

In Thunar's location bar enter:
```
smb://XPS-13-9300.local/public
```

**EDIT**: And your [Public] share isn't set up correctly if you are using this in a more peer-to-peer mode when john and sally just want to share some stuff.

---

### Post by makem2 on 2020-05-01
Well, with my previous knowledge (a little) that was easy to set up.

I read the manual for setting up the server and realised I had been there before.

I thank you again, solved.

---

### Post by makem2 on 2020-05-01
> **Morbius1 said:**
> There is a bug in gvfs that prevents any ubuntu system from accessing any server that disables SMB1 ( NT1 in samba-speak ). That means Win10 and now Ubuntu 20.04.

This means you cannot browse to then connect to a share through Thunar for those servers. 

But it doesn't mean you cannot access them at all - you just have to ask for it explicitly:

In Thunar's location bar enter:
```
smb://XPS-13-9300.local/public
```

**EDIT**: And your [Public] share isn't set up correctly if you are using this in a more peer-to-peer mode when john and sally just want to share some stuff.

Thank you for that information but I had solved the problem with help from Dennis N before I read your post.

I think for me, openssh-server and gigolo is the way to go and I will note your method.

---

### Post by TheFu on 2020-05-01
If you are still interested in using ssh-based solutions, between Unix systems, we can easily configure ssh-key-based authentication, so you'll be asked to unlock the key once every day or every 6 hours or every minute ... or never.  All the file managers on Linux should support   sftp://.... URLs using cached ssh-key credentials. LAN or internet (with just some ssh-port open).

From Windows, use WinSCP (which supports scp and sftp protocols). It is drag-n-drop.  I think FileZilla supports sftp too.  Someday, MSFT will add sftp to their file manager. They are only 25 yrs behind.  ssh has been THE WAY that Unix systems communicate since 1995.

I don't have samba running on anything newer than 16.04, but would really be surprised if that wouldn't work. Usually the problems with samba come down to 3 things:
[LIST=1]
[*]name resolution i.e. DNS
[*]different SMB protocol versions i.e. Win10 changed the default and so did the samba project.
[*]username authentication i.e. some networks want to use MS-AD for authentication, which can be tricky.
[/LIST]

Samba didn't have any encryption for a long time.  I think v2.1 and later have encryption which samba can enable pretty easily.

But really, using sftp is 5x easier to setup and use.  Plus, sftp, scp, ssh, rsync, sshfs, x2go, NX, most backup tools, etc can all be used over the internet. The encryption is considered secure enough for that to be allowed.  Locking down ssh automatically locks down all the others too. There are well understood controls to allow access by userid, subnet, groups, too.

Anyways, 
[LIST=1]
[*]1 command: 2 package installs, ssh and fail2ban on all the Linux systems, then
[*]2 commands: create the ssh-keys, push the public key to any remote systems, then
[*]1 command: verify that name resolution is working.  That's one of these: avahi, dns, /etc/hosts.
[/LIST]

If you want to get fancy, the ~/.ssh/config file can make life easier to access systems using different keys, different ports, different usernames, and only knowing the IP, which you'll never need to know again.  All ssh-based tools honor that config file, so connections to remote systems over odd IPs, using different accounts is something you'll never think about again.

Want to go over the internet to access a server you control?  Easy, provided that server has a static IP on the LAN and you can forward a tcp-port from the WAN IP into the LAN IP of the server.  Not needed for outbound connections or LAN-only connections.

Doing it the Unix-way makes for a great experience. Don't fight it. 

But we can try to get smb/CIFS working too.
* Note the time.
* Try to connect from the client to the server.
* Check the server-side log files for that time.
* What are the errors/warnings?

I know that ssh connections from 16.04 to 20.04 (mate, ubuntu and server) installs "just works."  Basically, ssh is the way I connect to other systems 99% of the time. Going the other way ... let me test that. I've kept my 20.04 Mate desktop pretty minimal to this point, since I think it will be what I migrate from 16.04 onto.

20.04 --[ssh]--> 16.04 Desktop worked using a password. Let me setup an ssh-key and push it to a few machines:
```
ssh-keygen -t ed25519
ssh-copy-id hadar
ssh-copy-id istar
ssh-copy-id lubuntu
ssh-copy-id nextcloud

```
Now, I can ssh, sftp, scp, rsync, rdiff-backup, sshfs from the 20.04 client (regulus), to any of those other systems without being prompted more than once every 12 hrs thanks to the ssh-agent and ssh-add.
```
$ ssh hadar
```

```
$ ssh-agent
$ ssh-add ~/.ssh/id_ed25519

```
There might be a GUI way to add this to some key-chain. IDK. I work on systems without any GUI mostly.

I really love ssh, if that isn't clear.

---

### Post by makem2 on 2020-05-01
Thank you[**[COLOR=#000000] TheFu[/COLOR]**]("https://ubuntuforums.org/member.php?u=1037685")  for your detailed information which I have bookmarked. I am happy with the Gigolo and openssh-server method. As Gigolo is already installed I think Ubuntu is pointing the way for me anyway as it is quite simple to set up.

I am able now to browse all machines and use copy/paste in thunar and Windows. It took less minutes to set up than it took hours to find the Gigolo solution.

I was able to connect FROM 20.04 to other machines. My problem was connecting TO 20.04. then I found there was a bug in the method I was using which prevented access. Can't find the link now as I've done so much trawling around.

I have messed around so much with this xubuntu install that I will reinstall it as it was a fresh install on a new machine. Even the /home partition will need replacing I think.

---

### Post by HermanAB on 2020-05-02
BTW, WIndows 10 now has OpenSSH available.

In general, Windows file browsers support only two network file systems by default: CIFS/Samba and Anonymous FTP.

With the addition of OpenSSH, you will also get SFTP support.  There is also a client program called Winscp that works pretty good on older versions of Windows.

---

### Post by makem2 on 2020-05-02
> **HermanAB said:**
> BTW, WIndows 10 now has OpenSSH available.

In general, Windows file browsers support only two network file systems by default: CIFS/Samba and Anonymous FTP.

With the addition of OpenSSH, you will also get SFTP support.  There is also a client program called Winscp that works pretty good on older versions of Windows.

Thank you.

I have used Winscp in the past.

---

### Post by Paulgirardin on 2020-06-08
> **makem2 said:**
> 

I have messed around so much with this xubuntu install that I will reinstall it as it was a fresh install on a new machine. Even the /home partition will need replacing I think.

Have a look at Peppermint OS It's Ubuntu based ,has the XFCE DE and has Nemo as the file manager (better than thunar or nautilus)
[https://peppermintos.com/](https://peppermintos.com/)

---

