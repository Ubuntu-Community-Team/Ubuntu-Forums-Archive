---
title: "What's the best way to share files over the Internet?"
date: 2008-05-15
forum: General Help
---

### Post by Endolith on 2008-05-15
I've commented on several related threads but can't find a good answer.

My goal:
Right now, I have friends who use OS X, Windows, and Ubuntu, and I want to share files with them over the net.  For each user, I want to share certain directories read-only, and certain directories that we can both modify and that they can upload into (though it would be best if they "lock" so we can't both modify the files at the same time and create conflicts).  They're not going to try to compromise my system after they've logged in, but I want to keep things away from them that they could damage accidentally.  I don't want them to be able to see each other's files or my file system, which includes external USB drives (I might want to share folders from these drives with them, but not the whole drives).

Ways I know of to achieve this goal:
[LIST=1]
[*]FTP server (but not secure and configuration seems to be complicated)
[*]scp over SSH (but the goal is to exchange files, not run commands, needs additional restrictions like chroot which is insecure? and scponly? complicated setup)
[*]VPN with Samba file sharing?
[/LIST]

What other ways are there?  Which is the best for my circumstances?

---

### Post by jimv on 2008-05-15
Someone's going to kick me for this, but I would go buy a web hosting plan from somewhere like HostGator.  They sell 350 gigs of space, and 3 terabytes of bandwidth for $5/month.  You could easily create an FTP account on it for you and your friends, and even email accounts if you want.  I use them to host about 6 websites ($8/month for all of em together), and they're pretty fast and reliable.

I'm sure there are other ways to do it, but this would be pretty easy.

---

### Post by Endolith on 2008-05-15
> **jimv said:**
> I'm sure there are other ways to do it, but this would be pretty easy.

Yeah I already have a web host.  This is for stuff that will be changing regularly, that I'll be editing directly from my computer.  Uploading to a separate server first is not very convenient.

---

### Post by jimv on 2008-05-15
SOmething I do is I mount my ftp share to a folder on my local machine, then it's not too inconvenient.

I use curlftpfs to do it:
[http://blog.mypapit.net/2007/05/how-to-use-ftp-filesystem-on-ubuntu-using-curlftpfs.html](http://blog.mypapit.net/2007/05/how-to-use-ftp-filesystem-on-ubuntu-using-curlftpfs.html)

I think you can do the same thing with SSH, but I haven't tried it:
[http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/](http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/)

Perhaps your friends could connect to your box with SSH and mount it on their machines

---

### Post by TeoBigusGeekus on 2008-05-15
Torrents of course!
Torrents were not created in the first place to download mp3s and porn movies, but to share files through the internet.
[http://www.poromenos.org/tutorials/bittorrent]("http://www.poromenos.org/tutorials/bittorrent")

---

### Post by jimv on 2008-05-15
I think he means more realtime file access then a torrent allows for.

---

### Post by Endolith on 2008-05-15
> **TeoBigusGeekus said:**
> Torrents of course!
Torrents were not created in the first place to download mp3s and porn movies, but to share files through the internet.
[http://www.poromenos.org/tutorials/bittorrent]("http://www.poromenos.org/tutorials/bittorrent")

Torrents are really nothing like what I was looking for.  They're meant for distributing files to lots of people.  This is for sharing files with one or two people on a day-to-day basis, and letting them modify those files.  Totally different application.

---

### Post by MJN on 2008-05-19
Take a look at FTP over SSL, aka FTPS. All the benefits if simple user-containment ala traditional FTP but with the security of an encrypted transport layer. vsftpd is but one of many such FTP servers that support FTPS, and there's sure to be an SSL-compatible client for OS X too. Configuration shouldn't be too difficult either (there are no doubt HowTo's available if you get stuck).
 
Mathew

---

### Post by Endolith on 2008-05-19
> **MJN said:**
> Take a look at FTP over SSL, aka FTPS. All the benefits if simple user-containment ala traditional FTP but with the security of an encrypted transport layer. vsftpd is but one of many such FTP servers that support FTPS, and there's sure to be an SSL-compatible client for OS X too. Configuration shouldn't be too difficult either (there are no doubt HowTo's available if you get stuck).
 
Mathew

This was already covered in another thread [http://ubuntuforums.org/showthread.php?t=596917&page=3#21](http://ubuntuforums.org/showthread.php?t=596917&page=3#21)  We shouldn't duplicate the same conversation here.

---

### Post by MJN on 2008-05-19
It was you that started this thread! :)
 
I thought it useful to post here as others will no doubt be unaware of your other posts in the archive (remember we all benefit from these discussions, not just you as the original poster).
 
Back to your issue, don't be afraid of text file configurations. Sure they can be bewildering at first but with familiarity you will soon see their benefits - you'll be in much tighter control and in many aspects, such as security, this can be a real benefit. They also promote a greater understanding of how a service works which in turn can usually make it easier to configure.
 
Mathew

---

### Post by Endolith on 2008-05-19
> **MJN said:**
> It was you that started this thread! :)
 
I thought it useful to post here as others will no doubt be unaware of your other posts in the archive (remember we all benefit from these discussions, not just you as the original poster).

But now do we copy all the responses from that thread over to this one?  Wouldn't it be better to just link to that one?
 
> Back to your issue, don't be afraid of text file configurations.

I'm not "afraid" of text file configurations.  I'd just rather use a real user interface when one is available.  And I'm sure there are one or two available in Linux.  There are a million solutions for things like this in Windows.

> Sure they can be bewildering at first but with familiarity you will soon see their benefits

They don't have any benefits.  :)  I mean, compared to memorizing a bunch of command line switches, or recompiling from source, a text file has benefits.  But not compared to a real user interface.

> you'll be in much tighter control and in many aspects, such as security, this can be a real benefit.

Encouraging users to manually edit configuration files following some dubious instructions online (or copy and paste commands they don't understand into a terminal) is bad for security.  The user interface should show the user all the configuration possibilities available to them without any security vulnerabilities, and warn them if they try to enable something that opens up holes, with links to documentation about the threat, etc.

> They also promote a greater understanding of how a service works which in turn can usually make it easier to configure.

The service should work without requiring any knowledge of its internal functions.  I want to share files with friends; not learn all about the inner workings of my firewall or SSH/FTP/VPN protocols.  That's like saying users should learn all about TCP/IP, HTTP headers, and HTML markup before they use a web browser.

---

### Post by MJN on 2008-05-19
Your stance sounds fairly ingrained so I'll let you continue the search alone as I'm sure you didn't come here to be convinced that the 'Windows way' is not necessarily best. ;)

Mathew

---

### Post by Endolith on 2008-05-19
> **MJN said:**
> Your stance sounds fairly ingrained so I'll let you continue the search alone as I'm sure you didn't come here to be convinced that the 'Windows way' is not necessarily best. ;)

I don't know why no one can answer the question.  I want to allow people outside of my LAN to access folders on my computers that change on a daily basis, and in some cases modify them.  I don't want them to be able to run commands or access other folders.  I want this to be secure.

What system/protocol is best for this?  FTP/SSL?  This doesn't seem like a very common solution, and seems to have a few different implementations.  (Also I have to purchase a certification key?  And it doesn't pass through firewalls very well?)  If this is the best solution, what's an easy-to-configure FTP/SSL server?

---

### Post by RMOP on 2008-06-08
Any progress? I'm trying to setup something similar, towards which I've made SOME progress. I want to be able to access manuscripts on my XP machine remotely. I've managed to get my eeePC Ubuntu machine to load my XP shares automatically when connected through my local WiFi network. I've also been able to configure a VPN (PPTP) from my eeePC to my XP box.

It SHOULD be possible to have those same XP shares connect over the VPN. I'll test that on my next trip. But I suspect it's going to entail more than my existing fstab entries which connect the shares over the local network. I tried connecting over the VPN from the local net, but that's not an adequate test for remote VPN usage, in my experience.

It appears that all of the files you want to share reside on your machine, and that you want to enable Many-to-One connections to your Ubuntu server. Seems that if you can get a One-to-One solution, that you should then be able to create limited shares with access permissions for multiple specific userid and pw.

CAVEAT: I've only done that so far from my Palm TX to my XP box, but that works quite nicely. If it can be done from a Palm, then surely it can be done more easily from a PC. Keep at it. Please post any interim progress.

---

### Post by Endolith on 2008-06-08
> **RMOP said:**
> Any progress?

Nope.  :)  I haven't touched this in weeks.

> **RMOP said:**
> I want to be able to access manuscripts on my XP machine remotely. I've managed to get my eeePC Ubuntu machine to load my XP shares automatically when connected through my local WiFi network. I've also been able to configure a VPN (PPTP) from my eeePC to my XP box.

I have a PPTP VPN setup on DD-WRT which I use to forward the Internet so my company can't see what I'm doing at work and I can access banned sites in China.   :)  I just use SSH to access my own files, with WinSCP in Windows.  My question is more about sharing files with other people.

> It SHOULD be possible to have those same XP shares connect over the VPN. I'll test that on my next trip. But I suspect it's going to entail more than my existing fstab entries which connect the shares over the local network. I tried connecting over the VPN from the local net, but that's not an adequate test for remote VPN usage, in my experience.

Not sure I understand this part.

---

### Post by teddyearp on 2008-06-08
Well, this is my first post and I am a **TOTAL** Ubuntu newbie with questions that I will post later in another forum.  But, I do share files with others, though I have not yet gone as far (yet) for others to be able to upload/change files on my server.

But, my server right now is an XP pro SP2 beast, dual 1.26g PIII's, and six hard drives totaling about 1.5Tbit of storage.  One 250gig HD is dedicated to my apache server under the "DocumentRoot" part of my apache config file.  The files I would like to share with others are in a directory that is not linked within any of my webpages, I just give those few the actual url for the folder.  The other folders on that drive are password protected.  If I want to change what are in those folders, I use remote desktop (if I'm not at home at the time) to log in and then move stuff around.

Now I'm looking into Joomla which may or may not give these users more access to my server if I so chose, but also Ubuntu as an OS since Linux is supposed to be more server friendly.

Howdy y'all!

:lolflag:

p.s. since my post is related to my windoz eperience, sorry if this is either not helpful and/or off topic

---

### Post by RMOP on 2008-06-09
What I mean was that, with my VPN client on my Palm TX, I can access any shares on my XP machine for which I have permissions enabled. I created a separate XP account for the VPN connection, but within the VPN tunnel, I can use my personal XP userid & pw to see my shares. Works just great. I use a little program called WiFile on the Palm, in addition to the VPN client.

It should be possible to give each of your friends a VPN account on your PC, and to then grant restricted permissions based on those same accounts to read/write to the shares of interest. I used a separate account for my VPN login, and then used my usual XP userid/pw to view my shares after VPN was established. No reason I couldn't have used the same userid  pw as for the VPN; I just didn't.

My reasoning fr thinking this to be relevant to your situation is that if I can mount share drives as folders on a Palm TX over a VPN connection to my XP box, it should be possible to do the same from any remote computer. It's done all the time. I just don't know how to do it myself. Yet. Its ironic that I've learned to do it from a Palm but not from a conventional PC.

---

### Post by Endolith on 2008-06-21
How about this:

Is there an easy-to-configure FTP server?

---

### Post by MJN on 2008-06-22
'Easy' is a relative term. I found VSFTP 'easy' to configure, but I know others haven't.

If you are new to the protocol then I'd say FTP is one of the more difficult ones to nail, however if you're familiar with how it works then it shouldn't pose any particular difficulties (other than accommodating the idiosyncrasies of the protocol itself).

Mathew

---

### Post by Endolith on 2008-06-22
> **MJN said:**
> 'Easy' is a relative term. I found VSFTP 'easy' to configure, but I know others haven't.

Command lines and configuration files are by definition *not* easy.  Telling people to use programs like this when they don't understand them is a very bad idea for security and safety.

I'm looking for something *easy* to configure, for personal file sharing.  It doesn't need to be "powerful".  It needs to be safe and simple.  I'm not going to be getting TBs of transfers per day from hundreds of users at a time, I don't think I need to do any advanced configuration options.  I just want my friend to be able to access some directories on my machine, with some read-only and some read-write.  This is for 1 friend to access right now, maybe expanded to 10 or so max if I get something running that is easy to add accounts to (with different directories) later.

> If you are new to the protocol then I'd say FTP is one of the more difficult ones to nail

Many years ago I ran graphical FTP servers in Windows and it was very easy.  I don't know why nothing like this seems to exist in Linux.

---

### Post by Endolith on 2008-06-22
PureAdmin for Pure-FTPd looks good, but doesn't work out of the box.  Any other suggestions?

---

### Post by MJN on 2008-06-23
> **Endolith said:**
> Command lines and configuration files are by definition *not* easy. 

I disagree. There is nothing in the definition of a raw text file that makes it difficult, particularly if it is configured safely and securely by default (as VSFTP is).

> Telling people to use programs like this when they don't understand them is a very bad idea for security and safety.I'm afraid you will have to learn a bit about whatever solution you end up with but don't worry, you won't be alone and these forums should prove beneficial to help walk you through it.

> I'm looking for something *easy* to configure, for personal file sharing.  It doesn't need to be "powerful".  It needs to be safe and simple.  I'm not going to be getting TBs of transfers per day from hundreds of users at a time, I don't think I need to do any advanced configuration options.  I just want my friend to be able to access some directories on my machine, with some read-only and some read-write.  This is for 1 friend to access right now, maybe expanded to 10 or so max if I get something running that is easy to add accounts to (with different directories) later.I've lost count how many suggested solutions you've had now over the numerous threads covering the topic so I'm not sure where else there is to go. You seem to finding fault with every one so far, even those in the no-need-to-configure-anything category. I assume you've been scouring the net for other ideas so we might be scraping the barrel now.

> Many years ago I ran graphical FTP servers in Windows and it was very easy.  I don't know why nothing like this seems to exist in Linux.If you're after point-and-click that's fine, and indeed Windows packages are generally very good at providing that feature. I think Windows may well prove to be the best idea for you?

Mathew

---

### Post by Endolith on 2008-06-23
Solved for now: [http://ubuntuforums.org/showthread.php?t=684590#5](http://ubuntuforums.org/showthread.php?t=684590#5)

---

### Post by MJN on 2008-06-23
Excellent! (Not to mention a relief too! ;-))

Mathew

---

### Post by Endolith on 2008-06-25
> **MJN said:**
> (Not to mention a relief too! ;-))


:roll:

> **MJN said:**
> I disagree. There is nothing in the definition of a raw text file that makes it difficult,

I completely disagree.  For simple file sharing, a config file that requires you to read through a [5000-word man page]("http://vsftpd.beasts.org/vsftpd_conf.html"), with unintuitive options like *nopriv_user*, *listen_address6*, and *setproctitle_enable* is most definitely not easy or necessary.

> I've lost count how many suggested solutions you've had now

Torrents, web hosts, SSH, vsftp, vsftp, and vsftp?  Only two or three were actually relevant to my question, and they're way too difficult for a less technically-inclined user to setup.

So I found an FTP server myself: 

[http://www.terinea.co.uk/blog/linux-ftp-server-with-a-graphical-user-interface-gui/](http://www.terinea.co.uk/blog/linux-ftp-server-with-a-graphical-user-interface-gui/)

FTP isn't really what I was looking for either, but it's the only thing I've found so far.

> even those in the no-need-to-configure-anything category.

Which ones were those?

> If you're after point-and-click that's fine, and indeed Windows packages are generally very good at providing that feature. I think Windows may well prove to be the best idea for you?

Guess so.  I'll be sure to recommend to all my friends to never bother with Ubuntu.

---

### Post by cariboo on 2008-06-25
Could you post here what you did to solve your problem?

I think what MJN was getting at is you have to have some knowlege of what you are doing or else you will end up like a lot of housewives that have set web servers to sell their extra knitting and get their servers hacked on a regular basis.

Remember there are always people out there looking for an open port on a computer, so that they can use it for there own purposes, if you don't have a little bit of knowledge of how to secure your service, you may end up with a big surprise someday.

Jim

---

### Post by Endolith on 2008-07-07
> **cariboo907 said:**
> Could you post here what you did to solve your problem?

I set up an FTP server using PureAdmin and Pure-FTPD.

[http://ubuntuforums.org/showthread.php?t=213266](http://ubuntuforums.org/showthread.php?t=213266)
[http://ubuntuforums.org/showthread.php?t=684590#5](http://ubuntuforums.org/showthread.php?t=684590#5)

> 
I think what MJN was getting at is you have to have some knowlege of what you are doing or else you will end up like a lot of housewives that have set web servers to sell their extra knitting and get their servers hacked on a regular basis.

And what I'm getting at is that telling those housewives to set up a command line server with a configuration file is much more prone to getting them hacked, since they will never understand what they are doing and will build up a mentality of just copying and pasting commands from dubious sources.  Without this mentality, we wouldn't have to worry about things like [this]("http://ubuntuforums.org/announcement.php?f=340").

> Remember there are always people out there looking for an open port on a computer, so that they can use it for there own purposes, if you don't have a little bit of knowledge of how to secure your service, you may end up with a big surprise someday.

And I am very afraid of that.  So I want a simple server setup that doesn't *let* me do bad things, by default.  It should be very secure and limited, and any attempt by me to do more advanced things that open up holes should be complained about with big error messages.  This isn't just about me; I can figure out a config file if I have to.  This is about trying to find a simple, safe, file sharing solution that regular people can use, too.  The kinds of people who think the pictures they posted on a web server are private and don't realize that people can find others in the series just by incrementing the URL number.

---

