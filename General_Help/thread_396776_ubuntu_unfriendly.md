---
title: "ubuntu unfriendly"
date: 2007-03-29
forum: General Help
---

### Post by j1mw3b on 2007-03-29
I normally use Fedora and/or Suse.  Read about how Ubuntu is so popular so thought I'd give it a try.  
Actually did try Debian Sarge several months ago and was disappointed by it.

Now Ubuntu and my problems - and the only reason I am posting this is to make suggestions that might make it easier for others first attempts.

1.  Confused about the server and desktop configurations.  I actually want both.  Why can't I have it?  Red Hat used to do this (maybe still do), but you were at least allowed to choose to install a customized combo.  
2. I chose desktop and now have to go thru the hassle of getting all my server stuff to work.
I had no choice to install it from the gitgo.  Bummer.  E.g. xinetd, mysql, apache, ftpd, telnetd, ntpd, webmin, and on and on.
2a. I did install a server version on a VMWare machine and didn't get very many servers.
3.  The only useful ftp/telnet servers i have found are inetutils - hard to believe in all the repositories, none exist.    
4.  I have enabled all the repositories but still had to download extra packages (libauthen-pam-perl, libmd5-perl) to get webmin to install.
5.  I am on my 2nd install - with the first everything just went haywire - couldn't get all of the Gnome menu items under "system"/"administration".
6.  I have to install all these servers!  Why not just install them and configure a default firewall to prohibit usage.

I am sorry for the soapbox preaching, but this thing is way to difficult.   Do a Fedora install and you will see a better way.  I'm still looking for a mysql.
I do expect some blasting for this post, but that's OK, I can take it.

Jim

---

### Post by zorkerz on 2007-03-29
I dont do any server work but it seems like a good idea to be able to do a custom install that could fit your needs for both. I don't know if this is possible or not.

---

### Post by zvacet on 2007-03-30
Install server edition(you can install LAMP) and if you want GUI install it

If you want GNOME
```
sudo aptitude install ubuntu-desktop
```

and for KDE
```
sudo aptitude install kubuntu-desktop
```

---

### Post by rnwld999 on 2007-03-30
Hey Jim, being a former Redhat user I can understand your issues, having made the jump from Redhat to Debian to Ubuntu.   It's like night and day but stick with Ubuntu for a little bit longer you'll learn to get around it and see why its a popular distro.  If you want the Server/Desktop then zvacet recommendation is what you need to do.  All my servers have no GUI (I still prefer command line).  

Your comment #6, well I use to do that until a very creative hacker showed me why you don't want to do that.  

BTW...your very brave to have tried Debian's Sarge you've probably been scarred for life now.

---

### Post by 23meg on 2007-03-30
> 1. Confused about the server and desktop configurations. I actually want both. Why can't I have it? Red Hat used to do this (maybe still do), but you were at least allowed to choose to install a customized combo.

2. I chose desktop and now have to go thru the hassle of getting all my server stuff to work.
I had no choice to install it from the gitgo. Bummer. E.g. xinetd, mysql, apache, ftpd, telnetd, ntpd, webmin, and on and on.


Ubuntu does not let you select which packages to install, since it's a single CD distro by principle, and most of its user base will require most of what's on the CD, and they can add things from the repositories after install. What you have to do is do a server install, and add whatever GUI you want on top of it, with the related -desktop metapackage (e.g. xubuntu-desktop), or if you want a simpler environment with less applications, something like kde-core.

> 2a. I did install a server version on a VMWare machine and didn't get very many servers.
3. The only useful ftp/telnet servers i have found are inetutils - hard to believe in all the repositories, none exist. 

Is there a specific package you were looking for and couldn't find? For FTP, a description search for "ftp" or "ftp server" in Synaptic after you've enabled Universe may help. Not sure about vmware.

> 4. I have enabled all the repositories but still had to download extra packages (libauthen-pam-perl, libmd5-perl) to get webmin to install.

Webmin *from the repositories*? It didn't handle all the dependencies and you had to download and install them yourself? Assuming you have a healthy sources.list, that's a bug; go ahead and report it.

> 5. I am on my 2nd install - with the first everything just went haywire - couldn't get all of the Gnome menu items under "system"/"administration".

Probably a dud burn / disk error, or failure on your part, if things are fine the second time around.

> 6. I have to install all these servers! Why not just install them and configure a default firewall to prohibit usage.

The Ubuntu approach is "basic set of packages, no open ports by default; add stuff yourself" instead of "preinstall servers and set firewall accordingly". It has to do with basic design principles; it's a deeply rooted decision and is unlikely to change. If you don't like it and can't live with it, Ubuntu may not be suitable for you.

---

### Post by tgm4883 on 2007-03-30
Don't know if your using edgy or feisty, but webmin installed just fine and resolved all dependencies on my edgy install.

I must have a better sources.list

---

### Post by j1mw3b on 2007-03-30
Well, the 2nd time around things working much better.  It is probable that webmin didn't work because I had insufficient repositories.

The VMWare comment was not that I wanted VMWare on Ubuntu - just that I installed the Ubuntu server on a VMWare WinXP host.

Was finally able to even get Freenx installed (but not working).  Also never succeeded in getting a vncserver to work, or a workable telnet/ftp.  Like why should I have to go and edit the entries in /etc/xinetd.d myself?

Another thing, in my past, root is the king.  But not here.  I can't login as root until I enable it in some "login window", and even then, when I now logon as root, I can't see all of the "system, administration" menu items - have to run them from command line.

See, this thing is fine for a simple desktop system, and I think that is it's target audience; but for a full-blown unix workstation, just too much trouble.

The clincher came when I started trying to get my mythtv to work and the usb ports aren't recognized (and subsequently the PVR-USB2).

Have moved back to my Fedora 6 for now.  I had read somewhere that mythtv and Ubuntu worked well together, but not really.

There must be good reasons for all this unfamiliar workings, but I don't get it.  I did save my Ubuntu 6.10 partition, so can try it again at a later date.

You know what I wish - that all the Linuxes would somehow come together and give less choices and more consistent behavior.  Like let's pick one and go for it - or at least narrow it down to 2 or 3 good distributions.  
I think that is the only way to defeat the dark side (MS) in the end.  Maybe a nice distribution named "Jedi"

---

### Post by 23meg on 2007-03-30
> Another thing, in my past, root is the king. But not here. I can't login as root until I enable it in some "login window", and even then, when I now logon as root, I can't see all of the "system, administration" menu items - have to run them from command line.

The root account is disabled by default. You won't ever have to log in as root; just use sudo.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

> See, this thing is fine for a simple desktop system, and I think that is it's target audience; but for a full-blown unix workstation, just too much trouble.

> There must be good reasons for all this unfamiliar workings, but I don't get it. I did save my Ubuntu 6.10 partition, so can try it again at a later date.


From your reply I'm guessing it's just that you're having too much trouble because you're used to working in the different paradigm of Fedora / Suse and lack familiarity with the Debian / Ubuntu way of doing things. I believe I'd have similar problems if I switched to Fedora this moment, but I'd figure things out as I got familiar with it.

> The clincher came when I started trying to get my mythtv to work and the usb ports aren't recognized (and subsequently the PVR-USB2).

Have moved back to my Fedora 6 for now. I had read somewhere that mythtv and Ubuntu worked well together, but not really.

You could have asked for help by starting separate, properly titled threads for each of your problems, and chances are they'd get solved, but if you don't want to be bothered, it's your call; use what works for you.

> You know what I wish - that all the Linuxes would somehow come together and give less choices and more consistent behavior. Like let's pick one and go for it - or at least narrow it down to 2 or 3 good distributions.
I think that is the only way to defeat the dark side (MS) in the end. Maybe a nice distribution named "Jedi"

What's keeping you from picking one and going for it now? It seems you're comfortable with Fedora / Suse, you've picked them, so how about just forgetting the rest? Just a suggestion.

Anyway, we have a [unified Linux thread]("http://www.ubuntuforums.org/showthread.php?t=328824") where you can... talk about that. Thankfully, it will never happen.

---

### Post by tgm4883 on 2007-03-30
> **j1mw3b said:**
> 
You know what I wish - that all the Linuxes would somehow come together and give less choices and more consistent behavior.  Like let's pick one and go for it - or at least narrow it down to 2 or 3 good distributions.  
I think that is the only way to defeat the dark side (MS) in the end.  Maybe a nice distribution named "Jedi"

Well you may have just summed up why you can't get this to work.  You want to defeat MS by being like MS.  Linux is not Windows.  Linux is not like Windows.  This is by design and a good thing.  If you want to use a distribution like Windows, where everything is easy for you then I suggest you use this little known distro called XP, I think it's made by a company called Microsoft

---

### Post by land0 on 2007-03-30
> **j1mw3b said:**
> 
You know what I wish - that all the Linuxes would somehow come together and give less choices and more consistent behavior.  Like let's pick one and go for it - or at least narrow it down to 2 or 3 good distributions.  
I think that is the only way to defeat the dark side (MS) in the end.  Maybe a nice distribution named "Jedi"

Interesting thought. However the diversity of distro's is what makes FLOSS unbeatable. The fact that with a little bit of effort one can have a computer solution that wraps around you and your work/play habits is unreal. This is not even touching on the fact that there is the freedom to choose a distro that matches ones personal philosophies. To narrow Linux based distro's down to only two or three would kill innovation and creativity. So I strongly disagree with you on this point. Ubuntu is not for everybody just like Redhat/Fedora is not for everyone. But Ubuntu does fill a gap that was never addressed before that in itself is huge! 

**Solutions:** You could always re-master Ubuntu into Jeduntu and add all the goodies you want. It would be welcomed I am sure. As you are probably not the only one to have the itch for a really easy to manage server/desktop hybrid. You also have the freedom to stick with Fedora or even roll your own. :guitar:  Groovy baby!

**BTW:** Did you ever notice that in the end it was the dark side that destroyed the dark side? M$ is the perfect example of why there is so much safety in diversity! 
[B]
Closing thought:[/B] The only reason there has never been and will never be a distro named Jedi is because of the Death Star :KS  sized onslaught of lawsuits that would rain down as a result. :)

---

### Post by fuzzynco on 2008-02-20
I'm trying to get basic services running, telnet / telnetd seems to be 
a problem. I tried what I could find but while the programs are there
I'm unable to make a connection, (from a local screen via telnet 
to the ip address of the box). It looks like inetd is running.
but not starting the telnetd daemon on getting a connection?

I'm logged in as a user locally, (not on X windows), trying to connect 
to the same machine with the basic telnet client. My intent is to be able 
to remote support the intended user of this box. ssh would be fine too,
I just need a console shell to work in). 

I was unable to locate the kernel config file, I'm guessing Linux 
keeps its system source some where different then BSD unix did?

How does one compile a custom kernel with ubunto?
Is there a howto or some other instruction sheet 
to follow?

:confused:

thanks

---

### Post by Niva on 2008-02-20
I think ubuntu is the friendliest distro in terms of working out of the box on most hardware and "just works."  However, I don't like the way repositories are managed and searched in ubuntu as compared to Suse.  Maybe it's because I used Suse much longer but the repositories/patterns work much more intuitively for me than in Ubuntu.

Anyways, this really could be operator unfamiliarity on my part, I really need to spend more time.

In favor of Ubuntu though it has the best message board system ever.  Even when using other distros I always find myself linked to these forums, they're amazing.  Now I'm here too :)

---

