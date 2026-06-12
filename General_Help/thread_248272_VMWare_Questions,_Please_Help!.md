---
title: "VMWare Questions, Please Help!"
date: 2006-08-31
forum: General Help
---

### Post by noob_Lance on 2006-08-31
Hey

As you can tell i need help with VMware server. 

I was wondering if there is any way to access my partition that hold all my media and other misc. files thru VMWare. I Just got it installed and have no clue what im doing.

Any help is appreciated :)

~Lance

---

### Post by NetworkGuy on 2006-08-31
If you have VMtools installed on your VMware partition, you can utilite shared folders.  This will allow you to do what you want.

---

### Post by noob_Lance on 2006-08-31
i did install it... but i have no clue what your talkin about lol

---

### Post by exxcomm on 2006-08-31
We need some more info please.

What partition is your media on? A windows partition?

VMware server is a program that creates "virtual computers" that you can install a total working operating system of a different type, but it does not  make other partitions more accessible.

If you don't know what partition or type, use gparted in the system tools area of the menu to see what type. Windows will usually be ntfs.

---

### Post by noob_Lance on 2006-08-31
ok. Well i have One hard drive.. seperated into a few partitions. The partition the media is on is partition #2, also the same parttion that VMware stored the windows OS.  as for type.. its fat32

~Lance

---

### Post by exxcomm on 2006-08-31
K then.

if you are using a raw disk for vmware ubuntu probably has already mounted partition 2 in /media/(h-s)da2

If you are using a vmware virtual disk you have to boot the guest OS and share the folder in Windows and then (if you have bridged or host only networking) you can connect to it as a regular samba share.

---

### Post by noob_Lance on 2006-08-31
its a virtual disk... can you help walk me thru the samba part. for some reason samba has been a real pain for me so far.

~Lance

---

### Post by exxcomm on 2006-08-31
Boot the guest OS (windows), log in, right click on the folder and choose sharing, set permissions to everyone read at least.

In ubuntu go to places in the menu bar and click on network servers.

You will have to use the same username and password (if this is xp home you will have to password that user in windows if it's not done already) as you do in windows.

as to how to mount the share in ubuntu I don't know.

in Debian you use
mount -t smbfs -o username=NAME,password=PASSWORD //xxx.xxx.xxx.xxx/SHARE NAME /MOUNT POINT 
(ubuntu seems to mount all recognizable partitions in /media so you may have to sudo mkdir /media/DIR)

Sorry, old time debian user. Not to hep on the ubuntu as yet but upgrading to dapper as I type.

---

### Post by noob_Lance on 2006-08-31
ok im lost... i have No clue what im doing

---

### Post by noob_Lance on 2006-09-01
anyone?

---

### Post by galileon on 2006-09-05
heya, i've been begging xen to give me networking for the past month, but i only tried vmware today, so i believe i can help you...

in ubuntu, System>Administration>Shared Folders

Click Add,

set Path by browsing to the place your media is mounted. eg /media/hda2, etc (ie wherever you stored your vmware files for woes xp)

set the Name for the share, set Allow Browsing Folder

Click General Windows Settings, set the workgroup to the woes one, Does not use Wins Server....

now, you need to have the same username and password into the linux box as well as the woes box (okay, maybe not, but thats the way i did it)

then, you need to add your username as a SAMBA user:

Open a console, (Applications>Accesories>Terminal), and type:

sudo smbpasswd -a your_user_name

this will tell samba to add your username as a samba user, and also type the password here

now if you browse to Places>Network Servers>Windows Network>your_workgroup>your_woes_xp_share, it might work... :)

i also disabled Simple File Sharing in windoze, tho i have no idea if its useful either way, but you can try...in windoze, open a folder, then Tools>Folder Options>View Tab, disable Use Simple File Sharing


if you have a firewall, eg zonealarm, when you try to access the share from ubuntu, zonealarm will tell you that an attack has been blocked...you need to copy the ip, and add it as a trusted zone, so zonealarm will let it pass...i dunno how to do that if you use woes_sp2_firewall_thingy...

hope that helps, post if you still have probs...

---

### Post by noob_Lance on 2006-09-06
i found an even easier way around it haha.. i had apache installed in ubuntu for local dev purposes.. so i just made a soft link to my music and images folders and now can access then thru my web browser haha and i also finally got my sound and USB working... but my printer is out fo ink :'( haha

---

### Post by DanielTJ on 2006-09-06
I Converted the .rpm to .deb and then installed the tools. but the vmware still says that no tools are installed. can anyone help me?

---

### Post by noob_Lance on 2006-09-06
open VMware, Power On your machine and under VM in your menu bar, select install VMware tools.

---

### Post by galileon on 2006-09-06
do you mean you dont have any vmware installed? i used the binaries from their website- tho it had to compile the module for my kernel - you'd need to have your source tree around...

[http://www.vmware.com/products/server/](http://www.vmware.com/products/server/)

VMware Server for Linux.
The core application needed to run VMware Server and interact with it on the local machine. TAR Binary. 	Binary (.tar.gz)
(md5sum:9846bff6c3c8af97d4e3ae
[http://download3.vmware.com/software/vmserver/VMware-server-1.0.1-29996.tar.gz](http://download3.vmware.com/software/vmserver/VMware-server-1.0.1-29996.tar.gz)

thats the one i used...

---

### Post by DanielTJ on 2006-09-06
> **noob_Lance said:**
> open VMware, Power On your machine and under VM in your menu bar, select install VMware tools.

ofcourse i did that a couple of times. but everytime a vmwaretools cd is mounted on the ubuntu. 
but as i said, i already installed it on ubuntu.

---

### Post by galileon on 2006-09-06
sorry, i misread your post...

when you click VM> Install Vmware tools, it launches a process in the guest operating system, as if the setup prog was launched from the guest...

i had a prob like this when i installed my woes xp again after i messed up the first...

i  clicked on install tools and it seemed not to do anything....what i did was shut down both systems (the guest, and host) and restarted them, then clicked the install tools again...

---

### Post by DanielTJ on 2006-09-07
Somebody told my to configure the vmware tools. but i dont know how.
he gave me this link, [http://www.vmware.com/support/ws55/doc/ws_newguest_tools_linux.html](http://www.vmware.com/support/ws55/doc/ws_newguest_tools_linux.html)
but i have still the following problems.
first: do you know how i can figure out the version of my kernell? because i get the message that this tool is not made for may kernel. 
second: it wants to compile it for my system. but it asks me where the c compiler is. the default directory is not acceptabel for him.i have installed gdd-4.0 . but i dont know where. can you help me with these?? 
thanks again.

---

### Post by galileon on 2006-09-07
hello, if it couldnt find the cc compiler, it looks to me vmware itself is not properly installed at all...

tell us if you get a similar screen to the one i attached....

also, the link you gave is for vmware workstation...which i have not tried...the free one is vmware server, on the link i gave above...

install instructions:
---------------------
download the file VMware-server-1.0.1-29996.tar.gz

open a terminal, cd into the place you saved it.

then:

1. sudo apt-get install gcc
2. tar -xvzf VMware-server-1.0.1-29996.tar.gz
3. cd vmware-server-distrib
4. sudo ./vmware-install.pl

if you installed gcc as mentioned above, it should find it in the default place, ie /usr/bin/gcc

it will also need to have your kernel headers in the proper place...

to find your kernel, type* uname -r* in a console

it sould give something similar to this:

2.6.15-25-686

which is my kernel in this case

in order to install the source tree, you need to do this:
sudo apt-get install linux-headers-2.6.15-25-686,

or replace the bit about the version by what you saw in uname -r

hope this helps now...post if you have any more probs,

cheers,

galileon.

---

