---
title: "VMWARE: Feisty Host, XP Guest, NAT DHCP Fails"
date: 2007-07-20
forum: General Help
---

### Post by Zooberdeaux on 2007-07-20
Here's the situation:

(1) Just installed Feisty on my T40 IBM Stinkpad.  Feisty 7.0.4 to be sure.

"Linux my-laptop 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux"

**Love it, love it love it.  Won't trade back to Winbloze for anything now.**

(2) Unfortunately, must run XP for corp requirements.

(3) Thus, installed VMWARE server, and had to do some serious hacks, but got it finally working.

(4) XP as a guest, with a SINGLE NIC, VMWARE tools, and the VMWARE side set to BRIDGE -- works perfectly.   E.G. Laptop is ethernet 802.3 physical networked via CAT5 RJ45, and I get a DHCP address to the laptop itself to Feisty, and VMWARE bridges the XP Guest OS NIC over to the physical network and the Guest OS (XP) gets a DHCP address, and all is well.  Works like a champ.  All day long.  And sundays, too.

(5) Then, all hell breaks loose:

(5a)  I go to the hotel.  No more ETH0.  ETH1 comes up on Feisty as Wireless 802.11.  Feisty gets back on the internet, and is happy once more.

(5b) I go into my Guest OS (XP) and notice, ehr, yeah, I setup a single NIC that was originally bridged thru the ETH0 (802.3 hard wired).  Now, uh, that isn't working.

(5c) I stop the VMWARE services ($home>./usr/bin/vmware stop) etc, etc.  

(5d) I run vmware-config.pl.  Follow the prompts, try to modify NETWORKING to include a SECOND NIC for the configuration (NAT).  E.G., I tell VMWARE that the Feisty ETH1 (which is 802.11) should be added to the VMWARE instance for the XP Guest OS as a NATTED secondary NIC.  

Does all this make sense so far?

(5e) Boot up the Guest XP os.  Hangs for a while.  Finally responds (and the Vmware tools are very slow to load, seem disabled at first).

(5f) Now XP Guest OS has two NICs (yep, this is  planned).    I disabled the ETH0 BRIDGE to NIC 1 (in Windows, right click the first NIC [orig bridged to ETH0] and disable.  Ensure second XP nic (set to NAT to 802.11 on Fiesty) is DHCP configured.  

(5g) Voodoo reboot of Guest.

(5h) Voodoo reboot of Host.

(5i) Restart VMWARE console, log into XP Guest.

(5j) Hangs.  DHCP not serving up ANYTHING to NAT Guest NIC on XP.  Nada.  Get's AIPA (169.254) addy.

What am I doing wrong?

VMWARE networking, to say the least, is VERY confusing.

---

### Post by finite9 on 2007-09-18
not a helpful response, just a "me too" response.  I had this working in dapper drake, but in feisty, i always get a 169.254 address.  cannot ping anything, but do have basic internet access, which does not work for my VPN connection within the WinXP guest to my workplace...I need a real DHCP address from my router in the guest!!

Am having exact same issue in both VirtualBox and KVM.

---

