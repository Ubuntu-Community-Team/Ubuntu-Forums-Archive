---
title: "MythTV box in order to get rid of cable"
date: 2008-02-18
forum: General Help
---

### Post by bhougland on 2008-02-18
Hey guys-

   I think I have read everything about Home theater Pc's in the past couple days but still have a few questions.  The main thing I would like to do is build a mythtv box in order to get rid of cable.  The problem is I don't really know how to allow all tv's in the house to access the mythtv box.  Here is what I am trying to accomplish:

1.  Get rid of cable 

2.  Get all of the streaming TV shows, music, etc into one place so it is easy for my fiancee to work the HTPC.  This must be very easy or she will get frustrated.  Should I use Mythtv, Miro, or The Entertainer?

3.  Be able to watch local football.  Does this mean that I will have to get a MypcHDTV 3000 card and an antenna to watch free OTA hdtv?

4.  If I am using mythtv I want this on one of the sides of the cube in Beryl.  Basically, I still want the functionality of the computer but for my fiancee I want an easy to use GUI like mythtv, or the entertainer, so she doesn't get confused.  So, for her I want it to be plug and play.

5. Have the remote be my Wii remote.

6. *most important* I would like to build it for under $800, am I dreaming?  :lolflag:

7.  I would like the Mythbox to be wireless, for the wifi.


How would you build such a system?  

Thanks in advance!

---

### Post by fowie on 2008-02-19
I use MythTV, so that's what my comments will be referencing
> 1. Get rid of cable
What will you watch instead?  Guess that's answered below, but sure, that's easily possible without a mythtv box, just unplug the coax....
> 
2. Get all of the streaming TV shows, music, etc into one place so it is easy for my fiancee to work the HTPC. This must be very easy or she will get frustrated. Should I use Mythtv, Miro, or The Entertainer?

MythTV works very well with networking you media over multiple computes, but sometimes it takes a little elbow grease beforehand so it looks easy in the end product.  For instance, with MythTV, all of the DVR shows I've recorded from my cable were accessible as soon as the box in my front room was online.  For my movies (hosted on a removable USB drive in the back room computer) I had to use samba to share the USB drive, and then add the device into my front-room computer's fstab so it would mount it on boot.  All I had to do was mount it to /var/lib/mythtv/videos though and everything shows up.

> 
3. Be able to watch local football. Does this mean that I will have to get a MypcHDTV 3000 card and an antenna to watch free OTA hdtv?

Yeah, you'll need a tv card to capture any kind of TV signal.  If you need HD you'll need an HD card.  I'm using cable so I don't have experience with OTA hd, but I hear that's pretty easy too.  Just make sure the card is supported by MythTV before you buy it (you can find out on the mythtv website)

> 
4. If I am using mythtv I want this on one of the sides of the cube in Beryl. Basically, I still want the functionality of the computer but for my fiancee I want an easy to use GUI like mythtv, or the entertainer, so she doesn't get confused. So, for her I want it to be plug and play.

Inside mythtv's frontend you have the option of running it inside a window or running it full-screen.  I've never really seen that work very well but I only tried it once and very briefly.

> 
5. Have the remote be my Wii remote.

Hmm, I have a Wii but never thought about using it for the remote, I wanted more buttons., but [this]("http://www.mythtv.org/wiki/index.php/Controlling_MythTV_using_a_Wii_remote") seems to be a pretty good resource for that

> 
6. *most important* I would like to build it for under $800, am I dreaming?

Depends what you want it to do.  If you want a super-nice HTPC, good luck.  I was able to just but a capture card for my desktop computer in the back room for $40, and then get a MCE remote for $30 and built an old computer out of free parts (1GHz AMD with a 64MB NVidia graphics card and a 802.11g wifi adapter) and used that as the media center that I hooked up to the TV.

```

7. I would like the Mythbox to be wireless, for the wifi.

```
Sure, I'm doing it.  Don't expect to stream HDTV over it though.  Heck, even SD gets choppy if someone else is using the wireless at the same time, so you'll need a totally independent router if you're doing more than just watching TV.  Otherwise it seems to work great as long as the signal is strong.

MythTV rocks, you'll love it.

---

