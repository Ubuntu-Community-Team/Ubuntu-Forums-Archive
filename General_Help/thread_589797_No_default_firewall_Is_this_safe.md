---
title: "No default firewall? Is this safe?"
date: 2007-10-24
forum: General Help
---

### Post by Meson on 2007-10-24
How come there isn't a firewall installed with Ubuntu by default?  What about users that connect directly to the internet?  Is this safe?

---

### Post by mannih2001 on 2007-10-24
It's reasonably safe, yes. A default Ubuntu install doesn't come with any active internet services. Thus all ports should be closed and there should be nothing to be afraid of. Unless you hate to be pinged, of course.

---

### Post by angry-broadcom-user on 2007-10-24
I was thinking about this recently, I did a firewall test on a website (sorry i can't remember what it was) and it only failed on one test (as ubuntu has a built in firewall), but if you want a firewall, this website tells you how to set up 'Firestarter' - a popular choice.
[http://www.debianadmin.com/secure-ubuntu-desktop-using-firestarter-firewall.html]("http://www.debianadmin.com/secure-ubuntu-desktop-using-firestarter-firewall.html")
[http://www.fs-security.com/]("http://www.fs-security.com/")

---

### Post by Meson on 2007-10-24
> **mannih2001 said:**
> It's reasonably safe, yes. A default Ubuntu install doesn't come with any active internet services. Thus all ports should be closed and there should be nothing to be afraid of. Unless you hate to be pinged, of course.
So if I have a p2p program and pidgin, my security depends on the security of those specific programs?

I'm not really a fan of firestarter.  The website has a 2005 announcement saying they're working on a new version.... I don't know what happened to that.  Also I use a wired connection at home and wireless out in public, and there doesn't seem to be much functionality to handle this.

---

### Post by mahousaru on 2007-10-24
> **angry-broadcom-user said:**
> as ubuntu has a built in firewa

Sorry just going to pick on this tiny bit :p

Unless you have run installed something configure that configures on boot, then the built in firewall should be set to allow all.  The built in firewall is the rock solid iptables, and where a XP software firewall is akin to wearing a pair of tights to protect your legs from a bunch of piranhas, iptables can actually be safely used as a internet firewall to protect your network.

iptables can be a little bit confusing at first, but if you understand top down rules and the idea of bouncers on a night club entrance with a list of who to allow or deny then it becomes a little easier to  understand.

To check what your firewall is set as you can use the command

```

sudo iptables -L

```

tbh apart from having a gander at it, I wouldn't recommend using the command line, but something like Firestarter as angry-broadcom-user suggested.

All of these tools such as Firestarter, Guarddog, fwbuilder are graphical front ends for configuring iptables.

ofc doesn't matter how good iptables is, if it isn't configured properly then it probably won't offer you much protection.

Remember with XP, you have so much exposing that if it represented your real life dress sense, you would most defiantly get arrested for indecent exposure :D

---

### Post by mannih2001 on 2007-10-24
> **Meson said:**
> So if I have a p2p program and pidgin, my security depends on the security of those specific programs?

Correct. A firewall wouldn't change a thing about that because you would have to allow connections to the ports opened by those applications.

---

### Post by oldos2er on 2007-10-24
You might want to read [http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by nacho32 on 2007-10-24
> **angry-broadcom-user said:**
> I was thinking about this recently, I did a firewall test on a website (sorry i can't remember what it was) and it only failed on one test (as ubuntu has a built in firewall), but if you want a firewall, this website tells you how to set up 'Firestarter' - a popular choice.
[http://www.debianadmin.com/secure-ubuntu-desktop-using-firestarter-firewall.html]("http://www.debianadmin.com/secure-ubuntu-desktop-using-firestarter-firewall.html")
[http://www.fs-security.com/]("http://www.fs-security.com/")


this is the site I believe do full all service scan
[sheild up]("http://www.grc.com/x/ne.dll?rh1dkyd2")

---

### Post by az on 2007-10-24
> **nacho32 said:**
> this is the site I believe do full all service scan
[sheild up]("http://www.grc.com/x/ne.dll?rh1dkyd2")

...Which will tell you that closed ports are insecure.  Which is completely false.  To think that having your firewall drop connections instead of refusing them aloows you to be "invisible" is a false sense of security.  Every single time you browse an internet site, they know who you are and what your IP address is.

---

### Post by Meson on 2007-10-24
the more i read the less i know

---

### Post by mahousaru on 2007-10-24
In addition to what az says, also an attacker can tell if someone is there if a device is set to drop.  If you drop a packet it will cause a delay so if someone knows what they are looking for, they can spot that something is at that address.  Dropping is meant to be pretty internet unfriendly, from what I've been told the polite thing to do is to deny.

*Edit* 

The above is in-regards to people thinking they are invisible by setting their firewalls to drop packets instead of denying them.  I remember grc used to harp on about it.

---

### Post by ViRMiN on 2007-10-24
Why would you want to be polite, if there's no legitimate reason to be trying to connect to a service you're either not offering or are protecting?  Go with "drop" I say...

---

### Post by KCPokes on 2007-10-24
> **ViRMiN said:**
> Why would you want to be polite, if there's no legitimate reason to be trying to connect to a service you're either not offering or are protecting?  Go with "drop" I say...

I agree.  The point is that it is not going to be common knowledge to everyone how a firewall handles a drop, thus the more people that assume there is nothing there, the better.  If someone wants to go fishing for something that is not there, I'm sure not going to be polite about telling them they are out of luck.

---

### Post by mahousaru on 2007-10-24
> **ViRMiN said:**
> Why would you want to be polite, if there's no legitimate reason to be trying to connect to a service you're either not offering or protecting?  Go with "drop" I say...

That is being polite to all the routers in between u and the scanner ;p

A good attacker would not be bothered by a firewall dropping packets.  If you have any internet services running that need to be exposed such as a web server then dropping doesn't do a thing.

For desktops a lot of the paranoia I think comes from the grief everyone has suffered at the hands of XP et al.  Ubuntu has taken a step in the right direction with making sure no services are available on the internet facing interface.  Remember lo is an interface and external traffic should never touch any services on them.

Errr not common knowledge?  It is like one of the first things I've been told in the firewall sections of every security course I've been on....  And I am guessing that lots of the naughty people* have a lot more geek levels then I do.

The only way to truly emulate being invisible is to cut your connection to the internet.  Even if you are dropping traffic to a specific port, the router needs to know you are there so will normally still send a packet to you which you drop and that causes the delay.  If you were really not there then the router would send an immediate host does not exist.

*I'm thinking attackers with more experience then just running a script...

---

### Post by ViRMiN on 2007-10-24
> **mahousaru said:**
> A good attacker would not be bothered by a firewall dropping packets.  If you have any internet services running that need to be exposed such as a web server then dropping doesn't do a thing.

That's a fair point; they already now a machine exists if you've got a service open; bit different if you've nothing on offer and are paranoid ;)

---

### Post by Meson on 2007-10-24
So if  you're running a webserver that's only listening on port 80, is there a need for a firewall?

If no, does it become necessary if say, you want to allow SSH but only to the local network and a set number of satallite offices?

---

### Post by dewey on 2007-10-24
> **Meson said:**
> If no, does it become necessary if say, you want to allow SSH but only to the local network and a set number of satallite offices?
You should be able to configure static ip addresses that are allowed to access the port with iptables.  There may be an option in the SSHD configuration, but I've never gone looking for it.

---

### Post by az on 2007-10-24
> **Meson said:**
> So if  you're running a webserver that's only listening on port 80, is there a need for a firewall?

If no, does it become necessary if say, you want to allow SSH but only to the local network and a set number of satallite offices?

In the context of a desktop system, you do not need a firewall.

In the context of an internet server, yes they are very useful.  

But when someone refers to what is installed "by default", I assume that they are referring to the ubuntu desktop and not the Ubuntu server.

---

### Post by bodhi.zazen on 2007-10-24
Firewalls are a recurring discussion :p

Here is some starting information :

The Ubuntu (Linux) firewall is called IP tables and is included with your Ubuntu installation.

The default settings are permissive (meaning they allow all traffic) and, if you are not running a server, you may feel this is adequate protection.

If you would like to configure your firewall the two options are to use a gui front end or write IP rules for yourself (there are various scripts on the web that will help with this).

The most popular gui tools are Firestarter and Guard dog (KDE). Keep in mind that these applications are not firewalls, but rather configuration tools. This is sometimes a source of confusion as the application should be run *only to configure your firewall*. Once configured, IP tables (the actual firewall) is active (at boot) *without having to run firestarter/guarddog*. firestarter will monitor traffic, but it runs as root and there are better monitoring programs, so configure you firewall, shut down firestarter/grauddog, and let IP tables do the rest :twisted:.

See these links for further information/how to use these tools :

[center][[color=red][Size=6]How to Firestarter[/size][/color]](http://www.debianadmin.com/secure-ubuntu-desktop-using-firestarter-firewall.html) - [[color=blue][size=6]How to Guard Dog (KDE)[/size][/color]](http://www.simonzone.com/software/guarddog/manual2/index.html)[/center]

Firestarter Home Page : [http://www.fs-security.com/](http://www.fs-security.com/)

**Default Firestarter Policies**:
> [list][*]New inbound connections from the Internet to the firewall or client hosts are blocked.
[*]The firewall host is freely allowed to establish new connections.
[*]All client hosts are allowed to establish new connections to the Internet, but not to the firewall host.
[*]Traffic from the Internet in response to connection requests from the firewall or client hosts is allowed back in through the firewall.[/list]

If you would like to learn more about IP tables, here are some starting points:

_**Iptables references_** :
[list][*][https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)
[*][http://www.linuxguruz.com/iptables/howto/](http://www.linuxguruz.com/iptables/howto/)
[*][http://iptables-tutorial.frozentux.net/iptables-tutorial.html](http://iptables-tutorial.frozentux.net/iptables-tutorial.html)[/list]

If you would like to learn more about basic Ubuntu security, please see this thread :

[[color=black]Ubuntu Security[/color]](http://ubuntuforums.org/showthread.php?t=510812)

If you would like to debate/discuss the use of firewall, please post here:

[ Recurring Discussions](http://ubuntuforums.org/forumdisplay.php?f=302)

---

### Post by mahousaru on 2007-10-24
@bodhi.zazen - Just responding to the quoted post, but if it continues I'll take it to the recurring section :)

> **Meson said:**
> So if  you're running a webserver that's only listening on port 80, is there a need for a firewall?

If no, does it become necessary if say, you want to allow SSH but only to the local network and a set number of satallite offices?

Your post is a good example of when you do need a firewall.  If it was just port 80 opened and exposed to the whole world then do you need another service running?  Well personally if you don't mind the administrative overhead then I would configure iptables just so I could have psad running and warning of attacks.  iptables on its own allowing port 80 means diddle squat, what you need is a rule to log and something to detect attacks.

Now in the case of your example, as soon as you have multiple services with different zones of access then yes you should employ iptables, or at the very least use a tcpwrapper.  

BTW this is not considering using the network for your access control!

---

### Post by bodhi.zazen on 2007-10-24
> **mahousaru said:**
> @bodhi.zazen - Just responding to the quoted post, but if it continues I'll take it to the recurring section 

Thank you mahousaru ;)

There is no problem with discussing how to firewall or the technical aspects, and I am in favor of leaving this thread open as long as it stays on topic.

---

### Post by Meson on 2007-10-25
So I get the feeling that on a Desktop a single firewall isn't really necessary and the program listening on each port (which is the only reason the port is open in the first place) should act as its own firewall.  For example, SSHD might as well be responsible for limitting its connections to specific hosts, rather than the firewall doing the job.

Sorry bodhi, I had already read your intro to security, but I still had questions.

---

### Post by mahousaru on 2007-10-25
@Meson - Hmmm if a desktop program will perform some type of access control (act like a firewall) or not is dependant on the program.  I know some like eMule you can load block lists, but this doesn't protect  the service from being compromised if there is a vulnerability out for it and someone buffer overflows it.  The firewall should act as a barrier before anything hits the program itself.  This is why the earlier stress of why it is kinda* pointless to firewall if you want expose all of your incoming ports to the evil that is the internet. 

**Kinda pointless unless you start looking at more advance stuff then just blocking*.

When you think about firewalls you should have a distinct picture in your mind of what it actually does.  For example for stuff going out of your pc

PC -> outgoing rules -> Internet

Most basic firewalls allow all outgoing.  *The one I stole from paranoid penguin many years ago that I use on my work servers actually needs every out going app specified in it.  Even then the connections are tracked and anti spoof rules are applied.  But is this type of administrative overhead most defiantly not needed on a desktop PC*.

Then there is the important part, which is stuff coming into your PC.

Internet -> incoming rules -> PC

Now this is where you have to think about what is running and if a firewall will be beneficial.  You have already stated desktop apps, so we can rule out all the stuff such as apache etc.  Most of the time the ports your program open such as bittorrent you want the whole world access to it, so a FW would give no real benefit.  But lets look at something like hotwayd.  Now this is a service that runs via xinetd and acts like a pop3 server converting webmail to pop mail.  This I would defiantly not want anyone from the internet connecting to.  The good thing is that by default it is set to localhost only so any connections from the internet will hit a non open port.  The reason why is it only accepts incoming pop3 requests from the loopback interface (which is internal only).

What that boils down to is that you have to consider the interface the program runs on as well.  ie. stuff running on the lo interface should be safe from internet even through you can connect to it. 

*Ofc if I am feeling paranoid and I do have a firewall wall up, I do have a anti-spoof rule which explicitly states no passing of localhost traffic to the internet!*

Well I hope I haven't muddied the water even more :p

---

### Post by Meson on 2007-10-25
You did bring up another question.  Say I have eMule open to the internet (of course otherwise it will be useless).  Is the only way to help ward off eMule specific vulnerabilities to run eMule as its own user with no other access to the system?

---

### Post by mahousaru on 2007-10-25
Opps sorry with Ubuntu the equivalent is aMule.  But the funny thing is eMule is one of the rare Windows programs that actually installs a unprivileged user and you can force it to run with non admin rights *shocked*

If you run aMule with your normal account then it will run as a normal user, basically it can only affect where you have rights.  It would need to sudo to escalate rights to do stuff to the system.  If you want to enforce a more secure model, then I suggest reading up how to create an AppArmor profile for it.

With AppArmor you can sandbox a process even further.

---

### Post by Meson on 2007-10-25
Ok, now I think I'm getting a little off topic, but...

If I'm not worried about any personal data contained by firefox... would you consider the NoScript plugin useless if ff is properly apparmored?

---

### Post by mahousaru on 2007-10-25
Since every time someone goes off topic a baby penguin is clubbed to death and eaten by a walrus that looks looks suspiciously like Steve Ballmer I shall PM you instead.

---

### Post by bodhi.zazen on 2007-10-25
> **Meson said:**
> Ok, now I think I'm getting a little off topic, but...

If I'm not worried about any personal data contained by firefox... would you consider the NoScript plugin useless if ff is properly apparmored?

Absolutely not !

Apparmor limits firefox access to your system files.

NoScript blocks java script hopefully limiting browser hijacks and ad block.

---

