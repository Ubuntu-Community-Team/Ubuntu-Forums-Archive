---
title: "HELP! Broken authentication system"
date: 2007-01-21
forum: General Help
---

### Post by heinkel_111 on 2007-01-21
I have two computers (running kubuntu 6.06 on server, 6.10 on client) on which I was setting up NFS shares and then I tried to configure an NIS domain, using [a setting up howto guide found on the ubuntu site.](https://help.ubuntu.com/community/SettingUpNISHowTo) 

This was all fine and dandy when I was configuring the server for my NIS domain, which happens to be the computer I am using at the moment. When I tried to configure my NIS client machine, however, I must have done something quite terribly worng :S I started noticing that sudo calls were going slow (this is probably where I should have started reversing my actions immediately). 

It was noticed in the guide that one guy had had to reboot to get the system up and running, so I did that and now the authentication appears to be completely broken. I cannot login at all. The standard KDE login just hangs, and when I try to do a console login, I get "timed out after 60 seconds" error messages.  When I try to login from this other computer to the troubled client using ssh, it prompts for password but then hangs for approx 1 minute and give me a "permission denied, please try again". I am wuite certain I type the password correctly. If I have submitted wrong password in the past, I twould get an immediate response that my password was wrong, not a response after much waiting.  


The mistakes I did was probably something related to step 2 and/or 3 in the workflow described for setting up the client in the HOWTO guide linked to above. 
This involves startup of nis and portmap, and manipulation of these files:
/etc/hosts.allow
/etc/passwd
/etc/groups
/etc/shadow
and finally
/etc/yp.conf 
but at this stage everything just hung up and I did a reboot which just led to more advanced problems :frown: 

I need some brilliant ideas on which way to approach such a fundamental problem. My first idea was to use knoppix as a rescue disc and undo changes to the above mentioned files, then reboot into kubuntu and hopefully be able to log in, roll bak NIS and start over again.

This seemed to not work, as knoppix mounted the /dev/sda3 as a read-only volume.
I  tried to umount it, but it kept saying it was busy with something (Knoppix' unionFS thingy?) so I was not able to umount it and remount it as read-write.

Suggestions please? I am rather desperate here, loosing access to my linux filesystems is bad....

---

### Post by heinkel_111 on 2007-01-21
*BUMP*
Adding some more info

I tried to run a Kubuntu livecd, and edit the configuration of the files in the /etc/ folder (mentioned which files above), and then restart.

However, to me it looks like the files in the /etc/ is a mixture of my old files and live-cd supplied files and that when I exit, the changes are not really saved there? (It is very hard to figure out this when it is not possible to even list the files using a normal login bwithout the livecd). It was much the same using knoppix.

Alternatives:
A: reformat /  (root partition), reinstall system (i guess i could roll back to dapper while i was at it, edgy never did much for me, and dapper is more stable.)
B: create another partition, install an alternative root directory in there, and configure system to boot from that partition?

Using either of these approaches I think I should be able to either
A: completely rebuild the authentication procedures
B: edit the necessary files in /etc/

From what I see, alternative B seems like it may be less work in total (thinking about stuff like reinstalling all the apps, etc...)

I am not going to start work on this before later tonight, so advice is very much welcomed.

---

### Post by heinkel_111 on 2007-01-21
YES! EUREKA! I RULE!  

Problem solved this way
... found 88 GB of available HD space, created a logical partition of 10 GB (ext3) using text-based kubuntu installer disk
...installed kubuntu 64 in said partion, dapper drake version (6.06 better than 6.10 anyway)
...rebooted into new install kubuntu 6.06. Turned out the install was lacking a lot, it was only a server version i think (no desktop). Anyway, I just needed a shell and the lovely **nano**, and a sudo that actually worked, all of which was now available.
... changed directory to /media/sda3 where my wounded edgy root resides.
...checked yp.conf and found syntax error
...corrected syntax error
...rebooted, this time into the edgy on sda3
HEY PRESTO! IT WORKS + NOW I HAVE NIS configured as well :)

---

