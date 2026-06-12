---
title: "Firestarter + Google problem"
date: 2005-06-12
forum: General Help
---

### Post by Stilgar on 2005-06-12
Ok, this one is really strange, if someone told me about it, I probably wouldn't believe them.

Anyway the problem is that google.com won't load up when firestarter is on. All other web sites work fine but google.com won't load. It looks it up successfully then says "waiting for www.google.com" in the status bar and it spins for a few minutes and then times out. Typing in a search in firefox's search box does the same thing.

Now here is where it gets really strange. "dig google.com" gives me an ip 216.239.57.99 for google. I type that into firefox's address bar and it loads up. Although its some kind of international page because it says "Google English". If I put in the google.de ip (216.239.59.104) it goes to the same page. But if I put in google.de itself it doesn't load (same behaviour as google.com).

Now news.google.com works. And clicking on my gmail bookmark (that takes me directly into the mailbox) work, but If I log out it doesn't load up the log in page.

ping [www.google.com](www.google.com) works. 

I rebooted to windows, firefox loads up google there fine.

I installed epiphany to make sure it wasn't a browser problem, but it behaves the same way.

So next I turn off Firestarter, and google loads up fine.

This is a new install, so firestarter is set to the default rules, with the exception that I enabled it to share Internet with eth1 (there are 2 NICs in this system).

Firestarter is ver 1.0.1, which apt reports as being up to date (well everything is up to date)

Ok so lets recap the weirdness:

- google.com won't load
- all other pages load (that I've tried)
- news.google.com loads
- gmail loads, but the gmail login page won't
- dig google.com returns an ip
- google's ip loads "google english"
- google.de won't load
- google.de's ip loads "google english"
- ping google.com is successful
- turn off firestarter and google works again.
- turn on firestarter and google stops working again.

Anyone have any ideas on this?

---

### Post by kkvenkit on 2005-06-13
I'm experiencing similar problems on my desktop, but do not on my laptop. Both are running the same version of ubuntu and all packages.

My desktop, however, uses hostap to create wlan0 because of a D-Link 520e1 card. My laptop has only eth0 (which is also wireless). I wonder if this is related...

---

### Post by pixelum on 2005-06-13
Same problem here exactly. I've searched all over the net for any info about this issue and this thread is the first I see that describes it. I wrote to the Firestarter people (fs-security.org, if memory serves) to let them know about this. Might it be a Ubuntu specific problem ?

---

### Post by pangloss on 2005-06-13
same problem here, but I notice it with some other web pages as well.

---

### Post by crispingatiesa on 2005-06-13
The same here, I just discovered during the weekend (it was ok before) , I'm also having problems with files with attachements (if to big)  in evolution. Sometimes they go thru sometime don't . By disconeccting firestarter everything works like a charm. 

I'm running Hoary with a wireless Dlink card in a home network.

---

### Post by crispingatiesa on 2005-06-13
I tried something else, I installed Internet Explorer with CrossoverOffice and tried again. The same problem with google, so it seems to be google + firestarter + ubuntu

---

### Post by PhoenixP3K on 2005-06-13
Well, I'm adding up to the long list. What surprised me is that it happened all of a sudden. 

I didn't find a way to fix it.

---

### Post by matthew on 2005-06-13
I tried and tried and could not reproduce the problem on my machine. I'm not sure what could be causing this, but I thought I would at least chime in with a counter-example to make the issue more strange.

---

### Post by Stilgar on 2005-06-13
Well it's good to know that I'm not alone, so if I am going crazy I'll have some company at the asylum.

Well to give a little more info, my NIC is a wired NIC, so we can eliminate it being a wireless problem (a lot of people here seem to have wireless).

I just installed Ubuntu this weekend. I figured it was a problem with my install, but a lot of people are reporting that it worked previously, they just started having the problem recently. 

Debian has 1.0.3 in their tree, I'm going to try that to see if that works. Mayby ubuntu just needs to use a more recent version of firestarter.

---

### Post by tread on 2005-06-13
My problem with firestarter is that gaim doesnt connect to msn if firestarter is enabled. I've made sure all the required ports are allowed. If I disable firestarter, I can log on to msn, then enabling firestarter doesnt kill my msn session. Its just the logging into msn which is the problem.

---

### Post by Stilgar on 2005-06-13
Ok I got the 1.0.3 version from debian:

[http://packages.debian.org/stable/admin/firestarter](http://packages.debian.org/stable/admin/firestarter)

and it loads up google perfectly. So whatever the problem is it seems to be specific for the 1.0.1-1ubuntu2 firestarter.

Anyways I submitted a report: [https://launchpad.ubuntu.com/malone/bugs/1018](https://launchpad.ubuntu.com/malone/bugs/1018)

I'm guessing that they just need to ubuntuise the debian package and put it into ubuntu's apt system and we should be able to update it and everything should be fine.

In the meantime, I would guess it should be ok to use the debian package (it works for me). Although I'm new to ubuntu so you might not want to listen to me...

---

### Post by crispingatiesa on 2005-06-14
I did what stilgar did and... it works now. Thanks a lot.., by the way what's the current price of spice in Dune today Stilgar? :-)

---

### Post by Stilgar on 2005-06-14
[QUOTE=crispingatiesa]I did what stilgar did and... it works now. Thanks a lot.., by the way what's the current price of spice in Dune today Stilgar? :-)[/QUOTE]

Well the only problem with the debian package is it dumps every hit on the firewall to  the logs and to the console, which can be very annoying. I don't think the ubuntu pacakge did that.

And the price of the spice is whatever Muad'Dib wants it to be, of course. If you a proble with that I'll have your water.

---

### Post by PhoenixP3K on 2005-06-14
I tryed installing a new version of Firestarter, but failed. Version 1.0.3 is not ready for Ubuntu I think. 

The thing I don't understand is why it's still version 1.0.1ubuntu that is in the universe library? It's a 2 version skip, they might of fixed that bug since then.

Now can anyone suggest an other firewall? Or do we even need a firewall?
I've checked on a security website an most of my ports were closed and a few were stealth. So I guess Linux has a minimal defense?

---

### Post by crispingatiesa on 2005-06-14
Reason is that even though you uninstalled firestarter, what you probably did was to unnistall the gtk front end but the firewall is still running. 

Did you download the .deb package and used dpk -i <packagename.deb>?

---

### Post by PhoenixP3K on 2005-06-14
[QUOTE=crispingatiesa]Reason is that even though you uninstalled firestarter, what you probably did was to unnistall the gtk front end but the firewall is still running. 

Did you download the .deb package and used dpk -i <packagename.deb>?[/QUOTE]

I tryed the RPM package. used alien -i firestarter-1.0.3.rpm

The debian package was a tar.gz and I can never manage to compile a program. I was careful enought to uninstall and delete all firestarter 1.0.1-1ubuntu2 files from the computer.

I am using Opera as default web browser and to connect to IRC. I'm running Hoary 5.04

The problem might of start appearing after uninstalling Mozilla Firefox...

---

### Post by PhoenixP3K on 2005-06-14
Found the .deb, installed it but can't run it... asks for root password?? I've read something to do with that isn't it gtksu or something?

---

### Post by crispingatiesa on 2005-06-14
Use: sudo dpkg -i <packagename.deb>  it should work, the deb version should be 1.03, in one of stilgar's post he included the link to the .deb package

To run it u can include the line "sudo firestarter --start-hidden"  in System => Preferences => Sessions => Startup Programs

---

### Post by chettyk on 2005-11-20
I have had Hoary Hedgehog with Firestarter running on both my desktop and laptop without a problem for several months now. But during recent days, I noticed that I could not access Google search ([www.google.com](www.google.com)) or Gmail. By a long process of trial and error, I finally realised that it was Firestarter that was creating the problem. The moment I shut it down, there was no problem accessing Google and Gmail. Start up Firestarter and the problem reappeared.

I prefer to have a firewall up and running, even though I am not running any server applications. So I tinkered around with the options in the 'Preferences' menu of Firestarter. Turns out that if I untick 'Block broadcasts from external network' under Advanced Options (Edit -> Preferences -> Advanced Options), Firestarter stops blocking Google and Gmail.

I have not changed the Firestarter options from the time I installed it. I'd love to know why this problem has manifested only now.

---

### Post by greghill on 2005-11-29
Thought I was the only one having this problem. My system behaves the same, and won't open any site containing the term "google". Only when Firestarter is running. As soon as I shut down Firestarter, everything is normal. Even my own web site, which has Google ads enabled, won't load.
Really strange. Have been trying to solve this problem for about 3 months now, without success. If anyone finds a solution to this, I'd like to know too. Thanks.
Greg

---

### Post by chantal on 2006-02-03
I am using Firestarter 1.0.1 with Hoary to surf the net from behind a router (Thomson 510 v4 ADSL), and I haven't had any problems with Google which I use as my home page for Epiphany and Firefox. My "Block broadcasts from  external networks" box is still ticked and I don't use ICMP or ToS filtering.

---

### Post by lordwolf on 2006-03-08
hi!

is anybody still going through this thread? i have EXACTLY the same problem, but the thing is, i don't think i even have a firestarter installed! can anybody help me?

:confused:

---

