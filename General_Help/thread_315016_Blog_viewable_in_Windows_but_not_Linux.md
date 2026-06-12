---
title: "Blog viewable in Windows but not Linux"
date: 2006-12-08
forum: General Help
---

### Post by SteveHoffmanUK on 2006-12-08
Using Dapper Ubuntu 6.06 with desktop i386 installation.

My son's blog is at [http://www.hofflimits.com](http://www.hofflimits.com)

I can view it with Windows XP Firefox without problems, but when I try to view it using Ubuntu Firefox I get error message:
> ERROR:  [www.hofflimits.com](www.hofflimits.com) is temporarily unavailable or does not exist. Please check the address and try again.

This is a permanent message - the blog is **never** available in Linux but always available in Windows. I thought it might be some problem with Linux Firefox, so I installed the Linux Opera browser and get the same message. 

Possibly relevant is the fact that the domain name is registered at reg-123.co.uk, who redirects it to hofflimits.blogger.com.

Can someone with both Windows and Ubuntu try to access this blog and confirm whether they have the same problem in Ubuntu? I didn't think it was possible to get different results from accessing the Web depending on the operating system you are running!

---

### Post by aysiu on 2006-12-08
Works fine for me in Ubuntu Firefox.

---

### Post by Psykotik on 2006-12-08
Same here. That's amazing, it has to be related to a bit of php code checking what OS is visiting...

EDIT : Since a new message has been sent :) I wrote "same here" because I cannot get the website under Ubuntu.

Running Ubuntu 6.10 and Firefox 2.0

---

### Post by aysiu on 2006-12-08
> **Psykotik said:**
> Same here. That's amazing, it has to be related to a bit of php code checking what OS is visiting...

EDIT : Since a new message has been sent :) I wrote "same here" because I cannot get the website under Ubuntu.

Running Ubuntu 6.10 and Firefox 2.0
That's weird. I'm also running Ubuntu 6.10 and Firefox 2.0 (I'm using the Firefox from Mozilla, not Ubuntu's Firefox--not sure if that makes a difference). But I can see the site just fine. I'm not using User Agent Switcher or anything special.

---

### Post by doobit on 2006-12-08
you can set Firefox to allow redirects. Check your security settings in preferences.

---

### Post by SteveHoffmanUK on 2006-12-08
Doobit wrote:> you can set Firefox to allow redirects. Check your security settings in preferences.

Where exactly in Preferences? I can't find any such option either under Preferences | Privacy or Preferences | Advanced | Security.

Am using Firefox 1.5.0.8 (latest Ubuntu version)

---

### Post by raid517 on 2006-12-08
> you can set Firefox to allow redirects. Check your security settings in preferences.

There's nothing in my security settings for that.

---

### Post by IcemanV9 on 2006-12-08
@SteveHoffmanUK - it works fine on my box. It runs on Dapper [i386] & Ubuntu-FireFox [1.0.5.8]. I don't think it's your browser(s). It could be related to the networking.

---

### Post by melancholeric on 2006-12-08
Didn't work for me, dapper & opera / epiphany /  ff 1.5.0.8

---

### Post by matthew on 2006-12-08
I'm using Ubuntu 6.10 with Firefox 2.0 and the site works fine for me.

---

### Post by earobinson on 2006-12-08
It dont work for me... I'm using Ubuntu 6.10 with Firefox 2.0

---

### Post by SteveHoffmanUK on 2006-12-08
IcemanV9 wrote:
> @SteveHoffmanUK - it works fine on my box. It runs on Dapper [i386] & Ubuntu-FireFox [1.0.5.8]. I don't think it's your browser(s). It could be related to the networking.

I agree that it is unlikely to be my browsers, since two different ones fail to access it on Ubuntu.

You may be right about the networking, but I need to point out that both my Windows XP machine (which can view the blog) and my Ubuntu machine (which cannot) are networked using the same wireless ADSL router and, of course, access the web through the same ISP. 

BTW, I have just tried to access the blog from my laptop, which is Ubuntu Edgy 6.10, and I get the same error message and cannot view the blog.

Any other thoughts? I appreciate everyone&#347; suggestions. This seems very weird to me.

---

### Post by bapoumba on 2006-12-08
So I am using epiphany-2.16.1 (edgy repositories) and it did not work.
To be noted, I got the same message with lynx (text web browser running from a terminal) :     
```
ERROR:  www.hofflimits.com is temporarily unavailable or does not exist. Please check the address and try again.
```.

```
ping www.hofflimits.com
PING users.blogware.com (216.40.34.100) 56(84) bytes of data.
From 10.78.254.203 icmp_seq=1 Packet filtered
From 10.78.254.203 icmp_seq=7 Packet filtered
From 10.78.254.203 icmp_seq=19 Packet filtered
From 10.78.254.203 icmp_seq=26 Packet filtered

--- users.blogware.com ping statistics ---
29 packets transmitted, 0 received, +4 errors, 100% packet loss, time 28021ms

ping ubuntuforums.org
PING ubuntuforums.org (82.211.81.186) 56(84) bytes of data.
64 bytes from ohiggins.ubuntu.com (82.211.81.186): icmp_seq=1 ttl=49 time=63.4 ms
64 bytes from ohiggins.ubuntu.com (82.211.81.186): icmp_seq=2 ttl=49 time=63.4 ms
64 bytes from ohiggins.ubuntu.com (82.211.81.186): icmp_seq=3 ttl=49 time=62.3 ms
64 bytes from ohiggins.ubuntu.com (82.211.81.186): icmp_seq=4 ttl=49 time=63.0 ms

--- ubuntuforums.org ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3009ms
rtt min/avg/max/mdev = 62.348/63.081/63.476/0.516 ms
PING ubuntuforums.org (82.211.81.186) 56(84) bytes of data.
```


Probably a network thing (what is filtering ? I do not know much about networking).

---

### Post by aysiu on 2006-12-08
Can anyone think of why it would work on my Ubuntu Firefox? I don't think I have any special settings enabled.

---

### Post by earobinson on 2006-12-08
i dont think its a firefox setting i think its a network setting do what the above post did and ping the site see what you get

---

### Post by bapoumba on 2006-12-08
@ aysiu : I could access to the exact same page as you showed via google cached pages.

The filtering thing in ping looks like this site allows only trusted IPs through their firewall. Once again, I am not a networking expert, so I may be wrong. And that is not consistent with SteveHoffmanUK being able to access the blog from Windows.

@ SteveHoffmanUK : anything in the blog's or the site policy ?

---

### Post by Lord Illidan on 2006-12-08
I can see the blog just fine here.

Ubuntu 6.10 + Firefox 2.0

---

### Post by Lord Illidan on 2006-12-08
It can be a problem with your dns settings, I think. Do you know how to change them to make them identical with your windows counterparts?

---

### Post by SteveHoffmanUK on 2006-12-08
bapoumba wrote:
> @ SteveHoffmanUK : anything in the blog's or the site policy ?

It's not my site, it's my son's, although I doubt he could answer the question. I can't imagine what kind of policy could cause this.

Trusted IP's? No, because, as you have pointed out, it works OK on my Windows machine via the same ISP as I have for my Ubuntu machines.

Browsers? No, because it works OK on my Windows Firefox.

OSes? No, because some here on Ubuntu can access it.

What else?

On my system the only variable that changes between the machine that works and the one that doesn't is the OS: Windows works, Linux (Ubuntu) doesn't.

Is there some setting on my Ubuntu system that is causing this?

---

### Post by SteveHoffmanUK on 2006-12-08
Lord Illidan wrote:
> It can be a problem with your dns settings, I think. Do you know how to change them to make them identical with your windows counterparts?

Haven't a clue about how to change dns settings. Can you please advise?

Aren't the dns settings done in the ADSL wireless router? If they are, then, of course, there's only the one setting used by both the Windows and the Ubuntu machines. Just a thought, and maybe an ignorant one!

ON EDIT:
Just to clarify, in my Ubuntu Networking settings, I have my wireless connection activated as wlan0; the DNS tab, under DNS Servers shows 192.168.0.1, the login address for my wireless router (Netgear DG834GT).

---

### Post by doobit on 2006-12-11
> **raid517 said:**
> There's nothing in my security settings for that.

Sorry... it's been a few days since I last looked here. I'm using Firefox 2.0. There is a checkbox for a phishing filter that blockes redirects to known phishing sites or sites not listed in Google, if that option is checked. It's in Options->Security
It probably doesn't affect the blog, but it can't hurt to check.

---

### Post by earobinson on 2006-12-12
ok so I installed firefox under wine (super easy btw) and firefox runs fine but I still can not view the blog, so its probaly a ubuntu network setting somewhere else

---

### Post by earobinson on 2006-12-12
so I tried the website on windows at work and got the same results [img]http://lh5.google.com/image/earobinson/RX7L-_C3BMI/AAAAAAAAAAw/9gGIRTEfKL0/cantViewInWindows.JPG?imgmax=1024[/img]

---

### Post by SteveHoffmanUK on 2006-12-12
Doobit wrote:
> I'm using Firefox 2.0. There is a checkbox for a phishing filter that blockes redirects to known phishing sites or sites not listed in Google, if that option is checked. It's in Options->Security

I am now using Firefox 2.0 in both Dapper (desktop) and Edgy (laptop), and there&#347; no such menu item as Options. Where do I find this?? 

There is Edit>Preferences>Security but nothing there about redirects.

Please explain!

Thanks

---

### Post by SteveHoffmanUK on 2006-12-14
So, to summarise the results so far:

Respondents who cannot view the blog [http://www.hofflimits.com](http://www.hofflimits.com) are:

1. Me: Ubuntu 5.05 Dapper and 6.10 Edgy, Firefox 1.5.0.8 and Firefox 2.0; Netgear wireless router connected to UK ISP Vispa

2. Psykotik: Ubuntu 6.10 Edgy User

3. melancholeric: Ubuntu 6.06 Dapper  Opera / Epiphany / Firefox 1.5.0.8

4. earobinson: Ubuntu Edgy 6.10 Firefox 2.0; also Firefox under Wine

5. bapoumba: Ubuntu 6.10 Edgy epiphany-2.16.1 (edgy repositories)

Respondents who can view the blog

1. Me: Windows XP Home, Firefox 1.5.0.8; Netgear wireless router connected to UK ISP Vispa

2. Aysiu: Ubuntu 6.10 Edgy, Firefox 2.0

3. IcemanV9: Ubuntu 6.06 Dapper [i386] Ubuntu-FireFox 1.0.5.8

4. matthew: Ubuntu 6.10 Edgy  Firefox 2.0 

5. Lord Illidan Ubuntu 6.10 Edgy Firefox 2.0

What can we conclude? There is no common factor that identifies either operating systems, Ubuntu versions or browsers as the cause of not being able to see the blog.

Some respondents suggest that the cause must lie in networking/dns settings, which might be different between my XP and Ubuntu machines, both of which use the same wireless router and ISP. I will therefore repost the problem in the Networking forum to see if experts there can help.

Many thanks to all who have responded to this thread.

---

### Post by raid517 on 2006-12-14
Try Useragentswitcher for firefox - just to be sure there is no hanky panky going on with with the host refusing certain clients.

However as many people have said already now, it sounds like Firefox is set up to prevent redirects.

If so, this isn't a flaw - it's a feature - meant to prevent phishing attacks and spoofing.

---

### Post by mcduck on 2006-12-14
> **raid517 said:**
> Try Useragentswitcher for firefox - just to be sure there is no hanky panky going on with with the host refusing certain clients.

However as many people have said already now, it sounds like Firefox is set up to prevent redirects.

If so, this isn't a flaw - it's a feature - meant to prevent phishing attacks and spoofing.

It can't be useragent thing, as many people with FF are also able to see the page.. Me included.

---

### Post by earobinson on 2006-12-14
> **SteveHoffmanUK said:**
> So, to summarise the results so far:

Respondents who cannot view the blog [http://www.hofflimits.com](http://www.hofflimits.com) are:

1. Me: Ubuntu 5.05 Dapper and 6.10 Edgy, Firefox 1.5.0.8 and Firefox 2.0; Netgear wireless router connected to UK ISP Vispa

2. Psykotik: Ubuntu 6.10 Edgy User

3. melancholeric: Ubuntu 6.06 Dapper  Opera / Epiphany / Firefox 1.5.0.8

4. earobinson: Ubuntu Edgy 6.10 Firefox 2.0; also Firefox under Wine

5. bapoumba: Ubuntu 6.10 Edgy epiphany-2.16.1 (edgy repositories)

Respondents who can view the blog

1. Me: Windows XP Home, Firefox 1.5.0.8; Netgear wireless router connected to UK ISP Vispa

2. Aysiu: Ubuntu 6.10 Edgy, Firefox 2.0

3. IcemanV9: Ubuntu 6.06 Dapper [i386] Ubuntu-FireFox 1.0.5.8

4. matthew: Ubuntu 6.10 Edgy  Firefox 2.0 

5. Lord Illidan Ubuntu 6.10 Edgy Firefox 2.0

What can we conclude? There is no common factor that identifies either operating systems, Ubuntu versions or browsers as the cause of not being able to see the blog.

Some respondents suggest that the cause must lie in networking/dns settings, which might be different between my XP and Ubuntu machines, both of which use the same wireless router and ISP. I will therefore repost the problem in the Networking forum to see if experts there can help.

Many thanks to all who have responded to this thread.
I also tried it with firefox windows, at work and got the same thing and ubuntu at home and got the same thing

Sorry but the site is not very good if so many comptuer cant see it ( I have tried 3)

---

### Post by mcduck on 2006-12-14
> **earobinson said:**
> 
Sorry but the site is not very good if so many comptuer cant see it ( I have tried 3)

Probably nothing wrong with the site itself, but the hosting service instead..

---

### Post by raid517 on 2006-12-14
> **mcduck said:**
> It can't be useragent thing, as many people with FF are also able to see the page.. Me included.


It's worth a shot.

To get to the bottom of anything, you have to eliminate all the possibilities first.

Anyway why are people ignoring the most obvious thing to check first - which is FF security settings?

These are likely to be the only varying factor between different users.

---

### Post by Lord Illidan on 2006-12-14
> **earobinson said:**
> I also tried it with firefox windows, at work and got the same thing and ubuntu at home and got the same thing

Sorry but the site is not very good if so many comptuer cant see it ( I have tried 3)

It doesn't have anything to do with the site, otherwise none of us would be able to see it.

Hosting? Perhaps.

inetnum:        194.154.164.0 - 194.154.165.255
netname:        UK-PIPEX-ATLAS-PROJECT-1
descr:          Atlas Project-1
country:        GB
admin-c:        HM655-RIPE
tech-c:         HM655-RIPE
status:         ASSIGNED PA
remarks:        ------------------------------------------------------
remarks:
remarks:        Please direct Abuse complaints to [email]hosting-abuse@pipex.net[/email]
remarks:        Complaints directed elsewhere may not be actioned.
remarks:
remarks:        ------------------------------------------------------
mnt-by:         AS5519-MNT
mnt-lower:      AS5519-MNT
mnt-routes:     AS5519-MNT
source:         RIPE # Filtered

role:           Hostmaster Contact
address:        PIPEX Communications
address:        The Hinshelwood Building
address:        Edmund Halley Road
address:        Oxford Science Park
address:        Oxford
address:        OX4 4GB
address:        United Kingdom
phone:          +44 870 909 8181
fax-no:         +44 1865 778 160
admin-c:        MATT1-RIPE
admin-c:        HM655-RIPE
admin-c:        ID40-RIPE
admin-c:        RIZ5-RIPE
admin-c:        FAZ5-RIPE
admin-c:        SJC2-RIPE
tech-c:         MATT1-RIPE
tech-c:         SH1765-RIPE
tech-c:         RIZ5-RIPE
tech-c:         ID40-RIPE
tech-c:         BRI69-RIPE
tech-c:         HM655-RIPE
tech-c:         FAZ5-RIPE
tech-c:         SJC2-RIPE
tech-c:         YSL1-RIPE
nic-hdl:        HM655-RIPE
abuse-mailbox:  [email]abuse@gxn.net[/email]
mnt-by:         AS5519-MNT
source:         RIPE # Filtered

% Information related to '194.154.164.0/24AS5413'

route:          194.154.164.0/24
descr:          PIPEX Communications
descr:          (GXN)
descr:          Carlton House
descr:          27A Carlton Drive
descr:          London
descr:          SW15 2BS
descr:          UK
origin:         AS5413
member-of:      AS5413:RS-PIPEX
remarks:
remarks:        ------------------------------------------------------
remarks:
remarks:        Please direct Abuse complaints to [email]abuse@gxn.net[/email]
remarks:        Complaints directed elsewhere will not be actioned.
remarks:
remarks:        ------------------------------------------------------
remarks:
mnt-by:         AS5413-MNT
source:         RIPE # Filtered

---

### Post by Lord Illidan on 2006-12-14
I can see the site in Firefox, Opera and Konqueror. Definitely not a browser problem then.

Does anyone of you who cannot see the site have DansGuardian or any firewall installed?

---

### Post by bapoumba on 2006-12-14
> **Lord Illidan said:**
> Does anyone of you who cannot see the site have DansGuardian or any firewall installed?

Yes, I have firestarter running, and there is a firewall in my DSL box.
I have no trouble updating with aptitude, or dowloading .ISO files with bittorent, or using jabber or IRC clients and such, you name it.

**Big news**, I did a ping to get the IP and do a whois, but :
```
ping www.hofflimits.com
PING www.hofflimits.com (194.154.164.82) 56(84) bytes of data.
64 bytes from 194.154.164.82: icmp_seq=1 ttl=50 time=65.3 ms
64 bytes from 194.154.164.82: icmp_seq=2 ttl=50 time=58.5 ms
64 bytes from 194.154.164.82: icmp_seq=3 ttl=50 time=66.4 ms
64 bytes from 194.154.164.82: icmp_seq=4 ttl=50 time=58.3 ms
64 bytes from 194.154.164.82: icmp_seq=5 ttl=50 time=60.3 ms
64 bytes from 194.154.164.82: icmp_seq=6 ttl=50 time=58.2 ms

--- www.hofflimits.com ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 5014ms
rtt min/avg/max/mdev = 58.257/61.201/66.422/3.402 ms
```

So the ping is going through now, and I can browse the blog. Could anybody else from the list check that ?

---

### Post by SteveHoffmanUK on 2006-12-14
I pinged on my Ubuntu (non-receiving) machine and got this:
```
Bytes	Source	Seq	Time	Units
64	194.154.164.82	1	88.5	ms
64	194.154.164.82	2	53.1	ms
64	194.154.164.82	3	76.6	ms
64	194.154.164.82	4	65.9	ms
64	194.154.164.82	5	44.7	ms
Time minimum:	44.70 ms
Time average:	69.55 ms
Time maximum:	88.50 ms
Packets transmitted:	5
Packets received:	5
Packet loss:	0%

```

What does this mean? (Networking ignoramus here) :rolleyes:

---

### Post by Lord Illidan on 2006-12-14
> **SteveHoffmanUK said:**
> I pinged on my Ubuntu (non-receiving) machine and got this:
```
Bytes    Source    Seq    Time    Units
64    194.154.164.82    1    88.5    ms
64    194.154.164.82    2    53.1    ms
64    194.154.164.82    3    76.6    ms
64    194.154.164.82    4    65.9    ms
64    194.154.164.82    5    44.7    ms
Time minimum:    44.70 ms
Time average:    69.55 ms
Time maximum:    88.50 ms
Packets transmitted:    5
Packets received:    5
Packet loss:    0%

```What does this mean? (Networking ignoramus here) :rolleyes:

It means that you can access the server. Which is a start.
Do you have a firewall or dansguardian? It could be blocking dns

---

### Post by bapoumba on 2006-12-14
Okay, so we'll need a network wizz here.
This happened with one site I am used to visit, but I do not know the english word for it. Their DNS servers were "flushing" (that is the closest word I can think of). Some IP ranges could access the site, some not. And that was changing with time.

I just checked the blog, could not access it anymore :/

I'll try to put their IP in my /etc/hosts (needs a reboot) :

```
194.154.164.82 hofflimits.com
```

edit : that does not work :/

---

### Post by Snowmayne on 2006-12-14
> **SteveHoffmanUK said:**
> I pinged on my Ubuntu (non-receiving) machine and got this:
```
Bytes	Source	Seq	Time	Units
64	194.154.164.82	1	88.5	ms
64	194.154.164.82	2	53.1	ms
64	194.154.164.82	3	76.6	ms
64	194.154.164.82	4	65.9	ms
64	194.154.164.82	5	44.7	ms
Time minimum:	44.70 ms
Time average:	69.55 ms
Time maximum:	88.50 ms
Packets transmitted:	5
Packets received:	5
Packet loss:	0%

```

What does this mean? (Networking ignoramus here) :rolleyes:

It's basically saying it's making a connection to the address.  Ping is basically something like 1 computer asking another computer 'are you there' and the second computer saying 'yup'. If you see the address, bytes sent and a time in milliseconds, it means the connection's good. Packet loss is in case there's a faulty connection somewhere and some machine somewhere dropped the packet - which means running a tracert for those with the time/inclination ;) 

So in a nutshell your machine called the address and got an answer. So far so good. Now it's just a question of WHY can't you see the page....
you might want to try a ping on the url (from the terminal window type ping [www.hofflimits.com](www.hofflimits.com) and see if that goes to the same address as the page that gives you the error message

BTW, I tried it on Maxthon 1.5.8 (ie 6 shell with tabs!) and firefox 2.0 on a WinXP pro box with no problems and using penguinet to a rhl box was able to access the page in elinks

---

### Post by bapoumba on 2006-12-14
The /etc/hosts thing did not do it, but .... I see that I have IPv6 enabled. Would the members accessing the blog have IPv6 disabled ?

I do not get it O_o :
```
~ $ ping 194.154.164.82
PING 194.154.164.82 (194.154.164.82) 56(84) bytes of data.
64 bytes from 194.154.164.82: icmp_seq=1 ttl=50 time=59.6 ms
64 bytes from 194.154.164.82: icmp_seq=2 ttl=50 time=57.4 ms
64 bytes from 194.154.164.82: icmp_seq=3 ttl=50 time=59.4 ms
64 bytes from 194.154.164.82: icmp_seq=4 ttl=50 time=58.4 ms
64 bytes from 194.154.164.82: icmp_seq=5 ttl=50 time=58.4 ms
64 bytes from 194.154.164.82: icmp_seq=6 ttl=50 time=61.1 ms

--- 194.154.164.82 ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 5011ms
rtt min/avg/max/mdev = 57.432/59.089/61.127/1.189 ms

~ $ ping www.hofflimits.com
PING users.blogware.com (216.40.34.100) 56(84) bytes of data.
From 10.78.254.203 icmp_seq=1 Packet filtered
From 10.78.254.203 icmp_seq=3 Packet filtered

--- users.blogware.com ping statistics ---
13 packets transmitted, 0 received, +2 errors, 100% packet loss, time 12010ms
```

The ping is ok on the IP, but not on the domain name and I cannot access the blog anymore :/ epiphany's cache is empty.

---

### Post by mcduck on 2006-12-14
> **bapoumba said:**
> The /etc/hosts thing did not do it, but .... I see that I have IPv6 enabled. Would the members accessing the blog have IPv6 disabled ?

no, probably it won't matter what you do on your machine if the hosting service is dropping connections from certain IP ranges or something..

edit: I tested with IPv6 enabled and disabled and the page worked with both.

---

### Post by Snowmayne on 2006-12-14
> **bapoumba said:**
> 
```
~ $ ping 194.154.164.82
PING 194.154.164.82 (194.154.164.82) 56(84) bytes of data.
64 bytes from 194.154.164.82: icmp_seq=1 ttl=50 time=59.6 ms
64 bytes from 194.154.164.82: icmp_seq=2 ttl=50 time=57.4 ms
64 bytes from 194.154.164.82: icmp_seq=3 ttl=50 time=59.4 ms
64 bytes from 194.154.164.82: icmp_seq=4 ttl=50 time=58.4 ms
64 bytes from 194.154.164.82: icmp_seq=5 ttl=50 time=58.4 ms
64 bytes from 194.154.164.82: icmp_seq=6 ttl=50 time=61.1 ms

--- 194.154.164.82 ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 5011ms
rtt min/avg/max/mdev = 57.432/59.089/61.127/1.189 ms

~ $ ping www.hofflimits.com
PING users.blogware.com (216.40.34.100) 56(84) bytes of data.
From 10.78.254.203 icmp_seq=1 Packet filtered
From 10.78.254.203 icmp_seq=3 Packet filtered

--- users.blogware.com ping statistics ---
13 packets transmitted, 0 received, +2 errors, 100% packet loss, time 12010ms
```


From what you showed right there it's going to 2 different addresses, and that's the problem right there. [www.hofflimits.com](www.hofflimits.com) should be resolving to the 194.154.164.82 address (which isn't giving any errors)  users.blogware.com (216.40.34.100) is where the problem is coming from.  Could be the hosting company is running what's called 'load balancing' (2 servers for the same site and they alternate who accesses which server to balance out how much traffic goes through). If one of those servers went for a nap, this could explain why some people can access and some can't

For example. doing a ping off my linux box i get:
```

$ ping www.hofflimits.com
PING www.hofflimits.com (194.154.164.82) 56(84) bytes of data.
64 bytes from 194.154.164.82: icmp_seq=0 ttl=49 time=98.9 ms
64 bytes from 194.154.164.82: icmp_seq=1 ttl=49 time=98.8 ms
64 bytes from 194.154.164.82: icmp_seq=2 ttl=49 time=98.7 ms
64 bytes from 194.154.164.82: icmp_seq=3 ttl=49 time=98.6 ms
64 bytes from 194.154.164.82: icmp_seq=4 ttl=49 time=98.4 ms
64 bytes from 194.154.164.82: icmp_seq=5 ttl=49 time=98.2 ms

--- www.hofflimits.com ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 5052ms
rtt min/avg/max/mdev = 98.283/98.662/98.980/0.299 ms, pipe 2

```
So i can get to the right place. 

Unfortunately about the only resolution (if that is the problem) is for the users to empty out cache (temp) files and folders completely and try again and hope they don't hit the same server. Or get in touch with the sysadmins over at  blogger and ask them to take a peek at their servers

---

### Post by SteveHoffmanUK on 2006-12-14
Lord Illidan wrote:
> Do you have a firewall or dansguardian? It could be blocking dns

No, I have no firewall or dansguardian on my Ubuntu machines.

---

### Post by bapoumba on 2006-12-14
> **Snowmayne said:**
> From what you showed right there it's going to 2 different addresses, and that's the problem right there. [www.hofflimits.com](www.hofflimits.com) should be resolving to the 194.154.164.82 address (which isn't giving any errors)  users.blogware.com (216.40.34.100) is where the problem is coming from.  Could be the hosting company is running what's called 'load balancing' (2 servers for the same site and they alternate who accesses which server to balance out how much traffic goes through). If one of those servers went for a nap, this could explain why some people can access and some can't
Okay, and that would explain why I did access the site once, thank you :)
I do not know a thing about networking .

> **Snowmayne said:**
> Unfortunately about the only resolution (if that is the problem) is for the users to empty out cache (temp) files and folders completely and try again and hope they don't hit the same server. Or get in touch with the sysadmins over at  blogger and ask them to take a peek at their servers
I did empty the cache in the first place, but that did not do it. So it's on their side, right ?

---

### Post by dorcssa on 2006-12-14
Well, I cannot see it with firefox, but with Galeon it works like a charm.

---

### Post by d3v1ant_0n3 on 2006-12-14
> **dorcssa said:**
> Well, I cannot see it with firefox, but with Galeon it works like a charm.

I found it worked fine in Firefox 2.0 for me, but not Galeon 2.0.2. How very very odd.

---

### Post by Snowmayne on 2006-12-15
> **bapoumba said:**
> Okay, and that would explain why I did access the site once, thank you :)
I do not know a thing about networking .


I did empty the cache in the first place, but that did not do it. So it's on their side, right ?

Only reason I've been able to answer any of this is 'cuz that's what they're slowly training me to do at this job and a few years ago at another job we had clients calling with the same type of problem. ;) 

What's basically happening is that your ip address & browser, when they go to the url get logged on their system so that the next time you go to the site, you end up being routed the same way. But because one of their servers isn't working properly, you'll end up going to the same spot. (Hence why some people can access in one browser or OS, but not another on the same system)

If you could have someone drop an email to the site admin and server admin and ask them to take a look at their machines (and point them to this forum thread for details ;) ) hopefully this'll get fixed :)

(wow, first time I felt my itty-bitty bit of knowledge was actually able to be put to use here hehe)

---

### Post by SteveHoffmanUK on 2006-12-15
Problem solved for me in the other (Networking) thread:

ipd106 wrote:
> Have you tried disabling IPv6? You can do this in the about:config in firefox, toggle network.dns.disableIPv6 to true.

I did the toggle and the blog is now viewable in my Ubuntu 1.06 desktop.

Does this work for others?

---

### Post by Man_Beach on 2007-01-11
For what it's worth, I too used to have a similar problem in that certain sites were viewable in windows but not linux, dual booting on the same machine and connecting to the internet through the same router with the same settings (first SuSE, then Ubuntu).
Browsers tried were IE6 and Firefox in windows (both worked), Firefox in SuSE and Ubuntu and Konqueror in SuSE (none worked).

After doing a Whois I found that I could type in the IP address and go to the sites in both SuSE and Ubuntu so it obviously wasn't a specific linux problem.

At least two of the sites that I can remember were [www.xec.gapbuster.com](www.xec.gapbuster.com) and [www.travelpharm.com](www.travelpharm.com)

After following the advice above of disabling IPv6 in Firefox I can now go to the above two sites with no problems.

---

### Post by earobinson on 2007-01-12
I think its fair to say this is more the sites problem than ubuntus

---

