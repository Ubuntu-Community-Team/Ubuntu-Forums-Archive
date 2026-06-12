---
title: "Howto: Mange LAN using VirtualBox"
date: 2007-06-10
forum: General Help
---

### Post by nqsonk9 on 2007-06-10
Hi guys,

How can we creat a LAN connection (or remote control) between Feisty and a Virual Machine using VirtualBox?
Please guilde me with WinServer2003 and XP SP2

Thks a lot.

---

### Post by harty83 on 2007-06-10
A lan connection is easy.  Open virtualbox, select your VM and then click on network on the right.  Make sure Enable Network Adaptor is checked and select NAT as the "Attached to."  If the Mac address is empty, click on Generate.  Finally check Cable connected if it is not already.  Do that for each VM.

Make sure you have guest additions installed in each VM.  If you do not, then mount the ISO, by clicking on File -> Virtual Disk Manager.  Then click on CD/DVD images.  If vboxguestadditions.iso is already listed, then you are good to go to the next step.  If not then click Add -> Browse to /opt/VirtualBox-1.4.0/additions/ -> double click on vboxguestadditions.iso -> click OK to close the virtual disk manager.  To mount the iso for the vm to use, select the vm then click on CD/DVD-Rom on the right.  Select "ISO Image File" and then select VBoxGuestAdditions.iso.  Boot into each VM, go My Computer, and double click on the CD-rom.  Follow the prompts to install the guest additions.  Networking should then be working.

Alan

PS (I didn't mean "a lan connection is easy" to be a put down.  I just meant it is simple to set up.)  Also, when you say "remote control" do you mean remote display where you can login to the vm from another computer via the network?  If so, you need to enable that by selecting the VM then click on Remote Display on the right.  Select enable then fill in the server port (whatever you want as long as it doesn't conflict with another port) and select a method of authentication.  I would probably select guest to let the guest control the connection which would be the easiest.

---

### Post by madcow72 on 2007-06-13
harty83,

Thanks for the details on enabling LAN networking!  Unfortunately, after doing exactly as you proposed, I still can't see my local network... I did type in my own MAC address, actually, instead of generating one because I have a Windows program that authenticates on MAC address.  Perhaps that is why I can't view the local network?  I'll try changing that to see if there's a difference, but other than that, any suggestions?  pinging LAN IP's gives no response.

Thanks again!

---

### Post by harty83 on 2007-06-13
Do you have internet access in the VMs?  You will not be able to ping other ips on the lan because of the NAT setup.  If you want to do that, you will have to create a bridge between the host and vm which will then make the vm act as if it was just a computer hooked into the network and will be given an IP from the router.  When you use a NAT setup, virtualbox gives the vm its own ip address, subnet, and gateway.  I'm afraid that bridging is beyond what I know so you will have to search for a how to.  Here is one I found just googling:

[http://www.virtualbox.org/wiki/Automatic_Bridge_Ubuntu](http://www.virtualbox.org/wiki/Automatic_Bridge_Ubuntu)

---

### Post by madcow72 on 2007-06-13
Just to report back, nope, using a generated MAC still does nothing toward allowing me LAN access.  Thanks for the information about NAT networking and pinging LAN computers.  I do have internet access and, like you said, an IP generated from the virtualbox.

I'll look at the link you sent and see if I can go the bridged route, but so far, still no access to my LAN!  I'm busy today, so my responses may be intermittent, but thanks for your help harty83!

---

### Post by madcow72 on 2007-06-13
Okay, I noticed this disclaimer at the top of the page you referred me to:
> NOTE: as of kernel 2.6.18 and later (i.e. with Ubuntu 7.04) this stopped working, as now normal users are no longer allowed to dynamically create TAP devices. This is caused by a kernel change. A fix for VirtualBox is planned.
Of course I realized this after attempting a few times.  What I need, is a LAN connection between my virtual box (Windows XP Pro) the network.  The ip addresses given by DHCP are just generic 192.168.3.XXX and I don't care what IP the virtual machine actually has in the end, as long as it can see our fileserver and other networked computers.  
I also found [this page]("http://www.virtualbox.org/discussion/1/126?discussion_action=set-display;display=tree") which could potentially do what I'm looking for, but so far no dice.  More on this as I explore.

---

### Post by onero on 2007-06-13
Hm, I personally haven't tried bridging, but I was planning on doing it soon (don't have the time now :)). Anyway, I was planning on using this guide to set up the network: [http://doc.gwos.org/index.php/VirtualBox#DSL_.2F_Wired_router](http://doc.gwos.org/index.php/VirtualBox#DSL_.2F_Wired_router)

Hope that works for you (as I'm going to be trying it out in a fewdays :p)

---

### Post by madcow72 on 2007-06-13
Woo-Hoo!!  Onero, that was the fix that fixed what needed fixin'!  Followed that guide and everything worked at first boot.  I've got the networks bridged and am able to connect to my server from within my virtual box.

Thanks again, and I hope it works for you when you get to try it.

---

