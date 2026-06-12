---
title: "Ubuntu Version for media server and remote desktop from windows help"
date: 2016-07-26
forum: General Help
---

### Post by corbula on 2016-07-26
Hey everyone, I've just signed up here because I need some help on what to use and how to set this up. I'm new to Linux and haven't used it before.

Let me explain, I've got an Intel Nuc which I want to use to store most of my media and use Plex Media Server to transcode and stream said content to different devices. My Nuc will also auto manage my downloads with the use of rutorrent and filebot to organise and rename it all. All of this I should be able to work out myself however, before that I need to get a remote desktop setup as there won't be a monitor connected to the machine. I need a way of checking on it and do some housekeeping, moving things off deleting files and general organisation now and then.

Also, my desktop is running Windows so I need to be able to remote in from a windows machine.

I've installed Lubuntu as I heard it was lightweight and figured less resources used on the OS the more for transcoding media. I've not been able to get any sort of remote desktop with vnc working though.

Someone elsewhere has suggested Ubuntu server with file manager? Not sure if that's a Linux thing or a Windows thing? 

I can install a different Ubuntu distro or it would make things easier as there's nothing on the machine at the moment.

Anyway, with what I want to do in mind what version of Ubuntu would be best? and what's the best way to be able to get a remote desktop from my Windows machine to Linux?

Thanks all. Let me know if you need to know anything else.

---

### Post by TheFu on 2016-07-26
You can install any program on any Ubuntu you like. If you loaded "Server" (no GUI), then you can load openbox if you want a light-GUI. The GUI isn't the OS, it is just another program. Try out 30 different GUIs, if you like. Just create a new userid (or use the "guest" account) when doing the testing to avoid conflicting config files which are stored in the user-account's HOME.

Don't worry about the GUI-version of Ubuntu that you install. Not a big deal to add or switch them. Maybe 3 minutes of effort for each.  [http://www.howtogeek.com/163154/linux-users-have-a-choice-8-linux-desktop-environments/](http://www.howtogeek.com/163154/linux-users-have-a-choice-8-linux-desktop-environments/)

VNC is kinda slow and not secure at all.  x2go is about 2-3x faster and works over ssh.  Follow the instructions at the x2go website - use their PPA.

BTW, learning ssh and the shell will really be much more efficient than using a remote desktop.

Can't help with the torrent stuff. Grabbing media that way isn't usually legal in my location. I've been using Plex for a few years.  Be certain you have solid, versioned, backups - just sayin'.  Backups are extremely important for anything you don't want to lose and pretty easy to setup on Linux.

---

### Post by corbula on 2016-07-27
Thank you for the help. 

Yea the torrent and media stuff is fine, I was merely saying that so you knew what I planned to do with it. 

I will try x2go with lubuntu first but if I'm still getting issues then I will try either server with a gui, straight Ubuntu or maybe Ubuntu mate. Would you say there is a benefit or reason to go with another versions instead of lubuntu? 

I will have a look at x2go. I'm guessing it works with Windows and Linux? 

Learning ssh and shell may well be more efficient than remote desktop but I need to be able to see the Linux desktop so I can see what it's doing and actually see and explore the files.

When I use the term remote desktop I just mean it as a general phrase to be able to see the desktop visually of the other machine.

---

### Post by TheFu on 2016-07-27
To manage files from any remote system, just use an **sftp** client.  Setup openssh-server and you get sftp automatically. Be certain to secure the ssh/sftp/scp/sshfs/x2go/rsync/rdiff-backup stuff.  Minimally, **fail2ban** and not using passwords (always use ssh-keys), should be sufficient. There are great sftp clients for every networked OS. Generate the ssh-keys on the clients, not the server. For Windows, WinSCP is a nice GUI client.  On Linux, every file manager (thunar, nautilus, caja, etc... ) has support for ssh:// URLs.  

Almost every program that uses ssh protocol will honor ssh-keys automatically. That means using ssh is both more secure than passwords AND more convenient. How often does that happen? ;)

x2go has clients for the main 3 desktops. It doesn't work with any GUI that requires 3D accel graphis - so Unity won't work.  LXDE and XFCE are usually what folks use. Think Mate should work with some keyboard mapping fixes, but I haven't tried it.

Lubuntu vs anything else is a personal choice.  I load Ubuntu server with ssh-server by default on all my systems.  Then I'll add openbox for a lite-GUI on desktop systems, but not on servers. Not much of a fan of learning 5 different ways to accomplish something due to 5 different GUIs. Learn the shell way and only need 1 way, for the next 30 yrs for all Linux systems regardless of desktop or server or any GUI. I'm using commands and scripts written in the early 1990s still.  Short term, the GUI seems easier, but that is a trap and time waster, IMHO.  My best advice for Learning Linux: [http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux) We all start out with the GUI and these days it is much nicer than when I started, but it is allows only about 20% access to the system.

Every session has a different desktop instance. If you are local to the machine and remote in, it isn't the same "instance" and may or may not appear to be the same.  I use x2go to remote desktop even from inside my house. That way the same session is available from anywhere.  Over the LAN, audio works well (it sets up a reverse ssh tunnel for audio). At a cafe, the reverse ssh tunnel fails (there router blocks inbound connections), so audio doesn't work.  With x2go, you can tune the bandwidth available which will increase the compression used. For internet, I leave it set to ISDN speeds and access from down the street or around the world (used on 5 continents) is the same, fast. Great for productivity stuff. Of course, a solid broadband connection is needed for this to be useful and a static WAN IP (or nearly static) is needed.  Dynamic DNS is helpful if you don't have a static IP.  If you want audio, there are other solutions, easily scripted.

ssh is amazing. It is the swiss-army knife of secure networking.  On bad network connections, tools like tmux make it tolerable between disconnections. Some people have bad network connections, but I've been lucky and always had solid connections the last 20+ yrs.

---

### Post by corbula on 2016-07-27
Thank you for all the help.

I've spent all night trying to get x2go working and after much trial and error, I'm stuck.

Here's what I've done so far. I've followed their instructions to install the server on my Lubuntu, that went fine. Then I installed the Windows Client which also went fine, however, upon trying to connect I was met with and error message about passkeys. I can't remember the exact error message. So, after searching I found it was something to do with the passkeys not matching and found this guide on the x2go wiki. [http://wiki.x2go.org/doku.php/wiki%3aadvanced%3aauthentication%3apasswordless-ssh](http://wiki.x2go.org/doku.php/wiki%3aadvanced%3aauthentication%3apasswordless-ssh)

After much messing around with the windows client section, it's really not very clear, at least to me. I've gotten as far as trying to connect via ssh.exe the problem I have though, is that there isn't a ssh.exe in the x2go folder. There is an sshd.exe which I tried with that but all I got was an error about I need to use an absolute path. So now I'm stuck and don't know what to do next.

Hopefully after I can connect with ssh and add the contents of the public key to the authorized keys I should be able to just using x2go as I should be able to.

Any help anyone?

---

### Post by TheFu on 2016-07-27
Did you install and setup ssh between the client and the server first?  That is necessary.  Putty is a popular ssh client for Windows.

Programs that end in 'd', like sshd, are the servers. 'd' means "daemon".

---

### Post by corbula on 2016-07-28
I don't think so. I just followed the instructions for installation on the x2go wiki. It didn't say anything about putty but putty is in the x2go folder so I thought it use that as the program is running. 

I did this first under the Ubuntu section for the server. 
[http://wiki.x2go.org/doku.php/doc:installation:x2goserver](http://wiki.x2go.org/doku.php/doc:installation:x2goserver)

Then this bit under Windows for the client section. 
[http://wiki.x2go.org/doku.php/doc:installation:x2goclient](http://wiki.x2go.org/doku.php/doc:installation:x2goclient)

---

### Post by TheFu on 2016-07-28
Get ssh working between your client and server first. Please. **sudo apt install openssh-server fail2ban** That should do it. Fail2ban prevents brute force attacks from a single IP, but it won't stop coordinated brute force attacks from thousands of IPs. This is why key-based ssh credentials will be needed later, but for now, just get ssh working between the client and server using passwords on the LAN.

x2go works over ssh so that is required.  I have never attempted to get x2go working without having a working openssh-server running and tested between the client and the server. ssh is how the Unix world communicates and how all Unix servers around the world are managed by administrators. I assumed the systems already had ssh. It is a way of life for me.  Right now, I'm ssh'd into about 8 other systems doing a little work. Sorry for my oversight.

---

### Post by corbula on 2016-07-28
Thank you. I will have a look later, can't right now. 

I knew it used ssh but thought that was set up as part of the process setting up x2go. Didn't realise it had to be done separately.

---

### Post by corbula on 2016-07-30
> **TheFu said:**
> Get ssh working between your client and server first. Please. **sudo apt install openssh-server fail2ban** That should do it. Fail2ban prevents brute force attacks from a single IP, but it won't stop coordinated brute force attacks from thousands of IPs. This is why key-based ssh credentials will be needed later, but for now, just get ssh working between the client and server using passwords on the LAN.

x2go works over ssh so that is required.  I have never attempted to get x2go working without having a working openssh-server running and tested between the client and the server. ssh is how the Unix world communicates and how all Unix servers around the world are managed by administrators. I assumed the systems already had ssh. It is a way of life for me.  Right now, I'm ssh'd into about 8 other systems doing a little work. Sorry for my oversight.

Right, sorry for the delayed reply. I've installed openssh on my Lubuntu and just tried Putty on my desktop and connected fine. I got the message saying welcome to Ubuntu. So that works.

What would you suggest now to get x2go working? I will try what I was trying before with the passkeys and see if I can get any further.

---

### Post by TheFu on 2016-07-30
It has been long since this started ... 

I've never gotten ssh-keys to work from Windows, but I've never tried. Get x2go working with passwords, then work on the key-based auth later.

Check the log files, get the EXACT ERRORS and google search with those. Remove any system specific things in the search. Also, look for youtube videos for x2go setup. Just be aware that there isn't any reason to use sudo or root except for the installation stuff. All x2go connections and configuration is done as a normal userid. I watched one of those videos and besides a thick accent, he did things that just aren't necessary, but the x2go settings examples where clear.

If this doesn't help, post the exact command and the exact error messages that you see either on the console or in log files.

It really isn't this hard on a system with ssh working already. There is something basic missing which I consider completely unimportant to mention. Have you looked for youtube videos showing an x2go setup?  Last time I setup a client (June-ish), was a 3 min effort, but that was on a Linux client (chromebook).

I'll ask a few questions to see if these spawn any ideas from your side.
* which desktop did you setup for the system to use?  xfce or lxde are recommended for x2go. Others don't "just work."
* which desktop did you specify inside the x2go configuration to be used? It needs to be one of those above.
* does x2go using passwords work on the LAN?  What do the log files show on the client AND on the server?  Always check the log files.
* inside the client, inside the session settings, disable printing and file sharing. They can be added later.
* do all the testing for now on the same LAN.
* Really, just adding the x2go PPA, doing an apt-get update and apt-get install {package} is all that is needed.

---

### Post by corbula on 2016-07-30
Well it looks like I've got it working.

I had to change the desktop in the client options to local desktop instead of LXDE. Then I started to get an error that 'VcXsrv windows xserver has stopped working', after some search it was to do with the screen resolution. I had to change the resolution of the linux server to a lower res and then the client to match and it worked after that.

All seems to be good now, the only minor issue is when you end a connection x2go crashes but it's not to much of an issue as you simply restart it and it works again.

Thanks for all your help.

---

### Post by TheFu on 2016-07-30
Yep. Completely forgot about the resolution thing.  That's 2nd nature to me.  I have to change resolutions all the time, because my dual monitor setup has 2 different sizes AND resolutions.  Plus, every time I change to a different physical machine thru a KVM, Windows gets confused and resets the screen resolution from 1920x1200 to something lower. Drives me crazy that Windows won't keep the resolution I tell it - automatic resolutions are great for non-programmers, but I shouldn't have to fight to get it to stay and do what I want .... Windows!!!!

Plus lots of people will have 4K resolutions which I've never touched. Don't know if x2go handles the higher resolutions automatically. Was that what happened to your system?

With LXDE, use lxrandr to control the resolution. Actually, lxrandr is a simple, nice tool worthy of being loaded onto any Linux system with a GUI to control the screens and resolutions.  There are other options, but lxrandr is exactly what I need.

Anyway, if this is solved, please mark the thread as SOLVED in the thread tools near the top.

---

### Post by corbula on 2016-07-30
Well, it was because I'm using an Intel Nuc which has a hdmi and my monitor doesn't. So to set it up I had to connect it to my TV, which is running at 1920x1080 and my monitor is maximum 1680x1050. Even though I was selecting a lower resolution in x2go it just couldn't handle it for some reason. When I change the resolution on my linux to lower and matched it with x2go it worked fine.

Thanks a lot, I will mark it as solved now.

---

