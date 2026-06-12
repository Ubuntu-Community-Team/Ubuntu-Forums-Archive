---
title: "Xbox Media Center File sharing with Ubuntu"
date: 2006-11-01
forum: General Help
---

### Post by ExZen on 2006-11-01
I was recently forced to install ubuntu on my laptop for lack of another option.  So far things have progressed smoothly, however one of the main functions windows served was to stream downloaded content to my xbox (through xbox media center) and to my TV.  

Now, I've downloaded a few shows, and I downloaded SMB (and set several files to share) but my computer does not register when I attach it to the router which is in turn connected to the xbox.  Does Ubuntu have a firewall up that I can't see?  If so, any idea how I'd disable it?  Thanks!

Using 6.10

ExZen

---

### Post by matthewstory on 2006-11-01
iptables -L -n will show you the firewall rules that are running, and iptables -F will flush the firewall rules, if there are any.

---

### Post by ExZen on 2006-11-01
I get the following msg when entering that command:

WARNING: Error inserting x_tables (/lib/modules/2.6.17-10-generic/kernel/net/netfilter/x_tables.ko): Operation not permitted
FATAL: Error inserting ip_tables (/lib/modules/2.6.17-10-generic/kernel/net/ipv4/netfilter/ip_tables.ko): Operation not permitted
iptables v1.3.5: can't initialize iptables table `filter': Permission denied (you must be root)
Perhaps iptables or your kernel needs to be upgraded.

---

### Post by hind3nburg on 2006-11-01
I use ccxstream for streaming to my xbmc and it's awesome. Great streaming and no screwing with samba.

[http://lnk4.us/affJ](http://lnk4.us/affJ)

---

### Post by ExZen on 2006-11-02
I've been looking at CCXstream, but it seems a bit complicated to get running, any tips?  I looked around the forums, and while there are some threads pertaining to it, none of them seem very clear about getting it up and running...

So there's no way for me to get it to work with Samba?  Curses, I thought for a second it was going to be easy to get my files to be accessed through my xbox...

---

### Post by Riao on 2006-11-07
I used to use CCXstream with windows many moons ago, but samba (in my opinion) is a much better way to do it.  The throughput is significantly faster with Samba.

Once Samba is installed and configured properly, your xbox can connect to it in the same fashion it can with any windows machine.  I've just verified this.  My xbox connects to my Ubuntu Linux box with no problem.

My guess is that:

1.  You need to configure your network.> my computer does not register when I attach it to the routerMake sure that your Ubuntu machine can see your router, and ping your xbox.

2.  You need to ensure that samba is configured correctly and that you have a smb share set up.  Also remember that you will have to create a smb user that you will connect with from the xbox.  An smb user is different from a linux user, unlike on a windows machine.

There is plenty of documentation here on the forums to set up samba properly.  I was able to set mine up in about 20 minutes just searching through the forums.

Remember to add the shares to userdata\sources.xml in xbmc.

Good luck!  (I'm sure you won't need it.  I'm a COMPLETE linux noob [I just installed Ubuntu on a spare machine today] but it was quite simple).

---

### Post by ExZen on 2006-11-08
I feel really bad now...its been a week and I still havn't gotten any of my shares to work...been frigging with samba most of the time, have given up on ccxstream.  I dunno, I havn't found the forums that useful for this either.  I'd glady post a how-to guide once I get it up and running myself.

---

### Post by tgm4883 on 2006-11-08
I use a program called webmin that seems much easier to use.  What it allows you to do is configure samba (and many other things) much easier.  I used it on my FC5 Fileserver, but it does also support ubuntu.  Check that out, and at the very least, if you dont like that, use SWAT.  Both are much easier than configuring with the config file.

---

### Post by Riao on 2006-11-08
This what I looked at to get everything working properly (linked to from the forums):
[https://help.ubuntu.com/community/SettingUpSamba#head-51f51bea37ef002e8c6d7dbfeeb486a47cdb0f88](https://help.ubuntu.com/community/SettingUpSamba#head-51f51bea37ef002e8c6d7dbfeeb486a47cdb0f88)

I just left this at the what the guide laid out and only share my home dir.  I don't mind browsing through a little bit with xbmc's gui.  I haven't tried setting up any other shares yet though.  This suits me for now.

---

### Post by dreamer_cast on 2006-11-08
Hey guy, I'll tell you how I have mine setup; first off, I'm running as root in Ubuntu, I have one of my external drives setup under "shared Folders" in the Administration Menu.  I choose a name for it and used Samba for the sharing type.  When I use XBMC, I just go to WORKGROUP SMB NETWORK, and my shared drive is there.  I think I setup Samba in XBMC to reflect my WORKGROUP as well.  I hope that helps,

Dreamer

---

### Post by KLineD on 2006-11-08
> iptables -L -n will show you the firewall rules that are running, and iptables -F will flush the firewall rules, if there are any.

Those commands should be entered as root, so change them to:
```
sudo iptables -L -n
sudo iptables -F
```

But I doubt you have a firewall in place if you didnt install one yourself. I remember setting up XBMC and Ubuntu myself, the first thing is to be sure you get an IP for your Ubuntu box from the router. I really need more information to exactly pinpoint your problem... still I'll try to give you some guidelines.

Verify in your network settings that you are using DHCP, or assign a valid static ip. If the xbox and ubuntu are on the same router they should see each other. Try ping ip_xbox and see if you get a response. You can see what ip is assigned to your xbox in XBMC settings.

When you get a ping, make sure both samba and XBMC are sharing on the same workgroup. To see/edit the workgroup in ubuntu:
```
sudo gedit /etc/samba/smb.conf
```
Edit the line Workgroup= to reflect that on your XBMC.ini file. Make sure the line in smb.conf is uncommented (remove the semicolon at the beggining)

Now you have to edit the shares on XBMC.ini, that is, tell XBMC where on your Ubuntu box are the files you want to stream. Of course those need to be set up in smb.conf first. The ini file in XBMC has some examples of how to do this, as well as smb.conf so follow those examples and you should be ok. 

One final note, if you get the directory listing in XBMC but get an access denied error, make sure you enter the correct user/pass information in the share info in xbmc.ini and also make you added that user/pass combination as a samba user:
```
sudo smbpasswd -a <username>
```
It will prompt for a new password for the username you entered, after that restart samba
```
sudo /etc/init.d/samba restart
```
and you should be ok

Hope it helps

---

### Post by ExZen on 2006-11-11
I've tried switching to both a static IP and DHCP, but I am unable to get Ubuntu to ping the xbox...any ideas?

---

### Post by KLineD on 2006-11-13
If you can't ping your Xbox and/or your PC then you'll never be able to share anything. Make sure you are connected to the same router and that all physical connections are ok.

Unfortunatelly that's all I can do for you :-k

---

### Post by ExZen on 2006-11-14
Yup, they're both attached to the same router, and the router was working perfectly when I had windows installed, so I'm fairly certain the problem doesn't lie there.

I don't suppose you know where I might find a good howto for this?  The forums are limited in the help they can provide for this.

---

### Post by KLineD on 2006-11-15
No I don't know where to find a good howto I'm sorry.

---

### Post by maniacmusician on 2006-11-15
1. What's the IP address of your xbox? As someone said above, you can find in XBMC

2. Switch to a static IP for your laptop, it'll make life a little easier

what KLineD outlined above is very good, and once you can ping your xbox, that is what you should follow. but first we need to be able to see it.

---

### Post by ExZen on 2006-11-16
When I get back from classes I'll post my IP and info from XBMC.  I'd do it right now, but I'm just heading out the door to write an exam.

I appreciate your patience guys, thanks for the willingness to help.

---

