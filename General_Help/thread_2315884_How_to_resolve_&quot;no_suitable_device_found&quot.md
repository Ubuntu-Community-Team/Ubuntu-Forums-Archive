---
title: "How to resolve &quot;no suitable device found&quot; for eth0 in libpcap?"
date: 2016-03-03
forum: General Help
---

### Post by artss2 on 2016-03-03
[COLOR=#000000]I need probably use root privileges in my libpcap console application, despite [/COLOR][COLOR=#000000]setting seteuid(0) returns the same error. Such error is invoked when using simple code with dev handler initialization by [/COLOR][COLOR=#000000]pcap_lookupdev(errbuf), and trying
[/COLOR][COLOR=#000000]to show dev in printf,that redirects to errbuf with "[/COLOR]not suitable device found". The same I get when [COLOR=#000000]pcap_create("eth3", errbuf), despite [/COLOR][COLOR=#000000] ifconfig shows eth0 ( &#1077;th3 here) and lo.[/COLOR][COLOR=#000000]
Maybe there is some other way f.e. with using sudo for whole file system? When taking into account - [/COLOR][http://ubuntuforums.org/archive/inde...t-1526065.html]("http://ubuntuforums.org/archive/index.php/t-1526065.html")[COLOR=#000000] maybe the last option with capabilities was not used.
What can be suggested to resolve this issue?[/COLOR]

When checking before and after seteuid(0); when using  printf(%s, geteuid()) I got 1000, but no 0, that should be root. So it  works not correctly or why?
When seteuid("root"); printf(%s, geteuid()); I got segmentation faults -- maybe there is another way to set super-user to unblock packet sniffing?
And I also tried such code in Terminal:
chown root:root /usr/bin/sudo
chmod 4755 /usr/bin/sudo
and it even in terminal requests that I need to setuid root??
So  I even do not know how to recover even root in Terminal

I recovered sudo in Terminal, but am interested do somethink like: 777 chmod that destroy sudo could be also recovered, or I just need to reinstall system again for it? If I destroy sudo by this way, could be packet sniffing to be allowed without root priveleges in libcap.
And I do not understand -- are there no means to packet sniffing - just to reveal interfaces in libpcap in ubuntu-like system?
I do not believe that I cannot do it? Maybe the Lubuntu (that is also non-pae as Xubuntu 12.04) do not invoke such error about suitable interface, or I need obligatory use ubuntu (that I cannot use as it is pae feautured)?

I have very strange feeling, that nobody in the profile forum have the expertize why lipcap C++ do not reveal existent (in ifconfig and tcpdump). I have already tried -- chmod 777 -R /usr/  and   chmod 777 -R /etc/network/interfaces -- nothing help. Meanwhile /etc/network/interface do not have eth* interface. But adding such line to it also do not change anything.
I am very confused. Should the issue in virtual machine? Anyway setuid (getuid) handle the 1000, but not 0 so probably root is not invoked -- so brobably it is the main task. How setuid(0) to be 0, but no 1000.

---

### Post by bapoumba on 2016-03-05
I do not have the expertise you require, but I do know it is a very bad idea to play with permissions in the root file system. It rarely can be recovered.

---

### Post by artss2 on 2016-03-05
[http://stackoverflow.com/questions/16682297/getting-message-sudo-must-be-setuid-root-but-sudo-is-already-owned-by-root](http://stackoverflow.com/questions/16682297/getting-message-sudo-must-be-setuid-root-but-sudo-is-already-owned-by-root) -- here is the way to recover despite I am did not checked  could it be worked with 777. Anyway what I lost? I cannot compile libpcap so I can substitute the same virtual image just with Codeblocks, no more? So maybe lubuntu could not have such bug or so?

I have applied chmod to all system. Despite a lot of files show - permission not allowed or so it came really to see the device in libpcap app in C. But after reloading xubuntu 12.04 virtual image there is warning about bad connection setting and no suitable device found appear again. But it seems for one session such approach is viable. So I am interested  what file when destroying its root privileges allowed to bypass no suitable device error? It is not interfaces file in network folder, no r /usr/ folder as I have applied 777 to this ones yesterday?

Despite it is uncomfortable, it shows just usbmon, but not eth0 (that I need) and lo that is shown in ifconfigure command. Meanwhile tcpdump -D additionally shows "any" interface except three previous ones. So I do understand -- is possible to reveal at least nessesary eth0 by libpcap? Despite maybe it is the result of virtual machine or applying 777 to the whole system...

---

### Post by HermanAB on 2016-03-07
Well, if you applied 777 to the whole system, then you will have to re-install.  Sorry.

---

### Post by artss2 on 2016-03-07
Why to reinstall. Untill I turn off I can use code block in such mode. After switching off everything of network is broken so I need just to put another ready virtual image of xubuntu. But main question is up: why i cannot snif on xubuntu, and why geteuid() shows 1000, but no 0?

It is very strange situation. When I use ubuntu 10.04 in virtual box i got the same situation. So Is it not real to sniff packet in virtual machine or I need install directly the ubuntu on machine? As when in ubuntu 10.04, (ready vbox image) I got "no interface found", and when applying chmod 777 -R / i got just usbmon1 device but no eth0, lo? The same as in ubuntu 10.04

sorry, the same as in xubuntu 12.04

I do not know but it is something inconciavable!! I run not ready vbox image, but run demo of ubuntu 10.4 in vbox and then installed fully it on vbox, but got again -- no "suitable device found", and after chmod 777 -- just usbmon?? Do vbox block libpcap?? Despite tcpdump works and ifconfig, should I install directly on disk ubuntu??

It all the same on ubuntu 10.04 vbox image, and on live cd ubuntu 10.04 itself.  So when there is usbmon1, eth0, lo devices accordingly to tcpdump -- libpcap found no one. When I cancel all root privilleges- chmod 777 - R / --libpcap found just usbmon1. But not eth0 that I need. I searched ubuntu filesystem and found such items: sys/class/net/eth0 , sys/devices/pri000 ... net .. , proc/4996/net/dev_snmp6/eth0 (a lot of proc). I applied chmod 777 just for this one. But in vain. Interestingly that interfaces list etc/network/interfaces  has just "lo" device but not eth0. What is the reason of it, old builds?

---

### Post by artss2 on 2016-03-22
Here is screen of error "no suitable device" even in Ubuntu Server, but tcpdymp and ifconfig work meantime

---

### Post by artss2 on 2016-03-25
It is really awfull and absurd situation. When It is late for me it worked. But on fedora 10 (the first one fedora i tried). Why it is so? Why no version of ubuntu server or desktop do not pass these existing devices. As I was instructed to use ubuntu for  libpcap???

---

