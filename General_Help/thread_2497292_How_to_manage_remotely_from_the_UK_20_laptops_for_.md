---
title: "How to manage remotely from the UK 20 laptops for a orphanage in Cambodia"
date: 2024-04-29
forum: General Help
---

### Post by lp.descamps on 2024-04-29
Hi,

I managed to get 20 Dell 7490 laptops that we will be bringing to an orphanage in Cambodia as a charity project.

Does anyone have any advice on how to manage them once I'm back in the UK?

I'm thinking of installing Edubuntu using autoinstall on them from a USB stick.

How would you do updates for all of them using a low internet speed?

I'm fairly technical so lacking experience in this area and only have one shot to get it right

Thank you for your inputs

---

### Post by TheFu on 2024-04-29
ssh.  Setup deployment accounts as part of each local workstation that can be accessed over ssh using ssh-keys, never passwords.   You'll need to setup at least 1 of the systems with an open port to allow ssh inbound, then use that system to jump to other computers.  Perhaps that "ssh jump box" should be a cheap raspberry pi and not one of these workstations, so you can lock it down for just ssh remote access into the LAN. Heck, you might put a wireguard VPN onto it, then have it contact your wireguard VPN server to open a tunnel so you can reverse into that entire LAN remotely.

For 20 systems, I'd setup ansible and ensure it works.

You should already be using ssh daily. If you aren't. stop and learn ssh.  It is how 

Lastly, I really hope you aren't using Ubuntu 16.04 and haven't for the last 3 yrs when support ended.  For a setup like this, 22.04 is the release you should be installing on the workstations, assuming ubuntu is the best option (which I wouldn't assume).

Anyway, you'll need to get ssh and wireguard working BEFORE you do anything else.  With wireguard on a gateway system, it can phone home to you without having any ports open at all, but you'll need to run a wireguard server and have at least 1 port open to the internet.  Your wireguard server needs to have a public, static, IP. May be best to pay for a $5/month VPS to be the wireguard server.  Then you can have a client at your home that connects into that server and sees the other LAN in Cambodia as a peer for connectivity.  There are lots of guides for doing this.

A key thing for LAN to LAN access over any VPN is that both LANs do NOT have the same private subnet.  If your home LAN is on 192.168.1.0/24, then you need to ensure that the LAN in Cambodia is something else.  I'd use 10.2.2.0/24. It just needs to be different an it is best to avoid the most popular subnets that cafes, libraries, hotels all use. There are thousands of choices for private networks that can be used.  Also, if your home LAN is on of the most common private LAN subnets, I'd change that immediately to something odd.  I've been using 172.22.21.0/24 and 172.22.22.0/24 and 10.6.6.0/24 and 10.6.7.0/24 for years now.  These are all in the private ranges, so they won't be routed over the internet, but for connecting VPNs, they work great.

Security and secured connections all start with good networking.

---

### Post by ActionParsnip on 2024-04-29
Local apt server for updates. You can also use the servers as an SSH jumpbox so you can jump from that to any server on the LAN.

---

### Post by ActionParsnip on 2024-04-29
+1 for ansible

---

### Post by lp.descamps on 2024-04-29
good idea on ansible! thanks!
for vpn, I was thinking to use tailscale

my signature was well out of date :-)

---

### Post by lp.descamps on 2024-04-29
thanks!

---

### Post by dragonfly41 on 2024-04-29
Charitable applications of IT do tax the mind.


Dumping some ideas to add to the deep knowledge of theFu.
You have a balancing act since network coverage, local support and training might need to be considered. On the other hand you do not want too much complexity to maintain in the delivered laptops which undoubtedly will fail at some point.


Why not aim to create a hybrid of centralised (cloud) service and stand alone (when network breaks)?


That is, create virtual edubuntu machines which can be configured centrally from home (Woking?) base. Virtual desktop sessions can be fired up. Setup a support office in Cambodia or through a local firm who offers charitable support. An example of what can be done is [https://www.rollapp.com/](https://www.rollapp.com/).  You might start by creating an account to be shared across the 20 Dell laptop users.
Since there will be communication breaks you might explore CloudAMQP (subject to regional coverage) where you can send batch messages to be acted on as the remote nodes are able to respond. TheFu refers to ansible scripts.


So design in redundancy to reflect expected breakpoints or failures. Human failures, system failures, poor network. Also bear in mind that Charity donators like to have visibility of where/how donations are applied.


I would add eLearning framework to your offering to get feedback on learning progress. Perhaps moodle.org or other to support local education workers and students.


Summarising:
Woking HQ, have dual PC's and drives and rdiff-backups (read TheFu advice on “backup religion”).
Setup account with say [LayerShift]("https://www.layershift.com/") (U.K. centre Manchester, recommended by this sole developer) which can launch VM's on a Pay as You Go basis.
Explore local coverage via [https://metfone.com.kh/](https://metfone.com.kh/)
Setup account with [https://www.cloudamqp.com/](https://www.cloudamqp.com/) to send/receive batch messages from RabbitMQ server to monitor and maintain remote nodes (Dell laptops). Although check coverage.
[https://www.cloudamqp.com/blog/new-regions-added-may-2021.html](https://www.cloudamqp.com/blog/new-regions-added-may-2021.html)
Have a VM created to monitor state of your outlying nodes (laptops). 
You might install Stacer or Prometheus on each laptop for monitoring remote stations.
Perhaps use Cubic (fron devops base) to customise the desktop ISO (to be burned into LiveUSB) with custom apps such as edubuntu
Grafana can monitor Prometheus outputs so Houston mission control (or Woking) can have a satellite view of status.
Seek charitable local support from Dell.
Leverage what3words to get a geo fix on where the Dell laptops are located. Always useful to see where charitable donations end up in locations.
Leverage DeepL for translation.
Leverage SVG for animation. SnapSVG.
Security and privacy are uppermost in mind.

---

### Post by TheFu on 2024-04-29
dragonfly41 is giving great advice, if the systems have *some* bandwidth to the internet all the time.  

I assumed internet bandwidth would be limited, or out completely, most of the time, and only enabled when necessary.  I helped setup a network like this in Nepal using a 1 Mbps fibre link that was only available when they had electricity. At the time, the entire country had rolling electrical outages for 6+ hours at a time that shifted 1 hour every day. Most people didn't watch the published schedules. They just dealt with it after it happened.  Once I was in a restaurant's toilet (no windows) when the power was cut around 2pm.  After that, I started taking a headlamp with me everywhere, always to avoid sitting in the dark, halfway done, trying to grope around to finish my business in completely unfamiliar places.  I was there less than a month and never had that happen again, even being prepared.

Only thing I might change is to replace W3W with GeoCodes (aka Plus Codes), which are OSS and supported by Google Maps.  "6XV3+3HC  Nepal" or easier "7MW56XV3+3HC" <---- put that into google maps or any other mapping tool that supports PlusCodes and it will always take you to the same location.  What3Words is proprietary.  PlusCodes are F/LOSS and can be calculated by anyone in any app, if they like. "7MW56XV3+3HD" is right next to the other location. It makes sense, unlike W3W codes.  If you don't need to be as precise, leave off 1 or two of the last numbers and the plus code rectangle will be larger.  So if you are meeting a boat on a lake, you don't need for than 500m² accuracy.  If you are meeting in a crowded stadium, then you'll want to get to 1m² accuracy.  Just depends on the needs.  [https://maps.google.com/pluscodes/](https://maps.google.com/pluscodes/)   BTW, Google didn't invent them.

In Nepal, most places don't have addresses, so deliveries are to the local store who keeps packages until you show up.  In other parts of the world, addresses are vaguely relative to some landmark.  In Costa Rica, I stayed in a home with an address that was *500m North of Johnny's Pizzeria*, Town, Province.  There were 3 homes with the same address on the side of the mountain, so the family name was the only differentiator.  Also, Johnny's Pizzeria had burned down 10 yrs earlier, so it was an empty lot.  PlusCodes were new at the time.  They make tremendous sense for addresses.  Sorta like postal codes, but add 2 more digits to get exactly where you need.

Wireguard topologies: [https://www.procustodibus.com/blog/2020/10/wireguard-topologies/](https://www.procustodibus.com/blog/2020/10/wireguard-topologies/)  I think you want what is in figure 1.2.  Which would make it possible for people who know the networking with systems inside either LAN for those systems to communicate.  That makes ssh + ansible for remote management pretty easy.  You can use any remote desktop you need in a fairly secure way, thanks to the VPN without having to install it on every workstation at the remote site.

Fire 3.1 is tempting, but it would require 1 of the LANs to be the Wireguard server, which can lead to security issues if misconfigured.  Much safer to have a VPS be the wireguard server and allow connections from specific countries, definitely not the whole world.  Remember, the VPN tunnel is only for systems management use, not general connectivity to the internet.  That will mean specific routing rules in the gateway between the remote LAN and your workstation would be best. Everything else would go through the internet by default.

It can be tempting to setup remote desktops using web-based tools like Guacamole. Just beware that security of most of those web-based remote desktops is generally very poor.  Still, it is your choice.  I seldom use remote desktops, unless I'm traveling to countries that cannot be trusted. Then I bring just enough of an OS with me to access my VPN and run an x2go remote desktop back to my home network and have full, secured, access to web browsers and email clients there.  If my laptop is stolen, I don't want to worry about any data on it being sensitive, so I leave all data back home.  BTW, the countries I don't trust when it comes to internet stuff would surprise people. There are a few in Europe/Oceania/Asia/Middle East with terrible privacy and encryption laws that I don't trust because their border people can demand anything be decrypted.  Much easier just to have a stock OS for them to look at and bring my real OS on a microSD card that fits into a USB3 adapter for booting and remote access use.  I'm not just paranoid. They are out to get me!   

Really, the best option for class rooms may be to have an ISO that each workstation boots from every time. No local storage used or saved.  Then you remove all sorts of issues. Every quarter or 6 months, send a new ISO for the teacher to clone for all students to get updated programs with their boot. No install needed.  Very little need to patch, since they are always booting from an ISO (read-only).

---

### Post by dragonfly41 on 2024-04-29
Perhaps something like [this ]("https://uk.crucial.com/ssd/x6/CT1000X6SSD9?_gl=1*hkql92*_up*MQ..*_ga*ODU5NzE2NDA0LjE3MTQ0MDk0OTM.*_ga_TRH736VMJG*MTcxNDQwOTQ5Mi4xLjEuMTcxNDQwOTUzMC4wLjAuNjA0NTQ2NDE2&gclid=Cj0KCQjwir2xBhC_ARIsAMTXk841U5TqBzsuogvfoySeQ8y6aHsZhmAoeJ9OzUFNn_eF_GzK9PSSctoaAvm_EALw_wcB&gclsrc=aw.ds")to plug in to one or two laptops serving the group of 20.
Configured as LiveUSB. Use rEFInd with customised charity GUI to boot up.

This was my [best guess]("https://www.gracehousecambodia.net/programmes") of your "Houston centre" based on clues.

Great story from TheFu.

[Post Script] Remembered [ngrok]("https://ngrok.com/") which can be installed in plugin USB SSD as above.
Then the host laptop(s) becomes server(s) accessed from Houston centre. Turning around the model.

---

