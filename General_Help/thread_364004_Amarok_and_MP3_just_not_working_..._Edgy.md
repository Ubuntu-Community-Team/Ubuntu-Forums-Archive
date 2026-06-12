---
title: "Amarok and MP3 just not working ... Edgy"
date: 2007-02-17
forum: General Help
---

### Post by samalex on 2007-02-17
Hi. I'm using Kubuntu 6.10 and Amarok just isn't working to play MP3's.  OGG files work, but none of the streaming MP3 stations pre-loaded nor my own MP3's nor MP3 Podcasts work.  They look like they're working and even the songs from streaming stations come up, but no audio.

I've reviewed the following sites:
[https://help.ubuntu.com/community/RestrictedFormat](https://help.ubuntu.com/community/RestrictedFormat)
[http://winanga.wordpress.com/2006/03/18/amarok-mp3-support-in-ubuntu-dapper/](http://winanga.wordpress.com/2006/03/18/amarok-mp3-support-in-ubuntu-dapper/)

And I've ran the following:
sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui

plus 

sudo apt-get install gstreamer0.10-plugins-ugly libxine-extracodecs

But nothing.  I've even rebooted.

Rhythmbox works, but Amarok seems to have more features.  

Suggestions?  

Thanks,

Sam

---

### Post by NeoChaosX on 2007-02-17
What exactly happens when you play an MP3 file in the player? libxine-extracodecs should be enough to get MP3 playback.

---

### Post by r4ik on 2007-02-17
May well be the same thing twice or there was one missing anyway this should do it.

sudo aptitude install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base \
gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codecs 

sudo /etc/init.d/gdm restart

just copy and paste.

Good luck !

---

### Post by AndyCooll on 2007-02-17
Which "engine" have you got Amarok using? (Setting > Configure Amarok > Engine)

:cool:

---

### Post by koshari on 2007-02-17
the latest builds have dropped the gstreamer engine, and only have the xine engine, so amarok will only need the xine librarys,

---

### Post by samalex on 2007-02-19
Hi Everyone,

I just ran the following command:
sudo aptitude install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base \
gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codec
... which did download gstreamer0.10-gl, but it appeared I already had everything else.  As for sudo /etc/init.d/gdm restart, I have no file called /etc/init.d/gdm on my system.

As for the Engine, I have 'xine Engine' selected, which is the only option here.  

When I try to download a streaming MP3, it acts as if it is playing as the counter on the bottom right of window counts... but if I play an MP3 file from HD, it acts like it's counting quickly.  Either way no audio.  OGG's do play though, so I know it's working to some degree.

Thanks for any suggestions ...

Sam

---

### Post by samalex on 2007-02-19
Hi.  

Another update on this.  The MP3 I was testing locally was a podcast, but when I try to open an mp3 song it does say Amarok currently cannot play MP3 files.  When I click Install MP3 Support it does nothing.

I'm having to use Rhythmbox, but Amarok is so much better IMO...  I'm at a loss on what to check next.  I can play MP3's from XMMS, Rhythmbox, plus all the KDE sounds work fine.

Thanks --

Sam

---

### Post by Amilius on 2007-04-19
I have the same problem you have, and have tried many ways I've seen in different forums, stuff like sudo aptitude install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base \
 gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse \
 gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codecs 
 
but everytime I try to run these commands I get the same message for all of them:

e2013@e2013-desktop:~$ sudo aptitude install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

what next?

---

### Post by Brucevdk on 2007-04-19
I'm not sure if this is going to help you guys, I didn't even really do anything and it's probably not this simple. But this is how I got Amarok to support MP3s.

[LIST=1]
[*]I installed Amarok, downloaded an MP3 and added it to the playlist
[*] After trying to play it Amarok asked if it could install MP3 support.
[*]I answered yes it it booted up Synaptic to install libmad0 and libxine-extracodecs (nowadays libxine1-ffmpeg)
[*]I restarted Amarok and I was able to play both local MP3s and streams.
[/LIST]

Now by reading the thread I do see at least samalex installed libxine-extracodecs, but I don't see libmad0 mentioned anywhere. See if you can *sudo apt-get install libmad0* it :)

Note that I already had the universe/multiverse repositories and what not enabled.

---

### Post by ronocdh on 2007-04-20
> **Brucevdk said:**
> I'm not sure if this is going to help you guys, I didn't even really do anything and it's probably not this simple. But this is how I got Amarok to support MP3s.

[LIST=1]
[*]I installed Amarok, downloaded an MP3 and added it to the playlist
[*] After trying to play it Amarok asked if it could install MP3 support.
[*]I answered yes it it booted up Synaptic to install libmad0 and libxine-extracodecs
[*]I restarted Amarok and I was able to play both local MP3s and streams.
[/LIST]

Now by reading the thread I do see at least samalex installed libxine-extracodecs, but I don't see libmad0 mentioned anywhere. See if you can *sudo apt-get install libmad0* it :)

Note that I already had the universe/multiverse repositories and what not enabled.
I went into Synaptic and added the packs Bruce pointed out; worked like a charm. Oh, how spoiled we are these days... ;)

---

### Post by eneth80 on 2007-05-06
Thank,it worked for me. I missed libxine-extracodecs

---

### Post by KingdomKid on 2007-05-10
> **Brucevdk said:**
> I'm not sure if this is going to help you guys, I didn't even really do anything and it's probably not this simple. But this is how I got Amarok to support MP3s.

[LIST=1]
[*]I installed Amarok, downloaded an MP3 and added it to the playlist
[*] After trying to play it Amarok asked if it could install MP3 support.
[*]I answered yes it it booted up Synaptic to install libmad0 and libxine-extracodecs
[*]I restarted Amarok and I was able to play both local MP3s and streams.
[/LIST]

Now by reading the thread I do see at least samalex installed libxine-extracodecs, but I don't see libmad0 mentioned anywhere. See if you can *sudo apt-get install libmad0* it :)

Note that I already had the universe/multiverse repositories and what not enabled.

Yep..worked for me too! I needed the libxine-extracodecs.

Thanks "Brucevdk"

---

