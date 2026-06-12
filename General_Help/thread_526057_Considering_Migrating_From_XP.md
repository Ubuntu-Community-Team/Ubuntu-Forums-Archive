---
title: "Considering Migrating From XP"
date: 2007-08-15
forum: General Help
---

### Post by marioluigi123 on 2007-08-15
So I've been following Ubuntu for a while, tested out the LiveCD of Edgy Eft (6.06), and I really think I'm ready to use it. 

I have tried Wubi, but that was unsuccessful after numerous attempts. As a result, I've decided to just change my ancient laptop (which I use primarily, but only for Internet access, Bittorrent, media, and a few emulators) to Ubuntu to see how I like it. I'm getting a new computer in about a year before I head off to college, so I'm not too worried. Basically, I have a few niggling concerns that I hope can be addressed before I make the move.

First, I want to ask how well the system will run Ubuntu. It's running XP Pro right now (which I keep pretty lite), so I think I'll be fine, but here's the specs:

Pentium III 797MHz
191MB RAM
ATI Rage Mobility 4MB Graphics Card (Yeah...I know. Looks like no Compiz Fusion for me.:()

Hopefully that's all nice and good. My second question is about hardware support. It's an old IBM Thinkpad A22m. I think IBM and Linux have a good compatibility track record, but I'd like to be sure it runs before I nix my Windows install. Basically, I want to know: if the LiveCD runs flawlessly (as far as hardware support and such), will Ubuntu run the same when it's installed?

Here's the rest of my concerns in a handy-dandy list format.

1) Can I file share with Windows computers? I frequently use BitTorrent, and with only a 9GB hard drive and lacking the tools to use external media storage, I need the file sharing available.
2) Can I use printer sharing with printers attached to Windows machines? This isn't too important but would be a nice feature.
3) I run an NES, SNES, and Genesis emulator, and I was wondering if there are suitable Linux replacements.
4) I absolutely love using uTorrent, and I saw in the Ubuntu Guide that it can be run under Wine. Is this true, and does it work reasonably well?
5) I tried VLC on Windows, but was unsatisfied with both its look (livable) and its lack of full-screen controls (unlivable). I then found Media Player Classic bundled with the K-Lite Codec Pack. Is there a suitable Linux equivalent for both the player and codecs? Is the Linux version of VLC better?
6) Can I copy over my Firefox profile (found under Windows in Documents and Settings/Application Data) to Firefox on Linux? Also, if I can, where would Firefox be installed under Ubuntu (assuming I use the default add/remove programs)?

Well, that's all the questions I have. Sorry for the long post. I hope that as soon as I can get these questions answered, I can fire up the CD burner. Thanks for your time!

---

### Post by n00buntu NJ on 2007-08-15
> **marioluigi123 said:**
> So I've been following Ubuntu for a while, tested out the LiveCD of Edgy Eft (6.06), and I really think I'm ready to use it. 

I have tried Wubi, but that was unsuccessful after numerous attempts. As a result, I've decided to just change my ancient laptop (which I use primarily, but only for Internet access, Bittorrent, media, and a few emulators) to Ubuntu to see how I like it. I'm getting a new computer in about a year before I head off to college, so I'm not too worried. Basically, I have a few niggling concerns that I hope can be addressed before I make the move.

First, I want to ask how well the system will run Ubuntu. It's running XP Pro right now (which I keep pretty lite), so I think I'll be fine, but here's the specs:

Pentium III 797MHz
191MB RAM
ATI Rage Mobility 4MB Graphics Card (Yeah...I know. Looks like no Compiz Fusion for me.:()

Hopefully that's all nice and good. My second question is about hardware support. It's an old IBM Thinkpad A22m. I think IBM and Linux have a good compatibility track record, but I'd like to be sure it runs before I nix my Windows install. Basically, I want to know: if the LiveCD runs flawlessly (as far as hardware support and such), will Ubuntu run the same when it's installed?

Here's the rest of my concerns in a handy-dandy list format.

1) Can I file share with Windows computers? I frequently use BitTorrent, and with only a 9GB hard drive and lacking the tools to use external media storage, I need the file sharing available.
2) Can I use printer sharing with printers attached to Windows machines? This isn't too important but would be a nice feature.
3) I run an NES, SNES, and Genesis emulator, and I was wondering if there are suitable Linux replacements.
4) I absolutely love using uTorrent, and I saw in the Ubuntu Guide that it can be run under Wine. Is this true, and does it work reasonably well?
5) I tried VLC on Windows, but was unsatisfied with both its look (livable) and its lack of full-screen controls (unlivable). I then found Media Player Classic bundled with the K-Lite Codec Pack. Is there a suitable Linux equivalent for both the player and codecs? Is the Linux version of VLC better?
6) Can I copy over my Firefox profile (found under Windows in Documents and Settings/Application Data) to Firefox on Linux? Also, if I can, where would Firefox be installed under Ubuntu (assuming I use the default add/remove programs)?

Well, that's all the questions I have. Sorry for the long post. I hope that as soon as I can get these questions answered, I can fire up the CD burner. Thanks for your time!

marioluigi123 - hopefully I can give you a few pointers that will help you find what you're looking for! 

1. YES!  You can access Shared folders from Ubuntu very easily - you can even have a "Windows Share" of your own in Ubuntu via Samba (google "Samba" for more info - it is very powerful, and works VERY well).
Not to mention the fact that you could easily install an FTP server, or install an SSH server, and use an SFTP client from a windows machine to pull/push files back an forth.
There are a number of other ways this could be done, but these are probably the easiest.  
This is easily one of Linux's strongest features IMO (anything related to networking/file transferring).

2. YES AGAIN!  You can share printers via Samba - however I have not tried this myself, so I cannot comment on the configuration.
I myself do printer sharing by the built-in implementation of CUPS (again, google it - you'll want to learn more), by which I have a printer attached to my Ubuntu box in the basement, and my wife prints wirelessly to it from her Mac OS X laptop - using all tools that come installed with Ubuntu.

See here for more info:  [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

3. I don't use any emulators, but my friend has some working and they seem to run pretty well.

4. YES!  When I first switched from Windows I too used uTorrent under wine - it worked flawlessly (probably even better than the available clients at the time that were comparable in features), however now you'd probably want to check out Deluge - it is native, and loaded with features (it's an awesome torrent client).

[http://www.deluge-torrent.org/](http://www.deluge-torrent.org/)

5. VLC is pretty nice in Ubuntu, I have it along with MPlayer installed on my machine and they will play any video file I throw at them.  There are SO MANY guides about getting these running that you shouldn't have a single issue (I'd start at [http://ubuntuguide.org](http://ubuntuguide.org))

6. Firefox 2 will be installed by default in Ubuntu 7.04 - it's the default browser too!  As far as moving your profile, I'm not sure but it shouldn't be too painful.



I hope this helps - welcome aboard!

Regards.

---

### Post by soxs on 2007-08-15
I've erased my windows just 3 weeks ago.. and I'm happy :guitar::KS

Feisty fawn ftw!

---

### Post by marioluigi123 on 2007-08-15
Thank you very much for the information. I've actually heard many of these programs/technologies thrown around (Samba, CUPS, Deluge, MPlayer) as I do follow Linux development somewhat. I guess I was just looking for a more personal response about someone who actually uses all these.

Well, you seem to have boosted my confidence, and though I think my next computer will be an XP/Ubuntu dual boot, it's a step. :)

I hate to say it after the nice reply, but I do have just one more concern. It comes from the following paragraph, copied and pasted from my original post:

Hopefully that's all nice and good. My second question is about hardware support. It's an old IBM Thinkpad A22m. I think IBM and Linux have a good compatibility track record, but I'd like to be sure it runs before I nix my Windows install. Basically, I want to know: if the LiveCD runs flawlessly (as far as hardware support and such), will Ubuntu run the same when it's installed?

If I can get that question answered, my quest will be complete.

---

### Post by Steve1961 on 2007-08-15
This link might help:

[http://www.thinkwiki.org/wiki/Category:A22m](http://www.thinkwiki.org/wiki/Category:A22m)

My only concern would be the amount of ram in your machine.  If you could stick another 128mb in you would get much better performance.  If not, I'd suggest going for xubuntu rather than Ubuntu.

---

### Post by marioluigi123 on 2007-08-15
Yeah, that's the machine.

I agree with the RAM issue. In this day and age, it's not much, but upgrading is not an option. Do you think regular, GNOME Ubuntu will still be workable? I don't mind perfect performance, and I'd keep programs running to a minimum. I've gotten used to the way everything runs on Windows XP with a low amount of RAM, and I have no qualms about it. I actually run a Firefox window with 25-30 open tabs, and I can manage that. Like I said, this computer is mostly for low end stuff: Internet access, BitTorrent, Media (like video and audio), and some basic emulators.

So knowing all that, do you still think that GNOME Ubuntu will work?

---

### Post by Steve1961 on 2007-08-15
> **marioluigi123 said:**
> Yeah, that's the machine.

I agree with the RAM issue. In this day and age, it's not much, but upgrading is not an option. Do you think regular, GNOME Ubuntu will still be workable? I don't mind perfect performance, and I'd keep programs running to a minimum. I've gotten used to the way everything runs on Windows XP with a low amount of RAM, and I have no qualms about it. I actually run a Firefox window with 25-30 open tabs, and I can manage that. Like I said, this computer is mostly for low end stuff: Internet access, BitTorrent, Media (like video and audio), and some basic emulators.

So knowing all that, do you still think that GNOME Ubuntu will work?

It will work, but it won't break any speed records.  You'll also need to install from the  alternative CD as your ram isn't enough for an installation from the live CD.

---

### Post by marioluigi123 on 2007-08-15
Well, sounds like I'm off to some happy computing. Luckily, I already have the 7.04 alternative iso. I'll try to post back in a few days with the results.

Again, thank you all for your help and time. This is actually part of the reason why I'm excited about using Ubuntu and Linux in general - a helpful community.

Thanks!

---

