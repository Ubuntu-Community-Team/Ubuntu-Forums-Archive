---
title: "I don't know what Virtural Machine to use."
date: 2006-12-06
forum: General Help
---

### Post by Phototrek1 on 2006-12-06
Hello,
I'm unsure what VM application i should use.  I'm use to MS Virtural PC 2004.  However,  I got rid of my primary computer and I'm now using Ubuntu 6.06 as my primary os.  I need a VM application that is as near as easy and functional as VPC.

I bassically need the VPC in Ubuntu 6.06. 
 
I've tried VMplayer and it errors out.

I've downladed bochs.  (Confuseing compared to the Windows version and i can't get it to work.)

I want to try XEN however the install/configure process is to scary. I really can't afford to messup Ubuntu again. 

I'm still learning Linux and I need the VM application so that I can use it as a testing bed.  I've messed up Ubuntu 4 times in 2months. So I've stopped configing and adding software except for the add/remove application.

So any pointers would help. Thanks

---

### Post by 23meg on 2006-12-06
Try QEMU. Do a forum search and you'll find a comprehensive guide for setting it up along with its accelerator module.

---

### Post by Hendrixski on 2006-12-06
I use Virtual PC at work, and it is really bad.  A client of ours uses VMware Server and it blew me away, it really integrates deeply so that at times you don't know when you're on the guest OS or when you're in the host.  A friend of mine uses Parallel on his Mac, and it looks like it gets the job done, though I didn't see any advanced features yet, so I shouldn't comment.

I'm really eager to try out Xen, I'll post everywhere about it when I finally do.

---

### Post by technodigifreak on 2006-12-06
> **Hendrixski said:**
> I use Virtual PC at work, and it is really bad.  A client of ours uses VMware Server and it blew me away, it really integrates deeply so that at times you don't know when you're on the guest OS or when you're in the host.  A friend of mine uses Parallel on his Mac, and it looks like it gets the job done, though I didn't see any advanced features yet, so I shouldn't comment.

I'm really eager to try out Xen, I'll post everywhere about it when I finally do.

VMWare Server rocks. Avoid VMWare player like the plague.  There is no end to uses for the Server version.

---

### Post by Macchi on 2006-12-06
I run VMware Server on Edgy and on Dapper and it works fine. But you should observe some details to avoid problems:

First: install some necessary packages (sudo apt-get update && sudo apt-get install build-essential linux-headers-`uname -r` netkit-inetd

Second: Download the latest VMware Server for Linux from [www.vmware.com](www.vmware.com), get the tar.gz package and untar it with tar xzvf and cd into it and run sudo ./vmware-install.pl

Third: If you have an international keyboard you might experience problems with the keyboard on the guest machine. In that case insert the line:
 xkeymap.usekeycodeMapIfXFree86 = true
in the file /etc/vmware/config

Fourth: Create your virtual machines and install the OS. I had problems with guest install of a Ubuntu 6.10 server running on a pentium mobile (Ubuntu) host. The solution was to use the alternate install.
Observe also file permissions and avoid any symbolic links while making clones and backups copies of virtual machines.

Fifth: The following adjustments might be necessary when you make copies and clones of virtual machines: First change the host name to another unique identifier on /etc/hosts,  then change /etc/hostname and reboot the virtual machine. If you have problems with networking after moving a machine then comment out the MAC address on /etc/iftab and reboot the virual machine. Later you might update and upgrade the guest machine and at last install VMware tools.     

The remote connection to virtual machines is cool, although I would like to try a connection over ssh. I have not yet tried Xen and had problems with the VMware player.
Hope it works fine for you. 
Enjoy virtualization!

---

### Post by Phototrek1 on 2006-12-06
Thanks,
 I see there is an overwhelming support for VMware Workstation.  Gee.. I guess i'll try it. :)  I did try QEMU and it works WAY! better than i expected.  I had Windows 98 installed and working great on my 800mhz 192mb computer. Qemu works faster then VPC on a 2ghz (Win XP) computer.  I guess it must be all the bloat ware.

Thanks for the help and i'm going to try VMware Workstation

---

### Post by salbrecht on 2006-12-06
I have a question in the area of Windows Virtualization also. I hope this is an appropriate thread to post this.

Hardware:
Dell Inspiron XPS Laptop
3+ghz HT cpu
2 gb ram
ATI Video, 256 mb ram. Screen is 1920x1200 pixels and 32 bit depth.

I have installed Microsoft Virtual PC 2004
I downloaded ubuntu-6.10-desktop-i386.iso

I start VPC, set up a machine with 512 mb ram.
I then drag the ISO file to the CD icon and Ubuntu loads and starts up.

The problem is that Ubuntu starts up in a screen resolution that renders the VPC display unreadable. I am unable to read any of the text so I can change the screen resolution set-up. Booting Ubuntu into the second menu choice (safe screen mode) results in the same scrambled display.

So it seems that Ubuntu loads and runs just fine, I just can't read the display.

Any thoughts on how I can set up the display before I boot Ubuntu?

Thanks folks

---

### Post by Techno.Scavenger on 2006-12-07
If I remember it correctly, VPC 2004 does not support linux out-of-the-box. You can try Virtual Server 2005 which I am sure supports few linux distribution (Red Hat I am sure is supported in Virtual Server) and it is free as well. I have an advice though. If you want to play with linux I highly recommend VMware as it is more linux friendly.

---

### Post by David Corrales on 2006-12-07
The problem with Vmware server is that you get a slow GUI when using its client.
I'm currently using Parallels and it's ok for regular use. They really need to add linux tools though =/

---

### Post by Phototrek1 on 2006-12-07
Try installing with the safe graphic install.  If i remember correctly VPC doesn't support 24bit graphics.  Start with 16bit and if the live cd works then install. Worth a shot and give it lots of memory. Plus use 1024x768  and below.  If you go above that i started haveing problems. Try starting with 800x600 if you can.

---

### Post by Hendrixski on 2006-12-07
> **salbrecht said:**
> 

I have installed Microsoft Virtual PC 2004
I downloaded ubuntu-6.10-desktop-i386.iso

I start VPC, set up a machine with 512 mb ram.
I then drag the ISO file to the CD icon and Ubuntu loads and starts up.

The problem is that Ubuntu starts up in a screen resolution that renders the VPC display unreadable. I am unable to read any of the text so I can change the screen resolution set-up. Booting Ubuntu into the second menu choice (safe screen mode) results in the same scrambled display.

So it seems that Ubuntu loads and runs just fine, I just can't read the display.

Any thoughts on how I can set up the display before I boot Ubuntu?

Thanks folks

Apparently that's normal.  i went through that same problem yesterday as well, the graphics looked like a black screen with some fuzzy lines, that remotely resembled the gnome desktop if I squinted at it.

Fortunately I memorized the install sequence so I just winged it an installed it, then when I started up the virtual PC I set the GRUB bootloader to start ubuntu in safe mode, or command line mode basicly.  Then I edited the /etc/X11/xorg.conf file so that the default bit depth was 16, not 24 (which Virtual PC can't handle).  Then I typed in startX and it works perfectly.

Then I Downloaded VMware Server, for free, off of their website and installed Ubuntu on that.  It's so much easier, faster, better, etc.  I don't think I'm ever going to user virtual PC again.

I still need to try Xen. :)

---

### Post by Phototrek1 on 2006-12-07
.

---

### Post by Phototrek1 on 2006-12-08
.

---

### Post by Phototrek1 on 2006-12-09
Hello, I have downloaded everything needed for vmware server.  The problem is that when i try to insall it Vmware says there is another version.  I had Vmplayer installed.  But have since removed it.  

Here is the Guide (pdf) i'm following (I get stuck at top of page 3)
I have also adaped it. Instead of logining at vmadmin i log in as grant.
[http://www.tudra.net/wp/wp-content/uploads/2006/07/VMWare%20Server%20on%20Ubuntu%20Dapper%20Drake.pdf](http://www.tudra.net/wp/wp-content/uploads/2006/07/VMWare%20Server%20on%20Ubuntu%20Dapper%20Drake.pdf)

Here is where i get stuck! ](*,) 

> grant@grant-desktop:~$ sudo mkdir /home/vmware_machines
grant@grant-desktop:~$ sudo chown grant:grant /home/vmware_machines
grant@grant-desktop:~$ sudo tar -xzf VMware-server-1.0.0-28343.tar.gz -C /home/grant
grant@grant-desktop:~$ sudo tar -xzf VMware-mui-1.0.1-29996.tar.gz -C /home/grant
grant@grant-desktop:~$ cd /home/grant/vmware-server-distrib
grant@grant-desktop:~/vmware-server-distrib$ sudo ./vmware-install.pl
A previous installation of VMware software has been detected.

Failure

Execution aborted.

grant@grant-desktop:~/vmware-server-distrib$



Thanks

---

### Post by Techno.Scavenger on 2006-12-22
To post #11.

If you need faster GUI response try to install NX Server from NoMachine. It is like terminal server/remote desktop server. You have to access your machine remotely though.  This really helps a lot, I swear. :D

---

