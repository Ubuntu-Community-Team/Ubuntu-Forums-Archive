---
title: "Ubuntu File Server"
date: 2014-11-18
forum: General Help
---

### Post by hessczoo on 2014-11-18
Hi everyone,

I am working on a new project for around the house and that is reconditioning my HTPC into a home server. I am looking mostly to have buIk storage for files, and perhaps use it as a print server. I would also like to backup my Windows machines into This server. This will be the sole Linux computer in my home network, which is comprised of 6 other Windows computers 2 of which are wired through an Asus AC68 Gigabit router. I am not new to Linux or Ubuntu but it has been a while and the first time for a home server. 

The specs of this machine are;

AMD A-10 5800I
8GB DDR3 RAM
Asus FM2A85M-PRO motherboard
2×2TB WD Green Hard Drives
256GB Crucial SSD.

So to sum up my questions;

Should I install Ubuntu Server or Desktop. A GUI will be preferred so is it easier to go with Desktop?

What should I use to share the files across the network? I would like to password protect all the data drives. SMB or NFS

I would also like to access this machine from outside my home network on my phone to grab files, does this change what software should I use?

What are my best options for raid? 0 or 5?

Thanks in advance, I am just getting back into dabbling with Linux again after a few years of hiatus and would appreciate some advice.

---

### Post by TheFu on 2014-11-19
This is all opinion.

In a home environment, you can use either desktop or server without much risk. X/Windows does increase the resources needed and does decrease overall system stability, but with 8G of RAM, it won't be any issue.

The way to share files with Windows machines on the LAN is through CIFS shares (samba).  NFS is much more efficient and faster and has many native permission sharing facilities ... but NFS on Windows sucks.  I was like you - mostly Windows machines. These days, I'm mostly Linux with just 1 Windows desktops and 1 Windows 7MC running inside a VM to record TV. Everything else is Linux and uses NFS.

The way to share files over the internet is through sftp (not plain FTP). By installing **openssh-server** and fail2ban - you've just setup sftp, scp, and ssh access that is secure enough to access from anywhere in the world - please disable passwords and only allow ssh-keys for remote access. WinSCP is a nice sftp client for Windows - there are client apps for every platform - on UNIX-like systems just use the CLI or any file manager (sftp://). 

Your choices for RAID 0/5 are both bad.  Use RAID1 or RAID10 and you still need excellent backups. RAID is never a substitute for backups. However, I wouldn't bother with RAID at all. If you want the storage to appear as a single directory to client machines there are other tools that will merge it but not risk all the data on both drives if 1 fails.

If you want to primarily share media files on the network - audio and video - then running a Plex Server will make any DLNA client device happy. I was using XBMC for a few years before discovering Plex.  Wish I would have switched to plex years earlier.  There is a plugin for XBMC - PleXBMC that makes the organized files under Plex available. The only downside I've found for Plex is that it doesn't handle commercial skipping EDL files whereas XBMC does.

Anyway - those are my opinions.

---

### Post by mastablasta on 2014-11-19
> **hessczoo said:**
> 
Should I install Ubuntu Server or Desktop. A GUI will be preferred so is it easier to go with Desktop?

you do not need a GUI, you can use a webgui instead. Zentyal has official support, but there are others as well. I am currently using Ajenti. very fast and has most of the features I wanted. you then control the server via your browser by typing the server's IP in the search bar.



> 
What should I use to share the files across the network? I would like to password protect all the data drives. SMB or NFS


SMB on LAN, sFTP on external. fail2ban by default does not save blocked IP. and by default is missing one entry as I recently found out. However I managed to set it up properly now so if you need help with that hit the PM button....

> 
What are my best options for raid? 0 or 5?


Raid is for redundancy not for backup. if you want redundancy then just go with Raid 1 in other cases it is not necessary, but TheFu explained it better.

a few more things:
> 
I would also like to backup my Windows machines into This server

How do you plan to do that on windows?

I have tested Luckybackup and it doesn't want to start the backup process for some reason on windows PC. haven't figured it out yet why. I might try to compile it form source.

I also tested Areca Backup - worked fine on test but I noticed it is creating some files on local disk and deleting them and it is not clear if these are just some temp config files or whole copies of the files. it does support all features that I want (automatic backup, nice GUI, snapshots in time, compressed and uncompressed backup, throttle of bandwidth...). however while trying to figure out what temp files it is writing I noticed that some users had issues with larger backups. so still testing

next one I think is duplicity or something similar (forgot it's name). still haven't begun with tests. this is mostly what I found for windows. rdiff is also an option but it's only CLI and has limitations.

> 
256GB Crucial SSD.


it's good to check the tweaks for SSD to extend it's life and such (reduce swapiness, log files? ...). 8 GB doesn't need much swappiness...

btw for only a file server the PC is very strong. I am mostly using between 250 and 400MB max (on updates and during workload). swap was never touched yet. I am thinking of investigating some virtual hosts option.

if you don't mind Debian Openmediavault has a nice GUI for servers. wish they made it on top of Ubutnu instead of Debian. but oh well... it was their decision. 

as for file sharing with outside users you might want to look at ownCloud. it's not perfect with it's client but pretty good. they have a simple client for win, Linux, android, ios... you name it. server is also descent with some nice plugins.

---

