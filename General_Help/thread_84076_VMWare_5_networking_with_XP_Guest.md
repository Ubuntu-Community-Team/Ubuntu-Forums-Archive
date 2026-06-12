---
title: "VMWare 5 networking with XP Guest"
date: 2005-10-30
forum: General Help
---

### Post by teraphase on 2005-10-30
Hi, Im a newbie to linux and have managed to install and get working VMWare 5 however I seem unable to get the networking working, can someone talk me through it in laymans terms, I think I want bridged networking (ie I want internet, and shares on guest pc). I have followed several guides and have just ended up confused. If someone has a "for dummies guide" would be helpful :P

Thanks in advance.

---

### Post by beefsprocket on 2005-10-30
It's a problem with vmware and the 2.6.12 kernel series. See this thread for solution: [http://ubuntuforums.org/showthread.php?t=77040&highlight=vmware+patch](http://ubuntuforums.org/showthread.php?t=77040&highlight=vmware+patch)

---

### Post by teraphase on 2005-10-30
OK, thanks for that mate. I just tried it but I still can't get networking to work, when i go into My Network places on VMware i see the virtual machine (named xpos) and VMWare shared folders - i cant see anything else, i tried installing samba too, but that doesnt seem to have helped much.

---

### Post by beefsprocket on 2005-10-30
But you can access the internet through your vmware machine right? If this is the case you'll need to figure out the samba thing between computers. As long as you can access the net vmware is working fine and shouldn't need any more attention.

---

### Post by teraphase on 2005-10-30
No, i havent managed to get the internet working on the virtual machine either.

---

### Post by beefsprocket on 2005-10-30
Hmm, you might try rebooting, running vmware-config.pl and rebuilding the modules. Wwhen prompted, create a new networking configuration using bridged mode. You'll then want to modprobe vmmon and vmnet. Try starting vmware with sudo /etc/init.d/vmware start and then run vmware as your normal user.

---

### Post by teraphase on 2005-10-31
all i get now is asking me to constantly reconfigure. I did some messing around and got somewhere, now when i try to config it I get this:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   Bridged networking on /dev/vmnet2                                   done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                   failed

---

### Post by beefsprocket on 2005-11-01
take a look in your /etc/vmware folder. Is there a blank file called "not_configured"? If so, delete it and then try running vmware.

I fought with vmware for a while over this file. Once I figured out that the patch was needed, I uninstalled the entire thing (originally I used checkinstall to create my own .debs). I then installed, patched, and then ran vmware-config.pl. The not_installed file is the thing that will always tell you that vmware is not configured properly and prompt you to rerun the config program.

---

### Post by teraphase on 2005-11-01
Yeah, I got it working about 10 minutes ago. I ended up removing, reinstalling and using NAT networking which seemed to let me do what I wanted to. Thanks for your help :)

---

### Post by beefsprocket on 2005-11-01
Good to hear. I suppose choice in networking could well determine your guest OS's vulnerability to malware and such. I might look into the various networking options now, so thanks for pointing out your solution ;)

---

### Post by thnogueira on 2005-11-04
I'm having problems to access the Internet via VMware. I followed the guides and it seems the /dev/vmnet interfaces are ok (at least i don't get any error during boot time). But there is no way I can connect, neither bridgeding nor NATing. No DHCP addres and if I configure the NAT manually I can't even ping the gateway. My configuration is:

vmnet0 -> bridged to eth0 (outside device)
vmnet2 -> configured to NAT at 192.168.1.0/255.255.255.0

I can't figure out what is wrong :confused:

---

### Post by andbert on 2005-11-04
Same problem here.
Input someone.

EDIT: I ran the config-thing again, and suddenly my eth0 is working good. Dont know why :)

---

### Post by thnogueira on 2005-11-04
Hi andbert,

did you run directly the vmware-config.pl program or you ran the vmware-any-any-update?

---

### Post by andbert on 2005-11-04
I tried both but Im quite sure it was vmware-config.pl who did the trick.
It looke like the gateway adress somehow was wrong on the first attempt...

Good luck

---

### Post by beefsprocket on 2005-11-04
[quote=thnogueira]did you run directly the vmware-config.pl program or you ran the vmware-any-any-update?[/quote]

You should run the update first and then vmware-config.pl. You should also check to make sure that the modules vmmon and vmnet are loaded *after* you do the above.

---

### Post by jobi21 on 2005-11-05
[QUOTE=teraphase]Yeah, I got it working about 10 minutes ago. I ended up removing, reinstalling and using NAT networking which seemed to let me do what I wanted to. Thanks for your help :)[/QUOTE]

Just out of curiosity, were you trying to use bridged networking via a wireless adapter? Bridged networking via wireless doesn't work on Linux.

---

### Post by teraphase on 2005-11-05
no, I was using a normal 10/100 LAN adapter connected to my broadband modem.

---

### Post by thnogueira on 2005-11-07
This issue is driving me crazy. It worked, but not anymore.
I could make each network adapter brigde to my real adapter in this way

vmnet0 -> bridged to eth0 (outside adapter)
vmnet2 -> bridged to eth1 (inside adapter).

Both vmnets were dynamicaly getting the ip configuration.

After a reboot in the virtual machine, I cant get vmnet2 to work anymore. Vmnet0 still working ok.
Any tip?

---

### Post by thnogueira on 2005-11-07
I'm fully networking again:rolleyes: 

My vmnet are both configured to bridged:
```

vmnet0 is bridged to eth0
vmnet2 is bridged to eth1

```

At Virtual Machine config file the second interface is configured as custom, and not as bridged:

```

ethernet1.present = "TRUE"
ethernet1.addressType = "generated"
ethernet1.generatedAddress = "00:0c:29:2f:9f:ab"
ethernet1.generatedAddressOffset = "10"
ethernet1.connectionType = "custom"
ethernet1.vnet = "/dev/vmnet2"

```

I beleive the most important change was adding in /etc/vmware/config:

```

vmnet2.Bridged = "YES"
vmnet2.BridgeInterface = "eth1"
vmnet2.HostOnlyAddress = "192.168.1.1"
vmnet2.HostOnlyNetMask = "255.255.255.0"

```

And voila!

---

### Post by lorenco on 2005-11-07
EDIT * Hmmmmmmmm - Just got to the end-* Comment not valid... ;)

---

