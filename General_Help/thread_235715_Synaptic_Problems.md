---
title: "Synaptic Problems"
date: 2006-08-13
forum: General Help
---

### Post by trinityj5 on 2006-08-13
Hi there :) 

I am very new to Linux so keeping your explananations simple would be appreciated, thank you :)

Basically having installed Ubuntu the other day, I wanted to access the internet... however I couldn't browse any web pages at all, I did some looking about on here and concluded that "ipv6" was my problem... So I disabled that in about:config in firefox and it cured my web browsing problems at once... However I still cannot get synaptic to access the net at all. I believe that I have diasbled "ipv6" system wide by doing following:

adding
```
# disables ipv6
blacklist ipv6 
```

to...
```
Sudo gedit /etc/modprobe.d/blacklist 
```

I then ran
```
 lsmod | grep ipv6 
```

and...
```
 ip a | grep inet6 
```

both of these returned no results, leading me to the conclusion that "ipv6" is disabled across my system, yet synaptic still can't download any repo information.


Any ideas at all would be much appreciated, I hope my post is clear!


John :)

---

### Post by skale on 2006-08-13
post "cat /etc/apt/soources.list"

---

### Post by trinityj5 on 2006-08-13
as requested here is the output of cat /etc/apt/sources.list

```
 john@Trinity:~$ cat /etc/apt/sources.list

# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb http://gb.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
# Line commented out by installer because it failed to verify:
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu dapper-security main
# Line commented out by installer because it failed to verify:
deb-src http://security.ubuntu.com/ubuntu dapper-security main
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe
deb http://archive.ubuntu.com/ubuntu/ dapper main universe restricted

```


Thanks for any help you can offer :)



John :)

---

### Post by trinityj5 on 2006-08-14
Hi there, anyone had any thoughts on this yet? :) 

Cheers for any help you can offer :)

---

### Post by thomasf on 2006-08-14
hmm...What exactly does apt-get say?
I disabled ipv6 by adding "alias net-pf-10 off ipv6" to /etc/modprobe.d/aliases but I guess that's not the source of problem.
Did you try to ping hosts in terminal?

---

### Post by trinityj5 on 2006-08-14
I will post the results of "apt -get" when I get home :) When you say ping hosts, what do you mean exactly? I can ping websites all day long...  Is this what you mean? Sorry if I am being thick... 

Cheers for all you help so far :)


John :)

---

### Post by trinityj5 on 2006-08-14
As promised here are the results of "apt-get"
```
john@Trinity:~$ apt-get
apt 0.6.43.3ubuntu2 for linux i386 compiled on Apr 18 2006 19:46:38
Usage: apt-get [options] command
       apt-get [options] install|remove pkg1 [pkg2 ...]
       apt-get [options] source pkg1 [pkg2 ...]

apt-get is a simple command line interface for downloading and
installing packages. The most frequently used commands are update
and install.

Commands:
   update - Retrieve new lists of packages
   upgrade - Perform an upgrade
   install - Install new packages (pkg is libc6 not libc6.deb)
   remove - Remove packages
   source - Download source archives
   build-dep - Configure build-dependencies for source packages
   dist-upgrade - Distribution upgrade, see apt-get(8)
   dselect-upgrade - Follow dselect selections
   clean - Erase downloaded archive files
   autoclean - Erase old downloaded archive files
   check - Verify that there are no broken dependencies

Options:
  -h  This help text.
  -q  Loggable output - no progress indicator
  -qq No output except for errors
  -d  Download only - do NOT install or unpack archives
  -s  No-act. Perform ordering simulation
  -y  Assume Yes to all queries and do not prompt
  -f  Attempt to continue if the integrity check fails
  -m  Attempt to continue if archives are unlocatable
  -u  Show a list of upgraded packages as well
  -b  Build the source package after fetching it
  -V  Show verbose version numbers
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See the apt-get(8), sources.list(5) and apt.conf(5) manual
pages for more information and options.
                       This APT has Super Cow Powers.

```

When I try "apt-get update" I get...

```
john@Trinity:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

```

As for pinging hosts I still don't really know what you mean... :???: I can do pretty much everything in firefox but the rest of my system, ie. Gaim and Synaptic, can't access the net at all....](*,) 

Any ideas appreciated :)



Thanks again


John

---

### Post by corstar on 2006-08-14
silly question, but are you using apt as super-user?

---

### Post by thomasf on 2006-08-14
> **trinityj5 said:**
> As promised here are the results of "apt-get"
Ups, sorry, saying apt-get I meant apt-get update command

> **trinityj5 said:**
> 
When I try "apt-get update" I get...


As corstar suggested, you should execute command sudo apt-get update

---

### Post by trinityj5 on 2006-08-15
ok, as requested, this is what I get when typing "sudo apt-get update"

```
 0% [Connecting to gb.archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubuntu.com (1.0.0.0)] [Connecting to archive.ubuntu.com (1.0.0.0)]

```

I left it like this for about 2 mins and nothing happened... 

Any further ideas?

Thanks for help so far :)

John

---

### Post by thomasf on 2006-08-15
> **trinityj5 said:**
> ok, as requested, this is what I get when typing "sudo apt-get update"

```
 0% [Connecting to gb.archive.ubuntu.com **(1.0.0.0)**] [Connecting to security.ubuntu.com **(1.0.0.0)**] [Connecting to archive.ubuntu.com (1.0.0.0)]

```



It seems that's DNS related problem. Brackets should contain proper IP address of gb.archive.ubuntu.
I found that some people have similar problem. Look at this threads 
[http://www.ubuntuforums.org/showthread.php?t=206692]("http://www.ubuntuforums.org/showthread.php?t=206692")
[http://www.ubuntuforums.org/showthread.php?t=99542]("http://www.ubuntuforums.org/showthread.php?t=99542")

To sum up - try to disable ipv6.If it won't work,probably you'll have to edit DHCP config (assuming you're using DHCP). Procedure is described here:[http://www.linuxquestions.org/questions/showthread.php?t=381026]("http://www.linuxquestions.org/questions/showthread.php?t=381026") Config file in Ubuntu is /etc/dhcp3/dhclient.conf

Provide some more info about the way in which you connect to the internet.Are you using ADSL modem, router etc?

---

### Post by trinityj5 on 2006-08-15
Thanks for all your replies so far, basically my computer connects to the internet via a router with an adsl2 connection, the router leases an ip address to me via dhcp. This is working ok as I can browse all I want... I believe that I have disabled ipv6, as explained in my first post in this thread... I will look through those pages and see if anything springs out at me.... 

Thanks for all your help so far

Any further ideas would be much appreciated :)


John

---

### Post by trinityj5 on 2006-08-15
right.... I have read through those other threads, performed various things that they suggested and after about 6 reboots later I am still at square one... anyone come up with anything yet?


Cheers for your help :)


John

---

### Post by thomasf on 2006-08-15
Did you try the trick with /etc/dhcp3/dhclient.conf ? What do you have in /etc/resolv.conf ?

---

### Post by trinityj5 on 2006-08-15
This is what my /etc/dhcp3/dhclient.conf file looks like btw...

```
 # Configuration file for /sbin/dhclient, which is included in Debian's
#	dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#	man page for more information about the syntax of this file
#	and a more comprehensive list of the parameters understood by
#	dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#	not leave anything out (like the domain name, for example), then
#	few changes must be made to this file, if any.
#

#send host-name "andare.fugue.com";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, host-name,
	netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}

```

Remember I am very new to linux, easily confused!!! :confused: 

Does anyone see anything awry?


Cheers 


John :)

---

### Post by trinityj5 on 2006-08-15
I have the following in /etc/resolv.conf

```
 nameserver 192.168.1.1 
```

no mention of other ip addresses...



John

---

### Post by thomasf on 2006-08-15
I guess that's router IP address.
ok, I think you have to get address of ISP's DNS server.

---

### Post by trinityj5 on 2006-08-15
Ok cool, any ideas how to find this out? Short of phoning them up tommorow?

Cheers as always :) You are being most helpful :)


John

---

### Post by jeffathehutt on 2006-08-15
Try this and see if it works.  Edit the file /etc/resolv.conf
```
gksudo gedit /etc/resolv.conf
```

Add these two lines to the top of the file:
```
nameserver 208.67.222.222
nameserver 208.67.220.220
```

If that fixes it, then it is a dns problem.  Right now your computer is trying to use the router as a dns server, but chances are, your router can't resolve the hosts.

---

### Post by trinityj5 on 2006-08-16
Edit: Sorry it's taken me so long to post!! Been a bit busy!!

Hi there, thanks for that suggestion :) However when I edit the file I can't seem to save it.... I get an error saying that I do not have the necessary permissions to save the file. I typed exactly what you said..
```
 gksudo /etc/resolv.conf
```

it opened the file fine, but I just cant save it... am I doing something blindingly obvious wrong?

I also tried..
```
 sudo /etc/resolv.conf
```
and the same thing happened.

One more thing, when I opened it with "gksudo" I got this bit of code in terminal as it opened the file... 

```
john@Trinity:~$ gksudo gedit /etc/resolv.conf
(gedit:5169): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
```

Any ideas? What am I doing wrong? I really want to try out that dns idea but I cant edit the file!  ](*,) 


John :)

---

### Post by thomasf on 2006-08-16
```
sudo gedit /etc/resolv.conf
``` really doesn't work?

Arggg...Type:
```
sudo nautilus
```
Go to /etc directory. Locate file resolv.conf.Right click - properties.Go to Permissions tab. It should look like this: [http://img100.imageshack.us/my.php?image=respermmv0.jpg]("http://img100.imageshack.us/my.php?image=respermmv0.jpg")
File owner - root, file group - root
Owner - only read and write checked
Group - only read checked
Others - only read checked

---

### Post by trinityj5 on 2006-08-16
Hi :) Thanks for getting back to me, I did as you said and checked the file properties in nautilus, however they are exactly the same as your ones. Root has permission to read and write, so it should be working fine :confused: I noticed when in the properties that I have changed the file before, on the 11th of August in fact, so I dunno what on earth is going on... When browsing /ect I noticed that the icon for resolv.conf has a gold padlock to the top right of the icon... does this mean it's locked? i'm so confused!

Also I noticed a file in /etc called "resolv.conf.dhclient-new" this has exactly the same information in it as "resolv.conf" and this is editable, do you have this file on your system?



Thanks for any help as always! :)



John

---

### Post by thomasf on 2006-08-16
> **trinityj5 said:**
> . When browsing /ect I noticed that the icon for resolv.conf has a gold padlock to the top right of the icon... does this mean it's locked? i'm so confused!



Yes,padlock means that file is somehow locked...I don't know what's going on :???:
Maybe file is immutable? Go to terminal and execute command:
```
sudo chattr -i /etc/resolv.conf
``` Now try to edit it using
```
sudo gedit /etc/resolv.conf
```


If doesn't work, let's try another way round. In GNOME go to System/Administration/Networking. In DNS tab delete router IP and enter DNS addresses mentioned by user jeffathehutt. Start terminal and execute ```
sudo apt-get update
```

---

### Post by trinityj5 on 2006-08-16
Hey Hey!!

Totally working now!! 

Thanks so much for your help :) 

Great stuff, now to installing compiz and xgl ;)


Thanks so much again :)



John :-D :-D

---

### Post by thomasf on 2006-08-16
Was resolv.conf immutable?

Try to reboot machine. Probably you will lose your DNS settings.
How to fix it?
[B]
Method 1:[/B]
Execute: ```
sudo gedit /etc/dhcp3/dhclient.conf
```
Add following lines:
```
prepend domain-name-servers = 208.67.222.222, 208.67.220.220;
```
Now reboot your machine and check whether it works.

**Method 2:**
Execute: ```
sudo gedit /etc/resolv.conf
```
File should look like this:
```
nameserver 208.67.222.222
nameserver 208.67.220.220
```
Execute ```
sudo chattr +i /etc/resolv.conf
```
Reboot your machine and check connection.


IMHO you should obtain IP of ISP's DNS. Probably it's much faster.

---

### Post by trinityj5 on 2006-08-16
Yeah, I managed to immute resolv.conf and it edited as it would normally (?) I am just downloading some updates and then I will mute that file again and reboot.... when you say check again, what do you mean? What should I check again? :)

Again, any ideas where I can get hold of the ISP's DNS addresses? Short of phoning them of course....


Cheers as always 


John :)

---

### Post by thomasf on 2006-08-16
> when you say check again, what do you mean?
Check whether apt-get works.

> again, any ideas where I can get hold of the ISP's DNS addresses?
Heh, I'm not an network expert but maybe there is a method to get them from your router. 
Probably you can find these addressess somewere on the internet. Try to google, vist your ISP site, ask other people..

---

### Post by trinityj5 on 2006-08-16
Hi there, after originally changing resolv.conf to include those DNS addresses "apt-get update" was running fine, so I did a system update and that all worked fine too. I then rebooted and "apt-get update" was back to it's old ways...so I ran... 

```
sudo chattr +i /etc/resolv.conf
```

As far as I understand it, that has now locked the file... so I rebooted and "apt-get update" is running fine and as I would expect (?). Would you suggest that I did your first method as well as a backup?? 

Thanks very much for your continued help :)


John

---

### Post by trinityj5 on 2006-08-16
Not sure that the DNS addresses are available on the net... I will keep looking and if all else fails I will call my (rather obscure :???: ) ISP. 


Thanks again for your help :)


John

---

### Post by thomasf on 2006-08-16
> **trinityj5 said:**
> I then rebooted and "apt-get update" was back to it's old ways...so I ran... 

```
sudo chattr +i /etc/resolv.conf
```

As far as I understand it, that has now locked the file... so I rebooted and "apt-get update" is running fine and as I would expect (?).

Ok,you've edited resolv.conf and the locked it using chattr.That's fine. Method 1 is maybe more elegant, but the best method is working method ;) so I think that you can leave it as it is. If problems occur, try method 1.

---

### Post by trinityj5 on 2006-08-17
Hehe, ok then, I will leave it :)

Thanks very much to all who helped me out on this thread :)


Thanks again!!


John:grin:

---

### Post by thomasf on 2006-08-17
I'm glad I could help :)

---

