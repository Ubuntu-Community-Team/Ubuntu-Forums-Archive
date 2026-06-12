---
title: "Using Samba between two Ubuntu computers"
date: 2014-03-04
forum: General Help
---

### Post by Tony_Lillie on 2014-03-04
I have a fully functional Samba share set up on computer #1 running Ubuntu 12.04. My Windows computers can see it and connect to it without issue. 

The problem is my laptop (computer #2) running Ubuntu 13.10 cannot connect to the share. I've spent several hours researching this and can't seem to find a straight answer that doesn't get convoluted with suggestions to use SSH or NFS rather than Samba. Obviously with several Windows computers on my network I need to be using Samba rather than NFS, and SSH does not allow for persistent mapping of the share, at least not without a great deal of complex configuration.

So, I need help getting the 13.10 machine to connect to the Samba share on the 12.04 machine. I really want to do this with Samba, not only because of the reasons I've already mentioned, but also because I would like to have a better understanding of Samba which is a pathway I'm already on. Said another way, I would much rather learn Samba better than start learning a new thing (at least for now).

I have tried connecting to the share through the "connect to server" option in the "files" dialog. I enter "smb://mediaserver/public" and I get an error dialog that says, "Unhandled error message: Failed to mount Windows share: Connection timed out". I wish I could say I had tried more things, but the information on this subject seems to be pretty thin, as most of the threads I found lead to recommendations to use SSH or NFS.

Please someone help me with SAMBA.

---

### Post by Morbius1 on 2014-03-04
Samba is made up of 2 parts: the actual file sharing part ( smbd ) and the Microsoft network discovery part ( nmbd ).

I'm reluctant to mess about with the nmbd part of this since your Windows machines seem to have no problems connecting so let's use Samba using a native Linux network discovery mechanism in parallel. Instead of this:
> I have tried connecting to the share through the "connect to server"  option in the "files" dialog. I enter "[COLOR=#0000cd]**smb://mediaserver/public**[/COLOR]"
Use this in Connect to Server:
```
smb://mediaserver.local/public
```
THe ".local" is enabled through the use of avahi which all your Linux systems should already have installed. The only requirements to have this work are:

[1] Everyone is in the same subnet - make sure everyone is connected to the same router.
[2] Avahi must be running on both server and client:
```
sudo service avahi-daemon start
```
[3] The firewall must allow port 5353 - so for the time being just disable all firewalls.

[COLOR=#0000cd][I]You can also make it so these can be browsed by creating an avahi / samba.service config file which is incredibly easy to do.


[/I][/COLOR][COLOR=#0000cd]**If you want to pursue the Microsoft method**[/COLOR] it comes with rules. Unless you've done something exotic with how your home network is wired there's usually only a limited number of things that can go wrong with browsing to a Linux samba server:

[COLOR=#0000cd]*Some of these items seem not to be this issue here since the Windows machine can connect but I'm posing them just in case and given the "Connection timed out" error I suspect item [5] is the culprit on the client:*[/COLOR]

[1] Multiple subnets - all boxes should connect to only one router.
[2] Samba services are not running - Turn them on:
```
sudo service smbd start
sudo service nmbd start
```
[3] Firewall is in the way - turn them all off for now
[4] Your host name is too long - it has to be 15 characters or less in length so run the following command and count the number of characters:
```
hostname
```
If it's 16 characters or more in length give your server ( for samba purposes only ) a shorter name by adding this line with a shorter name in the [global] section right under the workgroup line in /etc/samba/smb.conf:
```
netbios name = a-name-shorter-than-16-characters
```
[COLOR=#0000cd][5] Name Resolution.[/COLOR]
Microsoft allows for multiple mechanisms to convert a host's name to an ip address but the only one that works by default in Linux is "bcast" so place it first in order by adding a line in smb.conf - in the [global] section under the workgroup line - do this first on the client so as to minimize any interruption with Windows:
```
name resolve order = bcast host lmhosts wins
```
Note: After any kind of edit in smb.conf you should restart the samba services:
```
sudo service smbd restart
sudo service nmbd restart
```:

---

### Post by jp734 on 2014-03-04
Wild guess here but have you installed smbclient?

---

### Post by Tony_Lillie on 2014-03-04
For Bruce.

Here is the result of smbtree -d3
```
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface wlan0 ip=fe80::1e4b:d6ff:feca:6117%wlan0 bcast=fe80::ffff:ffff:ffff:ffff%wlan0 netmask=ffff:ffff:ffff:ffff::
added interface wlan0 ip=192.168.1.7 bcast=192.168.1.255 netmask=255.255.255.0
Enter tonylaptop's password: 
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name LILLIEZONE<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name LILLIEZONE<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name LILLIEZONE<0x1d>
Got a positive name query response from 192.168.1.9 ( 192.168.1.9 )
Connecting to host=192.168.1.9
Connecting to 192.168.1.9 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Got a positive name query response from 192.168.1.9 ( 192.168.1.9 )
resolve_lmhosts: Attempting lmhosts lookup for name LILLIEZONE<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name LILLIEZONE<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name LILLIEZONE<0x1d>
Got a positive name query response from 192.168.1.9 ( 192.168.1.9 )
Connecting to host=192.168.1.9
Connecting to 192.168.1.9 at port 445
Connecting to 192.168.1.9 at port 139
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
LILLIEZONE
resolve_lmhosts: Attempting lmhosts lookup for name LILLIEZONE<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name LILLIEZONE<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name LILLIEZONE<0x1d>
Got a positive name query response from 192.168.1.9 ( 192.168.1.9 )
Connecting to host=192.168.1.9
Connecting to 192.168.1.9 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
    \\TVSERVER               TVSERVER
Connecting to host=TVSERVER
resolve_lmhosts: Attempting lmhosts lookup for name TVSERVER<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name TVSERVER<0x20>
resolve_wins: Attempting wins lookup for name TVSERVER<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name TVSERVER<0x20>
Connecting to 198.105.246.114 at port 445
Connecting to 198.105.246.114 at port 139
Error connecting to 198.105.246.114 (No route to host)
Connecting to 198.105.251.114 at port 445
Connecting to 198.105.251.114 at port 139
Error connecting to 198.105.251.114 (No route to host)
cli_start_connection: failed to connect to TVSERVER<20> (0.0.0.0). Error NT_STATUS_HOST_UNREACHABLE
    \\TONYLAPTOP             tonylaptop server (Samba, Ubuntu)
Connecting to host=TONYLAPTOP
resolve_lmhosts: Attempting lmhosts lookup for name TONYLAPTOP<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name TONYLAPTOP<0x20>
resolve_wins: Attempting wins lookup for name TONYLAPTOP<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name TONYLAPTOP<0x20>
Connecting to 127.0.1.1 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\TONYLAPTOP\print$             Printer Drivers
        \\TONYLAPTOP\IPC$               IPC Service (tonylaptop server (Samba, Ubuntu))
    \\PRIMARY                
Connecting to host=PRIMARY
resolve_lmhosts: Attempting lmhosts lookup for name PRIMARY<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name PRIMARY<0x20>
resolve_wins: Attempting wins lookup for name PRIMARY<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name PRIMARY<0x20>
Connecting to 198.105.246.114 at port 445
Connecting to 198.105.246.114 at port 139
Error connecting to 198.105.246.114 (No route to host)
Connecting to 198.105.251.114 at port 445
Connecting to 198.105.251.114 at port 139
Error connecting to 198.105.251.114 (No route to host)
cli_start_connection: failed to connect to PRIMARY<20> (0.0.0.0). Error NT_STATUS_HOST_UNREACHABLE
    \\MEDIASERVER            MediaServer server (Samba, Ubuntu)
Connecting to host=MEDIASERVER
resolve_lmhosts: Attempting lmhosts lookup for name MEDIASERVER<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name MEDIASERVER<0x20>
resolve_wins: Attempting wins lookup for name MEDIASERVER<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name MEDIASERVER<0x20>
Connecting to 198.105.246.114 at port 445
Connecting to 198.105.246.114 at port 139
Error connecting to 198.105.246.114 (No route to host)
Connecting to 198.105.251.114 at port 445
Connecting to 198.105.251.114 at port 139
Error connecting to 198.105.251.114 (No route to host)
cli_start_connection: failed to connect to MEDIASERVER<20> (0.0.0.0). Error NT_STATUS_HOST_UNREACHABLE
    \\JOHANNA-PC             JoHanna Laptop
Connecting to host=JOHANNA-PC
resolve_lmhosts: Attempting lmhosts lookup for name JOHANNA-PC<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name JOHANNA-PC<0x20>
resolve_wins: Attempting wins lookup for name JOHANNA-PC<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name JOHANNA-PC<0x20>
Connecting to 198.105.246.114 at port 445
Connecting to 198.105.246.114 at port 139
Error connecting to 198.105.246.114 (No route to host)
Connecting to 198.105.251.114 at port 445
Connecting to 198.105.251.114 at port 139
Error connecting to 198.105.251.114 (No route to host)
cli_start_connection: failed to connect to JOHANNA-PC<20> (0.0.0.0). Error NT_STATUS_HOST_UNREACHABLE
    \\ETHAN-PC               
Connecting to host=ETHAN-PC
resolve_lmhosts: Attempting lmhosts lookup for name ETHAN-PC<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name ETHAN-PC<0x20>
resolve_wins: Attempting wins lookup for name ETHAN-PC<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name ETHAN-PC<0x20>
Connecting to 198.105.246.114 at port 445
Connecting to 198.105.246.114 at port 139
Error connecting to 198.105.246.114 (No route to host)
Connecting to 198.105.251.114 at port 445
Connecting to 198.105.251.114 at port 139
Error connecting to 198.105.251.114 (No route to host)
cli_start_connection: failed to connect to ETHAN-PC<20> (0.0.0.0). Error NT_STATUS_HOST_UNREACHABLE

```

What is that 198.105.246.114 address it keeps trying to connect to? If  it doesn't matter, please feel free to ignore that question.

To answer your other questions, the Laptop is a fresh install of 13.10  and I've made very few changes. Though I did try to install "smbfs" and  got the following error ```
 Package smbfs is not available, but is  referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  cifs-utils:i386 cifs-utils

E: Package 'smbfs' has no installation candidate

```

I also edited the /etc/samba/smb.conf file to reflect the correct  "workgroup" name and I added the following line below that ```
netbios  name = tonylaptop
```

I also added WINS to the following line ```
;   name resolve order = lmhosts host wins bcast
```

Those are the only changes I have made. I have not touched the server,  at least not in any way to address this problem. I created another share  a while back, but like I said, all my WIndows computers have unfettered  read/write access to those shares. The only computer that can't see  them is this new 13.10 laptop.

I look forward to chatting with you this evening if possible.

Best Regards,

Tony

---

### Post by Tony_Lillie on 2014-03-04
Morbius1,

It worked!! It instantly connected when I used ```
smb://mediaserver.local/public
```

So, the next question is why? Is there a reasonably understandable answer to that question? Just curious... it's the nature of a Linux user to want to know why, right.:P

Also, and more importantly, how do I map this permanently so it mounts automatically at login?

---

### Post by Morbius1 on 2014-03-04
> **Tony_Lillie said:**
> Morbius1,

It worked!! It instantly connected when I used ```
smb://mediaserver.local/public
```

So, the next question is why? Is there a reasonably understandable answer to that question? Just curious... it's the nature of a Linux user to want to know why, right.:P

Also, and more importantly, how do I map this permanently so it mounts automatically at login?
Samba clients and servers connect to each other by ip address not by name. If you want to use a name some mechanism must be available to convert the name to an ip address. There's may ways to accomplish this but the easiest is either with Microsofts bcast ( which I also covered in my original post ) or with Linux' avahi ( aka mDNS, zeroconf, ... )

The ".local" is an mDNS qualifier that each Linux and OSX  machine ( Avahi in OSX is called Bonjour ) attaches to it's host name and then can respond to when queried from another Linux or OSX machine. 

As far as automounting you can do the poor man's version:

Once Nautilus opens up to //mediaserver.local/public bookmark it: Bookmarks > Add Bookmark. It will show up on the left side panel of Nautilus just like a "mapped drive" did on Windows. It's not really automounting because you have to select the bookmark to actually mount it but it may be enough.

Other options are Gigolo or AutoFS. In both cases just make sure you specify the .local part of the host name.

[COLOR=#0000cd]***By the way***[/COLOR]: *Bruce?*
*You make things more difficult to diagnose if you are doing things via PM especially if you are modifying smb.conf.* *Luckily you would have to do a lot of damage to smb.conf for avahi not to work.*

[COLOR=#0000cd]***EDIT***[/COLOR]: *Actually it's a rather nasty thing for Bruce to do and designed among other things to make anyone helping you on the forum itself to look bad if things that were suggested were undone. Given that I'm pretty sure I know the real identity of Bruce.* ;)

---

### Post by Tony_Lillie on 2014-03-04
This entire situation concerning Bruce is very unfortunate and entirely MY fault. I was unable to communicate with him by PM because the stupid interface would not allow more than 5000 characters, so I stupidly posted my response to him in the public forum.

Morbius1, I am grateful for your Linux knowledge and willingness to respond to my issue, but you might keep your editorial comments about another equally if not more knowledgeable Linux pro to yourself. Bruce is a good guy who has helped me immensely in the past and was helping me again now. I totally screwed up by not keeping my private correspondence with him private.

Again, thank you for your help resolving my issue.

---

