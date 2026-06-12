---
title: "Web-Based File Manager"
date: 2013-07-30
forum: General Help
---

### Post by bmather9 on 2013-07-30
So I'm still pretty new to ubuntu, but I've been running my home server for about a year now.  I use a combination of Webmin and CLI and have a ZFS running with a RaidZ array I use to store all of my data.  

I'd really like to add a web-based interface, that I can navigate to in any common browser to login and download/upload files etc...  Really I'm looking for a web-based file manager similar to ajaxplorer or others out there.  The problem I've run into, is that I'm currently using both SFTP and Samba to share my files as well and have my unix permissions setup so that users have the proper access to certain directories/files.  It seems all programs like Ajaxplorer use the webserver user to accomplish all tasks, therefore my unix file permission are useless.  

Any good software out there?  Is there a better way to do what I'm trying to do here?

---

### Post by TheFu on 2013-07-30
You're already doing it the best way, by using sftp.  You could remotely mount the file system using sshfs, but that only works from UNIX/Linux clients, not any client.

A web interface introduces all sorts of security concerns.  The only way that I'd allow direct file access to non-public files over the web is if a full-strength VPN were required too - IPSec or OpenVPN, NOT pptp.  

There are web-based solutions for this stuff - Alfresco or some WebDAV thing. But they don't usually provide generic access anywhere on the file system.

Perhaps if you asked about great sftp clients for the platforms you care about, an alternative could be suggested?

---

### Post by bmather9 on 2013-07-30
> **TheFu said:**
> You're already doing it the best way, by using sftp.  You could remotely mount the file system using sshfs, but that only works from UNIX/Linux clients, not any client.

A web interface introduces all sorts of security concerns.  The only way that I'd allow direct file access to non-public files over the web is if a full-strength VPN were required too - IPSec or OpenVPN, NOT pptp.  

There are web-based solutions for this stuff - Alfresco or some WebDAV thing. But they don't usually provide generic access anywhere on the file system.

Perhaps if you asked about great sftp clients for the platforms you care about, an alternative could be suggested?

Well, the problem I run into is that on my own computers I have no problem using an sftp client or connecting through my VPN to use samba, but far too often I'll be on some random computer, or a friends computer and need a file from my server, but to access it, I have to install an FTP client, or connect to the VPN.  It would be very nice to be able to use the pre-installed web browser to download a few files.  Beyond that the ability to upload and become a full featured file manager shouldn't be impossible.  I don't need generic access to files anywhere on the system; everything I'd like to share is in one directory.  

If it's safe to open sftp to the world, then why not a web-based system as well?  

In short I'm looking for a way to share files without needing to install a client on almost any device, be it a PC, ipad or android phone.

---

### Post by azmyth on 2013-07-30
You can always setup an apache2 server and then allow display directory contents via the htaccess file. You can then set up the directory you want to allow viewed through a browser. You should also setup password protection. You can use a dns forwarding service to forward the dns to your home PC. I would be careful as it's not real secure or encrypted.

---

### Post by TheFu on 2013-07-31
> **bmather9 said:**
> If it's safe to open sftp to the world, then why not a web-based system as well?  

In short I'm looking for a way to share files without needing to install a client on almost any device, be it a PC, ipad or android phone.

sftp is a secure protocol that even governments cannot crack when used with keys. Throw in **fail2ban** on the server side and you have a very secure remote access solution.

HTTP and even HTTPS are NOT secure. There have been spoofed SSL certificates and HTTPS is based on a stack of cards where a failure of any part can break the entire thing.  When I travel overseas, I don't trust HTTPS at all.  A less-than-perfect DNS server can open everyone up to spoofed HTTPS sessions. An untrustworthy or hacked CA can create certificates for any entity on the Earth that will not be seen as incorrect by anyone except the people inside the spoofed company who actually make the CA requests (about 3 people for most companies).  OTOH, I know that my SSH keys and OpenVPN keys are used to make secure connections. No MITM is possible.

If you don't want to install any client, then use **portable apps** and store those on a USB flash drive that you take with you. That will cover Windows - **WinSCP** definitely works in a portable way.  For Android and iWhatever - I don't know of any secure, portable solutions. OTOH, with my own Android devices, there are lots of SFTP programs that work.  I really don't use anyone elses' portable devices - it isn't normal to share like that with my friends or family, since the Android device contains company, proprietary, data.  Can't share that with anyone.

HTTP is not secure and can NEVER be secure. HTTPS requires a trust level in the network provider, DNS, and every certificate authority in the world - I just can't trust that many entities, especially since many governments **are** the only provider and CA and DNS in some areas of the world.

That leaves OpenVPN and ssh to secure the connections. VPNs integrate deep into the OS, so there will never be an easy VPN to setup quickly except on very specific networks, for very specific OSes, with very specific configurations, connecting to very specific VPN servers.  Setting up dropbox would be easier, though infinitely less secure.

OTOH, ssh does have all the things you want. It is portable, secure, lite, supports ssh, scp, sftp, and sshfs all with just 1 server-side tool.  Client-side, it has lots and lots of options on almost every platform.

Sure, you **can** setup a web-based file manager, but this is one of those things that shouldn't be done, unless you want to share every file with everyone in the world.  In that case, knock yourself out, that is what web servers are all about.  

Allowing uploads from anywhere **is** a huge security risk in an absolute way.  OTOH, it seems that convenience could be more important than security in your environment. If that is the situation, check out **Alfresco** and **OwnCloud**. These are web-base file management tools and probably what you want.  Both are larger than ssh/sftp and both need server resources.  **WebDAV** is another generic name for web-based file management. Most full-featured web browsers support WebDAV.  I've run it for a few years, but never allowed it on the internet - it was full of server-side AND client-side security failings. These failings are enough that many companies prohibit the use of WebDAV completely.

Anyway, hopefully these are some options that will be helpful.  If you allow uploads, even authenticated, over the internet, be certain uploads go to a different SSL-protected domain than downloads come from. This is webapp security 101.

Lastly, I hope you slipped on the keybaord about running FTP - FTP and sftp are **very different**.  Almost nobody should be using FTP anymore [http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp) - ever.

---

### Post by SchnappiJedi on 2013-07-31
Just to clarify SSHFS is supported on Windows ([http://code.google.com/p/win-sshfs/](http://code.google.com/p/win-sshfs/)). However there are permission issues using SSHFS (such as not being able to delete or rename files in my experience). Forking this discussions if anyone knows how to solve permission issue using SSHFS I would love to hear it, however maybe a new thread is warranted.

---

### Post by TheFu on 2013-07-31
sshfs has limitations on every platform - softlinks, hardlinks, are just a few.  I think there are problems with ACLs too.
My use of sshfs has been only between systems that I completely control, so the uid/gid maps between all the systems are almost identical, if not exactly the same.

Back when I used NFS on Windows, there was a mapping file to map Windows users and groups to UNIX users and groups. Seemed to me like too much trust to allow a Windows user control (possible to claim a different GUI/UID and be nasty).  Still, sometimes, sshfs is just what we need especially if there's a big program on 1 machine, but you want it on another that doesn't have it and just want to access remote files.  Or sometimes I've created a complex Perl script that has lots of CPAN dependencies - too many to attempt installing on the other platform, but I still want to run the script. sshfs to the rescue.

---

### Post by bmather9 on 2013-07-31
> **TheFu said:**
> sftp is a secure protocol that even governments cannot crack when used with keys. Throw in **fail2ban** on the server side and you have a very secure remote access solution.

HTTP and even HTTPS are NOT secure. There have been spoofed SSL certificates and HTTPS is based on a stack of cards where a failure of any part can break the entire thing.  When I travel overseas, I don't trust HTTPS at all.  A less-than-perfect DNS server can open everyone up to spoofed HTTPS sessions. An untrustworthy or hacked CA can create certificates for any entity on the Earth that will not be seen as incorrect by anyone except the people inside the spoofed company who actually make the CA requests (about 3 people for most companies).  OTOH, I know that my SSH keys and OpenVPN keys are used to make secure connections. No MITM is possible.

If you don't want to install any client, then use **portable apps** and store those on a USB flash drive that you take with you. That will cover Windows - **WinSCP** definitely works in a portable way.  For Android and iWhatever - I don't know of any secure, portable solutions. OTOH, with my own Android devices, there are lots of SFTP programs that work.  I really don't use anyone elses' portable devices - it isn't normal to share like that with my friends or family, since the Android device contains company, proprietary, data.  Can't share that with anyone.

HTTP is not secure and can NEVER be secure. HTTPS requires a trust level in the network provider, DNS, and every certificate authority in the world - I just can't trust that many entities, especially since many governments **are** the only provider and CA and DNS in some areas of the world.

That leaves OpenVPN and ssh to secure the connections. VPNs integrate deep into the OS, so there will never be an easy VPN to setup quickly except on very specific networks, for very specific OSes, with very specific configurations, connecting to very specific VPN servers.  Setting up dropbox would be easier, though infinitely less secure.

OTOH, ssh does have all the things you want. It is portable, secure, lite, supports ssh, scp, sftp, and sshfs all with just 1 server-side tool.  Client-side, it has lots and lots of options on almost every platform.

Sure, you **can** setup a web-based file manager, but this is one of those things that shouldn't be done, unless you want to share every file with everyone in the world.  In that case, knock yourself out, that is what web servers are all about.  

Allowing uploads from anywhere **is** a huge security risk in an absolute way.  OTOH, it seems that convenience could be more important than security in your environment. If that is the situation, check out **Alfresco** and **OwnCloud**. These are web-base file management tools and probably what you want.  Both are larger than ssh/sftp and both need server resources.  **WebDAV** is another generic name for web-based file management. Most full-featured web browsers support WebDAV.  I've run it for a few years, but never allowed it on the internet - it was full of server-side AND client-side security failings. These failings are enough that many companies prohibit the use of WebDAV completely.

Anyway, hopefully these are some options that will be helpful.  If you allow uploads, even authenticated, over the internet, be certain uploads go to a different SSL-protected domain than downloads come from. This is webapp security 101.

Lastly, I hope you slipped on the keybaord about running FTP - FTP and sftp are **very different**.  Almost nobody should be using FTP anymore [http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp) - ever.


Thanks for the reply.  It sounds like I need to do more reading to fully understand the security implications of what I'd like to do.  My general idea is that since online banks trust SSL, then that should be good enough for my home server files.  Realistically most of what I'm serving are MP3's etc, but there are some documents with personal information as well.  So I certainly care about security, but maybe not to the extent of others.  I may need to rethink what I'm doing here.  

I do use SFTP (not FTP) and have a PPTP VPN setup through my ddWRT router which I chose because that VPN was natively supported by almost everything I could find (including android).  I haven't tested properly, but seem to get slow speeds when using the VPN.  I however do not use keys with my SFTP server, only password authentication.  

So if my banking information is accessible via the web, with nothing else protecting it other than my username and password combination, then why do I need more than a strong password to protect my SFTP server?  

It may be a stretch, but if a bank can serve my financial data over the web, then why can't I serve my personal data with the same (or roughly the same) level of security?

Right now ajaxplorer seems to be a fair solution to what I want.  I can run it HTTPS using password authentication (which seems similar to how online banks work).  Once logged in, I should be able to connect to the SFTP server via the localhost and then the unix permissions will be obeyed.  I'm running into some bugs with this right now, but in general it is working.

---

### Post by TheFu on 2013-07-31
> **bmather9 said:**
> Thanks for the reply.  It sounds like I need to do more reading to fully understand the security implications of what I'd like to do.  My general idea is that since online banks trust SSL, then that should be good enough for my home server files.  Realistically most of what I'm serving are MP3's etc, but there are some documents with personal information as well.  So I certainly care about security, but maybe not to the extent of others.  I may need to rethink what I'm doing here.  

I do use SFTP (not FTP) and have a PPTP VPN setup through my ddWRT router which I chose because that VPN was natively supported by almost everything I could find (including android).  I haven't tested properly, but seem to get slow speeds when using the VPN.  I however do not use keys with my SFTP server, only password authentication.  

So if my banking information is accessible via the web, with nothing else protecting it other than my username and password combination, then why do I need more than a strong password to protect my SFTP server?  

It may be a stretch, but if a bank can serve my financial data over the web, then why can't I serve my personal data with the same (or roughly the same) level of security?

Right now ajaxplorer seems to be a fair solution to what I want.  I can run it HTTPS using password authentication (which seems similar to how online banks work).  Once logged in, I should be able to connect to the SFTP server via the localhost and then the unix permissions will be obeyed.  I'm running into some bugs with this right now, but in general it is working.

Banks pay professionals to run and secure their websites. Banks are hit with online fraud ALL-THE-TIME, but they keep it quiet since banking is about depositor confidence. Learning they get hacked all the time doesn't build confidence.  Banks have insurance to cover their losses too. There is much that every bank IT department does that are not obvious to front-end users, however, much of what banks do is put there to make you feel confident, NOT to actually provide increased security.  It is like the TSA.  I think online banking rules in Europe are much stricter and require the use of user-installed SSL certificates provided by the bank, not just the globally accessible CAs in a list installed by Ubuntu, Microsoft, and Apple, ....

Basic web authentication is not secure and though it looks like the same thing that banks use, it most definitely IS NOT. Lots of methods for attacks, especially if you don't use SSL at all or use a self-signed certificate.  Basic Auth is used on web servers run by hobbyists. No real company would use it.

Web servers are primarily designed to serve as much content as quickly as possible, NOT to be secure.  Apache is designed to support thousands of features. How certain can anyone be that each of those features is secure?  SFTP is designed with security as the primary objective.  Different designs, yields different results.

I don't want to rain on your pptp VPN, but that has been hacked multiple times and shouldn't be used.  ssh alone is more secure, even with a password. When you use ssh/sftp/scp/sshfs or any program that leverages ssh (NX, rsync, rdiff-backup, ....) you get the security and usability for free.  The ~/.ssh/config file makes ssh-based connections easy, even on different ports with different userids.  **Fail2ban** + ssh makes ssh extremely hack-proof on Linux. The default settings for fail2ban are reasonable and will make a bad password the least of your concerns. Keys are better and much more convenient during use, but a strong password (22+ characters) is effectively the same.  [http://www.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://www.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures) has more ideas about securing ssh.

PPTP is better than no VPN, but not much.  I think of it as WEP for VPNs - better than nothing, but not too hard to crack. Either IPSec or OpenVPN are still considered secure, so those should be used instead of PPTP.  Friends who work full-time for security departments think that false security is worse than ZERO security, so they say nobody should use PPTP.

Lots of websites do things that are not secure. It is hard to know looking from the outside.  I've had a conversation with the company CEO where we explained that we cannot make the website uncrackable. It isn't possible. All we can do is have a good plan to recover after a breach occurs. He didn't like that, but he understood it.  Thousands of websites are hacked every day - most don't know it and end up being used to host warez and porn and malware or to launch attacks against other internet connected systems. All it takes is a tiny misconfiguration mistake that keeps the website working, but not secure. Follow a best practices guide when you setup your server and good luck.  

Sorry to go on and on.  Until you setup and get what you need working, it is impossible to learn. I hope this opens your eyes and gets the proper level of concern.  Everything will probably be fine, but don't be surprised if it isn't.

BTW, I'm leading a Linux Security session next week at my LUG, so practicing paranoia is part of that preparation. ;)

---

### Post by bmather9 on 2013-08-02
> **TheFu said:**
> Banks pay professionals to run and secure their websites. Banks are hit with online fraud ALL-THE-TIME, but they keep it quiet since banking is about depositor confidence. Learning they get hacked all the time doesn't build confidence.  Banks have insurance to cover their losses too. There is much that every bank IT department does that are not obvious to front-end users, however, much of what banks do is put there to make you feel confident, NOT to actually provide increased security.  It is like the TSA.  I think online banking rules in Europe are much stricter and require the use of user-installed SSL certificates provided by the bank, not just the globally accessible CAs in a list installed by Ubuntu, Microsoft, and Apple, ....

Basic web authentication is not secure and though it looks like the same thing that banks use, it most definitely IS NOT. Lots of methods for attacks, especially if you don't use SSL at all or use a self-signed certificate.  Basic Auth is used on web servers run by hobbyists. No real company would use it.

Web servers are primarily designed to serve as much content as quickly as possible, NOT to be secure.  Apache is designed to support thousands of features. How certain can anyone be that each of those features is secure?  SFTP is designed with security as the primary objective.  Different designs, yields different results.

I don't want to rain on your pptp VPN, but that has been hacked multiple times and shouldn't be used.  ssh alone is more secure, even with a password. When you use ssh/sftp/scp/sshfs or any program that leverages ssh (NX, rsync, rdiff-backup, ....) you get the security and usability for free.  The ~/.ssh/config file makes ssh-based connections easy, even on different ports with different userids.  **Fail2ban** + ssh makes ssh extremely hack-proof on Linux. The default settings for fail2ban are reasonable and will make a bad password the least of your concerns. Keys are better and much more convenient during use, but a strong password (22+ characters) is effectively the same.  [http://www.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://www.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures) has more ideas about securing ssh.

PPTP is better than no VPN, but not much.  I think of it as WEP for VPNs - better than nothing, but not too hard to crack. Either IPSec or OpenVPN are still considered secure, so those should be used instead of PPTP.  Friends who work full-time for security departments think that false security is worse than ZERO security, so they say nobody should use PPTP.

Lots of websites do things that are not secure. It is hard to know looking from the outside.  I've had a conversation with the company CEO where we explained that we cannot make the website uncrackable. It isn't possible. All we can do is have a good plan to recover after a breach occurs. He didn't like that, but he understood it.  Thousands of websites are hacked every day - most don't know it and end up being used to host warez and porn and malware or to launch attacks against other internet connected systems. All it takes is a tiny misconfiguration mistake that keeps the website working, but not secure. Follow a best practices guide when you setup your server and good luck.  

Sorry to go on and on.  Until you setup and get what you need working, it is impossible to learn. I hope this opens your eyes and gets the proper level of concern.  Everything will probably be fine, but don't be surprised if it isn't.

BTW, I'm leading a Linux Security session next week at my LUG, so practicing paranoia is part of that preparation. ;)

Thanks for the info; I was aware of the lack of security with PPTP VPN's when I set it up, but figured that it was better than nothing and that I would be frustrated using it if it wasn't well supported.  I'm making plans to switch to OpenVPN, since it seems  to be possible to connect to in through a web browser; although I'm not sure if this method allows the use of public/private keys.  

I also refreshed my understanding oh public/private keys, but still am a bit confused as to how I should implement it.  How do I transport my private keys?  I know I could store them on any of my computers safely, and even encrypt them with a password, and I guess carrying around a USB stick would work if I need to connect from a friend's computer, but what about android/ipad devices?

I guess I'm still a bit confused about the HTTPS connection as well, since it seems to use the same public/private key authentication, but the connection is made without me ever messing with a key.  I guess my laptop would have the public key and the webserver has the private key in this case?

---

### Post by TheFu on 2013-08-02
Understanding PKI is easy, and hard.  The technology is used all the time, but in slightly different ways that are incompatible.

Very early on, the **Security Now** podcast covered this stuff.  grc.com/sn  there are audio and high-quality transcripts for every episode. You probably need to visit around ep25-ep50 for how PKI works.

I've never heard that OpenVPN works from a browser. Doubtful.  OpenVPN is not a simple, lite-weight thing that is trivial to install and configure.  You won't be "quickly installing it on friends PCs and devices" to gain access.  It is meant for YOUR devices only.  You'll want to google for much more understanding on this topic.  There are books written about it, so my 100 words here ain't gonna cut it.

---

### Post by bmather9 on 2013-08-02
> **TheFu said:**
> Understanding PKI is easy, and hard.  The technology is used all the time, but in slightly different ways that are incompatible.

Very early on, the **Security Now** podcast covered this stuff.  grc.com/sn  there are audio and high-quality transcripts for every episode. You probably need to visit around ep25-ep50 for how PKI works.

I've never heard that OpenVPN works from a browser. Doubtful.  OpenVPN is not a simple, lite-weight thing that is trivial to install and configure.  You won't be "quickly installing it on friends PCs and devices" to gain access.  It is meant for YOUR devices only.  You'll want to google for much more understanding on this topic.  There are books written about it, so my 100 words here ain't gonna cut it.

Thanks, I'll check out the podcast.  Here's the link that shows the Quick start guide for OpenVPN: [http://openvpn.net/index.php/access-server/docs/quick-start-guide.html#asclient](http://openvpn.net/index.php/access-server/docs/quick-start-guide.html#asclient)
It talks about a feature that seem to be built in called "Connect client":

"[COLOR=#003366][FONT=Arial]The Connect Client Interface is a component of OpenVPN Access Server that allows users to connect to the VPN directly through their web browser. "

There is a screenshot at the bottom and looks to be just password authentication.  [/FONT][/COLOR]

---

### Post by koda2 on 2013-08-02
Does anybody know how can I disable ping & icmp requests? like, if somebody is PINGing my IP-Address, he/she should see nothing, but I SHOULD be able to ping websites/IPs though.  Any idea how can I do this? perhaps via gufw, or ufw..or any other similiar method?  If yes, please give me the exact command to disable ping & icmp requests.

---

### Post by TheFu on 2013-08-02
Google found this: [https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW) about enable/disable ICMP.

Most cheap, home routers have a block-ICMP checkbox.  That will work, but it doesn't really add any security to your network. It just makes troubleshooting harder.  If you don't have a hardware router, that would be the single most important thing to do to increase security for any system/network.

I'm preparing for a talk on Desktop Security at my LUG Thursday.  Here are the web pages I'll be referencing that might help:
* [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)
* [https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security)
* [http://blog.jdpfu.com/pages/wifi-security](http://blog.jdpfu.com/pages/wifi-security)
* [http://blog.jdpfu.com/pages/security](http://blog.jdpfu.com/pages/security)
* [http://blog.jdpfu.com/pages/secure-browser-settings](http://blog.jdpfu.com/pages/secure-browser-settings)

The last three are on my blog - security, virtualization and Linux are the main topics there.

---

### Post by Dmitry4567 on 2013-10-21
[COLOR=#000000][FONT=Arial]Hello,[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]You may be interested in file sharing/document management solution HTTP Commander. [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]It is web application popular in organisations who needs to share local files[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]for remote users (educatonal organisations and other.) It is alternative to FTP, WebDav, Sharepoint, Cloud storages etc.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]It works only in browser and also supports mobile divices. This file manager has integration with online document editors like Office 365, Google docs and clouds like DropBOx, [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]SkyDrive, Google Drive. [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Here is file manager web site [/FONT][/COLOR][http://element-it.com/asp-net-explorer-browser/online-share/web-file-manager.aspx](http://element-it.com/asp-net-explorer-browser/online-share/web-file-manager.aspx)

---

### Post by TheFu on 2013-10-21
> **Dmitry4567 said:**
> You may be interested in file sharing/document management solution HTTP Commander

[http://www.mollify.org/](http://www.mollify.org/) is a GPLv2 offering that seems similar to the above, commercial, offering.  I've never used either.
Also, the apache project probably has a file-server-via-web offering too, probably based on java (yuck).

---

