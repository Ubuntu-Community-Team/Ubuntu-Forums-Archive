---
title: "Help With VMPlayer"
date: 2006-07-09
forum: General Help
---

### Post by nami on 2006-07-09
Hi

I wanted to try out the VmPlayer so I installed it using synaptics and searched for vmware-player.  It installed without any errors.

According to this link
[https://help.ubuntu.com/community/InstallingVmPlayer](https://help.ubuntu.com/community/InstallingVmPlayer)

I have an old windows 95 cd and thought i will try that first.  So I used EasyVMX and selected the appropriate options.  It then gave me a .zip file to download. I downloaded it and extracted it onto my desktop.

I now have a Windows95 folder on my desktop.

It then says that I need to double click on the vmx file to start the virtual machine.  But each time I click that file it just opens up in gedit?

So instead I right click the file, and selected 'Open With "VMware Player"'.

I then got the following error:

[[IMG]http://img275.imageshack.us/img275/9386/screenshot11wg.th.jpg[/IMG]](http://img275.imageshack.us/img275/9386/screenshot11wg.jpg)

then when i click "ok", i get the following error:

[[IMG]http://img287.imageshack.us/img287/9193/screenshot23sm.th.jpg[/IMG]](http://img287.imageshack.us/img287/9193/screenshot23sm.jpg)

What am I doing wrong?

Please help

Thanks

nami

---

### Post by nami on 2006-07-09
I just tried to install it again from the terminal this time and got the following errors

> nami@nami-desktop:~$ [COLOR="RoyalBlue"]sudo apt-get install vmware-player[/COLOR]
[COLOR="Red"]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.[/COLOR]
nami@nami-desktop:~$ [COLOR="RoyalBlue"]sudo dpkg --configure -a[/COLOR]
Setting up vmware-player (1.0.1-4) ...
Now configuring VMware Player.  (This may take some time...)
Configuring a bridged network for vmnet0.

Configuring a NAT network for vmnet8.

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.202.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet8/dhcpd/dhcpd.conf that this program was about to
install already exists.  Overwrite? [yes]

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases that this program was about to
install already exists.  Overwrite? [yes]

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases~ that this program was about to
install already exists.  Overwrite? [yes]

The file /etc/vmware/vmnet8/nat/nat.conf that this program was about to install
already exists.  Overwrite? [yes]

Configuring a host-only network for vmnet1.

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.60.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet1/dhcpd/dhcpd.conf that this program was about to
install already exists.  Overwrite? [yes]

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases that this program was about to
install already exists.  Overwrite? [yes]

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases~ that this program was about to
install already exists.  Overwrite? [yes]
[COLOR="Red"]
Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual ethernet                                                   failed
Module vmnet is not loaded.  Please verify that it is loaded before
running this script.

invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player[/COLOR]
nami@nami-desktop:~$

---

### Post by nami on 2006-07-09
I managed to fix the problem above by uninstalling then reinstalling it again.

But now, when I insert the Windows 95 cd into the drive, and double click the  .vmx file, I get the following error?

[[IMG]http://img430.imageshack.us/img430/2571/screenshot3og.th.jpg[/IMG]](http://img430.imageshack.us/img430/2571/screenshot3og.jpg)

Any ideas?

nami

---

### Post by ejn on 2006-07-09
I think that Windows CD versions prior to Windows 2000 were not bootable. There should be a directory on the cd somewhere that will allow you to make a bootable floppy disk.

hope that helps,
Ed

---

### Post by nami on 2006-07-13
something went wrong with my ubuntu and had to reinstall it from scratch.  Now I am trying to install vmware player again and I am getting the original error I posted in this thread.  I have install and uninstalled many times but it makes no difference?

I'm getting the following error
[[IMG]http://img291.imageshack.us/img291/4886/screenshot9ba.th.jpg[/IMG]](http://img291.imageshack.us/img291/4886/screenshot9ba.jpg)

HELP!

---

### Post by matrooswolf on 2006-07-13
Just a suggestion
Did you try vmware server instead of player?
Sets up like a breeze.

[http://www.ubuntuforums.org/showthread.php?t=183209](http://www.ubuntuforums.org/showthread.php?t=183209)

---

### Post by scxtt on 2006-07-13
make sure you install EVERYTHING that synaptic offers for vmware ... i had this same problem (only w/ player) after a fresh install of dapper a few days ago ... all the same errors, but once i installed all vmware related packages - it worked ...

btw, don't waste your time w/ W95 - download a virtual appliance from  vmware.com to use (if you just wanna test it) ...

---

### Post by nami on 2006-07-14
2 questions:

1. what does vmware player that vmware server does not have?
2. what does vmware server that vmware player does not have?

---

### Post by scxtt on 2006-07-14
server is just more robust, and you can create VM's using it - whereas player (not suprisingly) "plays" already created VMs ... so if you've already got a few (and aren't planning to create any more) you can quickly use player [tho easyvmx.com can allow you to create the files necessary to get a new VM running (i used it last night to install FC5, worked flawlessly)] ...

one isn't better than the other, tho i recommend server if you're not to familiar w/ VMing overall since it can guide you through making VMs a little more intuitively than the easyvmx & player route ...

---

### Post by pchap123456 on 2006-07-15
I have the same exact problem as Nami, i.e.

S[COLOR="Red"]tarting VMware services:
Virtual machine monitor failed
Virtual ethernet failed
Module vmnet is not loaded. Please verify that it is loaded before
running this script.

invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
vmware-player[/COLOR]

I tried de-installing and reinstalling but the problem persists. I also installed VMNET (via Synaptics) but it didn't help.

Any hints?

Thanks, Phil

---

### Post by nami on 2006-07-15
I just tried again and STILL can't get it to work after a clean ubuntu re-install!!!

What's going on?

Is it a repository problem or something, or a bug in ubuntu?

---

### Post by nami on 2006-07-15
Also, I can't install vmware server, it says that i already have some vmware stuff installed even though i removed vmware player?

any suggestions?

---

### Post by nami on 2006-07-15
This is how I got it to work.

1. Do a complete removal from synaptics
2. Download the tar file from [http://www.vmware.com/download/player/](http://www.vmware.com/download/player/)
3. untar it
4.open a terminal, navigate to the folder
cd /path/to/folder
5. sudo ./vmware-install.pl
6. answer yes to overwrite a million times
7. When it asks to setup networking type in no
8. If you make a mistake start over.

If it complaints about you having vmware already installed, do a full drive search and remove any rouge vmware folders.  Unfortunately I cant remember which i removed and which i left.  I think I left all the once in the cache folders!

Then I followed the instructions above.

nami

---

### Post by Useless on 2006-07-16
Ha!  Looks like i am having the same problem.  I have tried reinstalling multiple times and i get the same error message.  Any suggestions?

---

### Post by nami on 2006-07-16
Useless -  You are better off using vmware server.  But if you still want "player", simply follow the instructions I posted before your post! :)

---

### Post by Useless on 2006-07-16
ha, the funny thing is, i have allready installed vmware server on another ubuntu machine here at home.  That is where i created the VM i want be able to use back and forth between the machine, but i wanted to install player on this machine because its a smaller app and it wont need as much.  Im gonna try and rip it all out again and install one more time.  If it works, i will let everyone know.  Otherwise, i will install server.  Wish me luck!

---

