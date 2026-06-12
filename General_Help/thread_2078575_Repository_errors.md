---
title: "Repository errors"
date: 2012-10-31
forum: General Help
---

### Post by cstoh on 2012-10-31
Hello there. I seem to have incorrect repository settings because whenever I click on the Sofware Updater I get these error messages :-
it spends some time searching then get this error message

Failed to download repository information
check your internet connection

I have very good internet connection. About 28 Mbps. I've set the Main Server as my server in Software Sources.
In the details box I get this

, W:Failed to fetch bzip2:/var/lib/apt/lists/partial/extras.ubuntu.com_ubuntu_dists_quantal_main_source _Sources Hash Sum mismatch
, W:Failed to fetch bzip2:/var/lib/apt/lists/partial/extras.ubuntu.com_ubuntu_dists_quantal_main_binary-i386_Packages Hash Sum mismatch
, W:Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_quantal_main_sourc e_Sources Hash Sum mismatch
, W:Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_quantal_universe_s ource_Sources Hash Sum mismatch
, W:Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_quantal_multiverse _source_Sources Hash Sum mismatch
, W:Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_quantal_universe_b inary-amd64_Packages Hash Sum mismatch
, W:Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_quantal_multiverse _binary-amd64_Packages Hash Sum mismatch
, W:Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_quantal_main_binar y-i386_Packages Hash Sum mismatch
, W:Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_quantal_universe_b inary-i386_Packages Hash Sum mismatch
, W:Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_quantal_multiverse _binary-i386_Packages Hash Sum mismatch
, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by Abhinav Kumar on 2012-10-31
You could try this in a terminal
```
sudo lshw -C network
``` and see if it lists your network resources.
Otherwise you may need to check your network resources:)

---

### Post by cstoh on 2012-10-31
> **Abhinav Kumar said:**
> You could try this in a terminal
```
sudo lshw -C network
``` and see if it lists your network resources.
Otherwise you may need to check your network resources:)

I tried what you suggested and this is the response :-

  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:25:64:da:44:5c
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.100 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:ce00(size=256) memory:fdeff000-fdefffff memory:fdee0000-fdeeffff memory:fde00000-fde1ffff



Is this OK?

---

### Post by Abhinav Kumar on 2012-10-31
are you able to browse the web ?
do you use any proxy ?

---

### Post by kanikilu on 2012-10-31
If you don't use a proxy, from what I've read, that "hash sum mismatch" error may be caused when a repo itself is getting updated. You may just want to wait a while and try again later, or maybe try a different mirror.

[http://forums.debian.net/viewtopic.php?f=10&t=63281](http://forums.debian.net/viewtopic.php?f=10&t=63281)

Failing that, maybe it can be solved with the SOP used on other repository errors?? ```
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update
```

---

### Post by cstoh on 2012-11-01
> **Abhinav Kumar said:**
> are you able to browse the web ?
do you use any proxy ?

Yes Abinav,I am able to browse the web. No I do not use proxy. Thanks for your concern

---

### Post by HiImTye on 2012-11-01
try switching your download server in the 'Ubuntu Software' tab of 'Software Sources' listed in the pulldown after 'Download From:'

---

### Post by cstoh on 2012-11-01
> **kanikilu said:**
> If you don't use a proxy, from what I've read, that "hash sum mismatch" error may be caused when a repo itself is getting updated. You may just want to wait a while and try again later, or maybe try a different mirror.

[http://forums.debian.net/viewtopic.php?f=10&t=63281](http://forums.debian.net/viewtopic.php?f=10&t=63281)

Failing that, maybe it can be solved with the SOP used on other repository errors?? ```
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update
```

I followed your advise and carried the above commands. The list of errors seem to have reduced. The only errors now are :-

Ign [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) quantal-proposed/universe Translation-en_SG
Fetched 27.4 MB in 13s (2,033 kB/s)                                            
W: Failed to fetch bzip2:/var/lib/apt/lists/partial/extras.ubuntu.com_ubuntu_dists_quantal_main_source_Sources  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/extras.ubuntu.com_ubuntu_dists_quantal_main_binary-i386_Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.

Following HilmTye's suggestion, I switched my download server in Software Sources to [http://ubuntu.oss.eznetsols.org/ubuntu](http://ubuntu.oss.eznetsols.org/ubuntu) from Main Server. I had used the function in the software sources to determine the best server in my location.

---

### Post by cstoh on 2012-11-02
> **cstoh said:**
> I followed your advise and carried the above commands. The list of errors seem to have reduced. The only errors now are :-

Ign [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) quantal-proposed/universe Translation-en_SG
Fetched 27.4 MB in 13s (2,033 kB/s)                                            
W: Failed to fetch bzip2:/var/lib/apt/lists/partial/extras.ubuntu.com_ubuntu_dists_quantal_main_source_Sources  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/extras.ubuntu.com_ubuntu_dists_quantal_main_binary-i386_Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.

Following HilmTye's suggestion, I switched my download server in Software Sources to [http://ubuntu.oss.eznetsols.org/ubuntu](http://ubuntu.oss.eznetsols.org/ubuntu) from Main Server. I had used the function in the software sources to determine the best server in my location.

Hello dear experts, can anyone help me? This thread has been dormant for a couple of days. How do I resolve this two last error messages? Thanks in advance.

---

### Post by Skylinr on 2012-11-04
I encountered this problem as well. I managed to solve it by inserting the disk which I installed Ubuntu from. Hope it helps for you too.

Edit: This enabled me to install some programs from Ubuntu Software Sources. Alternatively, you can remove the cdrom option under "Other Sources" in "Software Sources".

---

### Post by cstoh on 2012-11-09
> **Skylinr said:**
> I encountered this problem as well. I managed to solve it by inserting the disk which I installed Ubuntu from. Hope it helps for you too.

Edit: This enabled me to install some programs from Ubuntu Software Sources. Alternatively, you can remove the cdrom option under "Other Sources" in "Software Sources".

Thanks SkyLinr, when I had the CD option software sources, it got more error. Now I have removed thr CD option and I'm left with the messages in my earlier post.

---

### Post by Old_Grey_Wolf on 2012-11-09
Enter this command to remove any partial update lists from your previous failed updates/upgrades.
```
sudo rm -rf /var/lib/apt/lists/*

```
Enter the command ```
sudo apt-get update
```and post the complete output.

Enter the command ```
sudo apt-get upgrade
```and post the complete output.

I need to find out what GPG Key you need. The output of the commands will identify them. It could be something else; however, the output of the commands should identify the problem.

---

