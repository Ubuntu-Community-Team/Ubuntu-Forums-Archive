---
title: "Is it possible to sync 2 computers with identical distros and mirror packages ?"
date: 2016-11-22
forum: General Help
---

### Post by gh0zt362 on 2016-11-22
I have 2 laptops with ubuntu studio 16.04.1 LTS . 

One has had this distro for a long time and is WELL set up with preferred packages I installed and the other is pretty much a virgin install with a couple installed pacages .

Is there any way to sync these two top tops via Lan wifi or perhaps bluetooth and get the new install to download all installed packages from the other older well setup laptop?

---

### Post by ian-weisser on 2016-11-22
One assumes that both laptops use the same architecture (32-bit or 64-bit)

Copy across the entire contents of your /var/cache/apt/archives folder. It will save lots of time re-downloading the same packages.

Copy across any changes in sources: /etc/apt/sources.list and /etc/apt/sources.list.d

Copy across the list of packages (in the 'myselections' file):
```
sudo dpkg --get-selections >myselections     // Configured system
sudo dpkg --set-selections <myselections       // New system
```


Finally, sudo apt update, then sudo apt upgrade

---

### Post by gh0zt362 on 2016-11-22
> **ian-weisser said:**
> One assumes that both laptops use the same architecture (32-bit or 64-bit)

Copy across the entire contents of your /var/cache/apt/archives folder. It will save lots of time re-downloading the same packages.

Copy across any changes in sources: /etc/apt/sources.list and /etc/apt/sources.list.d

Copy across the list of packages (in the 'myselections' file):
```
sudo dpkg --get-selections >myselections     // Configured system
sudo dpkg --set-selections <myselections       // New system
```


Finally, sudo apt update, then sudo apt upgrade

I <3 you and this community . I mean that . Thanks mah dude ;)

---

### Post by gh0zt362 on 2016-11-22
wait , one question though ...   I just tried to ssh the computers lan ip and it failed on host cpu password which I know is correct . 

I know this is a networking question but what ami doing wrong ?

---

### Post by ian-weisser on 2016-11-22
Insufficient data. We cannot see what you are seeing unless you show us.
The target machine does have an ssh server installed? And configured? And running?

What is a 'host cpu password'?

---

### Post by gh0zt362 on 2016-11-22
> **ian-weisser said:**
> Insufficient data. We cannot see what you are seeing unless you show us.
The target machine does have an ssh server installed? And configured? And running?

What is a 'host cpu password'?
ok , sorry ..    

I have ssh installed on both machines , configured?  eeeee I dunno ... ??   I had ssh running on both computers . 

well call the computer im trying to connect to #2 and the computer making the connection #1

I first ssh lan IP 192.168xxxxxx of computer #1 in #2 terminal .   It drops a line and stays blank 

I then from computer #1 ssh #2 lan IP and it asks for password for root@192.168xxx (#2)   I put the sudo password in for #2 ( both computers have the same SU password ) and it says : permission denied ; please try again . 


I also just tried to do a gigalo ssh gui connection from #2 and the connection to #1 timed out and in this instance gigolo was running on #1 as well .


Both #1 and #2 have ssh installed but I dont remember configuring ssh  so this could be the issue

---

### Post by ian-weisser on 2016-11-22
'ssh' usually refers to the ssh *client only*, which is included with the default install of Ubuntu.
It requests an ssh connection from an *ssh server, *which is not included in desktop versions of Ubuntu, and must be configured before use.

To install and configure an SSH Server, see [https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

Or skip ssh and use an USB drive instead.

---

### Post by gh0zt362 on 2016-11-22
[SUB]ok I think youre right . looks like might be  ssh config issue . Setting #password authentication to no now on both machines. [/SUB]

---

