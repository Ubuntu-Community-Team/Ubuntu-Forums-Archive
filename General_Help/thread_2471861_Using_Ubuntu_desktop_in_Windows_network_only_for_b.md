---
title: "Using Ubuntu desktop in Windows network only for backup"
date: 2022-02-11
forum: General Help
---

### Post by jesrani on 2022-02-11
I have a small office with 10 computers and all are on Windows, ranging from XP to Win10. Some of these came with the machines to which they are connected so the operating system cannot be changed/updated without updating the equipment.
All computers are setup with same username/password/workgroup. The user is standard user. Admin user is enabled with common password. All computers have some a folders shared on network with Full Control to administrators only.
I have been using an Ubuntu desktop since more than 10 years to backup the shared folders on the network computers using RSync. The current computer is a Core2Duo desktop and has Ubuntu 14.04. It's working fine so far but the hardware is giving trouble and may fail (MB or HDD), so I was thinking of taking a new desktop with SSD and HDD and make a new setup so I wanted some advice.
I am not really familiar with Linux and don't use it myself. I have managed the earlier installation after taking advice on this forum and have the complete installation procedure written down. My query is whether I should again use Ubuntu for this purpose and use the same procedure as I have been doing for backing up the windows shares, or is there some easier option now available.
The setup I had earlier done was as below :
1) Made USB with Rufus and for Ubuntu 14.04 with Mate
2) Partitioned a 250Gb HDD manually, no partition selected for /boot, since my understanding was that /boot is for multiple OS booting. Made 2Gb SWAP partition, 30 Gb ext4 primary partition for /, 30gb ext4 primary partition for /home and 186Gb ext4 logical partition for /home. Now I am planning to install 120Gb SSD and 2Tb HDD so how should the partitions be?
3) Edited Network connection, named wired connection to same as other Windows Workgroup computers, changed IP to static. Is this still how it needs to be done?
4) Installed dconf-editor and dconf-tools. Do I still need these or anything better available?
5) Installed Desktop Sharing app, opened in dconf-editor with command vino-preferences, configured to accept incoming connection and gave password. In org->gnome->desktop->remote-desktop, using dconf-editor, changed port (forward set in router), lock screen on disconnect, use-alternative port also checked, require-encryption unchecked. Had to add the command /usr/lib/vino/vino-server –sm-disable to startup applications to get VNC working. Is this still the way to enable VNC. I access the computers through LAN as well as internet when I am not in office so this is required.
6) In Startup Applications, added command mate-screensaver-command --lock so that screen is locked after login so no one can access the desktop
7) Installed cifs-utils, winbind, system-config-samba, sbackup, gparted, cups. Are all these now preinstalled or is there anything new in their place?
8) Installed Webmin by downloading the .deb file. I think I used it for editing the Cron jobs and managing some other things. Is this still a good option?
9) Created /BackupDisk and /network under root and changed owner and group of these as well as /data to myself. I think I need to create /BackupDisk and /network (for backing up network shares) under the HDD now rather than SSD. Would that be correct?
10) Since the desktop is used without monitor/keyboard in /etc/default/rcS, made FSCKFIX=yes so that there is no interruption when having any error.
11) In Samba I added the Windows Workgroup name and username and password. For some reason I had to do sudo apt-get install --reinstall samba samba-common cifs-utils winbind system-config-samba followed by apt-get install --reinstall libsmbclient libsmbclient-dev libtevent0 libtalloc2 to get Samba working at that time. Not sure if this is still relevant.
12) Had done sudo pluma /etc/nsswitch.conf and added wins before dns in the line hosts to resolve computer name. Is this still needed?
13) Followed instructions in [https://ubuntuforums.org/showthread.php?t=637258](https://ubuntuforums.org/showthread.php?t=637258) to set up automount of Windows shares. Had to make some changes as needed to get things running.
14) A 1Tb HDD was added and mounted to /BackupDisk.
15) The network shares were mounted under /network with automount
16) I created .sh files in /data/Rsync to backup the folders under /network to /BackupDisk. Added Crontab scheduled jobs through Webmin to run the backup files automatically with command export DISPLAY=:0 && mate-terminal -x /data/Rsync/01_Su_Mo_Tu_We.sh. I also added a command to restart automount before the backups. This was needed as sometimes the windows computer shuts down and the mounted folder in Ubuntu becomes empty so if backup is run all the files in it are also deleted.
17) Achieved Ubuntu VNC running without monitor by “sudo apt-get install xserver-xorg-video-dummy” and then creating a /etc/X11/xorg.conf and adding commands to it. Is this still the way to do it?

Sorry for the very long post and I hope to get some valuable advice from this forum.

---

### Post by ActionParsnip on 2022-02-11
Ubuntu 14.04 is end of life (EOL)
Windows XP is also EOL
Why do you not have a domain controller rather than lots of local accounts? It'd make your life a lot easier.

---

### Post by jesrani on 2022-02-11
> **ActionParsnip said:**
> Ubuntu 14.04 is end of life (EOL)
Windows XP is also EOL
Why do you not have a domain controller rather than lots of local accounts? It'd make your life a lot easier.

Ubuntu 14.04 was working as it's only a backup computer. Now I want to replace since the old computer is having problem so I will put the new version of Ubuntu.
I can't replace XP in the computer it is installed since it is linked to an equipment so I have replace the complete equipment which is just too expensive.
I don't know about domain controller as we don't have an inhouse IT person and it is too expensive to hire one. We are in a small town with no local tech help. I want to keep things simple which I can handle myself.

---

### Post by mIk3_08 on 2022-02-11
> **jesrani said:**
> Ubuntu 14.04 was working as it's only a backup computer.
If you have plan to go with the ESM (Extended Security Maintenance) on Linux Ubuntu 14.04 heres the link below: 
[https://ubuntu.com/blog/ubuntu-14-04-esm-support](https://ubuntu.com/blog/ubuntu-14-04-esm-support) 
These can also help stabilize your Linux Ubuntu 14.04 Operating System.
Good Luck and Cheers.

---

### Post by dragonfly41 on 2022-02-11
[COLOR=#000000]"... so I was thinking of taking a new desktop with SSD and HDD and make a new setup so I wanted some advice".

[/COLOR]If you have a spare PC for experiments you could install on it an up to date Ubuntu LTS version and create virtual machines (Windows) to run your legacy equipment. Rufus on Windows can create Ubuntu LiveUSB. If that experiment works you can duplex the setup for operational reliability. If you already have Webmin installed you can leverage the Webmin Custom Commands option to create your own set of ops commands. Remember in modern Ubuntu to move to modern UEFI and not the legacy architecture.

In other words you could run Windows XP inside a vm on Ubuntu 20.04 parent. You might be able to use fewer PC's using virtual Windows images instead.

[P.S] This post seems similar to your problem of continuing with old equipment

[https://www.tek-tips.com/viewthread.cfm?qid=1769749](https://www.tek-tips.com/viewthread.cfm?qid=1769749)

---

### Post by TheFu on 2022-02-11
I didn't read the whole first post.  EOL OSes ...
For backups, check out backupPC. [https://backuppc.github.io/backuppc/](https://backuppc.github.io/backuppc/)

These days, end-user desktops shouldn't hold any company data. It should all be written directly to network drives. Backing up a storage server is much easier and you can tell all the end-users that when there is any issue, you'll perform a fresh OS install using the "golden image".  Ensure this change is in the corporate IT policy.

---

### Post by jesrani on 2022-02-12
> **dragonfly41 said:**
> [COLOR=#000000]"... so I was thinking of taking a new desktop with SSD and HDD and make a new setup so I wanted some advice".

[/COLOR]If you have a spare PC for experiments you could install on it an up to date Ubuntu LTS version and create virtual machines (Windows) to run your legacy equipment. Rufus on Windows can create Ubuntu LiveUSB. If that experiment works you can duplex the setup for operational reliability. If you already have Webmin installed you can leverage the Webmin Custom Commands option to create your own set of ops commands. Remember in modern Ubuntu to move to modern UEFI and not the legacy architecture.

In other words you could run Windows XP inside a vm on Ubuntu 20.04 parent. You might be able to use fewer PC's using virtual Windows images instead.

[P.S] This post seems similar to your problem of continuing with old equipment

[https://www.tek-tips.com/viewthread.cfm?qid=1769749](https://www.tek-tips.com/viewthread.cfm?qid=1769749)

I think VirtualMachines don't support PCI cards and the equipment is connected through PIC Slot. Can't reduce PC's since each PC is needed with the machine.


> **TheFu said:**
> I didn't read the whole first post.  EOL OSes ...
For backups, check out backupPC. [https://backuppc.github.io/backuppc/](https://backuppc.github.io/backuppc/)

These days, end-user desktops shouldn't hold any company data. It should all be written directly to network drives. Backing up a storage server is much easier and you can tell all the end-users that when there is any issue, you'll perform a fresh OS install using the "golden image".  Ensure this change is in the corporate IT policy.

We are not a corporate, just a small company in a small town in India. Cannot afford a dedicated IT person. I need to do things which I can manage.

Thank you all for the replies. I think I asked too many questions so I didn't get relevant answers. I will do some trial installations on my own and see what suits me best and ask specific questions if I am stuck up.

I would appreciate if I can just get an answer on how to best automount and backup Windows shares, whether through the method given in [https://ubuntuforums.org/showthread.php?t=637258](https://ubuntuforums.org/showthread.php?t=637258) or is there anything better available?

---

### Post by SeijiSensei on 2022-02-12
You might look into the Linux Terminal Server project [https://ltsp.org/](https://ltsp.org/).

---

### Post by TheFu on 2022-02-12
> **jesrani said:**
> We are not a corporate, just a small company in a small town in India. Cannot afford a dedicated IT person. I need to do things which I can manage. 

My response will actually save you effort and complexity. If you don't have a "golden image", no worry.  But having all data saved off the desktops is mandatory and a well-known, long-used, solution to all sorts of problems. If you have more than 5 people, centralized user management will be easier for both you AND the end-users. When a computer fails, you'll be able to bring in any other computer, tie it to the central LDAP, and because all the data is on a server (which is well backed up), the user will not have lost any data.

It is hard to ensure that 20 systems are backed up, especially desktops.  It is much easier to have 1-2 (former desktops) have RAID1 and plenty of storage along with relatively easy backups.  Plus, removing the MS-Windows backup complexity will make your life easier too.

All for $0.

Be aware that "automount" means something very specific in the Unix world. On Linux, this is handled using **autofs** which uses **automountd**.  Best to say "Mount at boot", if that is your goal. The better search terms should help you to find what you need.

---

