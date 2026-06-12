---
title: "Advice needed: I want to listen to my (at home) audio files at work"
date: 2006-09-27
forum: General Help
---

### Post by TeeAhr1 on 2006-09-27
I have about 30GB of audio sitting on the drive at home (Dapper Drake), in various formats (mostly mp3, some flac, some ogg).  I want to be able to browse these files from work (WinXP).  I don't want to stream, I don't need anything fancy, I just want to be able to access them from the office.  Is there some simple utility that will help me do such a thing?

---

### Post by Jussi Kukkonen on 2006-09-27
Well, windows is a problem... if it was linux at both ends you could just use ssh and mount the home disk from work with sshfs. Maybe there's something like that for Windows?

Opening a samba share would work, but I probably wouldn't do that -- internet can be a scary place for an innocent samba share. You should at least be very familiar with samba before doing that.

You said no streaming, but if you have a UPnP-capable player on Windows, you could try gmediaserver at home -- it's not that fancy. I have no idea how secure that is though.

---

### Post by btdown on 2006-09-27
I use Slimdevices "Slimserver" on my home machine, then access it via a web browser & winamp.

You can add this to your /etc/apt/sources.list:
```
# Slimserver respository
deb http://debian.slimdevices.com stable main
```Then apt-get update and apt-get install slimserver.

After it's installed you can navigate your web browser to **[URL="http://yourIp.com:9000"]```
http://yourIp.com:9000
```[/URL]**and open winamp and open url **[URL="http://yourIp.com:9000/stream.mp3"]```
http://yourIp.com:9000/stream.mp3
```[/URL]**

When you click and add songs in the web browser, they are streamed to your open winamp session. It works very well for me. Just make sure your port 9000 is open on your firewall. If for some reason you can't use port 9000, you can change the port in the administration settings.

Obligatory Screenshot:
[IMG]http://216.120.230.82/%7Ekrathis/slimserver.PNG[/IMG]

---

### Post by Jussi Kukkonen on 2006-09-28
> **btdown said:**
> I use Slimdevices "Slimserver" on my home machine, then access it via a web browser & winamp.


That doesn't look half bad... It does have the same potential security problems as a UPnP solution, though. What just popped into my mind was combining your slimserver suggestion (or my gmediaserver suggestion) with ssh tunneling. That would be fairly secure. There's some setting up of course and a little additional overhead from ssh.

---

### Post by bluenova on 2006-09-28
Also check out MPD or Music Player Daemon. It's a way to serve music to pretty much anything.

[http://www.musicpd.org/](http://www.musicpd.org/)

---

### Post by Jussi Kukkonen on 2006-09-28
> **bluenova said:**
> Also check out MPD or Music Player Daemon. It's a way to serve music to pretty much anything.

[http://www.musicpd.org/](http://www.musicpd.org/)
As far as I know MPD is a music player that allows remote control over IP. So it wouldn't be much use here...

---

### Post by btdown on 2006-09-28
Regarding overhead...I already tunnel my browser through an ssh tunnel my squid proxy with no problems.  I have been unable to tunnel the mp3 stream (so far) through the SSH encrypted tunnel. Even if I could, Im not sure how bad the latency would affect the quality/connection.

---

### Post by blackened on 2006-09-28
If you plan on using an SSH tunnel, then it would be a good idea to set up your /etc/hosts files to limit access to your works' ip ranges. Some iptable rules also might be in order. SSH brute force attacks have become a huge nuisance lately. More on setting these up [here]("http://www.debian-administration.org/articles/87").

---

### Post by btdown on 2006-09-28
I agree about the security...I have my Squid proxy only accept connections from my work IP, and I have installed denyhosts (you could also install fail2ban) for ssh brute forces...

 I am still not entirely understanding of the ssh tunnel setup for non squid-proxied stuff, but I'll keep plugging away.

---

### Post by TeeAhr1 on 2006-09-29
> **btdown said:**
> I use Slimdevices "Slimserver" on my home machine, then access it via a web browser & winamp.

Hmm.  Looks like exactly what I'm after, thanks.  Unfortunately, I'm having some difficulty setting it up.  When I try to add my music directory, I get an error that says "this doesn't seem to be a valid folder."  Any idea why that would happen?

---

### Post by btdown on 2006-09-29
> When I try to add my music directory, I get an error that says "this doesn't seem to be a valid folder." Any idea why that would happen?

What is the path to your music directory? Also if you have a lot of music,  and a slow machine, it took a while to scan my music for the first time and stick it in the db.

---

### Post by TeeAhr1 on 2006-09-29
/freezer-space/media/audio

I renamed it to that, because there were spaces in one of the folder names originally, and I thought that might be why I was getting that message.  No joy.  When I installed slimserver, I got a dialogue box asking me to set up Postfix.  Since I didn't know what I was doing, I told it to take no action.  Do I need to set that up to make this work, and if so, how do I do it?  As always, thx for the adivce and patience...

-p.

---

### Post by btdown on 2006-09-29
Hrm. I have no idea why it would ask you to set up Postfix. I dont have postfix installed on my machine either. It does require some dependencies (I think mysql and some perl libraries). Do you have the universe and multiverse repos enabled?

Is /freezer-space/media/audio the full path to the folder? Did you check the permissions on all the folders?

I would do an apt-get remove --purge slimserver, then reinstall it (apt-get install slimserver).

---

### Post by TeeAhr1 on 2006-10-02
It installed a bunch of dependencies when I apt-got it (heh, I love saying that), one of which was Postfix.  I have all repos enabled.  Tried to reinstall it, got the same message.

That's the path to the folder where the artist folders are.  So beneath it I'd have "/freezer-space/media/audio/bob dylan" for example.  Please tell me it's recursive, I'm not about to restructure my entire audio collection...

---

### Post by btdown on 2006-10-02
It's recursive...I've got 114gb of music and once it finally got through sticking everything in the DB, its pretty snappy. There's even an option in slimserver to schedule it to scan your library at a certain time.

You could try this...apt-get remove --purge slimserver, then REMOVE the repo you added for slimserver in /etc/apt/sources.list, and replace it with this one:

> #Slimserver beta
deb [http://debian.slimdevices.com](http://debian.slimdevices.com) unstable main


This will allow you to install the most current beta slimserver package ( I'm it running successfully now in Edgy) . It may solve some of your issues.

Then do an apt-get update and then apt-get install slimserver and see what it does. I would also temporarily set the permissions on the audio folder for 755 just to make sure it isnt a permissions problem. (You put your music folder in the root directory?) For testing purposes, you could also copy an album folder to your non-root user directory, change the permissons, then try to use that folder to test with.

Let me know what it says when you apt-get install the new slimserver.

---

### Post by soundmaster80 on 2006-10-13
I realize this is a week old and no one may be looking at it now but my two cents is for jinzora. I'm doing exactly what you are wanting to do. I have around 30gb of music stored on my server here. I use jinzora to connect to it. The one difference I can think of is that jinzora can use xspf (musicplayer.sourceforge.net) as a player. This means that as long as you have flash installed you don't have to have an extra player. I like this much better as sometimes I'm not at a computer with winamp installed or media player configured. Just a thought, oh, and the interface is pretty slick too :-)

---

### Post by TeeAhr1 on 2006-10-30
Coming back to this after several weeks and a new Edgy installation...

I installed Slimserver again, and now when I go to my IP, I get a "problem connecting" error.  Port 9000 is open, nothing's changed.  Any ideas what's going on?

---

### Post by calx on 2006-10-31
Im getting the same error **TeeAhr1** was talking about originally, 
[I]"New value for Music Folder rejected: Oops - "~/music" doesn't seem to be a valid directory. Try again."
[/I]
I also got the Postfix setup screen during the installation, I chose "local" though.


Made any progress **TeeAhr1**?

---

### Post by TeeAhr1 on 2006-11-01
No, now I can't even get to the Slimserver screen!  It's installed (on my new Edgy installation), and running, but I get "problem connecting to this page" when I put in my IP address.

---

### Post by bluenova on 2006-11-01
> **calx said:**
> Im getting the same error **TeeAhr1** was talking about originally, 
[I]"New value for Music Folder rejected: Oops - "~/music" doesn't seem to be a valid directory. Try again."
[/I]
I also got the Postfix setup screen during the installation, I chose "local" though.


Made any progress **TeeAhr1**?
I had that, to get round it I mounted:

sudo mount --bind /location/of/my/music /media/music

and then point slimserver to get my music from /media/music

it was then happy.

---

### Post by bluenova on 2006-11-01
> **TeeAhr1 said:**
> No, now I can't even get to the Slimserver screen!  It's installed (on my new Edgy installation), and running, but I get "problem connecting to this page" when I put in my IP address.
What about if you use 127.0.0.1:9000

---

### Post by ricp on 2006-11-01
take a look to [http://www.jinzora.org/](http://www.jinzora.org/) 

ricp

---

### Post by TeeAhr1 on 2006-11-02
> **bluenova said:**
> What about if you use 127.0.0.1:9000

That got me there, thanks.  Now, on to the next problem... :rolleyes: 

I plugged in my directory /media/freezer/bag-o-crap/audio and set it loose to scan last night, figuring it would take a while.  I just got home from work, and it claims to still be scanning, and it hasn't found anything.  What gives?

ricp: Thanks for the link, I'm checking out the website in another tab right now!

---

### Post by calx on 2006-11-03
Your a legend **bluenova**, that worked like charm.

---

### Post by bluenova on 2006-11-07
> **TeeAhr1 said:**
> That got me there, thanks.  Now, on to the next problem... :rolleyes: 

I plugged in my directory /media/freezer/bag-o-crap/audio and set it loose to scan last night, figuring it would take a while.  I just got home from work, and it claims to still be scanning, and it hasn't found anything.  What gives?

ricp: Thanks for the link, I'm checking out the website in another tab right now!
It doesn't seem to like more than 2 levels of directories. I would try mounting it to something simple like /media/music

---

### Post by TeeAhr1 on 2006-11-07
> **bluenova said:**
> It doesn't seem to like more than 2 levels of directories. I would try mounting it to something simple like /media/music

Ouch, that sux0rz.  My music is arranged like here's/my/path/Audio/Artist/Album/track.flac - to rearrange them all so they're two levels in would be impossible.  There's always at least two directories between ~/Audio and the actual files.  Hmmm... :-k

---

### Post by bluenova on 2006-11-07
I would check out [http://www.jinzora.org](http://www.jinzora.org)

I havn't had a look at it myself yet, but at first glance it looks like it might be a better solution.

---

