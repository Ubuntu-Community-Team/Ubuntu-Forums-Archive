---
title: "network settings being lost.."
date: 2006-08-04
forum: General Help
---

### Post by nismohasan on 2006-08-04
on every reboot i have to go into network settings and re enter DNS Addresses
& the domain name.

It DID used to work but stoped recently, i have no idea what caused it to occur.

Does anyone have any idea on how to fix it? It really has become annoying.

---

### Post by nismohasan on 2006-08-05
can anyone help?

---

### Post by ozorba on 2006-08-05
Under Gnome->Networking allows you to enter all the details. Make sure that you click OK on all wildows so that it can be saved in the network related files. Otherwise you end up entering the details each time you start up your computer.

---

### Post by nismohasan on 2006-08-05
i did, didn't solve the problem..

---

### Post by MishMich on 2006-08-05
I have the same problem.  I set the DNS under networking, press OK, everything works fine, then when I reboot the DNS entries have  gone and I have to enter them again.  I have tried vi-ing the settings manually in resolv.conf - same thing, it just replaces the nameserver with 127.0.0.1 when I reboot.  I tried chmodding to 444 - same thing.  I checked before I shut down - all the settings were there, bought it up and they were gone - makes no difference whether I do it in networking or using vi on the file - each time I shut down the settings are there in the networking tool & if I cat the file, and when it comes back up the file is 644 with the original localhost setting.  It looks like it is being deleted and replaced with a default resolv.conf each time I reboot.  Very irritating.  Everything works fine locally, but I have to re-enter the DNS each time I restart so I can use Firefox to browse.

Editing the file means that the DNS still works for Firefox, but the settings don't show under networking.  I am not using DHCP, as I access my ISP via a router; so I have fixed IP addresses my side of the router, and the router acts as a gateway to the ISP, which is DHCP (but I have had the same IP address assigned for 5 years now).

The PC in question is set up as a server with the gnome destop installed on top, but my laptop is set up as desktop, and the DNS entries seem to work fine on that, & set up the same way.

If I look at the file itself, it appears to be a link:

lrwxrwxrwx 1 root root       31 2006-07-24 16:28 resolv.conf -> /etc/resolvconf/run/resolv.conf

The /etc/resolvconf/run dir is itself a link:

lrwxrwxrwx 1 root root   19 2006-07-19 19:54 run -> /var/run/resolvconf

and it is there that the file resides:

-rw-r--r-- 1 root root 202 2006-08-05 15:54 resolv.conf

Mish

---

### Post by Sweezel on 2006-08-05
I also had this problem soon after I upgraded from Breezy to Dapper.

I decided to do a clean install of Dapper when I had time and it has worked fine since.

Did you guys upgrade or do a fresh install?

---

### Post by MishMich on 2006-08-07
Hi,

fresh stand-alone server install, then added the desktops & the LAMP stack & vsftp.  I think the DNS worked OK before I removed proftp, but proftp wouldn't work, so I removed it and installed vsftp instead after I got the LAMP stack working, & that worked fine.  Then I noticed the DNS problem.

Maybe now I have the hang of Ubuntu, I will do a fresh install and overwrite the old NT4 partition completely so I have 2 clean 8 GB disks to play with, instead of 2*4 & 1*2 GB partitions.  Now, what did I do to get it all running, and which configuration files should I keep... just wondering aloud.

Mish

---

### Post by hanzomon4 on 2006-08-07
I have the same problem.. It started after I set up a static ip on my side of the router

---

### Post by MishMich on 2006-08-07
Been looking into this a bit further, I found that somehow I was running on a newer version of Ubuntu than the one installed - tried selecting the original one to check that the problem was still happening, and it is.  I went through the help file that comes with the Networking tool, and I noticed this at the end:

3.14.&#8195;To create a new profile

Press the Network profiles button, a new window will appear letting you to save your current configuration as a profile pressing the Save current button. You must specify a name for the profile, optionally you can specify a description for this profile.

3.15.&#8195;To delete an already existing profile

Press the Network profiles button, in the network profiles window, select the profile you want to delete and press the Delete button.

3.16.&#8195;To switch the current profile

Change the current network profile menu, all the configuration will be switched automatically to the chosen profile.

----------------

I have had a look at the picture on the help file, and my Networking tool looks different:

This Network Profiles Button at the bottom doesn't exist on my Networking admin tool anywhere - not on any of the 4 tabs.  What there is is a location box at the top of the box (persists for 4 all tabs).  I can create a location in there, and select it.  I don't suppose it's that important, but there seems to be a slight discrepancy here.

Mish

---

### Post by MishMich on 2006-08-07
> **ozorba said:**
> Under Gnome->Networking allows you to enter all the details. Make sure that you click OK on all wildows so that it can be saved in the network related files. Otherwise you end up entering the details each time you start up your computer.

:-k 

I can't click OK on all windows - because when I click on OK under 'DNS', it closes the Networking Tool completely.  When I open it again, the settings are all there.  If I have only changed the DNS setting, what would be the point of re-opening Networking another three times, just to click OK on each window and have it close down again each time?  Or is there something wrong with the way it is working?  Is it not supposed to close when I press OK?

Mish.

---

### Post by MishMich on 2006-08-07
I tried setting the location to the name of my machine in the Locations box, and then saving that.  What seems to happen is that the although the location is not stored, when I bring the system back up, all that shows in the DNS is the localhost.  If I then select my pc-name as the location, the profile is changed, and the DNS entries are there again.  This makes life a bit easier than re-entering the details each time.

I guess I'll have to look at the commant-line setup for the network interfaces tomorrow, but looking at the resolv.conf & interfaces files didn't really show me anything out of the ordinary.  I guess the simplest way to resolve this would be if someone knows how to set the Networking so that it defaults to the loaction set, rather than a blank location that has no DNS (but all the other information), and entailing resetting networking each time I reboot.

Mish

---

### Post by hanzomon4 on 2006-08-08
Anybody know how to stop this from resetting?
I dual boot and this annoying

---

### Post by mrazster on 2006-08-08
Might wanna take alook at [*THIS](http://www.ubuntuforums.org/showthread.php?t=193850)* thread. Read the whole thread..!!

---

### Post by hanzomon4 on 2006-08-09
Read it all tried the two solutions offered, but no didn't work.

---

### Post by MishMich on 2006-08-09
rebuilt the system from scratch - that seems to have fixed it.

---

### Post by hanzomon4 on 2006-08-09
Rebuilt, Like what reinstallation of ubuntu

---

### Post by MishMich on 2006-08-10
yes, reinstalled it - lots of things seem to work better now.

Only slight problem I installed as an LVM, so none of the usual disk management tools work.  Not a problem though - I guess there'll be some LVM management tools out there somewhere.

---

### Post by hanzomon4 on 2006-08-10
Well thats not an option for me. 
I gotta figure this one out.

---

### Post by hanzomon4 on 2006-08-10
I fixed it.. here's how

First the only setting I had to reset after a reboot was the DNS. The config file where the DNS settings are stored is in /etc/resolv.conf. 
For some reasons getting my settings to stick using the Network configuration tool would not work, so I tried editing /etc/resolv.conf by hand.
That did not work because Ubuntu uses a dynamic DNS configuration. This will overwrite the etc/resolv.conf file at boot-up.
The solution is to add your settings to /etc/resolvconf/resolv.conf.d/base like this.
```
 sudo gedit /etc/resolvconf/resolv.conf.d/base
```
```
nameserver   192.X.X.X
```
Replace the "192.X.X.X" with your DNS number.

Okay my work here is done.

---

