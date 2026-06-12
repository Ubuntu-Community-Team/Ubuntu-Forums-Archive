---
title: "What would you do with a spare box?"
date: 2007-01-23
forum: General Help
---

### Post by Catsworth on 2007-01-23
Ok, so here's the deal.....you have a spare box as follows:

AMD K6-2 500Mhz Processor
192Mb Ram
2 x 60Gb HDD (non-raid)

You already have a decent laptop running Ubuntu (with a small XP partition for Games), a buffalo NAS (120Gb, built-in print server), and a Linksys ADSL router (4 port, wireless enabled, built-in firewall).

What would you do with the spare box, and why?

(Note: trashing it is not an option, the spare box should be used in some way on the network)

---

### Post by Daveski on 2007-01-23
Install Ubuntu server and use it as a testbed to learn about LAMP. Also no GUI would force me to become more adept (no pun intended) at the command line.

Run a web server / SSH / or even FTP for friends and rellies to connect to to share photos etc.

---

### Post by tribaal on 2007-01-23
I'd install a fresh desktop system on it and give it to a local charity. :)
Spread linux :)

Eventually I'd set it aside and make it crunsh for [rosetta@home]("http://boinc.bakerlab.org/rosetta/"), but that really depends on how you get your electric energy.

- trib'

---

### Post by tagra123 on 2007-01-23
Sounds like a real good file server.

---

### Post by lyceum on 2007-01-23
If you have time, put Fluxbuntu on it and help bug test. Then give it to someone who cannot afford a PC, or sell it on e-bay with Fluxbuntu or Xubuntu. Otherwise, the server idea sounds really good.

---

### Post by reclusivemonkey on 2007-01-23
> **Catsworth said:**
> 
AMD K6-2 500Mhz Processor
192Mb Ram
2 x 60Gb HDD (non-raid)

You already have a decent laptop running Ubuntu (with a small XP partition for Games), a buffalo NAS (120Gb, built-in print server), and a Linksys ADSL router (4 port, wireless enabled, built-in firewall).

What would you do with the spare box, and why?


Web server? So you can host your own website.
Game server? So you can host your own games.
Media centre? So you can share all your media all over the house.

Do you have any spare cash to throw at it?

---

### Post by ~LoKe on 2007-01-23
Web server/File server.

---

### Post by kerry_s on 2007-01-23
Use it to distro hop/test other OS's.

---

### Post by Falcorian on 2007-01-23
I use mine to crunch numbers for Einstein@Home (but I do that on all my computers, hey, I paid for the processor, it better be working 24/7!), and to work as a backup location for home folders (it runs Dapper Xubuntu). The newer old box is a file server (On Dapper). *shrugs*

---

### Post by Catsworth on 2007-01-23
> **reclusivemonkey said:**
> Do you have any spare cash to throw at it?

Nope, that's one thing I haven't got :)

Keep it coming guys :)

---

### Post by Devilotx on 2007-01-23
I'd use it as a file server or a Game server (like Call of duty 2 or something)

Or Use it as a distro pig, and just try different distro's on it to see what works best.

---

### Post by noalternative on 2007-01-23
Install xubuntu because it will work better on this machine, and possibly use it as a firewall or a spare.

Or I would give it away on [freecycle]("http://www.freecycle.org"), or to goodwill because many people can't afford computers at all.

---

### Post by LittleCleo on 2007-01-23
I have a box with nearly the same processor and ram specs. It is being used as an NX client.

---

### Post by ardchoille42 on 2007-01-23
Install apache and php, then use it for a wiki. There are lots of wiki's available. I would probably install Fluxbox, apache, php and [PmWiki]("http://www.pmwiki.com/") on it and use it for a wiki on my LAN. But, I am wondering if this box is sufficient enough to install a bunch of media apps (mplayer, xine, xmms, etc) and use it as a multimedia/stereo box.

---

### Post by kerry_s on 2007-01-23
Test your skills on a base(server/command-line) install build up. There nothing like a custom install you built just the way you want it. Plus it helps you understand how it all works.-> [ftp://ftp.osuosl.org/pub/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/mini.iso](ftp://ftp.osuosl.org/pub/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/mini.iso)

---

### Post by RandomJoe on 2007-01-23
Everyone else has good ideas as well.

I have a machine of approximately the same specs running as my router/firewall.  My WRT54G - which _could_ do a similar job - is relegated to just wireless AP!  The machine has three NICs, one to the cablemodem, one to the AP and one to the switch for my wired network.  It also has OpenVPN set up for remote access in (use DynDNS to keep track of the IP), and 'iptables' on a PC is far far more flexible and powerful than working within what you get on the average cable/DSL router.  (Yeah, some can be flashed with custom Linux, it's still easier on the PC!)

The box also has dnsmasq running, so it handles DHCP for both networks (wired & wireless), provides internal DNS services so I can use machine names instead of remembering IPs _without_ having to edit hosts files, provides DNS services for the 'net as well (caching recent entries for speed), and at one time I had OpenVPN running on my WLAN network as well so I could run the AP wide open, anyone could connect and get degraded service or if I set up OpenVPN for them they got full access.  I'm lazy so I got tired of maintaining the last bit... :roll: 

Oh yeah - ntpd keeps its time set correctly, and dnsmasq serves its IP to any connecting computer to use for ntp services.  So I don't query over the 'net for every computer in the house.

Forgot another function (glad I have all this written down somewhere!) - it also has the X10 "Firecracker" module on a serial port, and a cron job turns a few lights on/off in the house.  I wake up easier when the lights are already on in the morning!

And it sits all alone on a high shelf, nearly forgotten about it works so well...  It's been up around a year now, and the last downtime was when I rearranged the server closet...  (It's running a stripped-down Slackware.)

---

### Post by lotacus on 2007-01-23
I think it would just sit and collect dust. However, the past spare boxes I had, I used for learning and used as a test bed for anything that may interest me.

I installed FreeNAS
I installed Softwall? (I think that's the name)
I've installed many linux distros to figure out which one suited me before I commited to one. (thanks Ubuntu)

I've installed a gway? that uses connection teaming and sharing for fallback etc

I've attempted to use a box as a media center, but sadly enough, there were none (for linux) that were robust, easy, compatible enough, so I ended up using MCE.

I've also had a spare box which I ran folding@home, though I think these folding programs don't really serve much use. I have never read/learned about any new treatments in which were discovered by folding.

---

### Post by matthewstory on 2007-01-23
considering the lack of RAM and the sub-par processing power i think a game server is out of the question . . . i'd throw up Ubuntu Dapper Server without gnome, run Apache2 on it plus a samba server or NFS with SSHD and make it a diverse file server.  With apache you can stream video and music to VLC clients on your LAN, you can host files with NFS SMBD and SFTP to the rest of your stuff, and i'd set up a software RAID 0 to stripe the 2 disks to avoid having to do lots of annoying FS type stuff.

---

### Post by nix4me on 2007-01-23
Add another network card and install ipcop or monowall and have yourself a stellar firewall/router.

nix4me

---

### Post by K.Mandla on 2007-01-23
Install Fluxbuntu, FVWM-Crystal, Openbox or Cubuntu. And then use it like a music server, if you want.

---

### Post by business.geek on 2007-01-24
I would say i want a ubuntu system that runs XFCE.  I know you guys would say that I should use XUBUNTU but xubuntu is a bit of a disappointment for me.  and Its not yet updated to the latest stable release (4.4)

Currently Im trying to churn out a UBUNTU system that use XFCE that does not have the bulk of XUBUNTU. ill post the results in my website within the month  ([Pinoy Compuworld]("http://www.pinoy-compuworld.com/"))

or i can try fluxbuntu. any reviews about it yet?

---

### Post by goggles on 2007-01-24
Do you have any pets?

[http://www.ubuntuvideo.com/ubuntu_powered_cat_feeder](http://www.ubuntuvideo.com/ubuntu_powered_cat_feeder) :D

---

### Post by garak on 2007-01-24
I use my spare box as aMule server, so I can download files at home when I'm at work. :D

---

### Post by dad311 on 2007-01-24
web server
file server
printer server
Web filtering proxy server
Extra box to cruch video on

---

### Post by ineluki12 on 2007-01-24
[http://www.honeynet.org/tools/index.html](http://www.honeynet.org/tools/index.html)

---

### Post by xSauronx on 2007-01-24
id set it up as a desktop with something flashier than Xubuntu or turn it into a server or router or some such in the future for me to fiddle with

---

### Post by matthewstory on 2007-01-26
the honeypot idea is cool, I run one for the company i work for . . . i just don't know if i'd set up a personal box as a honeypot . . . but good call on honeynet.

---

### Post by airtonix on 2007-05-01
use it as a router/firewall/filterer.... your box is ubuntuGateway.

---

### Post by Selmer79 on 2007-05-01
This is probably going to sound weird on an Ubunty forum, but I'd say:
Set up the WLAN router as an Access Point only and install ClarkConnect on your box to get a really good firewall with LAMP on it.
Or figure out how to do the same with Ubuntu. ;)

> **dad311 said:**
> Extra box to cruch video on
Quite the masochist eh? (We are talking about encoding video here right?) On that hardware, a DVD-to-h.264 conversion with a crop and deinterlacing would probably take a day or two..

---

