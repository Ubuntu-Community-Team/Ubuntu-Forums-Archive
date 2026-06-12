---
title: "Seeking advice on Netdata"
date: 2021-02-13
forum: General Help
---

### Post by DuckHook on 2021-02-13
Due to some recent server crashes, I'm looking at installing [Netdata]("https://github.com/netdata/netdata") to track system variables/health. Does anyone have experience with this package? I'm primarily interested in the following:

[LIST=1]
[*]How useful is it really?
[*]Does it increase attack surface and, if so, by how much? Anything to worry about?
[*]Is there a large impact on system resources?
[/LIST]
Additional comments/observations are also very welcome.

---

### Post by The Cog on 2021-02-14
I had not heard of Netdata, so I had a look at their web site. It looks very slick and impressive. The screenshots look like grafana dashboards to me, no surprises there.
The claims of automatic per-second recording of so many variables are impressive. It sounds like a good quick way to hit the ground running.

But I have reservations, possibly unfounded. 
The web site looks professionally produced - makes me wonder if they intend to make the product commercial as soon as they have enough users becoming dependent on them. The fact that their non-standalone solution is a "cloud" solution could leave you very dependent on their servers for continued operation. And there is no mention of opening firewalls to enable the cloud to connect in and retrieve your stats, which makes me wonder if the agent phones home.
The fact that simply looking at their web site caused one Firefox thread to peg at 100% CPU and bring my laptop fans on gives me an uneasy feeling, too.

If you can get good answers to these points, which may just be my paranoia, then I think it looks very interesting and worth trying out.

---

### Post by DuckHook on 2021-02-14
Thanks for your thoughts.

Your concerns mirror mine, so if paranoid, we have at least each other for company.

I've gone ahead and installed it sandboxed within a container. It certainly is slick as shown by the attached screenshot.

[ATTACH=CONFIG]287962[/ATTACH]

I was motivated to look for something because I have a Nextcloud server that keeps hard crashing on me, freezing the kernel and not recoverable even with SysRq. Triage is proving elusive and difficult, but hints at something to do with ZFS, which I need for LXD. However, the Linux implementation of ZFS is very obscure and is missing analytical tools, especially with arc status. Scrounging around, I came upon Netdata, which I had never heard of before either.

To my surprise, it's available in the repos: ```
duckhook@Zeus:~$ apt show netdata
Package: netdata
Version: 1.19.0-3ubuntu1
Priority: optional
Section: universe/net
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Lennart Weller <lhw@ring0.de>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 38.9 kB
Depends: netdata-core | netdata-core-no-sse, netdata-plugins-bash, netdata-web
Recommends: netdata-plugins-nodejs, netdata-plugins-python
Homepage: https://github.com/netdata/netdata
Download-Size: 8,156 B
APT-Sources: http://ca.archive.ubuntu.com/ubuntu focal/universe amd64 Packages
Description: real-time performance monitoring (metapackage)
 Netdata is distributed, real-time, performance and health monitoring for
 systems and applications. It provides insights of everything happening on the
 systems it runs using interactive web dashboards.
 .
 It can run autonomously without any third party components or it can be
 integrated to existing monitoring tool chains (Prometheus, Graphite,
 OpenTSDB, Kafka, Grafana, etc).
 .
 This package is a metapackage depending on the typical netdata components.
```…and goes back for a few versions, which indicates that the agent at least is F/LOSS and has community support.

> **The Cog said:**
> 
The web site looks professionally produced - makes me wonder if they intend to make the product commercial as soon as they have enough users becoming dependent on them.
They say as much: > (…from their cloud sign-up page)

Manage all of your nodes in one place for free 

Netdata Cloud lets you and your team monitor and troubleshoot your entire infrastructure of Netdata nodes. See every metric from every system in real time.

Netdata Cloud is offered completely free of charge with no limits on the number of nodes, metrics or team members.

**In the future, we’ll be offering complementary paid services** for advanced user control and auditing, increased metadata retention, and enterprise plugins. The best is yet to come.…so at least they're up front about it.
>  The fact that their non-standalone solution is a "cloud" solution could leave you very dependent on their servers for continued operation.
Agreed. There's that addiction thing happening. I don't know of a self hosted alternative though.
> And there is no mention of opening firewalls to enable the cloud to connect in and retrieve your stats, which makes me wonder if the agent phones home.
Oh, it phones home alright. But they make all sorts of noises about how your data remains locally resident and protected, yada&#8209;yada&#8209;yada. Privacy is one of my primary concerns. I would consider simply using the agent and foregoing long-term analysis, but that seems absurdly self&#8209;limiting and defeats the whole point of the exercise.
> The fact that simply looking at their web site caused one Firefox thread to peg at 100% CPU and bring my laptop fans on gives me an uneasy feeling, too.
Probably a result of the animated GIF further down the page. I have noscript on by default and was surprised to see animation which led to my checking it out: it's rather clever actually, but on some machines, animated GIFs will hit the CPU pretty hard.
> If you can get good answers to these points, which may just be my paranoia, then I think it looks very interesting and worth trying out.
Well, your paranoia is shared by me. I'm going to sleep on whether I open a cloud account with them. If I do, it will likely be highly anonymized—piped through anonaddy and with fake credentials. Will have to decide if their access to my machine data is sufficiently compromising to pass up on what otherwise looks like a well designed offering.

Thanks for your input!

---

### Post by dragonfly41 on 2021-02-14
I have no knowledge of NetData.

I list these tools I have found through experiments.

[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

And you might find that **lynis** is already installed.

You need to run in sudo ..

sudo lynis show

this shows the options.

[P.S.] There is also **Stacer** for Linux monitoring.

[P.P.S.] and [having studied more]("https://www.google.com/search?q=ZFS+crashes+NextCloud&oq=ZFS+crashes+NextCloud&aqs=chrome..69i57.13582j0j4&client=ubuntu&sourceid=chrome&ie=UTF-8") about NextCloud I see that the above tools may not be of much use to you .. only for desktop.

---

### Post by HermanAB on 2021-02-14
How is netdata different from, for example netsnmp, openSNMP or Zabbix:

NetSNMP is the underlying system.
OpenSNMP is very compute intensive but it can handle a very large deployment. (I used it and it worked, but I changed to Zabbix)
Zabbix is light weight and scales to medium size deployments (I used it and it worked very well with about 3000 servers, plus about 10,000 modems and WiFi access points)

---

### Post by DuckHook on 2021-02-14
> **dragonfly41 said:**
> …you might find that **lynis** is already installed.
…[P.S.] There is also **Stacer** for Linux monitoring.
[P.P.S.] …I see that the above tools may not be of much use to you .. only for desktop.
Nonetheless, thanks for the suggestions. They may be useful in a capacity other than server monitoring, so are still helpful. I'm afraid, however, that they won't fulfill my immediate aim of monitoring ZFS.
> **HermanAB said:**
> How is netdata different from, for example netsnmp, openSNMP or Zabbix:

NetSNMP is the underlying system.
OpenSNMP is very compute intensive but it can handle a very large deployment. (I used it and it worked, but I changed to Zabbix)
Zabbix is light weight and scales to medium size deployments (I used it and it worked very well with about 3000 servers, plus about 10,000 modems and WiFi access points)
I've always shied away from enterprise&#8209;level platforms like SNMP because my impression of them is that they:
[list=1]
[*]are resource&#8209;heavy
[*]have a steep learning curve
[*]are ornery to implement, configure and maintain
[*]increase attack surface
[/list]
Please forgive my ignorance, but I'm just beginning to dip my toes into the whole sysadmin world. When you consider 3000 servers to be a "medium size deployment", then not only am I not in your league, I'm not even playing the same game. I'm looking for a quick and dirty solution to a five server SOHO that will require minimal supervision from me and won't be too taxing on my aging grey matter. I've already peered into Webmin (yes, notwithstanding their atrocious supply chain poisoning fiasco a couple of years ago) precisely because I value a dummy&#8209;friendly summary of system health/resource usage.

Netdata appeals because it is ludicrously easy to implement. The downside is the reporting back to mothership, which I need to think hard about. Were it not for this, it would be a no&#8209;brainer.

Don't get me wrong: I am open to all options. SNMP would allow me to also manage my printers, which is not really that big a deal, but would admittedly be a nice&#8209;to&#8209;have. I know nothing about Zabbix, but it sounds complicated.

With Netdata, all I had to do was: ```
sudo apt install netdata
```…and, presto, it was done. There is tremendous value in simplicity to simpletons like me. :-)

---

### Post by The Cog on 2021-02-14
You may find a reasonable answer by installing prometheus (stats gathering database) and grafana (displays dashboards based on data collected by prometheus) on a server, and installing prometheus node exporter on all your servers. The node exporter collects stats on the sever it runs on and exposes them in an http server. Prometheus can be configured with a list of servers (running node exported) to collect stats from. Grafana is a web server that offers dashboard views of the data inside prometheus.
- Node Exporter: agent running on all servers, web api allows querying those stats
- Prometheus: database and periodic querying of the exporters to get the stats
 - Grafana - web based dashboards showing stats stored by prometheus.
Basic setup is quite straightforward, and making your own dashboards only takes a day or so to get your head round. 

The above is not quite as slick as out-of-the-box netdata judging by what I have seen, but it may well be enough for you. All these 3 are in the repos, and I don't believe they phone home. I ran prometheus and grafana on a raspberry pi for my home PCs for a while, until the pi died. I haven't got round to replicating on the replacement pi.

---

### Post by HermanAB on 2021-02-14
BTW, Zabbix will work fine with five machines also.  It is very low intensity (that is why it can handle thousands of devices without stress) and quite trivial to set up.

OpenSNMP however, is a beast and best avoided.

---

### Post by DuckHook on 2021-02-14
> **The Cog said:**
> You may find a reasonable answer by installing prometheus (stats gathering database) and grafana (displays dashboards based on data collected by prometheus) on a server, and installing prometheus node exporter on all your servers…Basic setup is quite straightforward, and making your own dashboards only takes a day or so to get your head round.
Many thanks for this!

An alternative that I am more than willing to try. And being retired and all (and with the pandemic raging), what else have I but time?

I'll research a bit first to see if it's within my capabilities.

I might still forge on with Netdata too. In some ways, it may be instructive to compare the two. If I find the motivation and mental resources, I may even add SNMP to the mix—okay, that may be biting off more than I can chew.

---

### Post by DuckHook on 2021-02-14
> **HermanAB said:**
> BTW, Zabbix will work fine with five machines also.  It is very low intensity (that is why it can handle thousands of devices without stress) and quite trivial to set up.
Intriguing. Have you any links to favourite tutorials? I can easily do a websearch but they are not all of good quality.
> OpenSNMP however, is a beast and best avoided.
Appreciate this heads-up. Always happy to defer to greater wisdom.

ADDENDUM

Just visited the Zabbix site. Awesome. F/LOSS too, which I wasn't expecting. I wonder why it's not in the repos? Anyways, I never realized there was such a wealth of monitoring/admin products out there. It's embarrassing how cloistered and uninformed I've been. Have fallen so far behind over the years. And, in combination with my recent Nextcloud journey, it's humbling how much time and dedication some have put into resources that benefit the greater community.

Further ADDENDUM

Hah! There's a snap for Zabbix. @HermanAB: Would you recommend it? Snaps have certain drawbacks, but it would be easier to install than in isolation from their site.

---

### Post by DuckHook on 2021-02-15
FWIW, from the founder of Netdata: [https://www.netdata.cloud/blog/why-netdata-is-free/](https://www.netdata.cloud/blog/why-netdata-is-free/)

Also, FWIW, I don't have any problem with paying for good services. In fact, I *want* to deal with an org that charges me money for their services rather than skimming my data, and have recently made the often painful odyssey to self hosting and paid service providers for that very reason. Having said that, the above is at least somewhat reassuring. Will continue to poke around and am currently trying to deploy Zabbix for comparison.

---

### Post by HermanAB on 2021-02-15
Zabbix also has commercial support.

---

### Post by DuckHook on 2021-02-15
> **HermanAB said:**
> Zabbix also has commercial support.
Thanks, I noticed that while poking around their site.

BTW, my bad, but there is no snap. I was mislead by another pkg that had "Zabbix" in its name. It must be downloaded, installed, configured, etc.

Last but not least, your idea of "trivial" is a testament to your expertise. For me, the measures needed are quite intimidating. I'm still parsing through their documentation to determine if I am up to it. In all honesty, Netdata is looking increasingly attractive because of its childishly easy implementation. I will continue my slow slog though.

---

### Post by The Cog on 2021-02-15
With regards to SNMP - if you use a product that can slurp data from the prometheus node exporter, that is a lot easier than using SNMP. 
The node exporter finds pretty much you might be interested in (in a server, at least). In contrast and as far as I know, SNMP needs a lot of configuring, both the agent on the server and the collector that gathers the numbers. I spent quite a while working with an expensive software that collected and graphed SNMP stats. Given time, you could get very deep information on router performance, throughput and drop rates of nested policing policies etc, but it took days to get each graph right.

I just had a quick look at Zabbix, and I think that would be worth a try for you - The potted reports are probably all that you will need.

Yes, there are a lot of monitoring products.

---

### Post by DuckHook on 2021-02-17
Interim report card:

I took the plunge and signed up for Netdata's cloud. It turns out that the Netdata version in the repos is too old to have proper cloud agency, so I purged the repo version and installed Netdata using their one&#8209;liner, then just sat back and watched as all the building blocks automagically slotted into place. This in itself will give the gurus among us pause. Automation of this sort gives you guys the willies. I couldn't tell you what the script was doing, it just looked ridiculously cool and worked like a charm.

Pairing the agent with their cloud instance was another one&#8209;liner using a TLS certificate.

The result is quite the treat. I am now monitoring two of my servers with next to no effort on my part. Already seeing some areas that can be tweaked, though I will have to research the hows and wheretos. I was warned, in big bold print, that I would be uploading UUIDs and hostnames. This is unavoidable if I want useful monitoring. I believe IP and MAC addresses are masked before uploading. I couldn't find them on the readouts at any rate.

If this is how easy Netdata is, then despite my earlier questions and concerns, it's hard to see how others of my tech level can resist it. Frankly, had I known that monitoring could be this painless, I would have done it ages ago.

I am still intent on trying Zabbix. If I can get my summaries without relying on someone else's cloud and without too much handholding on my part, then I am game to try. However, it will be a much longer project, so I don't anticipate further updates any time soon.

I really appreciate the input from all of you. It's opened my eyes to a whole new world I had only heard about but never explored. Sorta like seeing Paris for the first time. Simply awesome.

---

### Post by DuckHook on 2021-02-20
Final Report Card.

I've decided to settle on Netdata for now. At the risk of belabouring the thread, this summary may prove useful to others who stumble upon it:

**Recap:**

For diagnostic reasons, I found it necessary to look for monitoring solutions. Research led to Netdata, which on the agent side is marvellous. Its big drawback (at least for me) is its reporting back to mothership. HermanAB graciously suggested Zabbix.

**Zabbix alternative:**

Zabbix looks highly attractive because it is entirely self-contained, but upon further thought and experimentation, the following came to light:

[list=1]
[*]Though a guru will find it trivial, a typical user must still climb a learning curve.
[*]It requires a dedicated server to host. One could double-duty an existing server, but for a small SOHO, this could constitute a significant portion of existing resources.
[*]To get similar functionality to Netdata cloud, it requires setting up a mail server.
[*]Again, for similar functionality, a database is also needed. Yet more maintenance and complexity.
[/list]
**TL;DR**

Netdata hits the sweet spot for general users with limited expertise. It trades the negative of cloud exposure for the positive of no&#8209;brainer implementation/use. While Netdata cloud is designed to scale (to enterprise level, so they claim), it is especially welcoming to beginners and SOHO applications. Since my objective is to chase down an obscure server problem and not to learn a new field, it is a good fit.

Many thanks to all of you for your help and advice.

---

