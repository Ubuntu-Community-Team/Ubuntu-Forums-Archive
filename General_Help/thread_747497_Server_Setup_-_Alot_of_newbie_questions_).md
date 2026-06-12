---
title: "Server Setup - Alot of newbie questions :)"
date: 2008-04-06
forum: General Help
---

### Post by Aaron-B on 2008-04-06
A quick bit of background info first.
I'm a web developer who has always been a windows user (with the exception of some time spent on OS9 while at college) and am going to be setting up a small form PC which is primarily going to act as a torrent download server. I have a little experience using the command line via ssh (on Solaris) but this will be my first linux install so I have a few questions :)

Any advice, links, recommendations are very welcome.

What it will be running on: [http://www.mini-itx.com/store/?c=44](http://www.mini-itx.com/store/?c=44)
PC will not be linked up to a monitor etc (after initial setup) instead I plan to manage it via VNC or similar.

So on with the questions!

[LIST=1]
[*] System will not have a cd/dvd drive etc so I plan on booting to a live install on a USB thumb drive and if possible install from an iso on an external hardrive. What is the best way to go about setting up the live install and performing the main installation?
[*] PC will be setup as a server with external access, what steps should I take to ensure it is secured? How can I limit access to an IP whitelist? Is there any special considerations I should take into account as I plan to run a webserver (apache) on the box as well (access to which will be limited via above whitelist)
[*] What software should I use to manage the box, I've used tightVNC before on windows, should I stick with this or just use ssh?
[*] I don't have a fixed IP address on my home connection (where this box will be) how should I go about setting up dynDNS or similar?
[*] As the main function of this box will be a remote controlled torrent server which torrent client should I use? I need a client I can control externally through a browser based control panel also something which supports RSS would be good :) An added bonus if it has a simple API which I can use to tie the torrent client to the web server etc.
[*] Again I want to ask about security, this will be a public facing server linked to my private home network so I want to be sure it is as locked down as possible.
[*] Anything else you think I should know as a newbie linux user :)
[/LIST]

I've got a week or so until the new box arrives, so I plan on doing alot of reading in that time in preparation. Hopefully I can turn up some of the answers to the questions above with a little help from Google but I thought it was best to ask here as well to get some expert advice! :)

And hopefully if all goes well with this install I can finally get round to ridding this laptop of Vista as well (tho I will sorely miss Photoshop & Flash!!)

cheers

---

### Post by someonestolemyname on 2008-04-07
An Ubuntu server install does not have a GUI, you need to manage it via SSH or install one to use it via VNC. I reccommend SSH, it is very easy, but just a coomand line.

For torrents, try [TorrentFlux]("http://torrentflux.com/"). It is a web-based torrent software that is very nice. Also very easy to setup.

As for everything else, I would highly recommend that you use Linux on the desktop for a while, and get to know how it works, and how to use the commandline, before attempting to set up a server. It is fairly easy, but requires a fair bit of command line usage. Also, running without a gui is very easy if you know how to use the command line.

For Apache setup etc., use [this website on the wiki]("https://help.ubuntu.com/community/ApacheMySQLPHP"). It helps a lot. Although the installation will be done if you choose that in the installer.

Good luck,

Daniel (enjoying his server, on an old desktop pc, under the desk)

As for setting up DynDNS, go to their website. It is on their side. If you have a Linksys router (at least mine) can connect to dyndns and tell them the IP address.

---

### Post by Aaron-B on 2008-04-07
So I would be better doing a server install rather than the normal desktop? (I know it seems like a silly question as the machine will be used as a server, but as a newbie am just checking that it is the right option instead of just using the normal desktop - seems that trying to do everything without any kind of a GUI could be a tall order >.<)

---

### Post by someonestolemyname on 2008-04-09
Well, I prefer servers without a gui as they are much more dependable, but I would recommend that you use linux iont he desktop first to get an idea of where all of the important files are, etc. Linux has it's quirks, but actually using it helps to learn them quickly.

---

