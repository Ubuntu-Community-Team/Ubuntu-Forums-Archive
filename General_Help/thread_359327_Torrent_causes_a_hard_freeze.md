---
title: "Torrent causes a hard freeze?"
date: 2007-02-11
forum: General Help
---

### Post by grsing on 2007-02-11
It appears that, when downloading a torrent (so far I've only tested using Bittornado, I'll try another program and see if I can reproduce it that way as well), after a period of time (doesn't appear to be a set period, but isn't particularly long, sometimes less than a minute, sometimes 5 minutes), my system goes into a hard freeze. By hard freeze, I mean that everything on screen stops, and if there is a sound playing, it continuously loops about half or a quarter second of it, and the only way to recover is via the power button; ctrl-alt-bksp and everything less does nothing. Does anyone know what could cause this, and/or how I could fix it? If you need the contents of any files or logs, just let me know which. Thanks!

Edit: as a small background, I was having a problem, which I believe was also linked to torrents, where my wireless internet connection would randomly drop, and I would have to restart to resolve it. That doesn't happen anymore, just the crashes. And, neither case occurs in Windows, also using bittornado, if that's useful in debugging it. Thanks again.

---

### Post by grsing on 2007-02-11
Nope, using the bittorrent program that comes with Ubuntu resulted in the same hard freeze (though it seemed to take longer). Any ideas?

---

### Post by Sklasko on 2007-02-11
Perhaps try using [uTorrent]("http://www.utorrent.com/") with WINE?

---

### Post by grsing on 2007-02-11
Running it now; I'll let you know what happens.

---

### Post by grsing on 2007-02-11
So far so good; I'll leave it running overnight, and if it hasn't frozen in the morning, I'll suppose that it's fixed. Thanks a bunch; so far, I actually like uTorrent better anyway, and this keeps me from having to use Windows to download torrents, which was terrible.

---

### Post by grsing on 2007-02-12
Well, no crashes, but it's running extremely slowly (mostly less than 1 kb/s). That's a different problem, though, so I'll start a new thread/look elsewhere. Thanks again.

---

### Post by pedwards on 2007-11-20
I can confirm:   
  
my system wil freeze with "bit torrent" and deluge,  im having problems with the repo'd version of azureus, so i cant comment on that.  I think the problem is a gusty bug that freezes on spikes in the network.  Can anybody point me in the direction of a solutin?

---

### Post by ipyrat on 2008-01-24
I have the same problem on ALL torrent clients including wine\utorrent.I have an amd64 processor,2gigs ram,and a 256 radeon graphics card.Starts downloading and freezes the entire system only holding power will stop it.

---

### Post by jimbojones on 2008-01-24
> **ipyrat said:**
> I have the same problem on ALL torrent clients including wine\utorrent.I have an amd64 processor,2gigs ram,and a 256 radeon graphics card.Starts downloading and freezes the entire system only holding power will stop it.

DItto:(

---

### Post by Lord Illidan on 2008-01-25
Are you all using wireless?

And as for deluge, are you using the latest version from the website or the one in synaptic?

---

### Post by hal10000 on 2008-01-26
I had the same problem for months using Azureus and Ktorrent on my gutsy-system. First I thought it was a problem with azureus or java, but changing versions did not take any effect. When trying Ktorrent I realized it was not a problem with azureus or java, so I thought it must have something to do with bittorrent itself.
But after reading posts on different forums I thought it might be a problem with the network or something similar.

I remember that I didn't have this problem on my old system, where Iwas using th old orinoco wlan-driver for my card (Netgear MA-311), so I changed my wlan driver from hostap back to the older orinoco driver and everything works perfect now.

That's a really strange behaviour, but I hope it might you help in case you have a wlan-card similar to mine.

---

### Post by sir_blargh on 2008-01-27
Similar problem here, but I cannot confirm that it's torrents that cause the hard freeze problem.  In the past two days, I've had the machine lock up hard three times.  Mouse froze, sound looped, cntrl-alt-backspace / switching to other terminals didn't work.  The machine wouldn't respond to ping, either.

In all three cases, I had deluge running and maxed out at 450 connections.  In one case, I had mplayer playing a video and was using HandBrakeCLI to try to rip a protected DVD (it failed -- and the machine froze).  In the other two cases, Deluge was again at 450 connections @ ~ 300kB/s download but I launched Amarok (music player) and it froze up after ~ 2 minutes of playing.

Unfortunately there's nothing in the log files -- what can I do to help pinpoint the problem?

**EDIT**  Forgot to add -- I'm *NOT* using wireless.

Thanks!

---

### Post by Redls1bird on 2008-05-01
I have the same problems with torrents.  The weird thing is deluge worked for me for about a day, really well!  Then it just quit.  Since then, ive never had it working again, not even with a reformat and fresh 7.10 install.  It doesnt matter what program i use, deluge, bit tornado, frost wire, bittorrent, whatever.

---

### Post by dbarbour on 2008-07-17
It sounds to me like an issue with wireless networking and Hardy. I recently changed from a wired connection to a wireless connection and that's when the issues started. I'm going to test on a wired connection here in a minute and will post results.

---

### Post by dbarbour on 2008-07-17
Swapped over to a wired connection and have been running Transmission for a while now. Would have hung on the wifi connection. Interesting...

---

### Post by dbarbour on 2008-07-17
> **dbarbour said:**
> Swapped over to a wired connection and have been running Transmission for a while now. Would have hung on the wifi connection. Interesting...

Meh... No dice. It actually lasted considerably longer, but still froze up. I'm going to run memtest86 tonight and see if I'm using some bad memory or something, so we'll see how that goes.

---

