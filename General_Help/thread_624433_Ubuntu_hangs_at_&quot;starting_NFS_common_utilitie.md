---
title: "Ubuntu hangs at &quot;starting NFS common utilities&quot;"
date: 2007-11-26
forum: General Help
---

### Post by countryclub on 2007-11-26
I get the following error when trying to load/boot:

"starting NFS common utilities"

Just hangs and never completes boot.

Any suggestions would be appreciated.

Thanks

---

### Post by Bigbro69 on 2007-12-21
*Bump*

I'm having the same issue. Not sure if the OP resolved his/hers or not.

---

### Post by fragos on 2007-12-21
I had NFS working nicely between Dell 7.04 and my 7.10 desktop.  I upgraded my Dell 1420n with Dell's recently released 7.10.  I don't seem to get the mount to connect any more from my Desktop to the 1420 bas the server.  The error message says it's a permision issue.  I'm still able to run remote desktop between the boxes.

---

### Post by khanh_coltech on 2007-12-21
i have a same error. :(
If u want to start ubuntu, u must boot in recovery boot.
After start "NFS conmon utilities" tune control-D.

---

### Post by Scruffy13 on 2008-01-03
I also have this problem, but it's only when I try to boot the real-time kernel. With the generic kernel it works fine. Any help on this matter would be greatly appreciated.

---

### Post by DutchKillerBee on 2008-01-04
+1

In my case it's it hangs after "starting NFS common utilities". So I think the process what's started after the NFS utilities is causing the problem. 
How can I find out what's causing this (the process)?

Thanks in advance.

Martijn

---

### Post by gurkZor on 2008-01-12
I also have the same problem, anyone who knows why?

The problem started after I inserted a new Wireless Network card; but that can't be the reason, can it?

---

### Post by fragos on 2008-01-12
By default NFS ver 3 is used but you can call out ver 4 as "nfs4".  4 is supposed to work better over the Internet but it still has bugs.  If you used "nfs4" you might change the option to "nfs".

---

### Post by dimis2410 on 2008-01-27
I had the same problem when i tried to set up a static IP... and this  worked for me :


> 
sudo gedit /etc/network/interfaces


and make the file look like this: 


> auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.1.100 
netmask 255.255.255.0
gateway 192.168.1.1

auto eth0

"192.168.1.100 " my static ip
"255.255.255.0" my subnet mask
"192.168.1.1" my routers/gateway ip
"eth0" my current ethernet interface

Change the addresses to yours...
and then restart networking...
> 
sudo /etc/init.d/networking restart


Now i'm sure that it will not hang on "Starting NFS common utils..."

:)

---

### Post by sh4d0w on 2008-02-02
i have the same broblem nfs stops for ever and i cant loging only with fresh install same again . any option from command line?

---

### Post by ondre on 2008-02-23
> **dimis2410 said:**
> I had the same problem when i tried to set up a static IP... and this  worked for me :





and make the file look like this: 




"192.168.1.100 " my static ip
"255.255.255.0" my subnet mask
"192.168.1.1" my routers/gateway ip
"eth0" my current ethernet interface

Change the addresses to yours...
and then restart networking...



Now i'm sure that it will not hang on "Starting NFS common utils..."

:)

Absolutely correct! Thanks for the help!

---

### Post by Deathmoon on 2008-03-17
I second this...this resolved the issue for me!  Thanks.

> **dimis2410 said:**
> I had the same problem when i tried to set up a static IP... and this  worked for me :





and make the file look like this: 




"192.168.1.100 " my static ip
"255.255.255.0" my subnet mask
"192.168.1.1" my routers/gateway ip
"eth0" my current ethernet interface

Change the addresses to yours...
and then restart networking...



Now i'm sure that it will not hang on "Starting NFS common utils..."

:)

---

### Post by eslin on 2008-04-22
This should be reported as a bug. 

I also have the problem.

---

### Post by Blaque on 2008-04-25
The above solution didn't work for me. I'm using DHCP. This started after upgrading to 8.04. Actually I don't believe its the NFS common utilities thats causing the problem. It hangs after that says ok. The next statement appears to deal with IPv6. I remember reading about a problem with this before. Does IPv6 compatibility need to be disabled?

---

### Post by fragos on 2008-04-25
I'm not sure of the exact steps you're taking. I've used NFS in Gutsy and now 8.04. Assuming NFS common was sucessfully instaled There are steps you need to take on both communicating machines before a mount can suceed. 1st /etc/exports needs to call out an NFS relationship. I use my desktop as the client and my laptop as the server. The line in /ect/exports on my laptop is "/home/fragos    192.168.1.100(rw)". I have identical user accounts on both machines. That line refers to my desktop. I start it 1st so DCHP always gives it the same address from my router. Before trying to connect to my laptop I run "sudo exportfs -rv" on the laptop so it will respond to a request from my desktop. On my desktop I've created a directory to use for the mount point. The IP assined to my laptop varies some so I need it to issue the mount command. Laptop files are now available in the mount point folder. I use Unison to sync my working files and it's configured to do a local sync between between folders on my desktop -- one being the mount point.

---

### Post by gummih on 2008-04-27
I had this error after upgrading a somewhat troubled 7.10 to 8.04
I realized that my /etc/networks/interfaces file was empty

after adding the lines
auto lo
iface lo inet loopback

then everything worked fine

---

### Post by burasa on 2008-06-10
I had the same problem and solved it by removing ldap in /etc/nsswitch.

My apologies goes to nfs-common for unfairly suspecting it.

To change /etc/nsswitch boot into the recovery mode (use the grub menu) or to runlevel 1. Obviously it will also hang at a certain point. Press ctrl-alt del when it hangs and you should be prompted to type in the root password. Confirm and you are in the system.

NB. if you don't have a root password (most common on ubuntu) I would recommend that you boot using a live cd, chroot to create it, or to simply mount your root (/) and change /<mount point>/etc/nsswitch

Good luck

---

### Post by iimess on 2008-06-11
I have a related problem.

Ever after I upgraded to 8.04, Ubuntu would randomly act weird, including (all at the same time):
- Some keyboard shortcuts would fail to work
- The starting terminal window would disappear by itself (my .bashrc accesses a network share)
- Basic commands (ls, cp) would hang. Even with absolute path.
- Entering a user name in, say, Ctrl + Alt + F1 would hang
- ssh from another machine would not return a password prompt
- Ctrl + Alt + Backspace would not restart X (something's killed but I don't see the login screen; same as logout)
- In Ctrl + Alt + F8, I can press Ctrl + Alt + Del and it hangs at stopping NFS common utilities.

It's the last problem instance that I think it's related.
At this point I'll have to hard reset the machine.



I use a static IP and my /etc/network/interfaces already includes:
auto lo
iface lo inet loopback
auto eth0
(etc etc...)

---

