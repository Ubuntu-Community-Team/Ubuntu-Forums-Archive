---
title: "Ubuntu, Plesk &amp; cPanel"
date: 2008-04-06
forum: General Help
---

### Post by SteveHillier on 2008-04-06
Thats, it guys and gals.  I've had it.  I retire defeated.
Ok so what am I on about?
I am trying to build a webserver so that I can transfer all my clients webstes off our current server (RedHat & Plesk) which is somewhere in the US and repatriate the service back in the UK under our complete control.
OK, so I have built an AMD X2  machine all up to spec.  I installed Gusty, set up networking, set up the UPS system, set up mail server, set up DNS Server, set up online backup and then went to install Plesk.
Ok, they have an auto installer for a range of distros including Gutsy (and Debian), so that looks good.  Download the relevant files and run it.  It fails.  Message simply saying System may be inoperable - contact support.  A phone call to UK support who say phone toll free to the States.  No such thing, it's only toll free inside US.
The support team seem to come from Planet Zogg.  Certainly their ability to communicate was poor.  I send a log file across.  I get instructions back which I follow and try again.  It fails again.  Another call and I get this subtle question - "What is your licence key?".  Now Plesk allows you to download and install and then obtain a key (by which time you are sgoing to start paying) but unless and until I can get a working Plesk system why am I going to pay any money to them.  But no, without a licence key there is no support.  
After several retries I gather from the log file that Plesk is trying to do something with MySQL and the password fails.  Digging in a Plesk forum I come across a gem.  Plesk requires that you do NOT set a password for MySQL.
Long story short, I rebuild the OS, set up LAMP (with X installed) and try Plesk again.  No passwords unless I have to.  No unnecessary servers.  It fails.  This time I note log file is saying "Cannot resolve hostname and dnsdomainname - Please edit /etc/hosts to include"  but....
/etc/hosts does contain the host name.  Type hostname at the command line and it gives it back to me.  When Plesk fails it destroys the dependecies links so these have to be rebuilt
I have now had 4 rebuilds of Gutsy and nothing makes any difference.  I suspect Plesk likes the user root to be present, It certainly does not like having a mail server installed. But nowhere in their documentation to they tell you about all of this.
I was advised to look at cPanel, support for this listed on Redhat, Fedora, Suse. but not Debian or Ubuntu.
I trawled this forum but the only references to Plesk and cPanel are from those who have tried and failed.  I considered using Debian, but what hope that Plesk will install on it and cPanel does not suggest support.  I have looked at other systems but they don't do what I am used to doing.  I even thought about going back to buying a dedicated server off the shelf, but I have just paid out for a phone line and broadband to run this server.
Whilst writing this on my Gates machine at home, I am building a Fedora system on my server machine and I will see where I go from there.
So sorry Ubuntu, I did give you a try on this one but I have spent enough time on this.  This is not me with a hobby, this is me in a work environment trying to get a job done.  I don't have time to be a guinea pig for Ubuntu nor Plesk in trying to get the two to work together
I will keep you for a desktop machine and I will continue to work to support, but oin this one I am going with what should work because it is already out there.

---

### Post by chewearn on 2008-04-07
dear Steve
This is your second generic posts I read on this subject.  I wonder why you feel the need to post about your frustrations here?

Give the community a break; let us help with solvable problems, not listen to complaints we can't do anything about.  Unfortunately, you are hit by an obscure problem, few if any at all in this community can help you solve.

Ref. your previous complaint:
[http://ubuntuforums.org/showthread.php?t=745369](http://ubuntuforums.org/showthread.php?t=745369)

You know, if you pay plesk, and pay them good, I'm sure you get the help you need.  Just saying.

---

### Post by SteveHillier on 2008-04-07
Perhaps we should have an "I want to rant" forum!!
however problem solved.
I will put his in a new thread as well so people don't have to read the diatribe.
I loaded Fedora 8 but Plesk would not install complaining that it did not have a product for this OS.
So I went for a Fedora 7 download and while I was waiting I looked at the settings in /etc/hosts.
Lo and behold the clue.  The name and all variants were sitting on the line with the loopback IP.
so it read
```
127.0.0.1 webserver.hchosting.org.uk webserver localhost localhost.localdomain hchosting.org.uk
```
So I rebuild Gutsy while I was waiting for the download, edited /etc/hosts to match and Plesk installed no problemmo.

---

