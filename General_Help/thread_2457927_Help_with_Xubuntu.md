---
title: "Help with Xubuntu"
date: 2021-02-12
forum: General Help
---

### Post by verumreflexio on 2021-02-12
hI, I like move all the windows os systems to a open source OS. Simple right? Yes and No. I have tried many of flavors (Ubuntu 20, LinuxMint, Lubuntu many others). Each on requires so much tweeking meet my requirements it has become beyond frustration. Iot there addition is that settings in Ubuntu 20 to get simple things to work (like sharing) is possible via a simple setting, But move to a different flavor and settings are hard to find, or require installation of other packages and manual configurations to my requirements, it has become beyond frustration. I am leaning to Xubuntu because Its the only on that can complete install on the HP Pro X2 612 at all. All others fail when you press the install, no errors or anything, just the install starts and just stop.
Here are my requirements and I would like to see I can get Xubuntu do this.
Hardware
Asus B400A Laptop  I5 8gb ram
Hasee Laptop I7 8gb ram nvidia card
HP Pro X2 612 G1 I5 4gm ram
Requirements
1) Ideally I would run the same software on all machine and be able to do a migration of all changes. I have not been successful a doing this.
2) Duel monitor support on restart - I like to remotely admin from Windows and Ubuntu and will it have to restart successfully unattended.  Unfortunately this is not seem possible on most almost all ubuntu 20 based implementations.
3) Remote Desktop support like Microsoft OS. I tried this on and kinda got it to work on Ubuntu but haven't a clue on xubuntu
4) I like to share folders and have both windows and Xubuntu machines to have access.
5) I like to share media to have dnla access from both windows and xubuntu
6) I like to play DRM content through Chromium
7) Get duel monitor to work on HP Pro 612 G1. This model has a display port. The second monitor is distorted and flickers. This happens on all flavors on Ubuntu.


How do I do all these things on xubuntu. Sharing of folders and media is a simple setting Ubuntu 20, I cant find it on Xubuntu for instance. Are there scripts to compete all the steps to setup remote desk top complete. Any help would be most appreciated.

thanks

tim

---

### Post by TheFu on 2021-02-12
First, Linux isn't Windows. It is a completely different OS and expecting to do things the same way will just frustrate you and us.  The decades of using some other OS has warped your mind.

File and storage sharing is trivial, fast, and supports native permissions between Unix systems.  The problem is that you've been warped into thinking the MSFT way was the best or only way to accomplish it.  Use sftp and/or NFS for this.  NFS makes network storage appear to be local. It is machine-to-machine sharing, not end-user to machine sharing.  sftp is built-into every Linux file manager. Just use sftp://192.168.x.x/ in the URL to connect to another system.  You can use a DNS name, if you run a DNS server or you can use an alias, if you have a ~/.ssh/config file setup to address the alias-to-DNS or IP settings.

See - it is just different.  Unix was doing these things years before Windows existed. See how non-Windows people might be frustrated on Windows having to learn the method used there?

I've never had the issues you are claiming with dual monitors. They "just work."

Remote admin is almost always over ssh.  **ssh** is how Unix system connect.  With ssh, we get scp, sftp, sshfs, NX remote desktops, remote editing, backup and restore tools, rsync, tunneling, browser proxies, and the list goes on and on.  Coming from Windows, you've probably never heard of most of these things, unfortunately.  For a remote desktop, use **x2go**, but setup ssh first.  There is a client and a server side.

I understand that Win10 supports NFS. I don't have Win10.  You can use **sftp** from Windows to access any Unix system.  If you want a GUI, use **WinSCP**.

DLNA - there are multiple servers.  miniDLNA, Rygel, Plex Media Server, Jellyfin Server, Emby Server are a few off the top of my head.  I've tried them all. Each has strengths and weaknesses.  None magically work without some text configuration performed. These are network servers - no point-n-click here.
[http://manpages.ubuntu.com/manpages/focal/man5/rygel.conf.5.html](http://manpages.ubuntu.com/manpages/focal/man5/rygel.conf.5.html) . A few how-to articles for Rygel have been written.  But if you google'd "DLNA server ubuntu", I bet you've find some guides and options.

DRM content is too vague. Nobody can guarantee that on any platform.  My solution was to buy a roku and be done with it.

The hardware questions are to broad for any single person to help.  Best to deal with 1 computer and 1 problem in a thread. I'd say to only do one computer at a time, so people who see multiple threads don't get confused between the different systems. Plus solutions you learn on one could apply to others.

Dual monitor isn't really specific enough to get help.  Always need to say which GPU and DE are being used, along with the exact release of which OS and drivers are being used.

The first thing would be to provide a HW overview.  Do that by running this command:  **inxi -Fz** posting both the command and the results wrapped in 'code tags' so the output lines up in these forums.  Code Tags How-to: [https://ubuntuforums.org/misc.php?do=bbcode#code](https://ubuntuforums.org/misc.php?do=bbcode#code)

And never underestimate the Desktop Guide for help: [https://docs.xubuntu.org/2004/](https://docs.xubuntu.org/2004/)

---

### Post by verumreflexio on 2021-02-12
hi, i wasn't really knocking lunix and sorry you got that impression. I'm a retired cto. Mostly windows but i was a unix admin for a couple years 20 years ago. I love when things just work too. i understand they are fundamental different systems. I consider Microsoft os malware, I also want open source  alternatives to be acceptable to general user.

What i a  trying to do is have the similar capability and ease of use.

I'm  glad that you got your duel monitor to work out of the box without any changes. I'm 3&0 on that on 3 different machines. i 

i'm glad its so easy to set up sharing on xubuntu. on ubunto 20 i could go to settings and turn it on for both media and file sharing. where is the same setting in xubuntu
?

thanks for the tips on remote desk top. so you just install and they work, ok

ok ill try out  dlna. point and click, 

no os for home use would ever become popular if requires roku to play protected video. i actually got this to work myself without going to roku, one requirement fulfilled.

i'll get together the other hw info.

thanks















i


.

---

### Post by TheFu on 2021-02-12
> **verumreflexio said:**
>  I'm  glad that you got your duel monitor to work out of the box without any changes. I'm 3&0 on that on 3 different machines. 

I had to configure the dual monitor in the display settings - Ximera or something like that was the mode. This let a single X/Server span multiple monitors. In the old days, we'd have 2 X/Servers running, one for each display.  The mouse could move between them, but no copy/paste between the X/Servers. Web search found this: [https://askubuntu.com/questions/62681/how-do-i-setup-dual-monitors-in-xfce](https://askubuntu.com/questions/62681/how-do-i-setup-dual-monitors-in-xfce) 
Start > Settings > Settings Manger, then open the Display item.  I don't use any DE, so cannot easily check it.

> **verumreflexio said:**
>  i'm glad its so easy to set up sharing on xubuntu. on ubunto 20 i could go to settings and turn it on for both media and file sharing. where is the same setting in xubuntu?
Ubuntu 20 isn't sufficient detail.  20.04 or 20.10?  NFS is NFS across all Linux systems. There isn't a GUI.  And when there is a GUI, it tends not to work for sharing stuff.  Web search found the official NFS documentation: [https://ubuntu.com/server/docs/service-nfs](https://ubuntu.com/server/docs/service-nfs)
For sftp: [http://manpages.ubuntu.com/manpages/bionic/man8/sftp-server.8.html](http://manpages.ubuntu.com/manpages/bionic/man8/sftp-server.8.html) is the server.  **sudo apt install ssh fail2ban** will install the server.  This is one of the few network services that "just work", post install.  
On the client,   **sudo apt install ssh fail2ban**  will install the client tools.  From that point on, any Linux file manager should be able to access any sftp server as already explained.

> **verumreflexio said:**
>  ok ill try out  dlna. point and click, 
Only the client-side is point-n-click. The server side for every DLNA server I know requires text configuration .... it needs to be told where and what type of media you have in broad terms .... like 
[LIST]
[*]Movies are in /svr/movies
[*]TV is in /srv/tv
[*]Music is in /srv/Music
[*]Photos are in /srv/Photos
[/LIST]
Each in that list can be on different mounts or different areas. Some people might have a NAS for most or some of the media - mounted to the DLNA server using NFS.

Don't try to share DLNA stuff out of your HOME directory. That's asking for problems. Also, it is best to ensure the media file system(s) use native Linux file systems, not NTFS or exFAT or FAT32.  There are reasons, but as a former Unix admin, you already know those.

> **verumreflexio said:**
>  no os for home use would ever become popular if requires roku to play protected video. i actually got this to work myself without going to roku, one requirement fulfilled.

I'm passed caring how popular Linux becomes for others.  Stopped worrying about that 15 yrs ago after attempting to lead all the horses to water for a decade.  A $30 roku saved me wasting even 15 minutes more of effort, after I'd wasted 6 hours.  That was 5+ yrs ago.  Linux-Mint did work, but Ubuntu didn't back then. The roku is on a network alone, much of the internet access is blocked for that device, since it really likes to report home about every button pressed.  The same can be said for Plex Media Server, though the Roku is 3x worse than plex.  Oddly, my remaining Windows machine keeps trying to connect to the MSFT IPv6 tunnel service, even though IPv6 is disabled on that system. 

I completely understand that some people feel the need to make everything work, always. We all have different points on different topics where we've wasted too much effort.  I wrote some scripts to handle recording OTA TV based on schedule data rather than use any pre-built solution.  That has been working about 18 months. Most people wouldn't create a custom TV schedule data parser like I did. We all have different itches. ;)  For me, 5 yrs ago, buying a Roku solved the DRM issue with very little effort after I'd wasted 6+ hrs trying to get it working.  I honestly haven't attempted to get it working again since then. Knowing that DRM stuff changes with each release and sometimes with patches for the current release, I expected lots of hassles with it going forward.  Access to the streams with very little chance of problems was a goal for me.  Plus, I tend to run my browser over a locked-down, remote, ssh X11 session, so video inside a browser really isn't very high on the list of priorities here. Now I'm curious.  Just tried my only paid paid streaming service in this browser and **it worked.** Nothing special needed.  The browser is running inside a firejail sandbox.  Hummmm. Perhaps it will work under Kodi too.  We tend to watch video stuff using kodi (actually OSMC) on a raspberry pi connected to our projector.

You probably already know this, but nobody here works for Canonical. The best way I know to get to a Canonical employee is via IRC.

---

### Post by verumreflexio on 2021-02-12
just a update. DRM is not working on Xubuntu. It worked on ubuntu, linex mint and a few other flavors with winevine and minor configuration. 
I enabled drm on firefox and got error 'SlingTV is not supported on Ubuntu, odd since it works on the other ubuntu. So  any workarounds?

Is there a different file editor. The default editor search function is hidden with a short cut. Is there a ubuntu 20 type file manager  I can install.

This may be a silly question. I like on ubunto i can flip between cinemmon to the default  interface. On the default interface I can turn on sharing easily,Can I do the same interface on xubuntu.

thanks

---

### Post by TheFu on 2021-02-12
For SlingTV - they have a free trial until Monday 1700-midnight daily - [https://www.sling.com/deals/special-offer](https://www.sling.com/deals/special-offer) lists the supported platforms.  Android is the closest. I don't see any Linux or BSD desktop OSes listed.  I do know that Roku works. Tried it a few days ago.

Have you tried spoofing the browser *user agent* yet? Often, websites will only look at that string to deny access.  I just spoofed Firefox and it failed to matter, error was that firefox wasn't supported.

BTW, with the Roku, there wasn't any sign-up or sign-in required for the free trial. It just worked. ¯\_(&#12484;)_/¯

As for DRM, did you install the **restricted extras** stuff?  [https://askubuntu.com/questions/248769/what-is-the-difference-between-ubuntu-kubuntu-xubuntu-and-lubuntu-restricted-e](https://askubuntu.com/questions/248769/what-is-the-difference-between-ubuntu-kubuntu-xubuntu-and-lubuntu-restricted-e)

Editor? You can use any editor you like. There must be 100 of them. All personal preference.  I'm certain you seek **vim**, the only editor anyone in the world would ever want. ;)  Editors are holy wars, as you know.  **sudo apt install vim**

---

