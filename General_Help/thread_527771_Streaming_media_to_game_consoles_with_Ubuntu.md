---
title: "Streaming media to game consoles with Ubuntu?"
date: 2007-08-17
forum: General Help
---

### Post by nutz on 2007-08-17
First of all I wasn't exactly sure how this should be categorized so I just put it under general.

For about two weeks now I have been trying to get my 360 to read media served by my Ubuntu machine. I have tried several programs such as xbox360mediaserve, geekbox and ushare. But as of yet none of them have been successful for me and it is getting pretty frustrating.

I have searched high and low on the forum and even followed some of the guides that members posted links to. I also broke down and tried running a Windows client named FUPPES. Even though the windows client installed under wine just fine it failes when you launch the program. Ha! It was worth a try...

Anyway; some of these programs supposedly also work with the PS3. I am running out of ideas here so I thought I would start a new thread to see where the development on this topic stands. What programs if any have you gotten to work and how did you do it? If possible I would like to get FUPPES working since it does trans coding from many common formats on the fly. Shouldn't something like this be a standard upnp device with native OS support? Like the way digital cameras and such are handled? What can be done here to make this less painful?

---

### Post by nutz on 2007-08-19
bump

---

### Post by weblordpepe on 2007-08-19
I've got no clue about any of this, but surely the XBOX / 360 can view files shared from a Windows machine?
In which case you could use a samba share.

Or am I just talking out my butt?

---

### Post by nutz on 2007-08-19
It's not as simple as just sharing the files. You need to have a upnp media server for it to connect to. Media Player 11 does this for Win XP. But I don't have a windows machine.

---

### Post by weblordpepe on 2007-08-20
Really? How rank. Dont you just hate proprietary stuff?

---

### Post by nutz on 2007-08-20
Well the PS3 and other network media devices work the same way. I can't believe Ubuntu doesn't have any support for networked media devices.

---

### Post by weblordpepe on 2007-08-22
Maybe you should go beyond Ubuntu & look at general linux stuff. How do these networked media devices work anyway?

You're not talking about NFS or something are you? I really have no clue here but I can't amagine its much of a difficult thing.

---

### Post by notwen on 2007-08-22
Not sure if this is what you're looking for or if it will help, but you may want to check out [this]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#Streaming_Media_Server").  =]

---

### Post by nutz on 2007-08-22
I am looking for something like [this]("http://fuppes.ulrich-voelkel.de/").

For some reason I can't get this program to work though. It does transcoding realtime and supports both the PS3 and 360.

---

### Post by nutz on 2007-08-23
bump

---

### Post by radioraheem8 on 2007-08-24
Hey all, I can't comment on X360, but the PS3 is quite easy to set up as a media server with feisty ubuntu.  Try MediaTomb; there are handy directions on Google (sorry I can't access the site as I am at work, or I'd include the link), step by step.  One thing though, the instructions are for edge, so be sure to replace it with feisty if that is your version.  (took me about an hour to realize this last night)

Then open Mediatomb, and browse to your media files.  Add them to the media server.  Make sure the PS3 has media servers enabled, then do a search for it (usually takes a minute).  Ta da, porn and music on your PS3!  Although I did this last night, I had some trouble with the audio files.  Mpegs did work well, though.  

I know the PS3 works with Windows XP Media PLayer 11; I can't imagine the X360 having a conflict issue with any Windows platform...

---

### Post by nutz on 2007-08-24
Does it support transcoding? If not then it isn't any better than the twonkeymedia that I already have setup.

I would like to stay away from MS products unless they are free and open source.

---

### Post by weblordpepe on 2007-08-27
Ohh so you want to stream your music to the Xbox??

Man its times like these that I wish [Orb]("http://www.orb.com") ran in linux

---

### Post by nutz on 2007-08-27
> **weblordpepe said:**
> Ohh so you want to stream your music to the Xbox??

Man its times like these that I wish [Orb]("http://www.orb.com") ran in linux


Will Orb talk to the 360? Does it transcode into formats the 360 will play?

---

### Post by weblordpepe on 2007-08-28
I dont know. It does windows media format or mpeg.
Orb just plays in your web browser + media player. I think it can do either wma or realplayer or something else.

---

### Post by cevil203 on 2007-08-28
i used tversity on vista for streaming podcasts like diggnation straight to my 360 which was nice , and it allowed me to stream divx files from my pc to it also. unfortunately i can not help you, i just wanted to say that. :D

---

### Post by weblordpepe on 2007-08-28
Booooo!

---

### Post by boogieboarder97 on 2007-08-30
i used tversity and orb on windows they worked good but tversity supports a lot more formats and transcodes but it uses a lot of memory. orb is a great program ur right they should make a client for linux. orb transcodes i no this because if i play an .avi file through orb it works and .avi files dont work if you put it on portable media and try to play it throgh the file browser for some reason even though its windows video file. orb can also stream over the internet (not only on LAN) in a flash enabled web browser. i have tried both through wine and crossover they dont work when i try to open them well tversity starts up but wont start sharing when you press the start sharing button. ive read in the tversity forum that they might come out with a linux version soon and also the admin said users reported that it worked under the vmware program. and also upnp is using computer ports to share the media such as xxx.xxx.x.xxx:8080 but most linux oses come with all ports closed for security reasons but u can edit this with fire starter. im gonna go try fuppes or w/e

---

### Post by boogieboarder97 on 2007-08-30
BTW from what ive heard micro$uck vista sends your info to the mpaa and other stuff like that so dont plan on using limewire or bittorrent i still dual boot to xp just for orb though

---

### Post by Nowlan1971 on 2007-10-08
I have been using WMC 2.0 (windows Media Connect) to stream music and video to XBMC. Very easy to set up on XP, so long as you don't have Media player 11 installed, MP 11 has it built in. 

I dual boot my Desktop with XP and Ubuntu, it would be nice to get it set up to stream Media to XBMC with Ubuntu rather than XP. 

I would like to go the route of uPnP rather than SMB. I have just set up ubuntu on my desktop, but have been using it since june on my Laptop. 

I will be trying some things in the next couple nights and report back.

---

### Post by aldenhg on 2007-10-09
It's not what you're looking for, but the 360 supports USB Mass Storage devices - even iPods! You could throw all your media on an external hard drive and rock out that way. Also, in the Marketplace there's a free download to support AAC audio, so that's awesome. I'd be really interested in getting the networked solution to work as well. I've got a P4 tower with a huge hard drive and tons of media just waiting to be streamed.

---

### Post by theonlyalterego on 2007-10-09
I've probably spent as much time, as seemingly many other have hunting for a solution to the linux -> xbox360 problem. So far I've run into the same walls as posted in this thread, but here's a new solution I just stumbled upon:

[http://forums.tversity.com/viewtopic.php?p=32586]("http://forums.tversity.com/viewtopic.php?p=32586&sid=b8dbc9d676b49f8099293a2503276832")

> I just tried to get TVersity going on VirtualBox with pretty decent success. I am running Ubuntu (64bit 7.10beta even) and was able to get VirtualBox configured to share audio, video, and network drivers. A bridged network has to be created to get the TVersity to share across the network, and the user manual for VirtualBox covers exactly what to do.

[...]

Now I'm kinda suck because the transcoding and streaming isn't fast enough for my xbox360. I haven't figured out if it's due to virtualization (doesn't seem to be that for sure since I can play back the video on the virtual machine fine through windows media player) or if there's some sort of network bandwidth issue inherent to this bridged configuration.

[...]

As long as you pause the video for a couple minutes at the beginning of playback, everything is fine. Seems like it works great as long as you can deal with not starting movies immediately.

I haven't yet tried this (still at work) but I'll be trying it within the next few days... let me know if anyone else has any success.

~ego

---

### Post by aldenhg on 2007-10-11
Tversity says it's just a UpNP server. Isn't there anything like that natively for linux? I mean, DD-WRT is linux and it does UpNP.

---

### Post by Octagonal on 2007-10-12
> **aldenhg said:**
> It's not what you're looking for, but the 360 supports USB Mass Storage devices - even iPods! You could throw all your media on an external hard drive and rock out that way. Also, in the Marketplace there's a free download to support AAC audio, so that's awesome. I'd be really interested in getting the networked solution to work as well. I've got a P4 tower with a huge hard drive and tons of media just waiting to be streamed.

Going from the guide posted here:
[http://linux.vanvalkinburgh.org/2007/05/25/stream-videos-to-xbox-360-with-patched-ushare/](http://linux.vanvalkinburgh.org/2007/05/25/stream-videos-to-xbox-360-with-patched-ushare/)

I was able to setup a share that is accessible from my 360 using Ubuntu Feisty.

I too was thinking USB mass storage devices would be a good idea but the 360 only recognizes FAT32 file systems which limit you to 4GB max. file size.  So if you want to watch any HD movies you're probably out of luck--so I looked for something else and found ushare--which seems to work great so far.  The 360 is supposed to support avi, wmv, and mpgs but I have only seen wmvs work so far... I'm assuming the problem is codec related.

---

### Post by Lonergan on 2007-10-22
I've been looking into this as well for my PS3.  In XP, I run TVersity and it has real-time transcoding which makes life REALLY nice since my server is in the basement and my PS3 on the main floor.  It is also nice to have access to all of my music on the main floor.  However, moving to linux, I'm stuck a bit because real-time transcoding is not yet available from any product I am aware of that works under linux.  

I currently use MediaTomb and it works like a charm (very little disconnecting, which if it does disconnect could be related to the wireless connection or something else) though it does not have transcoding of course.  I do know that Mediatomb devs are working hard on transcoding.  Since Mediatomb is used in some pretty major hardware from big names, I can see this transcoding becoming a reality very soon.

With Ubuntu selling on Dells quite well, I don't think it will be too long until someone releases something that has real-time transcoding but for now, the options are rebooting to Windows, Windows under VM or just forgetting about realtime transcoding.  SAMBA works to an extent but at least for the PS3, a real UPnP server is needed, like Mediatomb.

---

### Post by Octagonal on 2007-10-22
You may want to give fuppes a shot... that has some experimental transcoding.  I've not tried the transcoding but fuppes (once setup is complete--which is a pain) works like a charm.

---

### Post by cas118 on 2007-10-24
You probably want to check out [Mediatomb]("http://mediatomb.cc/").

It's open source, in active development, Jin the admin regularly contributes to the forum if people are stuck.

If you're not scared of a little compiling (there are instructions on the site), then you can try to use the latest features such as transcoding.

I have it running as a Daemon on my Feisty install. If I want to stream some music, I just stroll up to my PC - turn it on - and wander away. No muss, no fuss.

It's one of the few Linux uPNP servers that works with my Nokia 770, too!

---

### Post by ricadelic on 2007-11-04
I've got the same issue here to get an Archos 605 Wifi finding my tunes. 

i've found uShare & MediaTomb, and i'm gonna try em out both..

---

