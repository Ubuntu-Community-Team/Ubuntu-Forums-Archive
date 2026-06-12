---
title: "Update manager won't install updates"
date: 2008-06-24
forum: General Help
---

### Post by Warlon on 2008-06-24
My update manager shows me I have updates available, but it won't install them. When I click "install updates" it shows me the "reading package information" progressbar and then nothing happens. I have been having this problem now for a while. 

Updates install just fine when I run apt-get upgrade.

I'm running 8.04.

---

### Post by Warlon on 2008-10-10
Bump! Please help! Does anybody have any idea on how to diagnose this problem? Any log files or debug messages I could investigate?

Right now my update manager shows I have two updates available, but it won't install them. If I open synaptic and click on "mark all updates" it won't select anything and the apply button stays gray.

Am I doomed to run apt-get upgrade from the command line from here to eternity?

---

### Post by drs305 on 2008-10-10
> **Warlon said:**
> Bump! Please help! Does anybody have any idea on how to diagnose this problem? Any log files or debug messages I could investigate?

Right now my update manager shows I have two updates available, but it won't install them. If I open synaptic and click on "mark all updates" it won't select anything and the apply button stays gray.

Am I doomed to run apt-get upgrade from the command line from here to eternity?

Have you tried apt-get and does apt-get work? If not, run this in terminal and see what kind of error messages you get:
```
sudo apt-get update && sudo apt-get upgrade
```

Even if you are doomed it will do the job until someone can figure it out.

How about System, Administration, Update Manager? No success there either?

---

### Post by Warlon on 2008-10-10
I just run apt-get update and like I mentioned earlier, it installed the updates without any abnormal output. I also tried running update-manager from Administration, but it has the same problem as the panel applet and does not install anything.

I had proposed and backport -updates enabled at some point earlier, so my best guess is that this may have something to do with it.

---

### Post by drs305 on 2008-10-10
This may seem to be a bit odd, but sometimes the loss of synaptic and add/remove is caused by a corrupted host file.

Look up your hostname:
```
hostname
```
Either inspect the hosts file with 'cat' or back it up and open it for editing:
```

cat /etc/hosts
*or*
sudo cp /etc/hosts /etc/hosts.bak1
gksu gedit /etc/hosts

```
The second line normally looks like this. The computer name should match the results of the 'hostname' command, with no additions such as .network, .web, .local, etc. :
```

127.0.01  localhost
127.0.1.1  **yourhostname**
```
It should not look like:  yourhostname.web, yourhostname.gworld, etc.
If there isn't, comment whatever that line says and add a corrected line.

---

### Post by Warlon on 2008-10-10
This is my /etc/hosts file. Spider is my hostname.

```
127.0.0.1	localhost
127.0.1.1	spider

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

I can install programs from Synaptic normally, It's just the updates that it refuses to handle.

---

