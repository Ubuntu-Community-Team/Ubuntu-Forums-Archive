---
title: "Is Samba read/write rate performance on Ubuntu 20.04 capped at around 11MB/s?"
date: 2021-04-22
forum: General Help
---

### Post by mike4ubuntu on 2021-04-22
I've noticed that no matter what I do, I can only get read/write performance of around 11MB/s with my Ubuntu 20.04 file server running Samba Version 4.11.6-Ubuntu using Ubuntu, MacOS 10.15, Windows 10 clients for a file of around 250GB. If I share a folder on Windows, I can get above 100MB/s performance with the same clients and file size. Is Samba just that bad compared to Windows? It's pretty consistently around 10x slower on Ubuntu Samba. I have a lightly loaded 1Gb/s LAN, so 100MB/s (1B=~8b) is about as good as you can do. I've tried many conf commands in smb.conf. I'm ready to give up and just host my file service on Windows. Any last minute ideas before I make the change in Host?

the [GLOBAL] part of smb.conf:
```

log level = 1
#std#socket options = TCP_NODELAY IPTOS_LOWDELAY SO_RCVBUF=131072 SO_SNDBUF=131072 SO_KEEPALIVE
socket options = TCP_NODELAY SO_RCVBUF=131072 SO_SNDBUF=131072 SO_KEEPALIVE IPTOS_THROUGHPUT

#no better than buf=131072#socket options = TCP_NODELAY IPTOS_LOWDELAY SO_RCVBUF=2097152 SO_SNDBUF=2097152
# this one is really slow#socket options = TCP_NODELAY IPTOS_LOWDELAY SO_SNDBUF=8192 SO_RCVBUF=8192
read raw = Yes
write raw = Yes
strict locking = No
strict allocate = Yes
allocation roundup size = 4096
server signing = No
oplocks = yes
max xmit = 65535
dead time = 15
getwd cache = yes
#min receivefile size = 32768
min receivefile size = 16384
use sendfile = true
aio read size = 16384
aio write size = 16384
#aio read size = 32768
#aio write size = 32768
use sendfile = true

# Performance specific for MacOS
min protocol = SMB2
vfs objects = fruit streams_xattr  
fruit:metadata = stream
fruit:model = MacSamba
fruit:posix_rename = yes 
fruit:veto_appledouble = no
fruit:wipe_intentionally_left_blank_rfork = yes 
fruit:delete_empty_adfiles = yes 
```

---

### Post by ActionParsnip on 2021-04-22
How about SSHFS / SFTP instead? I assume you have installed openssh-server... Mac OS can connect to SFTP natively

---

### Post by mike4ubuntu on 2021-04-23
OMG, the performance of sftp is even worse.  Can't get more than 4MB/s.  At least I could get 11MB/s with Samba.  Judging from all of the replies on other forums, it just seems that that's about the best that Samba can do.  Is it just a factor of SAMBA code performance, or is there a setting that really caps the bandwidth?

---

### Post by HermanAB on 2021-04-24
The performance is not capped.  SMB is just a very inefficient and chatty protocol.  SFTP will be even worse, since is also has to encrypt and decrypt the data.  Run tcpdump or wireshark to see what is going on.

---

### Post by SeijiSensei on 2021-04-24
I use NFS whenever possible.

---

### Post by HermanAB on 2021-04-25
Note that ordinary FTP is also much faster.  FTP is natively supported by Windows file managers also.  The user level security is bad, but so is that of SMB.

---

### Post by TheFu on 2021-04-25
> **mike4ubuntu said:**
> OMG, the performance of sftp is even worse.  Can't get more than 4MB/s.  At least I could get 11MB/s with Samba.  Judging from all of the replies on other forums, it just seems that that's about the best that Samba can do.  Is it just a factor of SAMBA code performance, or is there a setting that really caps the bandwidth?

I don't have samba on 20.04, but on 18.04, this version works:
```
samba            2:4.7.6+dfsg~ amd64
```

I see 65-75MBps transferring files FROM Windows to Ubuntu using SMB v2.1.  Something isn't right on your systems. I don't know what it is. With 20.04, a number of samba defaults changed. At the same time, Win10 changed some of those defaults ... and some didn't line up to make it easy to install and *just work*.

I get better performance with NFS, but that is harder to use with Windows. I understand NFS is part of some Win10 versions. It was in Enterprise and Ultimate Win7 releases, but not Home or Professional. Getting the Windows UserID ---> Unix uid/gid mappings setup was always a hassle.

**sshfs** is dog slow, always.  I only use it when a complex program/tool is on 1 system and the data to be input/acted on is on any other system, but not available over NFS. Moving that complex setup to the system that has the data would be too much effort, so sshfs can be used for access while I have lunch or sleep. That doesn't help Windows users. Too bad.

**sftp** is natively supported by nearly all Unix file managers.  Just put sftp://..... as the URL into the file manager. Because it is encrypted, there is overhead, but nothing as bad as sshfs. That doesn't help Windows users. Too bad.

**scp** and **rsync** feel a little faster than sftp. Again, if I don't have access to either side of the storage using NFS, then I'll use those to transfer.  scp for files inside 1 directory that aren't already on the other side and rsync when an entire directory structure is involved. That doesn't help Windows users. Too bad.

Windows has **WinSCP** as an scp and sFTP program. It integrates with MS-Explore - full drag-n-drop and has a 2-pane layout for source and target. Most end-users would figure this out.

I stopped using plain FTP around 2002. Security.  If I need to make a file accessible to a few friends, I'll bury that file in a web server I control and send those friends the exact HTTPS link. Then I'll use 'at' to delete the file in 1-2 weeks automatically. I use 'at' to schedule future events all the time.  Right now, 14 things are scheduled for this week currently.

To share a file, even a huge file, with one of my Linux buddies, I'll use **Magic Wormhole**. It is in the repos or there is a snap package if you only want to touch storage in your HOME directory (which I seldom desire). I use the APT package. Snagged a 31G set of files a few weeks ago from a friend. Left it running overnight.

Anyway - when it comes to performance issues, break apart the problem and work backwards.  Fix issues in order.
[LIST=1]
[*]Check the network performance - **iperf3**
[*]Check the disk and file system performance **fio**/bonnie++
[*]Check the samba protocol performance - increase logging to see any issues.
[/LIST]

Blaming Samba when the disk is about dead isn't exactly fair, especially when others are getting 65+ MB/sec (520Mbps) transfers.
```
$ time cp  Home_Movie-2004.mkv /Data/K/

real    0m17.190s
user    0m0.007s
sys     0m1.722s

$ \du -s Home_Movie-2004.mkv
1913392  Home_Movie-2004.mkv

$ df -Th  .
Filesystem       Type  Size  Used Avail Use% Mounted on
//172.22.22.14/K **cifs**   74G   19G   55G  26% /Data/K

$ mount |grep /Data/K
//172.22.22.14/K on /Data/K type **cifs** (rw,relatime,vers=2.1,cache=strict,username=tf,uid=1000,forceuid,gid=1000,forcegid,addr=172.22.22.14,file_mode=0664,dir_mode=0775,soft,nounix,serverino,mapposix,rsize=1048576,wsize=1048576,bsize=1048576,echo_interval=60,actimeo=1)
```

Using Windows Exploder, saving files to CIFS storage I see about 50% of the GigE connection in Task Manager ... which is 62.5 MBps. Both disks involved are not SSDs, but old WD disks.  Blue inside the Linux system and a true WD-Black in the Windows box. WD-Black drives are quality and fast in my experience. The 5 yr warranty doesn't hurt either.

Using the numbers in my actual transfer commands above, we can do some calculations:
1913392 bytes / 17.19 seconds = 113 MB/sec ... using clock time. That really isn't fair, because there is disk caching in RAM that makes it seem faster than it is.  Plus, on a GigE network, 125MB/s is the theoretical max possible without using link aggregation.

Going in the opposite direction, it took 24.524s ... so that works out to 79.33 MB/sec. I cheated and stored the file on an SSD this time. Redoing it to the WD-Blue ... was about the same 25.8s.

Transferring lots of small files is drastically slower. That's about the overhead in creating files, allocations, sectors, etc.

Hopefully, this has provided some ideas for steps.  I'm happy to post my smb.conf stuff, if that would help.  I mount Windows storage using autofs, so that won't be too helpful.  Also, I ran all the commands initiated from the Linux side because I know how to capture transfer data there, but not on Windows.  Capturing random screens during the xfer just doesn't seem scientific.

---

### Post by mike4ubuntu on 2021-04-26
Thanks for everyone's help.  I haven't tried NFS, but it seems hard to implement on Windows.  I tried some of the TheFu's numbers, but nothing seems to help so far.  It seems like Windows native SMB support is just a lot faster than SAMBA especially for large files.  I think I'll probably just have to start using Win10 as my file servers.  Windows as a file server gets consistently 110 MB/s which is close to the theoretical max.  I'm curious to try WSL 2.  The latest Microsoft preview version has Linux GUI support and can run Ubuntu 20.04.  I guess SAMBA just isn't as good as the real thing, but I would have expected it to be better than 10% as good.

---

### Post by TheFu on 2021-04-26
> **mike4ubuntu said:**
> Thanks for everyone's help.  I haven't tried NFS, but it seems hard to implement on Windows.  I tried some of the TheFu's numbers, but nothing seems to help so far.  It seems like Windows native SMB support is just a lot faster than SAMBA especially for large files.  I think I'll probably just have to start using Win10 as my file servers.  Windows as a file server gets consistently 110 MB/s which is close to the theoretical max.  I'm curious to try WSL 2.  The latest Microsoft preview version has Linux GUI support and can run Ubuntu 20.04.  I guess SAMBA just isn't as good as the real thing, but I would have expected it to be better than 10% as good.

Something isn't right on your systems. I don't know what it is. That doesn't mean it is bad for everyone.
If you want to give up, fine.
If you want help, post similar commands and output, so data is provided for others to see. It s frustrating when no facts are provided.

---

### Post by mike4ubuntu on 2021-04-29
yes, something could be wrong with the system, but what?  If there are better settings for SAMBA I would like to see them.  Also, if there are, why are they not the defaults.  This performance issue with SAMBA seems to be common theme in all the forums.  I provided those conf settings in my first post.  I've experimented with the conf files settings based on others having similar problems.  Again, the MacOS and Windows share servers running on the same subnet, don't seem to have this performance issue.

I've also investigated the network settings.  I've used iperf3 to get network performance numbers, which indicated a possible issue with the interface itself.  I have the SAMBA server going through the same 1Gbit router as the Windows and MacOS server.  I even replaced the SAMBA server's Ethernet cable with a new Cat 8 cable.

However, I can't rule out an issue with the Ethernet interface

```

lspci | grep -i ethernet
06:00.0 Ethernet controller: Intel Corporation I210 Gigabit Network Connection (rev 03)
07:00.0 Ethernet controller: Intel Corporation I210 Gigabit Network Connection (rev 03)

```
The 1Gbit light is on the RJ45 jack.

iperf3 stats:
UDP numbers seem ok, but TCP numbers don't, although.  I suppose the UDP numbers should be faster than TCP to some degree, but don't understand the wide discrepancy.

iperf3 UDP:
```

iperf3 -u -b 1Gbps -l 1000 -c ss.ss.ss.ss
Connecting to host <SAMBA Server>, port 5201
[  4] local cc.cc.cc.cc port 57998 connected to ss.ss.ss.ss port 5201
[ ID] Interval           Transfer     Bandwidth       Total Datagrams
[  4]   0.00-1.06   sec   778 KBytes  6.00 Mbits/sec  797
[  4]   1.06-2.03   sec   261 KBytes  2.20 Mbits/sec  267
[  4]   2.03-3.01   sec   270 KBytes  2.25 Mbits/sec  276
[  4]   3.01-4.06   sec   283 KBytes  2.22 Mbits/sec  290
[  4]   4.06-5.03   sec   266 KBytes  2.23 Mbits/sec  272
[  4]   5.03-6.01   sec   264 KBytes  2.21 Mbits/sec  270
[  4]   6.01-7.04   sec   281 KBytes  2.23 Mbits/sec  288
[  4]   7.04-8.05   sec   277 KBytes  2.25 Mbits/sec  284
[  4]   8.05-9.05   sec   274 KBytes  2.27 Mbits/sec  281
[  4]   9.05-10.04  sec   273 KBytes  2.25 Mbits/sec  280
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bandwidth       Jitter    Lost/Total Datagrams
[  4]   0.00-10.04  sec  3.15 MBytes  2.63 Mbits/sec  5.947 ms  375/3305 (11%)
[  4] Sent 3305 datagrams

iperf Done.

```


iperf3 TCP :
```

perf3 -b 1Gbps -c ss.ss.ss.ss
Connecting to host <SAMBA server>, port 5201
[  4] local cc.cc.cc.cc port 63848 connected to ss.ss.ss.ss port 5201
[ ID] Interval           Transfer     Bandwidth
[  4]   0.00-1.01   sec  8.38 MBytes  69.5 Mbits/sec
[  4]   1.01-2.00   sec  8.88 MBytes  75.1 Mbits/sec
[  4]   2.00-3.00   sec  8.75 MBytes  73.5 Mbits/sec
[  4]   3.00-4.00   sec  9.12 MBytes  76.4 Mbits/sec
[  4]   4.00-5.01   sec  8.88 MBytes  74.1 Mbits/sec
[  4]   5.01-6.01   sec  9.00 MBytes  75.6 Mbits/sec
[  4]   6.01-7.01   sec  9.00 MBytes  75.1 Mbits/sec
[  4]   7.01-8.01   sec  8.88 MBytes  74.9 Mbits/sec
[  4]   8.01-9.01   sec  9.00 MBytes  75.1 Mbits/sec
[  4]   9.01-10.00  sec  9.00 MBytes  76.2 Mbits/sec
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bandwidth
[  4]   0.00-10.00  sec  88.9 MBytes  74.5 Mbits/sec                  sender
[  4]   0.00-10.00  sec  88.9 MBytes  74.5 Mbits/sec                  receiver

iperf Done.

```

looks like Max~9 MBytes, can't explain why so low.

---

### Post by rsteinmetz70112 on 2021-04-29
Since this is a SAMBA problem you might want to try the Samba mailing list. The SAMBA devs visit there and there are a number of people intimately familiar with what it does.

---

### Post by TheFu on 2021-04-29
Could be a network config issue if you have both NICs enabled.  The routing table might be messed up.

The UDP numbers are worse than the TCP ones!  2.25 Mbps is terrible!
Could the client be over wifi with 3 cement walls in the way?

9.00 MBytes/sec seems like a 100 base-tx NIC is being used.

```
$ iperf3 -V -b 1Gbps  &#8211;length 1000 -c hadar
iperf 3.7
Linux regulus 5.4.0-72-generic #80-Ubuntu SMP Mon Apr 12 17:35:00 UTC 2021 x86_64
Control connection MSS 1448
Time: Thu, 29 Apr 2021 16:43:44 GMT
Connecting to host hadar, port 5201
      Cookie: gwx4qjrqqlcslresbrway3cbixlczcycrnwx
      TCP MSS: 1448 (default)
      Target Bitrate: 1000000000
[  5] local 172.22.22.3 port 60930 connected to 172.22.22.6 port 5201
Starting Test: protocol: TCP, 1 streams, 131072 byte blocks, omitting 0 seconds, 10 second test, tos 0
[ ID] Interval           Transfer     Bitrate         Retr  Cwnd
[  5]   0.00-1.00   sec   119 MBytes   999 Mbits/sec    0    130 KBytes       
[  5]   1.00-2.00   sec   119 MBytes  1.00 Gbits/sec    0    168 KBytes       
[  5]   2.00-3.00   sec   119 MBytes  1.00 Gbits/sec    0    239 KBytes       
[  5]   3.00-4.00   sec   119 MBytes  1.00 Gbits/sec    0    264 KBytes       
[  5]   4.00-5.00   sec   119 MBytes   999 Mbits/sec    0    264 KBytes
```

Your samba config seems extremely complex.  Mine is all defaults, except I force a different workgroup and set 
```
min protocol = SMB2
server signing = mandatory
```

In the "homes" share, 
```
[homes]
  comment = Home Directories
  hosts allow = 127.0.0.1 172.22.22.0/24 
  hosts deny = 0.0.0.0/0
  browseable = yes
  guest ok = no
  writable = yes
  create mask = 0640
  directory mask = 0750
  valid users = %S
```
That's it.  65-75 MB/s from Windows.

As I said, it is something about your setup.
Morphus posts about Samba in these forums. For Win10 clients: [https://ubuntuforums.org/showthread.php?t=2434383](https://ubuntuforums.org/showthread.php?t=2434383)

Samba changed some defaults with 20.04, then Microsoft changed their defaults on Win10. Both these changes happened fairly quickly and broke connections for many people - mainly those with older SMB1 devices which had zero security.

If all your clients are Win10, use 
```
min protocol = SMB3
server signing = mandatory
```
for better performance and better security in the global smb.conf section.

I should be clear about my iperf3 run.  That's a VM on the same host talking with the host directly.
```
$ iperf3 -c hadar
Connecting to host hadar, port 5201
[  5] local 172.22.22.3 port 60946 connected to 172.22.22.6 port 5201
[ ID] Interval           Transfer     Bitrate         Retr  Cwnd
[  5]   0.00-1.00   sec  3.07 GBytes  26.3 Gbits/sec    0   2.25 MBytes       
[  5]   1.00-2.00   sec  2.97 GBytes  25.5 Gbits/sec    0   2.39 MBytes       
[  5]   2.00-3.00   sec  2.84 GBytes  **24.4 Gbits/sec**    0   2.52 MBytes       

```
From separate physical machines, I only see
$ iperf3 -c hadar
Connecting to host hadar, port 5201
[  4] local 172.22.22.4 port 50076 connected to 172.22.22.6 port 5201
[ ID] Interval           Transfer     Bandwidth       Retr  Cwnd
[  4]   0.00-1.00   sec   114 MBytes   954 Mbits/sec    0    376 KBytes       
[  4]   1.00-2.00   sec   112 MBytes   942 Mbits/sec    0    376 KBytes     
and one of xfers had 35 retries. I reran it with your setup and it was still 932+ Mbps.

To see issues with the routing table:
```
route -n 
```
or 
```
ip route | column -t
```

---

### Post by The Cog on 2021-04-29
It may be worth running the command ```
ip link -s -s
``` and see if there are any errors.

---

### Post by dinkidonk on 2021-04-29
What type of storage is used on your Linux system? If it is encrypted, how? Have you verified that your Linux system actually has a gigabit connection to the (I assume) router? Even if a cable is rated for gigabit, cheap (or really long) ones will not allow more than 100M. Maybe try with a cable you know will allow gigabit bandwidth.

---

### Post by TheFu on 2021-04-29
On 20.04, I just setup a samba server.
```
sudo apt install samba
sudo ufw allow  samba
```

Added a local samba user using smbpasswd
```
sudo smbpasswd -L -a thefu
```

Edited the smb.conf file:
sudoedit /etc/samba/smb.conf

Left everything as default, except ... 
```
[global]
   workgroup = MyWorkGroupNameNotYours
...
   client min protocol = SMB2
   min protocol = SMB2
   server signing = mandatory

[homes]
   comment = Home Directories
   hosts allow = 127.0.0.1 172.22.22.0/24
   hosts deny = 0.0.0.0/0
   browseable = yes
   guest ok = no
   writable = yes
   create mask = 0640
   directory mask = 0750
   valid users = %S
```

Restart samba.
```
sudo service smbd restart
```

Changed to Windows.  In the URL textentry field, put in [FONT=Courier New]\\regulus\thefu <enter>[/FONT]
was prompted to enter a username and password.  Filled those in.  My network has a DNS server, so regulus lookup is automatic. Use the IP if that doesn't work on your network.

Then searched for files to to copy - larger sized files will have less overhead - found some home movies and copied about 2GB of files.  Saw 50-54 MB/sec.  That's 400 Mbps ... the target storage is an SSD with ext4 on LVM. Tests to a WD-Blue HDD showed the same throughput.

That's the total effort involved. Nothing else. I checked my command history.  If that doesn't work for you, I don't know.  Maybe purge samba and start over with an empty /etc/samba/?

---

### Post by Tadaen_Sylvermane on 2021-04-29
I know people love to do custom configs and stuff and I'm sure they do make a difference. I find minimal changes to stock unless absolutely necessary. That being said have you tried an unmodified as installed smb.conf with only the minimum required for your shares? I was getting 90MBs to my server when it was in my house over ethernet. Now across the yard via wireless bridge it maxes transfer speed at around 50-60MBs. Still well ahead of yours. My config is as stock as it gets save for adding my specific snapraid pool share. The only files that really take long enough to get a read  are 1-2 gig ripped dvd mkvs.

*EDIT* Sorry. TheFu beat me to it.

*EDIT 2* Just had an idea. I know you ran a command to show the interfaces and tried a different cable. Post the output of

```
sudo ethtool "$INTERFACE" | grep Speed
```

That should tell you the current negotiated speed. 11MBs is about the max on a 10/100 line so I can't help but wonder about that. Theoretically the rj45 port could be bad and even though it reads the chip as a gigabit nic it only negotiates at 10/100.

It's a reach I suppose. I did spend about 20 minutes chasing down a problem with my headphones today only to discover that I had plugged the 3.5 mic plug into the ear plug and vice versa. They were fine the whole time. In your case, maybe you are looking at the wrong light?

---

### Post by Morbius1 on 2021-04-30
> **Tadaen_Sylvermane said:**
> I know people love to do custom configs and stuff and I'm sure they do make a difference. I find minimal changes to stock unless absolutely necessary. 
Yep, I'm right there with you. Especially in this case since had the OP run testparm on his smb.conf he would have received an unusually long warning:
> WARNING: The "allocation roundup size" option is deprecated
Loaded services file OK.
WARNING: socket options = TCP_NODELAY SO_RCVBUF=131072 SO_SNDBUF=131072 SO_KEEPALIVE IPTOS_THROUGHPUT
This warning is printed because you set one of the
following options: SO_SNDBUF, SO_RCVBUF, SO_SNDLOWAT,
SO_RCVLOWAT
Modern server operating systems are tuned for
high network performance in the majority of situations;
when you set 'socket options' you are overriding those
settings.
Linux in particular has an auto-tuning mechanism for
buffer sizes (SO_SNDBUF, SO_RCVBUF) that will be
disabled if you specify a socket buffer size. This can
potentially cripple your TCP/IP stack.

Getting the 'socket options' correct can make a big
difference to your performance, but getting them wrong
can degrade it by just as much. As with any other low
level setting, if you must make changes to it, make
 small changes and test the effect before making any
large changes.

I'm not very good at this aspect of samba since it's never been a problem - at least not to the extent detailed here. About the only time I did do something was for one particular user in which I had him add the following:
```
socket options = IPTOS_LOWDELAY TCP_NODELAY 
```
And only because the samba documentation suggested it.

It made a difference but nothin' to write home about.

---

### Post by mike4ubuntu on 2021-05-03
Some good suggestions on what to look at for sure.  I took TheFU's minimal conf suggestion and surprisingly it made no apparent difference in performance.  Which is a big indication that the conf settings I was experimenting with are unnecessary.  It looks like I didn't mention that the shared folder drives on the SAMBA server are actually encrypted.  I guess I should expect that to impact performance to some degree.  However, the shared folder on the Windows 10 server is encrypted also, and writing to that folder from a remote client still gets about 100 MBytes/sec.  I'm going to try to mount another unencrypted disk to see if there's a bit of an impact.  I should have thought of that earlier.

some of the suggested network analysis:
```

sudo ethtool enp7s0 | grep Speed
	Speed: 1000Mb/s

```

network config: I am only using one ethernet port, enp7s0
```

ifconfig
enp6s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether ...  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device memory 0xfa300000-fa37ffff  

enp7s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 10.1.10.20  netmask 255.255.0.0  broadcast 10.1.255.255
        ...  prefixlen 64  scopeid 0x20<link>
        ether ...  txqueuelen 1000  (Ethernet)
        RX packets 53723907  bytes 77409275233 (77.4 GB)
        RX errors 0  dropped 806  overruns 728  frame 0
        TX packets 20634883  bytes 18238685671 (18.2 GB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device memory 0xfa200000-fa27ffff  

```
All of the Windows, MacOS, and Linux SAMBA serves are going through the same netgear gs108 gigabit switch that is up-linked to an orbi router extension to a verizon router.
```

route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.1.10.1       0.0.0.0         UG    100    0        0 enp7s0
10.1.0.0        0.0.0.0         255.255.0.0     U     100    0        0 enp7s0
10.1.0.0        0.0.0.0         255.255.0.0     U     100    0        0 enp7s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp7s0

```

---

### Post by dinkidonk on 2021-05-04
If you are using a managed router, try to enter the settings of the router and see if the link speed for the slow performing system is as it should be. On my NETGEAR router, the information is located under "Advanced -> Internet Port -> Show Statistics" and reads "1000M/Full" under "Status" for devices with gigabit connection.

---

### Post by mike4ubuntu on 2021-05-04
> **dinkidonk said:**
> If you are using a managed router, try to enter the settings of the router and see if the link speed for the slow performing system is as it should be. On my NETGEAR router, the information is located under "Advanced -> Internet Port -> Show Statistics" and reads "1000M/Full" under "Status" for devices with gigabit connection.
no, The GS 108 is just an unmanaged 8-port switch.  There are no settings like that.  The LEDs indicate that all of the servers connected to it are connected at 1Gbps.  Again, the MacOS and the Win10 serves seem to communicate with each other at 1Gbps (100MBps), but the LINUX servers are slow.  I thought it was just SAMBA, but now I believe it's probably the ethernet connection.  The disks are encrypted with LUKS, which may be contributing to it, but I haven't mounted an unencrypted disk to test that yet.

---

### Post by TheFu on 2021-05-04
LUKS encryption is ~ 3% overhead, but it could be higher on systems without AES CPU extensions.  That would explain why sftp is slow too.  sftp is expected to be slower than samba or NFS since sftp has encryption and the others usually do not.

I'd suggest stepping back.  
This isn't a samba problem. 
It is a networking problem.  The iperf3  tests proved that last week. Post#12 shows the type of iperf performance that should be seen.  Looks like the network there is only seeing 10% of the bandwidth.

Things to check:
[LIST]
[*]NIC drivers or driver setting issues
[*]Firewalls
[*]Bad routing
[*]Other hardware failure
[*]Try booting from older "Try Ubuntu" ISO files.
[/LIST]

If possible, start with an overview of the system.  **inxi** is a great tool at looking at hardware. So is **lshw**.
**inxi -Fz** - provides an overview of the system and filters sensitive stuff.
**inxi -Nnxz** - gets detailed networking information and filters sensitive stuff.

Adding more 'x' to any command provides more details. I've seen *-Fxxxz* used.
'z' filters sensitive stuff.

When I look at the routing table provided above, there is a duplicate line. Could that be causing issues?

---

### Post by dinkidonk on 2021-05-04
In #14 I suggested that a bad ethernet cable could be the culprit, did you try another cable that is known to be good for gigabit?

---

### Post by mike4ubuntu on 2021-05-12
Yeah, I tried a bunch of cables.  I even swapped in the cables from the MacOS and Win10 servers that seem to have better performance.  Nothing changed.  However, I think you guys are right that it is really a network performance issue. I going to load Ubuntu 20.04 and 21.04 onto another server with a newer ASUS motherboard next week.  The SAMBA server is running 20.04 on an old X99 motherboard, but he LAN drivers seem to be the latest for the Intel I218-V Ethernet ports.

The duplicate entry in the routing table is kind of strange, but that was the default since installation.  Could be a result of having multiple ethernet ports on the motherboard, though.  I also see that on other X99 motherboards with multiple ports.

---

### Post by TheFu on 2021-05-12
> Intel I218-V Ethernet
Hummmm. Aren't there serious driver issues with that hardware?

Also, I would just boot from a Try Ubuntu Flash drive with a different release version to see if the performance is tied to 1 specific release (i.e. kernel). Takes about 3 minutes to create a flash drive like that.  You can install samba, iperf3, inxi, lshw, and whatever else you need into those "Try Ubuntu" environments too. The installed programs are lost at reboot, but for quick testing that doesn't matter.

If only 1 NIC has a link, then there should only be one table entry per LAN and 1 for the gateway and 1 for localhost, lo.  Delete the extra one. Yours is showing 2 lines for the same NIC interface. That isn't good.

---

### Post by mike4ubuntu on 2021-05-13
> **TheFu said:**
> Hummmm. Aren't there serious driver issues with that hardware?
Is it all Intel NIC drivers or just specially for I218?

---

### Post by TheFu on 2021-05-13
i218

I have no issues at all with i210, i211 or Intel PRO/1000 drivers.  These are usually igb and e1000e drivers.

In theory, the i218 device should be using the e1000e driver. 
[https://www.intel.com/content/www/us/en/support/articles/000005480/ethernet-products.html](https://www.intel.com/content/www/us/en/support/articles/000005480/ethernet-products.html)

So you'll want to validate that.  Lots of different ways - inxi -Nxx, lshw, lspci, ... Pay attention to the exact 3rd+ level versioning of the adapter and the driver. Really don't want to manually build and load a driver if that can be avoided.  It would almost be better if the NIC was faulty.  $25 for a new NIC makes this go away.

---

### Post by mike4ubuntu on 2021-05-25
> **TheFu said:**
> i218

I have no issues at all with i210, i211 or Intel PRO/1000 drivers.  These are usually igb and e1000e drivers.

In theory, the i218 device should be using the e1000e driver. 
[https://www.intel.com/content/www/us/en/support/articles/000005480/ethernet-products.html](https://www.intel.com/content/www/us/en/support/articles/000005480/ethernet-products.html)

So you'll want to validate that.  Lots of different ways - inxi -Nxx, lshw, lspci, ... Pay attention to the exact 3rd+ level versioning of the adapter and the driver. Really don't want to manually build and load a driver if that can be avoided.  It would almost be better if the NIC was faulty.  $25 for a new NIC makes this go away.

Sorry for the delay.  I got sidetracked with other issues.  I began exploring the driver issue along with a new nic.  I bought a cheap Startech ST1000SPEXI, which uses the i210 chipset.  Unfortunately, that didn't seem to make a difference according to iperf3.   That adapter does appear to be using the igb driver.
lshw
```
              *-network
                description: Ethernet interface
                product: I210 Gigabit Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: enp4s0
                version: 03
                serial: e8:ea:6a:09:5a:ec
                size: 1Gbit/s
                capacity: 1Gbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=igb driverversion=5.6.0-k duplex=full firmware=3.25, 0x800005cd ip=10.1.10.20 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
                resources: irq:37 memory:fa200000-fa2fffff ioport:c000(size=32) memory:fa300000-fa303fff memory:fa100000-fa1fffff

```
ifconfig
```
enp4s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 10.1.10.20  netmask 255.255.0.0  broadcast 10.1.255.255
        inet6 fe80::5b6d:1f8f:31ea:34c1  prefixlen 64  scopeid 0x20<link>
        ether e8:ea:6a:09:5a:ec  txqueuelen 1000  (Ethernet)
        RX packets 1302083  bytes 1796853540 (1.7 GB)
        RX errors 0  dropped 10  overruns 0  frame 0
        TX packets 625493  bytes 63957974 (63.9 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device memory 0xfa200000-fa2fffff  

```
```
iperf3 -V -b 1Gbps -c 10.1.10.50
iperf 3.7
Linux lic2u 5.8.0-53-generic #60~20.04.1-Ubuntu SMP Thu May 6 09:52:46 UTC 2021 x86_64
Control connection MSS 1460
Time: Tue, 25 May 2021 14:24:01 GMT
Connecting to host 10.1.10.50, port 5201
      Cookie: kjzq2ygg5zytxko5ylywbxsrhul63r2qoarf
      TCP MSS: 1460 (default)
      Target Bitrate: 1000000000
[  5] local 10.1.10.20 port 38898 connected to 10.1.10.50 port 5201
Starting Test: protocol: TCP, 1 streams, 131072 byte blocks, omitting 0 seconds, 10 second test, tos 0
[ ID] Interval           Transfer     Bitrate         Retr  Cwnd
[  5]   0.00-1.00   sec  1.54 MBytes  13.0 Mbits/sec    0   61.3 KBytes       
[  5]   1.00-2.00   sec  1.35 MBytes  11.3 Mbits/sec    0   61.3 KBytes       
[  5]   2.00-3.00   sec  1.38 MBytes  11.5 Mbits/sec    0   61.3 KBytes       
[  5]   3.00-4.00   sec  1.50 MBytes  12.6 Mbits/sec    0   61.3 KBytes       
[  5]   4.00-5.00   sec  1.35 MBytes  11.3 Mbits/sec    0   61.3 KBytes       
[  5]   5.00-6.00   sec  1.47 MBytes  12.3 Mbits/sec    0   61.3 KBytes       
[  5]   6.00-7.00   sec  1.35 MBytes  11.3 Mbits/sec    0   61.3 KBytes       
[  5]   7.00-8.00   sec  1.47 MBytes  12.3 Mbits/sec    0   61.3 KBytes       
[  5]   8.00-9.00   sec  1.35 MBytes  11.3 Mbits/sec    0   61.3 KBytes       
[  5]   9.00-10.00  sec  1.35 MBytes  11.3 Mbits/sec    0   61.3 KBytes       
- - - - - - - - - - - - - - - - - - - - - - - - -
Test Complete. Summary Results:
[ ID] Interval           Transfer     Bitrate         Retr
[  5]   0.00-10.00  sec  14.1 MBytes  11.8 Mbits/sec    0             sender
[  5]   0.00-10.00  sec  13.8 MBytes  11.6 Mbits/sec                  receiver
CPU Utilization: local/sender 1.2% (0.1%u/1.1%s), remote/receiver 0.0% (0.0%u/0.0%s)
snd_tcp_congestion cubic

iperf Done.

```
which is even slower than a NUC10 I have connected with wifi
```
NUC10 running Wifi:
[  4] local 10.1.10.205 port 60992 connected to 10.1.10.50 port 5201
Starting Test: protocol: TCP, 1 streams, 131072 byte blocks, omitting 0 seconds, 10 second test
[ ID] Interval           Transfer     Bandwidth
[  4]   0.00-1.00   sec  28.5 MBytes   238 Mbits/sec
[  4]   1.00-2.00   sec  31.1 MBytes   261 Mbits/sec
[  4]   2.00-3.00   sec  31.5 MBytes   264 Mbits/sec
[  4]   3.00-4.01   sec  34.9 MBytes   292 Mbits/sec
[  4]   4.01-5.00   sec  35.8 MBytes   301 Mbits/sec
[  4]   5.00-6.00   sec  34.4 MBytes   288 Mbits/sec
[  4]   6.00-7.00   sec  35.4 MBytes   297 Mbits/sec
[  4]   7.00-8.00   sec  32.9 MBytes   276 Mbits/sec
[  4]   8.00-9.01   sec  32.0 MBytes   268 Mbits/sec
[  4]   9.01-10.00  sec  34.6 MBytes   291 Mbits/sec
- - - - - - - - - - - - - - - - - - - - - - - - -
Test Complete. Summary Results:
[ ID] Interval           Transfer     Bandwidth
[  4]   0.00-10.00  sec   331 MBytes   278 Mbits/sec                  sender
[  4]   0.00-10.00  sec   331 MBytes   278 Mbits/sec                  receiver
CPU Utilization: local/sender 18.6% (2.3%u/16.2%s), remote/receiver 0.0% (0.0%u/0.0%s)
```According, to this, it would just be better to put a Wifi card into the SAMBA server.  To verify, I copied a 250GB file from another Windows server to the NUC10 running Win 10 as well, and got 50MBytes/sec pretty consistently.

---

### Post by TheFu on 2021-05-25
Back to checking the CAT5e cable, switch ports, routing tables?
11.3 Mbits/sec seems very much like 100 base-tx speeds.  Are you 100% certain the cable is CAT5e or better?  Have you checked the switch ports?

Have you tried booting a "Try Ubuntu" from an 18.04 release?  Then install iperf3 and re-run the tests.  That would tell us if it is something about the 20.04 install or not. It would also point towards a hardware issue if the performance on 18.04 was bad too.  Could also try a "Try Ubuntu" 20.04 boot environment to see if the install is the issue. If the "Try Ubuntu" environments provide good performance then you'll know the HW is fine.

---

### Post by HermanAB on 2021-05-25
Check the ethernet configuration with ethtool to see whether it is indeed in Gigabit full duplex mode.

[https://linuxhint.com/ethtool_commands_examples/](https://linuxhint.com/ethtool_commands_examples/)

---

### Post by mike4ubuntu on 2021-05-26
> **HermanAB said:**
> Check the ethernet configuration with ethtool to see whether it is indeed in Gigabit full duplex mode.

[https://linuxhint.com/ethtool_commands_examples/](https://linuxhint.com/ethtool_commands_examples/)

Yeah, I've tried swapping cables with faster running systems and checking the LEDs on the switch which indicate 1000Mbps.  I even put in an Asus 10-Gigabit XG-c100c NIC.  The ethertool gives this:
```
sudo ethtool enp4s0
Settings for enp4s0:
	Supported ports: [ TP ]
	Supported link modes:   100baseT/Full 
	                        1000baseT/Full 
	                        10000baseT/Full 
	                        2500baseT/Full 
	                        5000baseT/Full 
	Supported pause frame use: Symmetric Receive-only
	Supports auto-negotiation: Yes
	Supported FEC modes: Not reported
	Advertised link modes:  100baseT/Full 
	                        1000baseT/Full 
	                        10000baseT/Full 
	                        2500baseT/Full 
	                        5000baseT/Full 
	Advertised pause frame use: Symmetric
	Advertised auto-negotiation: Yes
	Advertised FEC modes: Not reported
	Speed: 1000Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	MDI-X: Unknown
	Supports Wake-on: pg
	Wake-on: g
	Current message level: 0x00000005 (5)
			       drv link
	Link detected: yes

```
Yesterday, when I ran iperf3 with this NIC, I was still only getting ~10MBytes/sec transfer speed.  Today I got this:
```
iperf3 -V -b 1Gbps -c 10.1.10.50
iperf 3.7
Linux lic2u 5.8.0-53-generic #60~20.04.1-Ubuntu SMP Thu May 6 09:52:46 UTC 2021 x86_64
Control connection MSS 1460
Time: Wed, 26 May 2021 15:07:42 GMT
Connecting to host 10.1.10.50, port 5201
      Cookie: nrx2trv7dsa3zolebtkl7dsgqglo3q6vsg3f
      TCP MSS: 1460 (default)
      Target Bitrate: 1000000000
[  5] local 10.1.10.20 port 34642 connected to 10.1.10.50 port 5201
Starting Test: protocol: TCP, 1 streams, 131072 byte blocks, omitting 0 seconds, 10 second test, tos 0
[ ID] Interval           Transfer     Bitrate         Retr  Cwnd
[  5]   0.00-1.00   sec  6.20 MBytes  52.0 Mbits/sec    0    439 KBytes       
[  5]   1.00-2.00   sec  3.62 MBytes  30.4 Mbits/sec    0    439 KBytes       
[  5]   2.00-3.00   sec  3.62 MBytes  30.4 Mbits/sec    0    439 KBytes       
[  5]   3.00-4.00   sec  3.50 MBytes  29.4 Mbits/sec    0    439 KBytes       
[  5]   4.00-5.00   sec  3.50 MBytes  29.4 Mbits/sec    0    439 KBytes       
[  5]   5.00-6.00   sec  3.50 MBytes  29.4 Mbits/sec    0    439 KBytes       
[  5]   6.00-7.00   sec  3.62 MBytes  30.4 Mbits/sec    0    439 KBytes       
[  5]   7.00-8.00   sec  3.50 MBytes  29.4 Mbits/sec    0    439 KBytes       
[  5]   8.00-9.00   sec  3.50 MBytes  29.4 Mbits/sec    0    439 KBytes       
[  5]   9.00-10.00  sec  3.50 MBytes  29.4 Mbits/sec    0    439 KBytes       
- - - - - - - - - - - - - - - - - - - - - - - - -
Test Complete. Summary Results:
[ ID] Interval           Transfer     Bitrate         Retr
[  5]   0.00-10.00  sec  38.1 MBytes  31.9 Mbits/sec    0             sender
[  5]   0.00-10.00  sec  36.6 MBytes  30.7 Mbits/sec                  receiver
CPU Utilization: local/sender 1.4% (0.4%u/0.9%s), remote/receiver 0.1% (0.0%u/0.1%s)
snd_tcp_congestion cubic

iperf Done.

```
which is not quite where it should be, but better.  Not sure why the difference from day to day.
  The next step is to use the "Try Ubuntu" thunbdrives to see if there is some kind of configuration issue with the current servers.  This issue seems to affect both Ubuntu 20.04 systems running on X99 Motherboards.

---

### Post by TheFu on 2021-05-26
> **TheFu said:**
>  
Have you tried booting a "Try Ubuntu" from an 18.04 release?  Then install iperf3 and re-run the tests.  That would tell us if it is something about the 20.04 install or not. It would also point towards a hardware issue if the performance on 18.04 was bad too.  Could also try a "Try Ubuntu" 20.04 boot environment to see if the install is the issue. If the "Try Ubuntu" environments provide good performance then you'll know the HW is fine.

And?

---

### Post by HermanAB on 2021-05-26
What kind of ethernet switch do you have between the hosts?  Try iperf with a straight wire connection, no ethernet switch.

You should also look at the data packets with tcpdump, since that way, you will quickly see whether there is a misconfiguration, duplicate addresses, an ethernet loop, or whether someone is running a spam server or a bitcoin miner or whatever nefarious packets, over your network and clogging up the pipes.

---

### Post by mike4ubuntu on 2021-05-26
> **TheFu said:**
> ...Have you tried booting a "Try Ubuntu" from an 18.04 release?  Then install iperf3 and re-run the tests.  That would tell us if it is something about the 20.04 install or not. It would also point towards a hardware issue if the performance on 18.04 was bad too.  Could also try a "Try Ubuntu" 20.04 boot environment to see if the install is the issue. If the "Try Ubuntu" environments provide good performance then you'll know the HW is fine.
Wow, ok, looks to be a config issue.  Can't imagine what config item it would be, but I booted up "20.04 Try Ubuntu" and sure enough full speed:
```
mike@ubuntu:~$ iperf3 -V -b 1Gbps -c 10.1.10.50
iperf 3.7
Linux ubuntu 5.4.0-42-generic #46-Ubuntu SMP Fri Jul 10 00:24:02 UTC 2020 x86_64
Control connection MSS 1460
Time: Wed, 26 May 2021 19:15:50 GMT
Connecting to host 10.1.10.50, port 5201
      Cookie: 6kslwsuq5zaz2sf3zzh37rug5z4m75s2twnf
      TCP MSS: 1460 (default)
      Target Bitrate: 1000000000
[  5] local 10.1.10.20 port 56954 connected to 10.1.10.50 port 5201
Starting Test: protocol: TCP, 1 streams, 131072 byte blocks, omitting 0 seconds, 10 second test, tos 0
[ ID] Interval           Transfer     Bitrate         Retr  Cwnd
[  5]   0.00-1.00   sec   114 MBytes   956 Mbits/sec    0    218 KBytes       
[  5]   1.00-2.00   sec   113 MBytes   949 Mbits/sec    0    218 KBytes       
[  5]   2.00-3.00   sec   113 MBytes   949 Mbits/sec    0    218 KBytes       
[  5]   3.00-4.00   sec   113 MBytes   949 Mbits/sec    0    218 KBytes       
[  5]   4.00-5.00   sec   113 MBytes   950 Mbits/sec    0    218 KBytes       
[  5]   5.00-6.00   sec   113 MBytes   949 Mbits/sec    0    218 KBytes       
[  5]   6.00-7.00   sec   113 MBytes   949 Mbits/sec    0    218 KBytes       
[  5]   7.00-8.00   sec   113 MBytes   949 Mbits/sec    0    218 KBytes       
[  5]   8.00-9.00   sec   113 MBytes   950 Mbits/sec    0    218 KBytes       
[  5]   9.00-10.00  sec   113 MBytes   949 Mbits/sec    0    218 KBytes       
- - - - - - - - - - - - - - - - - - - - - - - - -
Test Complete. Summary Results:
[ ID] Interval           Transfer     Bitrate         Retr
[  5]   0.00-10.00  sec  1.11 GBytes   950 Mbits/sec    0             sender
[  5]   0.00-10.00  sec  1.10 GBytes   949 Mbits/sec                  receiver
CPU Utilization: local/sender 2.7% (0.1%u/2.5%s), remote/receiver 0.0% (0.0%u/0.0%s)
snd_tcp_congestion cubic

iperf Done.

```
Now comes the harder part, to find out which config item is guilty of the degradation.
Thanks very much.  I wouldn't have guessed it without your help.  Besides blaming SAMBA initially for it, I was guessing maybe hardware after SAMBA.

---

### Post by mike4ubuntu on 2021-05-29
Finally determined the cause of this network bandwidth degradation.  It was caused by a large IPv4 IPTABLES rules file.  The SAMBA servers aren't directly accessible by outside world anyway, so they don't need such a large rules file.  They just need the basic UFW rules for only allowing access from local private network.  Next step is to determine how many rules cause the degradation or what is a reasonable threshold before degradation is a serious factor.  Thanks for all you help in tracking this issue down.

---

### Post by HermanAB on 2021-05-29
With iptables, deny everything, then allow the two or three ports that you need to have.  That's it.

---

### Post by TheFu on 2021-05-29
> **mike4ubuntu said:**
> Finally determined the cause of this network bandwidth degradation.  It was caused by a large IPv4 IPTABLES rules file.  The SAMBA servers aren't directly accessible by outside world anyway, so they don't need such a large rules file.  They just need the basic UFW rules for only allowing access from local private network.  Next step is to determine how many rules cause the degradation or what is a reasonable threshold before degradation is a serious factor.  Thanks for all you help in tracking this issue down.

Use **ipset** when you need lots of individual subnets blocked to create a single **iptable** rule.  As soon as there are more than 100 rules, I switch to ipset.

---

### Post by TheFu on 2021-05-29
$ wc -l /etc/ipset.up.rules
6957 /etc/ipset.up.rules

so this machine has nearly 7K rules.  iperf3 running to it as a server:

$ iperf3 -c blog44
 ... 
well, that didnt work. Guess the firewall is working? ;) Let me open port 5201 and try again.
```
$ sudo ufw allow 5201
Rule added
$ iperf3 -s

```

And from the client machine:
```
$ iperf3 -c blog44
Connecting to host blog44, port 5201
[  4] local 172.22.22.6 port 54236 connected to 172.22.22.44 port 5201
[ ID] Interval           Transfer     Bandwidth       Retr  Cwnd
[  4]   0.00-1.00   sec  3.54 GBytes  30.4 Gbits/sec    0   3.09 MBytes       
[  4]   1.00-2.00   sec  4.06 GBytes  34.9 Gbits/sec    0   3.09 MBytes       
[  4]   2.00-3.00   sec  4.12 GBytes  35.4 Gbits/sec    0   3.09 MBytes       
[  4]   3.00-4.00   sec  3.63 GBytes  31.2 Gbits/sec    0   3.09 MBytes       
[  4]   4.00-5.00   sec  3.55 GBytes  30.5 Gbits/sec    0   3.09 MBytes       
[  4]   5.00-6.00   sec  3.58 GBytes  30.7 Gbits/sec    0   3.09 MBytes       
[  4]   6.00-7.00   sec  3.55 GBytes  30.5 Gbits/sec    0   3.09 MBytes       
[  4]   7.00-8.00   sec  3.62 GBytes  31.1 Gbits/sec    0   3.09 MBytes       
[  4]   8.00-9.00   sec  3.57 GBytes  30.7 Gbits/sec    0   3.09 MBytes       
[  4]   9.00-10.00  sec  3.89 GBytes  33.4 Gbits/sec    0   3.09 MBytes       
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bandwidth       Retr
[  4]   0.00-10.00  sec  37.1 GBytes  31.9 Gbits/sec    0             sender
[  4]   0.00-10.00  sec  37.1 GBytes  31.9 Gbits/sec                  receiver

iperf Done.
```
Oops.  That's from the same physical machine - different virtual machine.  Let's try another machine on the network.
```
$ iperf3 -c blog44
Connecting to host blog44, port 5201
[  4] local 172.22.22.4 port 41690 connected to 172.22.22.44 port 5201
[ ID] Interval           Transfer     Bandwidth       Retr  Cwnd
[  4]   0.00-1.00   sec   114 MBytes   955 Mbits/sec    0    378 KBytes       
[  4]   1.00-2.00   sec   112 MBytes   941 Mbits/sec    0    378 KBytes       
[  4]   2.00-3.00   sec   112 MBytes   941 Mbits/sec    0    378 KBytes       
[  4]   3.00-4.00   sec   112 MBytes   941 Mbits/sec    0    378 KBytes       
[  4]   4.00-5.00   sec   112 MBytes   941 Mbits/sec    0    378 KBytes       
[  4]   5.00-6.00   sec   112 MBytes   943 Mbits/sec    0    417 KBytes       
[  4]   6.00-7.00   sec   112 MBytes   941 Mbits/sec    0    417 KBytes       
[  4]   7.00-8.00   sec   112 MBytes   941 Mbits/sec    0    417 KBytes       
[  4]   8.00-9.00   sec   112 MBytes   941 Mbits/sec    0    417 KBytes       
[  4]   9.00-10.00  sec   113 MBytes   948 Mbits/sec    0    571 KBytes       
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bandwidth       Retr
[  4]   0.00-10.00  sec  1.10 GBytes   943 Mbits/sec    0             sender
[  4]   0.00-10.00  sec  1.10 GBytes   941 Mbits/sec                  receiver

iperf Done.
```

940-ish Mbps.  Good enough.
109.168.161.4 is
Here's what the single iptables rule looks like that uses ipset:
```
$ sudo iptables -L |grep count
DROP       all  --  anywhere             anywhere             match-set countryblock src

```
And to test which source IPs are being blocked, ipset has a test capability:
```
$ sudo ipset test countryblock 109.168.161.4
109.168.161.4 is in set countryblock.

```
Sorry to the good people in that netblock, but there are some nasty servers there too. All traffic from there is dropped. Period. Only for about 3 minutes, every 3 months, do I relax the blocks so that let's encrypt certs can be renewed. About 18 months ago, LE decided to require testing of access from multiple locations around the world. For a little time, I tried to figure out where those would be, but they changed and I figured for the time it took to renew, my risks were tiny. I could have switched to DNS as the domain validation method, but I've outsourced DNS and modifying it is a hassle.

Anyways, ipset is the method you want. I read that it scales to huge lists. Just make a different "named" ipset for each rule you need.

---

### Post by mike4ubuntu on 2021-05-29
> **TheFu said:**
> Use **ipset** when you need lots of individual subnets blocked to create a single **iptable** rule.  As soon as there are more than 100 rules, I switch to ipset.
Yeah, we use ipset for very specific sets like SPAMHAUS and some others.  However, the main rule set was setup some time ago for all the different country ranges, plus many single addresses for high spam/bad repeaters detected over time.  There are over a 100K rules.  Overly complicated to say the least.  The list needs to be paired down for sure.  We initially took the approach to block certain countries and geographical regions, and then left everything open, and then creating our own black lists of single addresses that seemed to cause problems.  A lot of it was automated and consequently created a large numbers of rules, because lets face, there are a lot of bad actors in the internet world that are constantly port scanning and trying to hack in to anything connected to the internet.

---

### Post by TheFu on 2021-05-29
For email, I have a gateway email server that does all the blocking in/out.  It doesn't actually hold any email.  Just does blocking and filtering.

Scaling the gatway up or out isn't hard.  Think it is using just 384MB of RAM now.  I don't block entire country subnets from email, but I do not block single IPs either.  Spammers get shut down every week, so having individual IPs longer than 1 week probably isn't very useful.  Perhaps having 6 months of blocks in a rotation would make sense?  Just add the daily spammers into an ipset file, then add up those daily files into 25 weekly files. The scripting ain't hard for that.
When the iptables are loaded using match-set, modifying the ipset block has immediate impact without touching the iptables at all.
Have 26 weekly files. That would get a rolling 25-26 weeks of blocked lists - about half a year. Just shift each week the file up one number. Append new subnets/ips to the current ipset block.  There are different hash types for subnet and single IPs, so once the permanent subnet blocks are known and saved, then all the others will be individual IPs?

Of course, I don't do this myself. My spam blocks are usually around violation of SPF rules or stupid new domains like .icu, .surf or .click.  I also decided to block email from anyone claiming to be from .cn or .ru or .gq domains.  Other bad things in the email headers are clues for spam too - old User-Agents, bogus charsets, stuff like that.  Who in the world would use Outlook Express today?  Nobody except spammers.

Of all the rules, I feel the worse about 1 clothing vendor who I like, but they just won't stop spamming.  They make great, thick, t-shirts. Very comfortable, but I've been unable to get their spam to stop.  9 spam message since May 24.  27 the week before that.  These are just to me.  I only keep 4 weeks of mail logs. In a larger business, perhaps 4-6 months of logs would be desired?

---

### Post by HermanAB on 2021-05-30
IMHO if you need hundreds of iptables rules, then you are doing it wrong.

Regarding Email Spam, years ago I noticed that the faster my server, the more spam I get.  I then added a 1 second delay into my postfix server, which made it react like a very lame and overloaded machine.  It caused spam to drop to next to nothing.  Nowadays, this technique is called a greylisting delay and it is a regular Postfix feature.  [https://help.ubuntu.com/community/PostfixGreylisting](https://help.ubuntu.com/community/PostfixGreylisting)

Between greylisting and a few RBLs, you can make spam practically go away, with very little effort on your part.

---

### Post by piperun on 2021-11-07
I would recommend against adding "fancy" config options to samba since afaik playing around with socket option is usually going to result in a net-loss rather than a net-gain (according to [smb.conf ]("https://www.samba.org/samba/docs/current/man-html/smb.conf.5.html#SOCKETOPTIONS")).
The only settings from my testing I've noticed a performance gain is:
```

use sendfile = yes # around 1% transfer speed increase
interfaces = "#.#.#.#;capability=RSS,speed=10000000000" # 10% transfer speed increase

```

Also when I tried:
```

aio read size = 16384
aio write size = 16384

```
It made the transfer in the beginning slower.

```

write cache size = 262144

```
Seems to be deprecated or at least there's no documentation (anymore).

If you got 2 NICs you could try multi channel.

---

### Post by hk42 on 2021-11-08
Even on very old devices provided they have gigabit Ethernet I get at least twice  that speed and it is the processor that limits it.
The main advantage of samba is that it allows easy sharing of data between lots of devices:
Android , Linux ,TV's ,Wxp ,etc.
If you want to access an Ext4 partition from those samba is the easy solution.

---

