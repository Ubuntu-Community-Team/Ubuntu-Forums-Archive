---
title: "Ubuntu core hostnames"
date: 2024-01-15
forum: General Help
---

### Post by jafesellers on 2024-01-15
Hi all I have a few raspberry pi 2 b's here at the house that currentally have core 22 installed on them that I was trying to run microcloud on. The problem I am running into is ubuntu core by default seems to set the hostname to ubuntu on all of them and microcloud seems to need the hostnames to be different on all connected servers. Is there an easy way to make it so that on startup it either randomizes the hostname or sets it to something like the serial number of the pi ?

---

### Post by Bashing-om on 2024-01-15
jafesellers - hello

The way i do this is to edit
/etc/hosts
/etc/hostname
to the name i desire.
then run:
```

sudo hostnamectl set-hostname <new-hostname>

```

[INDENT]hope this helps
[/INDENT]

---

### Post by jafesellers on 2024-01-15
That will work but i have to do it to each one is there a way to make it run once on startup ? Like maybe a cron job or something like that? So that it runs 
Sudo hostnamectl set-hostname $(grep Serial /proc/cpuinfo |cut -c 19-26)
That way I can dd the image from one Miro to another and have it just auto setup each one to be different ?

---

### Post by MAFoElffen on 2024-01-15
> **Bashing-om said:**
> 
The way i do this is to edit
/etc/hosts
/etc/hostname
to the name i desire.
then run:
```

sudo hostnamectl set-hostname <new-hostname>

```[INDENT]hope this helps
[/INDENT]

Specifically... with a bit more details to get around and prevent a Debian 'nss' bug ([http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=316099](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=316099)). This is what I do. Lets say I want to make my HOSTNAME as "server-01"
```

sudo su -
HOSTNAME="server-01"

```
Use either of these next two
```

hostname $HOSTNAME
# OR
hostnamectl set-hostname $HOSTNAME

```
Then 
```

hostname > /etc/hostname
nano /mnt/etc/hosts

```
To make these changes in that file, the first line will say
```

127.0.0.1    localhost

```
...after that line, I add a line saying either
```

127.0.1.1       <HOSTNAME>
# or if the system has a real name in DNS:
127.0.1.1       <FQDN.HOSTNAME>

```
Such as this
```

127.0.0.1    localhost.localdomain localhost
127.0.1.1    server-01

# The following lines are desirable for IPv6 capable hosts::1     localhost ip6-localhost ip6-loopback
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

---

### Post by jafesellers on 2024-01-15
I kind of understand the process of setting hostnames manually. Though didn't know the hostnamectl command that is new to me :) is there a way to not log into each pi ? I basically would like an on initial startup each time 
If hosttname != grep Serial /proc/cpuinfo |cut -c 19-26
Then 
sudo hostnamectl set-hostname grep Serial /proc/cpuinfo |cut -c 19-26
sudo reboot

else contine normal startup

---

### Post by HermanAB on 2024-01-15
The central place to set it is on the DHCP server on your router.

---

### Post by MAFoElffen on 2024-01-15
Maybe you might want to install nmap and use something from this output:
```

mafoelffen@msi-ubuntu:~$ sudo nmap -sP 10.0.0.* 
Starting Nmap 7.80 ( https://nmap.org ) at 2024-01-15 11:06 PST
Nmap scan report for _gateway ([Sanitized])
Host is up (0.012s latency).
MAC Address: [Sanitized] (Technicolor CH USA)
Nmap scan report for [Sanitized]
Host is up (0.012s latency).
MAC Address: [Sanitized] (Intel Corporate)
Nmap scan report for [Sanitized]
Host is up (0.0030s latency).
MAC Address: [Sanitized] (Raspberry Pi Trading)
Nmap scan report for [Sanitized]
Host is up (0.0045s latency).
MAC Address: [Sanitized] (Unknown)
Nmap scan report for [Sanitized]
Host is up (0.0038s latency).
MAC Address: [Sanitized] (Google)
Nmap scan report for [Sanitized]
Host is up (0.075s latency).
MAC Address: [Sanitized] (Google)
Nmap scan report for [Sanitized]
Host is up (0.0029s latency).
MAC Address: [Sanitized] (Unknown)
Nmap scan report for [Sanitized]
Host is up (0.0059s latency).
MAC Address: [Sanitized] (Roku)
Nmap scan report for [Sanitized]
Host is up (0.35s latency).
MAC Address: [Sanitized] (Unknown)
Nmap scan report for [Sanitized]
Host is up (0.0096s latency).
MAC Address: [Sanitized] (Seiko Epson)
Nmap scan report for [Sanitized]
Host is up (0.0066s latency).
MAC Address: [Sanitized] (Intel Corporate)
Nmap scan report for [Sanitized]
Host is up (0.0087s latency).
MAC Address: [Sanitized] (Giga-byte Technology)
Nmap scan report for [Sanitized]
Host is up (0.11s latency).
MAC Address: [Sanitized] (Roku)
Nmap scan report for msi-ubuntu ([Sanitized])
Host is up.
Nmap scan report for msi-ubuntu ([Sanitized])
Host is up.
Nmap scan report for msi-ubuntu ([Sanitized])
Host is up.
Nmap scan report for msi-ubuntu ([Sanitized])
Host is up.
Nmap scan report for msi-ubuntu ([Sanitized])
Host is up.
Nmap scan report for msi-ubuntu ([Sanitized])
Host is up.
Nmap scan report for msi-ubuntu ([Sanitized])
Host is up.
Nmap scan report for msi-ubuntu ([Sanitized])
Host is up.
Nmap scan report for msi-ubuntu ([Sanitized])
Host is up.
Nmap scan report for msi-ubuntu ([Sanitized])
Host is up.
Nmap done: 256 IP addresses (23 hosts up) scanned in 6.66 seconds

```
You set the IP WildCard to what you want it to search, then I parse that to do what I want with it...

---

### Post by jafesellers on 2024-01-15
basically I would like to run the equivalent of  
if [ $(hostnamectl hostname) !== $(grep Serial /proc/cpuinfo |cut -c 19-26) ]; then  echo hostname not correct changing hostname; sudo hostnamectl set-hostname $(grep Serial /proc/cpuinfo |cut -c 19-26); sudo reboot; else echo hostname correct; fi
on start up for each pi that way they all the pi's have a uniqie hostname for microcloud init when I run that

---

### Post by TheFu on 2024-01-15
Once you change the hostname as outlined above, that will stick.
It would be trivial to create a little script to do it over ssh.  

I don't use Ubuntu Core, so I don't know how immutable the system files might be.
If you are going to manage more than 5 systems, I'd highly recommend learning a DevOPS tool, like **Ansible** to handle things of this sort centrally.

---

### Post by jafesellers on 2024-01-15
So there is 8 pis but if I could build it into a script and get the script to run on start... just not sure how to get a script to run o start in core

---

### Post by TheFu on 2024-01-16
> **jafesellers said:**
> So there is 8 pis but if I could build it into a script and get the script to run on start... just not sure how to get a script to run o start in core

*Ubuntu Core* is different enough that I don't feel able to recommend anything.  If you don't get better answers, perhaps hopping onto the Ubuntu Discord channel for Ubuntu Core would be better?  I understand that real Ubuntu people hang out there. 

I did ask an AI engine how to accomplish the task.  It suggested that using cloud.init was the way.
> Here are the steps to automatically set the hostname in Ubuntu Core using cloud-init:

Create a cloud-config file: Start by creating a cloud-config file that includes the desired hostname configuration. The cloud-config file is a YAML-formatted file that contains initialization directives for cloud instances.

Specify the hostname: Within the cloud-config file, specify the desired hostname under the “hostname” key. For example, to set the hostname to “my-ubuntu-core”, the cloud-config file would include the following:

```
#cloud-config
hostname: my-ubuntu-core
```
Apply the cloud-config file: Once the cloud-config file is created and includes the desired hostname, it needs to be applied during the boot process. This can be achieved by providing the cloud-config file to cloud-init when launching or configuring an Ubuntu Core instance.

Reboot: After applying the cloud-config file, reboot the Ubuntu Core instance to apply the new hostname configuration.

By following these steps, the hostname in Ubuntu Core can be automatically set using cloud-init and a custom cloud-config file.

All that seems reasonable. I've never done it myself and have always purged cloud-init from my systems, since I have little use for it.
Ref: [https://ubuntu.com/core/docs/ubuntu-core-configuration](https://ubuntu.com/core/docs/ubuntu-core-configuration)

There's also IRC. Ubuntu had lots of different channels on IRC.  Actually, I shutdown my IRC-bouncer when IRC was bought by a suspicious new owner. That's been 2-4 yrs ago now.

---

### Post by jafesellers on 2024-01-16
I'll look into hat thanks. Would you happen to had the ubuntu discord link available? If not I'm sure I could go find it. I wonder if it can take execute a command to st the hostname from or if I would still need to touch the file on each SD card.

---

### Post by jafesellers on 2024-01-18
Ok so there is apparently a way to get cloud init to do it the part I am missing is how do I get ubuntu core to run cloud-init on startup and then where does my cloud-cinfig file need to be for that to work ?

---

