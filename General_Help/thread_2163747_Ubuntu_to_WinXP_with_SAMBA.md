---
title: "Ubuntu to WinXP with SAMBA?"
date: 2013-07-19
forum: General Help
---

### Post by hbnmgr on 2013-07-19
I used to be able to connect to my WinXP PC using Samba under Ubuntu Studio. After several updates, it seems no longer installed.
Here is my output in terminal;
 > 
 
stephen@Linus2us:~$ sudo /etc/init.d/samba stop 
sudo: /etc/init.d/samba: command not found 
stephen@Linus2us:~$ sudo /etc/samba stop 
sudo: /etc/samba: command not found 
stephen@Linus2us:~$ sudo /etc/init.d/samba stop 
sudo: /etc/init.d/samba: command not found 
stephen@Linus2us:~$ samba stop 
The program 'samba' is currently not installed.  You can install it by typing: sudo apt-get install samba4 You will have to enable the component called 'universe' 
stephen@Linus2us:~$ net usershare info --long 
stephen@Linus2us:~$ smbtree 
 HBNET     \\MAINSYS                 
stephen@Linus2us:~$ testparm -s
 Load smb config files from /etc/samba/smb.conf 
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384) 
WARNING: The "null passwords" option is deprecated
 Processing section "[print$]" 
Processing section "[printers]" 
Processing section "[MyFiles]" 
Loaded services file OK.
 Server role: ROLE_STANDALONE 
[global]
     workgroup = HBNET
     netbios name = MAINSYS
     server string =
    null passwords = Yes
     username map = /etc/samba/smbusers
     syslog only = Yes
     announce version = 5.0
     name resolve order = hosts wins bcast
     socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
     printcap name = CUPS     idmap config * : backend = tdb  

[print$]     path = /var/lib/samba/printers
     write list = root     create mask = 0664
     directory mask = 0775     guest ok = Yes  

[printers]     path = /tmp
     guest ok = Yes
     printable = Yes
     print ok = Yes
     browseable = No  

[MyFiles]
     path = /home/samba/
     force user = stephen
     force group = stephen
     read only = No     create mask = 0644 

stephen@Linus2us:~$ sudo apt-get install samba4 
    Reading package lists... Done Building dependency tree
     Reading state information... Done Package samba4 is not available, but is referred to by another package.
      This may mean that the package is missing, has been obsoleted, or is only available from another source
      E: Package 'samba4' has no installation candidate 
 

How do we now connect to a WinXP machine on a local network? I connect through a router from PC to PC. The Router is connected to Modem/Net.
Is there another Tuturorial besides the one I followed which apparently is now outdated?

ANY help is appreciated.
Thanks!
hbnmgr

---

### Post by dino99 on 2013-07-19
the error says : samba not installed :lolflag:

---

### Post by DeathByDenim on 2013-07-19
You only need the samba server if you want to share folders **from** the Ubuntu machine **to** the Windows machine. You seem to want the reverse though. To access files that are on the Windows XP machine, you need only smbclient, which is probably already installed. Does this command work:
```
smbclient //winxpmachine/shared
```
, where you need to replace "winxpmachine" with the IP of your Windows computer and "shared" with the name of the shared folder.

I think you can even open your file manager and in the location bar type smb://winxpmachine, where you need to replace winxpmachine with the IP of your Windows computer.

---

### Post by deadflowr on 2013-07-19
By default, Ubuntu comes with a samba-client, but not a samba-server.
But that shouldn't prevent you from accessing an XP machine from the Ubuntu machine.
Only accessing the Ubuntu machine from the XP machine.

What method are you using to connect to the XP machine?
I think most file managers have a "browse network", or something similar which will find any machine on your local network, to which it can connect.

---

### Post by Morbius1 on 2013-07-19
[COLOR=#0000cd]**Note1**[/COLOR]: If you want help please make an effort to provide the output of commands in a readable format and if desired place them in >  tags not ```
 tags.

[COLOR=#0000cd]**Note2**[/COLOR]: You've made a mess of things I'm afraid since you are using an outdated HowTo and the error message you received ( about installing samba4 ) was written by an idiot.

[1] I have no idea if Ubuntu installs Synaptic by default so install it:
[CODE]sudo apt-get install synaptic
```
[2] Use synaptic and do a "Search for Packages" on samba4. Then do a "Mark for complete removal" on all the ones that start with samba4.

[3] Still in synaptic install the following packages:
samba
samba-common
samba-common-bin
smbclient

If they are listed as installed then do a reinstall.

[COLOR=#0000cd]**Note3**[/COLOR]: All of this Samb4 stuff happened because you ran the following command:
[QUOTE]sudo /etc/init.d/samba stop
There is no "samba" service in Ubuntu only in Debian ( and very old versions of Ubuntu ) and it's replacement is not in /etc/init.d it's in /etc/init. So if you want to start, stop, or restart the samba service it's:
```
sudo service smbd stop
```

None of this will likely resolve your issue by itself but only get you back to the default state before you followed your HowTo.

---

### Post by hbnmgr on 2013-07-19
> **DeathByDenim said:**
> You only need the samba server if you want to share folders **from** the Ubuntu machine **to** the Windows machine. You seem to want the reverse though. To access files that are on the Windows XP machine, you need only smbclient, which is probably already installed. Does this command work:
```
smbclient //winxpmachine/shared
```
, where you need to replace "winxpmachine" with the IP of your Windows computer and "shared" with the name of the shared folder.

I think you can even open your file manager and in the location bar type smb://winxpmachine, where you need to replace winxpmachine with the IP of your Windows computer.

Actually, I wish to go both ways! Makes sense to me, as I did it before some 'updates'.

The output of your code follows;

[quote]
Connection to "IPADDRESS" failed (Error NT_STATUS_CONNECTION_REFUSED)
[/guote]

As to Morbius' Post;
Reinstalled those items you mentioned in #3 - All that was installed.
Now what? Since as you say, there is no Samba Service - then what are these items?

Still confused with no clear direction to go ?!!?

Thanks for your time and patience.

---

### Post by hbnmgr on 2013-07-19
> **deadflowr said:**
> By default, Ubuntu comes with a samba-client, but not a samba-server.
But that shouldn't prevent you from accessing an XP machine from the Ubuntu machine.
Only accessing the Ubuntu machine from the XP machine.

What method are you using to connect to the XP machine?
I think most file managers have a "browse network", or something similar which will find any machine on your local network, to which it can connect.

When using File MGR, I recieve this Error when attempting to Open "My Local Network";
> FAILED TO RETRIEVE SHARE LIST FROM SERVER


Perplexed ! ! !

---

### Post by deadflowr on 2013-07-19
When you ran DeathbyDemin's smbclient command, did you switch out the //winxpmanchine/shared with the windowsxp ip address?
If you need help finding it install nmap.
```
sudo apt-get install nmap
```
And then run the command
```
 sudo nmap -sP 192.168.1.1/24
```

This should list all the machines on your local network.
try the smbclient //ipaddressfor windowsXp again.

---

### Post by hbnmgr on 2013-07-19
Yes!
Now I get this Error, after Re-Install of SMB files;
> 
stephen@Linus2us:~$ smbclient //192.168.2.51/SharedDocs
WARNING: The "null passwords" option is deprecated
Enter stephen's password: 
Connection to 192.168.2.51 failed (Error NT_STATUS_CONNECTION_REFUSED)



Any Suggestions?  Neither computer seems to able to see the other. I have ZoneAlarm on the WinXP with the IP of the No.2 Ubuntu machine in the Trusted Zone.
Same setting as before when it did work. However, they can both PING each other ... therefore they do see each other!

Confused !?!?!?

---

### Post by Morbius1 on 2013-07-19
If you reinstalled samba-common we need to see the output of this command again: 
```
testparm -s
```
If you followed          deadflowr's advice and installed nmap then what is the output of this command:
```
sudo nmap -sS -sU -T4 192.168.2.51
```
You need the following ports open on the Windows machine ( and the Linux machine ) for all this to work:
> PORT     STATE         SERVICE
139/tcp  open          netbios-ssn
445/tcp  open          microsoft-ds
137/udp  open          netbios-ns
138/udp  open|filtered netbios-dgm

You might want to disable any firewalls you have on both machines in the mean time just to make sure they are not getting in the way.

---

### Post by hbnmgr on 2013-07-19
Apparently, I had renamed the No.2 Ubuntu computer on the Network. When WinXP finally showd two items in the Network, I double clicked the unfamiliar one, it asked for a username and password. So I input my username and password to the No.2 Ubuntu Machine and Presto - I'm in like Flint. Transferring files - OK.

However, clicking on MY LAN stills give me an Error. So my No.2 Ubuntu computer cannot PEER to WinXP, but can still PING it.

Sometimes its a Mystery to me ! ! !

---

