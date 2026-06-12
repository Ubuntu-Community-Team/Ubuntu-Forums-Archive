---
title: "Is there a step-by-step guide to transfer files between two Linux computers?"
date: 2018-03-23
forum: General Help
---

### Post by sonicking on 2018-03-23
Hi,

I have two Linux computers - one is running Mint 18.3; the other one is running Ubuntu 16.04 LTS.

Can someone provide a very detailed guide to transfer files between them via a typical Ethernet cable, if possible?

I believe I need to connect the two computers with the ethernet cable and then set up static IP addresses on both computers.  Then I can some software (such as NitroShare) to select and transfer?  

If such operation is indeed possible, I would really appreciate it if someone can explain the step-by-step procedural to me like I am a 4 year-old.  Thanks!

---

### Post by Tadaen_Sylvermane on 2018-03-24
If they are on the same network you only need the ip address of the target, then just use either scp or rsync on the command line.

---

### Post by sonicking on 2018-03-24
> **Tadaen_Sylvermane said:**
> If they are on the same network you only need the ip address of the target, then just use either scp or rsync on the command line.

Hi, thank you.  I believe what I want to do is feasible. But I would need a much more thorough explanation to perform the steps.  Could you provide those when you have time?

---

### Post by HermanAB on 2018-03-24
OK, I can try to explain it:

First, you need a cable and you need to disable NetworkDamager, since it will automatically bugger things up for you
On A and B:
$ sudo killall NetworkManager
$ sudo killall dhclient
Now connect an ethernet cable between two computers A and B.

On A:
Configure ethernet port with one address
$ sudo ifconfig eth0 192.168.1.1 netmask 255.255.255.0 up

On B:
Configure ethernet port with another address
$ sudo ifconfig eth0 192.168.1.2 netmask 255.255.255.0 up

On A:
Tell netcat to listen on port 1234 and save the incoming file
$ sudo nc -l -p 1234 > filename

On B:
Tell netcat to send the file to the other computer IP address and port number
$ sudo nc 192.168.1.1 1234 < filename

La voila!

---

### Post by SeijiSensei on 2018-03-24
[https://ubuntuforums.org/showthread.php?t=2387690&p=13751043&viewfull=1#post13751043](https://ubuntuforums.org/showthread.php?t=2387690&p=13751043&viewfull=1#post13751043)

---

### Post by Morbius1 on 2018-03-24
> Can someone provide a very detailed guide to transfer files between them via a typical Ethernet cable, if possible?

I believe I need to connect the two computers with the ethernet cable  and then set up static IP addresses on both computers.  Then I can some  software (such as NitroShare) to select and transfer?  
Are you talking about a direct connection between these two machines or is a router involved?

It's been way too long for me to remember how to do a direct connect but I think it matters in the responses you get.

---

### Post by Tadaen_Sylvermane on 2018-03-24
scp and rsync work the same way. this is the basic format

I use -auv for most things on my rsync scripts and such.
```
rsync -auv --progress /file/or/folder/to/transfer $USER@ip.address:/path/to/put/file/or/folder
```

or scp

```
scp -r /file/or/folder/to/transfer $USER@ip.address:/path/to/put/file/or/folder
```

---

### Post by sonicking on 2018-03-24
> **Morbius1 said:**
> Are you talking about a direct connection between these two machines or is a router involved?

It's been way too long for me to remember how to do a direct connect but I think it matters in the responses you get.

I would like to connect the two machines with just a typical Ethernet cable.  No router.  Thanks.

---

### Post by sonicking on 2018-03-24
> **HermanAB said:**
> OK, I can try to explain it:

First, you need a cable and you need to disable NetworkDamager, since it will automatically bugger things up for you
On A and B:
$ sudo killall NetworkManager
$ sudo killall dhclient
Now connect an ethernet cable between two computers A and B.

On A:
Configure ethernet port with one address
$ sudo ifconfig eth0 192.168.1.1 netmask 255.255.255.0 up

On B:
Configure ethernet port with another address
$ sudo ifconfig eth0 192.168.1.2 netmask 255.255.255.0 up

On A:
Tell netcat to listen on port 1234 and save the incoming file
$ sudo nc -l -p 1234 > filename

On B:
Tell netcat to send the file to the other computer IP address and port number
$ sudo nc 192.168.1.1 1234 < filename

La voila!

Thanks.  I have a question though.  If I "kill" the NetworkManager, do I need to re-enable it after I am done?  How?

Once it's connected, do you recommend to use NitroShare or any program?  I may want to share a whole folder as opposed to one or two files individually.

---

### Post by HermanAB on 2018-03-25
If you kill NetworkManager, then you got to restart it again later with:
$ sudo systemctl restart networking.service

Once connected, you can start the sshd service or a FTP server or whatever you want.  There are umpteen ways to share files.

You can even make a tar ball and transfer it with netcat.

---

### Post by sonicking on 2018-03-25
> **HermanAB said:**
> If you kill NetworkManager, then you got to restart it again later with:
$ sudo systemctl restart networking.service

Once connected, you can start the sshd service or a FTP server or whatever you want.  There are umpteen ways to share files.

You can even make a tar ball and transfer it with netcat.

Hi, I am trying things out.  

```
sudo killall NetworkManager
```

This works to stop my connection.  BUT, this below does not restart it!
```
sudo systemctl restart networking.service
```

Instead, I needed to use this line:
```
sudo service network-manager restart
```

I was able to google this on my phone. :)

I did not reboot my computer altogether.  But would both NetworkManager and dhclient restart themselves from a computer reboot????

---

### Post by HermanAB on 2018-03-25
How to restart a service depends on your version of Ubuntu - whether you use Poetering's folly or not.

If you kill a service, the computer configuration is not changed, so it will run again on the next boot.

---

### Post by sonicking on 2018-03-25
> **HermanAB said:**
> How to restart a service depends on your version of Ubuntu - whether you use Poetering's folly or not.

If you kill a service, the computer configuration is not changed, so it will run again on the next boot.

Good to know!   How about the requirement to configure the ethernet IP addresses?

```
sudo ifconfig eth0 192.168.1.1 netmask 255.255.255.0 up
```

Once I am done with all the file transfers, do I need to do anything to re-configure the IP addresses back to the way they were?  Or would a computer reboot be sufficient to make the computers the way they were???

---

### Post by sonicking on 2018-03-25
Hi, I have another update.  I did the manual step-up of IP addresses on both computers.  They were able to ping each other with the *ping* command.  When I tried to transfer a small file, it failed.

```

$scp /home/aaron/Downloads/introcast0703.pdf ann@192.168.1.1:/home/ann/Downloads
ssh: connect to host 192.168.1.1 port 22: Connection refused
lost connection
```

Any idea why? Thanks.

---

### Post by HermanAB on 2018-03-25
You need to enable sshd first.

---

### Post by sonicking on 2018-03-25
> **HermanAB said:**
> You need to enable sshd first.

Oh...what is SSHD and how to enable it?  Did I need to disable it after I am done? Thanks.

---

### Post by Dennis N on 2018-03-25
> Oh...what is SSHD and how to enable it? Did I need to disable it after I am done? Thanks. 

sshd is short for ssh daemon, whicn listens for incoming connections. Have you installed openssh-server on the remote machine? That also installs the daemon, and it would be started at startup, so after a restart sshd should be running.

And you need not disable it after the transfers.

---

### Post by sonicking on 2018-03-25
> **Dennis N said:**
> sshd is short for ssh daemon, whicn listens for incoming connections. Have you installed openssh-server on the remote machine? That also installs the daemon, and it would be started at startup, so after a restart sshd should be running.

And you need not disable it after the transfers.

No.  Unless this came with the installation, I have not installed this on either computer.  Is it easy to do so?

Also, if I want to transfer files from either computer to the other one, would I need to install this on both computers???  Thanks.

---

### Post by Dennis N on 2018-03-26
> **sonicking said:**
> No.  Unless this came with the installation, I have not installed this on either computer.  Is it easy to do so?

Also, if I want to transfer files from either computer to the other one, would I need to install this on both computers???  Thanks.

openssh-server is not installed with the default installation. Install it at least on the remote computer. The installation is all automatic in that it will work without any configuration by you. You can optionally set up some security policy configurations on who or what can log in etc. and this should be looked into since the ssh server will remain active. 

But, my only use of ssh is on a network with a router present to assign IP addresses, so I am not sure how the direct connection (called an ad hoc connection) actually would be set up. Looks like you have already been advised here how to do that - a google search turns up further advice -> here is a thread on this forum on how to set it up that was apparently successful but used samba - but that may be overkill - I would try what was suggested first.

[https://ubuntuforums.org/showthread.php?t=1167974](https://ubuntuforums.org/showthread.php?t=1167974)

---

### Post by sonicking on 2018-03-26
> **Dennis N said:**
> openssh-server is not installed with the default installation. Install it at least on the remote computer. The installation is all automatic in that it will work without any configuration by you. You can optionally set up some security policy configurations on who or what can log in etc. and this should be looked into since the ssh server will remain active. 

But, my only use of ssh is on a network with a router present to assign IP addresses, so I am not sure how the direct connection (called an ad hoc connection) actually would be set up. Looks like you have already been advised here how to do that - a google search turns up further advice -> here is a thread on this forum on how to set it up that was apparently successful but used samba - but that may be overkill - I would try what was suggested first.

[https://ubuntuforums.org/showthread.php?t=1167974](https://ubuntuforums.org/showthread.php?t=1167974)

Is Samba easier than openssh-server?  I feel like the fact that openssh-server not requiring additional configuration may be easier.  I mean, I am only sharing locally....But could someone confirm?   Thanks!

---

### Post by strixtux on 2018-03-27
There is a way for direct ethernet-to-ethernet transfer, what you need is an inverted ethernet cable which put out1 to in2 and vice versa. With a regular cable this ain't gonna work. You can get such a cable for USB as well. Might turn out much easier than readjusting all software...

---

### Post by Morbius1 on 2018-03-27
Before you run out and try to find crossover cables how old are these two machines?

From Wikipedia:
> [h=2]Automatic crossover[/h]Main article: [Medium Dependent Interface § Auto MDI-X]("https://en.wikipedia.org/wiki/Medium_Dependent_Interface#Auto_MDI-X")
 Introduced in 1998, this made the distinction between uplink and  normal ports and manual selector switches on older hubs and switches  obsolete.[SUP][[4]]("https://en.wikipedia.org/wiki/Ethernet_crossover_cable#cite_note-dove-4")[/SUP]  If one or both of two connected devices has the automatic MDI/MDI-X  configuration feature, there is no need for crossover cables.



---

### Post by Morbius1 on 2018-03-27
OK, I just did this based on Dennis N's posted link for two reasons:

[1] The procedure sounded very familiar to me.
[2] It is the least disruptive method outlined so far and easily reversed.

** I connected an Ethernet cable between two machines.
** On each machine I disconnected the network - through the network manager - and edited my connection method to Local-Link Only
** Then I enabled the Wired connection again.
** Since both Linux machines use avahi I opened up a terminal on one machine and ran:
```
thunar smb://xub1710.local
```
And I was able to connect to that machine, enter it's share, and add a file.

In your case so as to reduce your degrees of freedom I would install ssh of both machines before I started all this and connect to them with ssh not smb:
```
thunar ssh://xub1710.local
```

I am a Xubuntu user so replace:

**thunar** with whatever your file manager is called
**xub1710** with whatever your host name is called on the other machine - and don't forget to add the "**.local**" at the end.

When I was done with transferring files I reset the network method back to where it was before and restarted the network connection.

---

### Post by sonicking on 2018-03-27
Hi.  Thank you for everyone's help.  I have done what I needed.  I am going to provide my own step-by-step guide and hope the next person can benefit.

1) When both of your computers are still connected to the Internet, install openssh-server by typing in the Terminal:
```
sudo apt-get install openssh-server
```

2) Plug your Ethernet cable to both computers to link them physically.

3) Do the following on BOTH computers:

Click on the **NetworkManager** icon (the one that indicates you are connected to the Internet), you want to disconnect the Wireless connection*.  
Then you click **Network Connections** and a small window will appear.  Select the** Wired connection **under *Ethernet*. Click on the **Edit** button. Another window will appear.  Select the **IPv4 Settings** tab.  Choose **Manual** in the *Method dropdown*.  Under *Addresses*, click the **Add** button.  For computer 1, enter **192.168.1.1** in *Address* and **255.255.255.0** in *Netmask*.  Then **Save.  **For computer 2, enter **192.168.1.2** in *Address* and **255.255.255.0** in *Netmask*.  Then **Save.**

*I am not sure whether disconnecting the wireless connection is necessary.  But I did it.

4) In the Terminal, test things about by pinging each other.  On computer 2, you type:
```
$ ping 192.168.1.1
```
Then you will should see:
```
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=0.473 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.474 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=0.779 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=0.589 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=64 time=0.423 ms

```
You can stop this by hitting [B]Ctrl and C together.

[/B]Similarly, you can ping computer 2 from computer 1.

5) Now you are ready to transfer files by typing this in the Terminal
```
scp /home/aaron/Downloads/introcast0703.pdf ann@192.168.1.1:/home/ann/Downloads
```

In my command, *aaron* is the user in computer2.  *ann* is the user in computer1.  This is sending a pdf file from Aaron's computer2 to Ann's computer1.  When you enter this command, you will be asked if you want to continue connecting.  You type **yes** and hit enter.
Then you will be asked for Ann's user password on computer2.  You enter that password. 

This is all.

---

### Post by sonicking on 2018-03-27
To reinstate the computers back to their original states.

[COLOR=#000000]On the [/COLOR]**NetworkManager **icon, you want to **reconnect** the Wireless connection.
Then you click **Network Connections **and a small window will appear. Select the **Wired** connection under *Ethernet. *Click on the **Edit** button. Another window will appear. Select the **IPv4 Settings** tab. Choose **Automatic(DHCP)** in the *Method dropdown*.

---

### Post by HermanAB on 2018-03-27
Modern ethernet Phi (everything made in this century) will reverse the tx and rx wires and allow two computers to connect when using a 1:1 cable.  A cross-over cable is not needed.

---

### Post by lighthousebeacon on 2018-03-27
If it helps, I use a small utility program called FreeFileSync, to move in bulk files and folders from my main rig to backup rig. Works a treat. I know you mentioned nitroshare but just adding my 2 cents worth. Might help. Cheers

---

### Post by sonicking on 2018-03-27
> **HermanAB said:**
> Modern ethernet Phi (everything made in this century) will reverse the tx and rx wires and allow two computers to connect when using a 1:1 cable.  A cross-over cable is not needed.

Yes, I can attest to this.  I just used the free Ethernet cable from Verizon.

---

### Post by sonicking on 2019-01-26
Ok, this sucks.

The steps I posted before were working.  

Then tonight I upgraded one of the computers to Mint 19.1 (Tessa), those same steps do not work again!  

Can someone provide any suggestion???  Thanks.

---

### Post by HermanAB on 2019-01-26
Well, the least hassle method, is to ensure that sshd is running on one or both of the machines and then use scp.

---

### Post by sonicking on 2019-01-27
> **HermanAB said:**
> Well, the least hassle method, is to ensure that sshd is running on one or both of the machines and then use scp.

How exactly do I check this?  I tried to reinstall [COLOR=#000000][FONT=&quot]openssh-server[/FONT][/COLOR].  But it is already the latest version.

Also, I restored the Mint machine back to 18.3.  The problem remains.  So I think this is not due to the upgrade of the system, but something else.  Maybe one of the kernel upgrades???

---

### Post by HermanAB on 2019-01-27
See whether you can log into the machine itself:
$ ssh username@localhost

If that works, find the IP address:
$ ip addr show

Then try to log in from the other machine:
$ ssh username@ipaddress

Read the Snail Book:
[http://www.snailbook.com](http://www.snailbook.com)

La voila.

---

### Post by sonicking on 2019-01-27
> **HermanAB said:**
> See whether you can log into the machine itself:
$ ssh username@localhost

If that works, find the IP address:
$ ip addr show

Then try to log in from the other machine:
$ ssh username@ipaddress

Read the Snail Book:
[http://www.snailbook.com](http://www.snailbook.com)

La voila.

It says Permission denied.  :(

---

### Post by HermanAB on 2019-01-27
Well, it would help if you say which one of the three commands says permission denied.  

We cannot see your screen.

---

### Post by The Cog on 2019-01-27
> Read the Snail Book:
[http://www.snailbook.com](http://www.snailbook.com)
Ha! That has to be the most useless web page I have ever seen. Every link redirects to a paywall page.

@sonicking:
It helps to post both the command you type as well as the resulting output, just so we can see that you didn't mis-type the command.

---

### Post by sonicking on 2019-01-27
I plugged in the ethernet cable connecting both computers.


Computer1's authorized user is **ann**.
Computer2's user is **aaron**.


On Computer1's Terminal, I typed

```

ann@ann-Inspiron-3252:~$ ifconfig
enp3s0    Link encap:Ethernet  HWaddr 64:00:6a:11:18:8d  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::eaaa:4c12:3b5c:801e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:452 errors:0 dropped:0 overruns:0 frame:0
          TX packets:469 errors:13 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:56254 (56.2 KB)  TX bytes:57520 (57.5 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:6795 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6795 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:586481 (586.4 KB)  TX bytes:586481 (586.4 KB)


ann@ann-Inspiron-3252:~$ ssh aaron@localhost
aaron@localhost's password: 
Permission denied, please try again.
aaron@localhost's password: 


ann@ann-Inspiron-3252:~$ ip addr show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet [127.0.0.1/8]("http://127.0.0.1/8") scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp3s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 64:00:6a:11:18:8d brd ff:ff:ff:ff:ff:ff
    inet [192.168.1.1/24]("http://192.168.1.1/24") brd 192.168.1.255 scope global enp3s0
       valid_lft forever preferred_lft forever
    inet6 fe80::eaaa:4c12:3b5c:801e/64 scope link 
       valid_lft forever preferred_lft forever
3: wlp2s0: <BROADCAST,MULTICAST> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether 4c:bb:58:da:65:12 brd ff:ff:ff:ff:ff:ff
ann@ann-Inspiron-3252:~$ ssh [EMAIL="aaron@192.168.1.2"]aaron@192.168.1.2[/EMAIL]
ssh: connect to host 192.168.1.2 port 22: No route to host

```


On Computer2's Terminal, I typed

```

aaron@aaron-Aspire-E5-575 ~ $ ifconfigenp3s0f1  Link encap:Ethernet  HWaddr 54:ab:3a:80:f7:60  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:152 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:19307 (19.3 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:4883 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4883 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:459361 (459.3 KB)  TX bytes:459361 (459.3 KB)

aaron@aaron-Aspire-E5-575 ~ $ ssh ann@localhost
ann@localhost's password: 
Permission denied, please try again.
ann@localhost's password: 


aaron@aaron-Aspire-E5-575 ~ $ ip addr show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp3s0f1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 54:ab:3a:80:f7:60 brd ff:ff:ff:ff:ff:ff
3: wlp2s0: <BROADCAST,MULTICAST> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether c8:ff:28:2c:92:51 brd ff:ff:ff:ff:ff:ff

aaron@aaron-Aspire-E5-575 ~ $ ssh ann@192.168.1.1
ssh: connect to host 192.168.1.1 port 22: Network is unreachable


```

Any suggestion would be much appreciated.

---

### Post by Dennis N on 2019-01-27
> Then tonight I upgraded one of the computers to Mint 19.1 (Tessa), those same steps do not work again! Can someone provide any suggestion??? Thanks. 

I think this is the problem:

If you reinstall the OS (and the SSH-server), the security key sent from the server (host) will be different. What security key? On first connection, the client stores a security key sent from server (host) located at the IP address. Next time you try to connect, it checks the server key sent from that IP address against the already stored key to be sure the computer is the same one. In this case, it doesn't match stored key, so SSH client refuses to connect to server!

A way out is to delete the key stored in the file **~/.ssh/known_hosts** and try again.

A key is a long string like:
```
|1|/+Y7fyMU9q5Mwwj0tYQGV1SdOpc= followed by more characters
```
If you have connected to several computers in the past, each one has a key stored here. You probably have just one stored key.

---

### Post by sonicking on 2019-01-27
> **Dennis N said:**
> I think this is the problem:

If you reinstall the OS (and the SSH-server), the security key sent from the server (host) will be different. What security key? On first connection, the client stores a security key sent from server (host) located at the IP address. Next time you try to connect, it checks the server key sent from that IP address against the already stored key to be sure the computer is the same one. In this case, it doesn't match stored key, so SSH client refuses to connect to server!

A way out is to delete the key stored in the file **~/.ssh/known_hosts** and try again.

A key is a long string like:
```
|1|/+Y7fyMU9q5Mwwj0tYQGV1SdOpc= followed by more characters
```
If you have connected to several computers in the past, each one has a key stored here. You probably have just one stored key.


Yes.  I indeed see two different keys (two long texts) in this file.  Do I just manually delete all the texts and then save?

---

### Post by Dennis N on 2019-01-27
> Yes. I indeed see two different keys (two long texts) in this file. Do I just manually delete all the texts and then save? 
Yes, that would be the simplest thing to do.

---

### Post by sonicking on 2019-01-27
> **Dennis N said:**
> Yes, that would be the simplest thing to do.

Do I do this on both computers?  Or just the one that I tried to upgrade the operating system?

In the future, do I just do this every time I upgrade the OS?  

Thanks again!

---

### Post by Dennis N on 2019-01-27
> **sonicking said:**
> Do I do this on both computers?  Or just the one that I tried to upgrade the operating system? In the future, do I just do this every time I upgrade the OS?  Thanks again!
You need to do this on the client, not the one you upgraded, which is the host (server). As long as the IP address of the host doesn't change, and the host OS doesn't change, after the initial log on it should recognize the host and connect again without a problem.

---

### Post by The Cog on 2019-01-28
Looking at post #36, I see that compter 2 (Aaron's) does not have an IP address. 
In post #24 you seem to have the right idea, but it seems that for some reason it's not worked. Perhaps go over the configuration instructions again, reboot and try again. 

There is no point trying ssh until both computers have IP addresses. 192.168.1.1 and 192.168.1.2 are a good address pair to have chosen. Both computers show the wired interface as UP,LOWER_UP so the cable is plugged in and working, it's just the missing IP address that's the problem at the network level.

---

### Post by sonicking on 2019-01-28
Thanks everybody.  It works now!

---

