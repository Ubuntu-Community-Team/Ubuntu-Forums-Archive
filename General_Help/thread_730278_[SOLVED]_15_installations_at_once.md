---
title: "[SOLVED] 15 installations at once"
date: 2008-03-20
forum: General Help
---

### Post by TJCIB on 2008-03-20
I am at a small school.  We have a lab with 15 computers.  I want to install Ubuntu for a number of reasons.

What we have:
The computers networked via 24-port switch to modem
The computers have various hardware combos, mostly donated machines

What we don't have:
A server or computer with the gusto to act a server and install Edubuntu or run any type of thin client
Not all computers can boot via USB or LAN, but all have CD drives

What I need:
To install Ubuntu on all 15 machines
To have a separate logins for each student user (we have about 40 users)

I am simply looking for suggestions.  I know I could install each computer individually, update/upgrade them all separately, and manually install all 40 users and passwords on each system, then install all the programs I need on each separately.  That would suck the bandwidth out of our entire city and take a lot of keystrokes (which I have found Linux users like to avoid).  I am willing if thats what it takes though.

I have looked into making an image of the first drive and using it on the others, I don't think thats for me.  I have also tried rolling my own distro into a liveUSB and booting, but only 7 of the 15 can boot from USB, so that is pointless.
I have read [http://ubuntuforums.org/showthread.php?t=466387](http://ubuntuforums.org/showthread.php?t=466387) which got me started, but I am still pretty new and don't think I am quite capable of editing files and matching things to that extent.  If this is the best way, tell me to suck it up and learn.  I have researched, but am still very confused about it the process hinted on that thread.  Anyone have a good resource to help me get through this method if I need to?

Any suggestions?  (Besides "get a server and use Edubuntu")

Thanks.

---

### Post by Mustard on 2008-03-21
Wow..thats some serious stuff. :)

I've been sitting around thinking of some ways you might do it that could cut down on time and replication.  I have no experience with this at all though.

Initially I would be googling for information on a 'network installation' for Ubuntu.  I found some results, but I think it would be best for you to read them, rather than have me come back and parrot what I found.

Looking over the restrictions you have though, I'm not sure how succesful that would be,  If you could work out which one can boot via LAN and setup a minimal ftp server that would at least cover some of the machines.

---

### Post by Sef on 2008-03-21
> To have a separate logins for each student user (we have about 40 users)

If you assigned each student to one computer, (so 2 or 3 students would share each computer), just do this:  System > Administration > Users and Groups.    That way you could set each student an account that would not have administrative privileges. (Unless you gave it to them.)

> I have looked into making an image of the first drive and using it on the others, I don't think thats for me.

Why wouldn't it be for you?

---

### Post by jou770d on 2008-03-21
The only idea I can offer is installing ubuntu on one device, changing everything you want then using some tool ( _["]Remastersys]("http://loscompanion.com/forums/index.php?board=58.0)_ for example) to create a back-up CD and install it on the other devices.
It's what I did to copy my changes from my laptop to my desktop. However when I did it I came out with a back-up DVD not a CD which might prove to be a problem for you if you only have cd drives.

---

### Post by Mustard on 2008-03-21
If all the hardware was the same it would be easier, but with different hardware on all the machines it complicates the process.

---

### Post by justleen on 2008-03-21
copying images is the quickest way to install them. problem would be the different hardware but i'd still give it a go. Second option or me would be manually installing the systems.

You could try to setup something of network server to roll out from, but i'm thinking that in the time you set this up, you can setup 30 machines by hand..
 [http://www.debuntu.org/how-to-unattended-ubuntu-network-install](http://www.debuntu.org/how-to-unattended-ubuntu-network-install), might be worthwhile 
software PXE boot, through PXELINUX.. this will allow you to just boot a system, and PXE will look for a roll-out server.. again, not sure wether this is a time saver, but it defenitly will save you time in the long run, consedering fresh installs, or adding new machines.


For you users, i'd use[ NIS or LDAP]("https://help.ubuntu.com/community/Servers") for authentication. Or, like Sef says, if you know which users logon where, just create to accounts locally.

If you want all 40 users on all systems, i'd go for a scripts that i can run to create all the users. that way you only have to type them once, and run the script on each client (i'd be happy to help you with that / write that for you)

---

### Post by Mustard on 2008-03-21
How could he set up a cache to save downloading all the package updates for every machine?

Could you just update one machine then cp the packages on to the other machines?

---

### Post by justleen on 2008-03-21
> **Mustard said:**
> How could he set up a cache to save downloading all the package updates for every machine?

Could you just update one machine then cp the packages on to the other machines?

Yes. All downloaded / installed packages are in /var/cache/apt/
you can copy those over.

you could even use apt-get upgrade --download-only
that will only download packages, not install. that way your sure you got all the update-pacakges locally.

personally, i backup that folder.. on a new install i just run a dpkg -i *.deb..  this works quite well.. synaptic does give some small errors, but synaptic is also able to fix these, with minimal downloading

---

### Post by ad_267 on 2008-03-21
You could use APTonCD to download the updates and software only once and then just use the cd to update the other computers.

Edit:
> Yes. All downloaded / installed packages are in /var/cache/apt/
you can copy those over.
That might be simpler, probably exactly what APTonCD does but without the GUI

---

### Post by TJCIB on 2008-03-21
Wow, I go to sleep and come back with so much help...gotta love the forums...

Given the responses, this is what I think I will try:

Set up one computer exactly how I want it, keeping notes on exactly what I did.
Then try to use PartImage or something to image the drive and use the restore function on another machine.  That seems the fastest.

If the differences in hardware cause too many problems, I will use my notes to write some scripts to accomplish some of the tasks I need (adding users/groups, getting media codecs, etc), and will use APTonCD to do the programs, so I have a hard backup of them.  Its not a lot, just some typing programs for the younger kids, wine, and a few things.

Thanks to the others for your help.  I tried setting up a PXE boot, but our network isn't set up correctly for it.  I tried Edubuntu and some other things, but our network setup really struggles with it.

I did try using remastersys which came up with a DVD not a CD, which as you said, is the problem since none of the computers have a DVD drives let alone DVDBurners.  Any way to do that by mounting the ISO?  I didn't think so.

I appreciate all the help.  This is why I wanted to switch to Ubuntu, even though I know much less about it.

I appreciate any other thoughts.

Peace, and thanks from Brazil!

---

### Post by smoka on 2008-03-21
I'm not too sure about the installing, but once you have them up and running one handy thing for you to use for updating all the machines is setting up one machine (or Virtual Machine) running apt-cacher

You can then point all of the machines to this machine to update.

It's really quite handy, check it out, here's the best link I've found for setting it up:

[http://ubuntuforums.org/showthread.php?t=564301](http://ubuntuforums.org/showthread.php?t=564301)

---

### Post by TJCIB on 2008-03-21
That does look nice.  Thanks for the tip

---

### Post by justleen on 2008-03-21
Good luck, and let us know how you got on!

ps: can i recommend[ elog]("http://midas.psi.ch/elog/") for your notes-keeping? I think its a brilliant tool! (its in the repros)

---

### Post by jou770d on 2008-03-21
> **TJCIB said:**
> 
I did try using remastersys which came up with a DVD not a CD, which as you said, is the problem since none of the computers have a DVD drives let alone DVDBurners.  Any way to do that by mounting the ISO?  I didn't think so.

Actually I've just discovered that it is possible to boot from an iso but I think that the script method is probably the easiest. (In case you're interested: [http://ubuntuforums.org/showthread.php?t=666267](http://ubuntuforums.org/showthread.php?t=666267))

---

### Post by TJCIB on 2008-03-21
Here's how it went so far...

I tried using an image, but it didn't work due to the major hardware differences.  But it is nice to have that image of the original machine in case something breaks down the road.

I installed ubuntu off a LiveUSB as well as LiveCD on a few computers.  I wrote a small script to enable and install the necessary repositories as well install the updates/upgrades as well as the necessary codecs.  Its not perfect, but it works.

I set up all the needed users and groups on the first machine.  I then copied the relevant parts of /etc/shadow /etc/passwd etc/group and made sure all the group IDs, user IDs and such didn't conflict with anything.

I used a script to create /home directories for each user as well as assign ownership and rights to each director for its respective user.

When I logged into a copied user, I got an error concerning themes, and some other things.  It said it would retry at the next log in.  So I logged out, relogged in, and no errors.  Everything was functional.

I believe I have it.  All users have their own /home directories with correct ownership and permissions.  Everything is updated.  I can't think of something else to do....if anyone can think of something I'm missing, please post it so I can check it out.

Thanks for all your help.

*edit* sorry....i have 4 computers up and running

---

### Post by TJCIB on 2008-03-24
they are all working now.

The only issue is still with the update manager notification.

When I set it to fetch through the proxy, the notification switches from "available updates" to "installed programs have missing dependencies".  I can't use the graphical update manager then.  I can still use synaptic as well as the terminal.  So I guess its no big deal.
It has something to do with apt-cacher since I didn't do it one one terminal and it doesn't have that problem.

Thanks again...problem solved

---

