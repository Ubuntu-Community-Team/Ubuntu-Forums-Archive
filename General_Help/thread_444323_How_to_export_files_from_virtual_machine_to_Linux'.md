---
title: "How to export files from virtual machine to Linux's hardrive?"
date: 2007-05-15
forum: General Help
---

### Post by oliverb4ss on 2007-05-15
I'm running XP on Virtualbox.

I have made a 10GB space for it, but I need to move some files from the .vdi image I have for Windows to my home folder in Linux.

Is there any way to do it?

---

### Post by thelinuxguy on 2007-05-15
> **oliverb4ss said:**
> Is there any way to do it?

I use VMware and not Virtualbox. But you must be having some sort of network on the XP box. 
Share folders under Windows and access it from Linux. Copy the required files.
Or vice versa.

---

### Post by cisforcojo on 2007-05-15
There IS a way but I'm not sure how to do it. I'm looking into the same thing right now. I'll let you know. I know it involves using ssh.

---

### Post by oliverb4ss on 2007-05-15
I'd appreciate it, if you'd keep me posted. :)

---

### Post by cisforcojo on 2007-05-17
From what I understand, you basically set up an LAN between the virtual XP and Ubuntu. Now where I'm stuck is at setting up Remote Desktop in XP. I have a botched CD, it's getting worse and worse. It gives me errors about missing files when I install and I have to skip them and then download the dlls from the internet. I've tried installing Remote Desktop: Insert XP CD -> Perform Additional Tasks -> Remote Desktop but it says my computer is already configured and to go to Start -> All Apps -> Accessories -> Communication -> Remote Desktop... but there is no option. 

THIS is where I am currently stuck.

---

### Post by thelinuxguy on 2007-05-17
> **cisforcojo said:**
> I've tried installing Remote Desktop

Start >> Run >> mstsc
Does the Remote desktop window open?
You don't need Remote Desktop for copying the files. You need to setup a LAN and then share the relevant folders.

oliverb4ss: Do you have a LAN setup between the virtual and real machines?

---

### Post by mdurham on 2007-05-18
I don't think you can access directories/files on the guest from Linux using VBox, but you can access Linux directories/files from the VBox guest, providing they are shared.

---

### Post by cisforcojo on 2007-05-18
No mstsc file. 

Sorry I'm REALLY green about networking. How could I connect to my virtual XP shared folder from linux?
I don't even know how to do this between linux and XP. I always FTP files, which I suppose could be an option. 
How is this normally done though?

---

### Post by mdurham on 2007-05-18
> How could I connect to my virtual XP shared folder from linux?
cisforcojo, as I said in my previos post, you can't go that way, you must go from your XP to Linux.
Select "System->Administration->Shared folders" and select a directory to share, then you will be able to access it from the guest XP You can share more than one directory
Cheers.

---

### Post by thelinuxguy on 2007-05-18
You may have come across [http://www.virtualbox.org/wiki/Sharing_files_on_OSE](http://www.virtualbox.org/wiki/Sharing_files_on_OSE) already. It clears a few things.

It does not mention anything about sharing folders from Windows. mdurham, do you have some more info on this? As to why the sharing of folders from Windows wouldn't work?

---

### Post by mdurham on 2007-05-18
> **thelinuxguy said:**
> You may have come across [http://www.virtualbox.org/wiki/Sharing_files_on_OSE](http://www.virtualbox.org/wiki/Sharing_files_on_OSE) already. It clears a few things.

It does not mention anything about sharing folders from Windows. mdurham, do you have some more info on this? As to why the sharing of folders from Windows wouldn't work?

thelinuxguy, I read this somewhere a few weeks ago after trying to do just that, I'll look for it tomorrow and let you know if I find it. I'm off to bed now, it's late.
Cheers

---

### Post by oliverb4ss on 2007-05-18
Okay, I found a really easy solution for this.

This originates from howtoforge.com forums.

All you have to do is install WinSCP ( [http://winscp.net/](http://winscp.net/) ) on your XP virtual machine.
Then, on Ubuntu, open a terminal and run

sudo apt-get install ssh openssh-server

and

sudo ifconfig

to find out Ubuntu's IP address. That's the IP address you must use in WinSCP to connect to the Ubuntu system.

I tried, it works. :)

---

### Post by cisforcojo on 2007-05-19
Me too. Works perfectly. Thanks buddy!

---

### Post by total wormage on 2007-05-19
if i am not mistaking, i got file sharing either way around to work by just adding my guest win xp (in vmware) to the network that already runs in my house.

i just gave my xp install a ip and bridged the connection... as i don't have a working xp install right now i can't test this anymore.
there should be a wiki page or how to about this, this question has come up a lot.

anyhow, glad it all worked out with winscp ;]

---

### Post by thelinuxguy on 2007-05-26
> **mdurham said:**
> thelinuxguy, I read this somewhere a few weeks ago after trying to do just that, I'll look for it tomorrow and let you know if I find it. I'm off to bed now, it's late.
Cheers

Glad that Winscp and ssh have provided a solution. However, it turns out that you have to set Vbox networking to Bridge mode (as opposed to NAT) and sharing works either way. I followed the steps in the guide here: [http://doc.gwos.org/index.php/VirtualBox#Networking]("http://doc.gwos.org/index.php/VirtualBox#Networking") and assigned a static IP inside the VM and it works as expected.

It is mentioned in the guide that the internet connection should be up after the bridge has been created. However, thats not the case at my end. I cannot access the internet when the bridge is up. But I can access the internet from the VM alright.

So I have put the commands to create and delete the bridge in 2 scripts that I run before and after using Vbox (extra echo statements are helpful when running from nautilus):

startvboxnetwork.sh
```


#!/bin/sh

sudo modprobe tun
sudo chmod 0666 /dev/vboxdrv
sudo chmod 0666 /dev/net/tun

sudo brctl addbr br0 
sudo ifconfig eth0 0.0.0.0 promisc 
sudo brctl addif br0 eth0 
sudo dhclient br0

sudo tunctl -t tap1 -u thelinuxguy
sudo brctl addif br0 tap1 
sudo ifconfig tap1 up

echo '=================='
echo 'Bridge configuration complete'

read dummyvar

```

stopvboxnetwork.sh
```

#!/bin/sh

echo 'sudo ifconfig br0 down'
sudo ifconfig br0 down
echo '============='

echo 'sudo ifconfig tap1 down'
sudo ifconfig tap1 down
echo '============='

echo 'sudo tunctl -d tap1'
sudo tunctl -d tap1
echo '============='

echo 'sudo brctl delbr br0'
sudo brctl delbr br0
echo '============='

read dummyvar

```

I haven't tested whether deleting the bridge is necessary or just bringing it down restores internet on the host.

Edit: 

1) It doesn't work. I had to delete br0 using the second script.
2) For having internet on the host and using Vbox at the same time
    [INDENT]a) configure a second pppoe connection (rppppoe has this facility...can't say about others) using br0 as the interface
    b) remove the default gateway (through br0)
```

sudo route del default

```

However, I couldn't get both the guest and host to be connected to the net at the same time. But this is not related to Vbox as it was same with the VMware setup I have and also with 2 separate physical machines. I could dial in only from one machine at a time (I have a setup wherein I have to "dial in" over pppoe as opposed to having internet just by switching the router on). [/INDENT]

---

### Post by mdurham on 2007-05-26
Thanks for your efforts thelinuxguy. I find that just using NAT is okay I just don't have host->guest contact. I do have guest->host and full internet on both so I have no problem. It's no big deal not having host->guest. I can't find where I read about this but I'm sure it was on the VBox site somewhere.
Thanks again, Mike

---

### Post by thelinuxguy on 2007-05-26
> **mdurham said:**
> It's no big deal not having host->guest.
I doubt useful applications like 2X Application Server ([http://www.2x.com/applicationserver/](http://www.2x.com/applicationserver/)) will work in the absence of host->guest connectivity.

Regards.

---

