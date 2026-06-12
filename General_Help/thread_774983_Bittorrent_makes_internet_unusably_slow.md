---
title: "Bittorrent makes internet unusably slow"
date: 2008-04-29
forum: General Help
---

### Post by MangasColoradas on 2008-04-29
I am using Deluge and Hardy and I am finding that even if I am uploading/downloading at like 5kbs it is as though I am taking up my whole bandwidth.

Using Windows I can download at 450kbs and upload at 25kbs and internet speed is unaffected. 

I have checked the bandwidth settings in Deluge and even lowered a lot of the settings compared to what I would normally use and its still the same...using bittorrent makes the internet unusable!

I disabled UWF but that makes no difference.

---

### Post by MangasColoradas on 2008-04-30
It seems OK now, I have no idea why. Oh well.

---

### Post by Virtual_Ron on 2008-04-30
when this happens to me, its usually because I have my upload cap set too high.   From what I understand, setting it at around 75% or so of your upload max is a good number.   I have 768 up, and set my upload cap at 65.

---

### Post by bingoUV on 2008-04-30
It seems like deluge takes its name quite seriously. Try transmission for some time. When I did so, internet slowing for other browsing was much less affected than with deluge. YMMV.

---

### Post by danwood76 on 2008-04-30
Basically if you set the upload too high there is no head room for your internet requests to go out through and you end up not being able to use the internet.
If you share your internet in your house your better off setting your upload cap around 50% as other people may want to upload aswell.

---

### Post by Virtual_Ron on 2008-04-30
> **bingoUV said:**
> It seems like deluge takes its name quite seriously. Try transmission for some time. When I did so, internet slowing for other browsing was much less affected than with deluge. YMMV.

I had some problems with deluge as well... until i compiled from source.  Now its my absolute favorite torrent client.

---

### Post by tamoneya on 2008-04-30
I used to have a similar problem and you may want to take a look at your router.  Linksys routers do not handle the torrent protocol very well since it involves many simultaneous connections and the firmware that they ship with is susceptible to crashing when you have so many open connections.  if this is the case and you do have a linksys router you can fix it like i did by installing dd-wrt as the firmware.
[http://www.dd-wrt.com/dd-wrtv3/index.php](http://www.dd-wrt.com/dd-wrtv3/index.php)

---

### Post by trippinnik on 2008-04-30
How many connections do you have it set to? Having too large a number of outgoing and incoming connection regardless of upload/download setting can also really put a hurting on internet speeds.  Also ISPs (especially universities) will throttle you if you have to many connections because it looks like a virus infected pc or some other problem.

---

### Post by MangasColoradas on 2008-04-30
> **Virtual_Ron said:**
> when this happens to me, its usually because I have my upload cap set too high.   From what I understand, setting it at around 75% or so of your upload max is a good number.   I have 768 up, and set my upload cap at 65.

I know that, I have it set at around 75% myself.

As I stated the problem does not happen under Windows  only under Ubuntu and Deluge. 
My settings for Bittorent were the same under Windows as Ubuntu, same connections, same upload rate etc.

I lowered all the settings from the my usual Windows settings, connections etc and it was still bad...however after rebooting modem, router and computer bittorrent seems fine. :)

tamoneya-I was thinking of doing that. :)

Maybe the problem does not occur under Windows because Windows limits the number of open connections you can have and Linux doesnt?

The main thing is, it is fine now, phew! :)

---

### Post by MangasColoradas on 2008-04-30
> **bingoUV said:**
> It seems like deluge takes its name quite seriously. Try transmission for some time. When I did so, internet slowing for other browsing was much less affected than with deluge. YMMV.

Transmission kills my router, lol.

Its definitely a router/connections thing.

---

### Post by tamoneya on 2008-04-30
even if you arent having connection issues with your router you should still consider using dd wrt because it is a much more powerful interface.  I dont have any numbers on my router speed but it seems to run a lot better and I was actually able to boost the wireless range because you cane "overclock" the router.  I boosted the power to my antenna.

---

### Post by MangasColoradas on 2008-04-30
Yea tam, I have a WRT54GS and I read that the firmware you mentioned is really good. 

I will be doing that. :)

---

### Post by bingoUV on 2008-04-30
> **danwood76 said:**
> Basically if you set the upload too high there is no head room for your internet requests to go out through and you end up not being able to use the internet.
If you share your internet in your house your better off setting your upload cap around 50% as other people may want to upload aswell.

But I lose out on my full upload potential even when I do not need to upload anything. For general browsing, a small packet uploaded for every page you visit should be enough. But it should be uploaded urgently so that download from the server starts quickly. If I am reading a page for 3 minutes, torrent should use my full upload potential for those 3 minutes rather than 50% or 75%. 

So any bittorrent client that requires you to limit upload rate is over aggressive. Unless bittorrent is very urgent.

---

### Post by tamoneya on 2008-04-30
> **MangasColoradas said:**
> Yea tam, I have a WRT54GS and I read that the firmware you mentioned is really good. 

I will be doing that. :)

Lucky you .  I have the WRT54G v 6.  They cut the memory in half when they made it more efficient and their isnt quiet enough space to run the full version of dd wrt.  Instead I have to run what is called the micro version. :(

---

### Post by danwood76 on 2008-04-30
> **bingoUV said:**
> 
So any bittorrent client that requires you to limit upload rate is over aggressive. Unless bittorrent is very urgent.

The issue you have is that each program doesnt talk to others using the internet, thats just not how they work.

Some routers have whats called Qos (Quality of Service) which performs what you describe.
It basically traffic shapes, gives priority to HTTP, or whatever you set it to and shapes all others whilst there are http packets waiting.

DD-WRT does have this function I think, its been a while since I used my linksys.
The buffalo I have is far far more stable.

---

### Post by MangasColoradas on 2008-04-30
> **tamoneya said:**
> Lucky you .  I have the WRT54G v 6.  They cut the memory in half when they made it more efficient and their isnt quiet enough space to run the full version of dd wrt.  Instead I have to run what is called the micro version. :(

I have the GS v6 which also has only 2mb so I need the micro too.

I have looked at their site and cant work out which to download though.

edit
found it, its dd-wrt.v23 sp1 micro

---

### Post by bingoUV on 2008-04-30
> 
The issue you have is that each program doesnt talk to others using the internet, thats just not how they work.

Sentence too complicated and has too many meanings for me to understand.
1. You mean "xterm does not talk to emacs using the internet" is my issue? These are just two programs taken to illustrate my confusion.
2. By "each program", do you mean bittorrent clients and by "others" you mean browsers?
3. Of course it does not work like that. Why would two programs running on the same computer talk to each other using the internet? You saying something else?

Sorry, the sentence just bamboozled me.

[B]Router
[/B]We should buy routers rather than change our bittorrent clients from deluge to transmission?

---

### Post by Bloemetjesgordijn on 2008-11-23
I currently have the same problem (with 8.10). Transmission slows my web browsing very much. (Never had this problem when I had Hardy)

As soon as I kill Transmission it is faster, but not as fast as it should be

If I look at my ethernetconnection when I am browsing, it is most of the time idle

As this thread is old, did you solve it??

Cheerz

Bloemetjesgordijn

---

### Post by detroit/zero on 2008-11-23
By installing new firmware in your router, you're swatting flies with a sledgehammer.

I don't know about transmission; I've never used it. In Deluge, though, aside from setting your bandwidth caps at a reasonable percentage of your highest speeds, you should also limit the number of connections that Deluge is allowed to establish. By a whole lot..

The default settings for my crappy Telecom Polska ADSL (with a crappy TP wireless router) line gave 256 connections, with 64 half-open connections. Using those settings, it would make using the rest of the internet all but impossible, much like you say, but it would only take a matter of minutes before TP would cut my service, probably figuring me for an infected PC like someone else noted.

Through trial and error, I found that a maximum of 88 established connections and 8 half-open connections works without killing my service. Just as important is the Connection Attempts Per Second setting. I have mine set to 10, again, through trial and error. Yours may be different.

You shouldn't have to change the firmware for your router. I have the same WRT54G that you have, and when I used it with the cable connection I had at my old apartment, it worked fine with the default bandwidth settings in Deluge. I could even jack it up a little bit..

Note: None of this takes into account bandwidth throttling by your ISP. Make sure you use encryption and port forwarding to limit your visibility.

---

### Post by gregology on 2010-05-01
Transmission's default is set to 260 peers, I cut that back to 50 and my torrent speed has actually increased. Maybe just coincidence but internet browsing had speed up :guitar:

---

