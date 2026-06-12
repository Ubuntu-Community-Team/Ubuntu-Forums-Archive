---
title: "Trendnet wireless problem"
date: 2007-04-04
forum: General Help
---

### Post by k5cqb on 2007-04-04
I have followed the instructions to install the trendnet wireless driver with ndiswrapper locate here;
[https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29)

When I list the installed driver using "ndiswrapper -l" command I the reply;

byford@Byfords-Crib:~$ ndiswrapper -l
Installed drivers:
inffile invalid driver!
mrv8000c                driver installed, hardware present 
byford@Byfords-Crib:~$ 


The wireless card shows up in the device manager but not in system-admin-networking.

Attached is the screen shot of the device manager;

Have I missed something?  Any suggestions are appreciated,
Thanks
Jim

---

### Post by RaZer0r on 2007-04-04
you got the wrong inf file to install your wireless card into ndiswrapper, look for other drivers and uninstall the other!
```

ndiswrapper -r "driver"

```
you can get "driver" by using "ndiswrapper -l" to list the current driver installed

---

### Post by k5cqb on 2007-04-04
Thanks RaZer0r,
I managed to get rid of the "inffile invalid driver" warning.  I'm not exactly sure how I did it, I think I did it by typing in "sudo ndiswrapper -e inffile" and then reinstalled the mrv8000c driver.  Now0 when I list the driver this is my reply;

byford@Byfords-Crib:~$ ndiswrapper -l
Installed drivers:
mrv8000c driver installed, hardware present
byford@Byfords-Crib:~$ 

The invalid warning is gone and it shows the mrv8000c driver there but does not give me a device id for the wireless card.  I am assuming this is the correct driver as I downloaded it from trendnet.  I run the iwconfig and it does not acknowledge any wireless devices.  Is there a different driver I should be using?

---

### Post by RaZer0r on 2007-04-04
do you use network-manager, you might want to try install that too... you can find it using synaptic, of you can google for it, there was an good howto around here, but i'm unable to find it atm, i'll let you know whenever i find it

---

### Post by k5cqb on 2007-04-05
I tried to load network manager from add/remove but got an error saying that it could not be installed on my computer type (i386).  I tried the "sudo aptitude install network-manager" and got this reply;

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be automatically installed:
  dhcdbd libnl1-pre6 libnm-util0 network-manager-gnome 
The following NEW packages will be installed:
  dhcdbd libnl1-pre6 libnm-util0 network-manager network-manager-gnome 
0 packages upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 726kB of archives. After unpacking 2863kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main dhcdbd 1.14-2ubuntu2
  Temporary failure resolving 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main libnl1-pre6 1.0~pre5+svn21-2ubuntu2
  Temporary failure resolving 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main libnm-util0 0.6.3-2ubuntu6
  Temporary failure resolving 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main network-manager 0.6.3-2ubuntu6
  Temporary failure resolving 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main network-manager-gnome 0.6.3-2ubuntu6
  Temporary failure resolving 'archive.ubuntu.com'
byford@Byfords-Crib:~$ 


I went into the software sources and deselected the mirrors option and it started the download for network manager but then I got an error box with this reply;
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/d/dhcdbd/dhcdbd_1.14-2ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/d/dhcdbd/dhcdbd_1.14-2ubuntu2_i386.deb)
  Temporary failure resolving 'archive.ubuntu.com'


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/libn/libnl/libnl1-pre6_1.0~pre5+svn21-2ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libn/libnl/libnl1-pre6_1.0~pre5+svn21-2ubuntu2_i386.deb)
  Temporary failure resolving 'archive.ubuntu.com'


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager/libnm-util0_0.6.3-2ubuntu6_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager/libnm-util0_0.6.3-2ubuntu6_i386.deb)
  Temporary failure resolving 'archive.ubuntu.com'


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager_0.6.3-2ubuntu6_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager_0.6.3-2ubuntu6_i386.deb)
  Temporary failure resolving 'archive.ubuntu.com'


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager-gnome_0.6.3-2ubuntu6_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager-gnome_0.6.3-2ubuntu6_i386.deb)
  Temporary failure resolving 'archive.ubuntu.com'

Now it also says my repository is out of date.

I have a feeling that that could be corrected by accessing the internet but it wont recognize my card, ha.  Kind of a catch 22 deal.

---

### Post by spankymasterc on 2007-04-05
U can install network-manager in synaptic or in add/remove programs try those dont do terminal.... :D

---

### Post by k5cqb on 2007-04-05
_synaptic_ does not find network manager
_add/remove_ originally said it could not be installed on my computer type (i386).  I found another post that suggested I uncheck the mirror option in software sources.  I did that and now although it tries to install, I get the above message reference fail to fetch.

---

### Post by spankymasterc on 2007-04-05
have u tried the deb?

---

### Post by k5cqb on 2007-04-05
No but I will be trying it later this afternoon, thanks.

---

### Post by k5cqb on 2007-04-05
Well, I am trying to install the file you posted.  I tried add/remove and it gives me the error;

Failed to check for installed and available applications

This is a major failure of your software management system. Check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information: 'sudo apt-get update'.

So then I try synaptic manager and I get seom more errors about unable to list programs and that I need an internet connection to update.  I unzipped the debian network manager to the home folder and searched for it via synaptic manager but nothing shows up.

Thanks for taking so much time to help but would Feisty Fawn be easier?  2-3 hrs a night working on the same problem for the past week is wearing me out](*,)

---

### Post by k5cqb on 2007-04-06
I want to thank y'all for your help and patience.  I swithced to Feisty Fawn last night so I guess this thread is no longer valid.  I still have some of the same problems but I have been able to gather some more info.  I am going to start a new thread since I am using a new version.

Thanks again,
Jim

---

