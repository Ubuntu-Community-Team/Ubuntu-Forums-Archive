---
title: "New Ubuntu &amp; have only two problems"
date: 2008-02-19
forum: General Help
---

### Post by Alien18 on 2008-02-19
Hi All,

This is my first post here so go easy on me :)

While I consider myself a bit of a techy, I was a Linux virgin until recently, I now have Vista and Ubuntu 7.10 dual booting off two separate HDDs.

There are only a two main problems and one minor one:

1) The keyboard responsiveness is extremely slow! It takes forever to type anything!It was like this on the first boot, the 2nd boot it worked fine, but every boot up since then it has been the same, SLOW!  I've googled as best I can and only seem to find that people are suggesting it a problem with "Slow Keys" in the Accessibility menu, but all those features are disabled. So it shouldn't be anything like that.  If anyone has any idea's I'd be very grateful.

2) The internet is slow on Ubuntu, in Vista I regularly max my connection at 480kbps, but I'm getting anywhere between 50-70kbps in Ubuntu, I've even tried DownThemAll, the accelerator for firefox, but that still only manages the same max speeds.  I've googled this as well and many suggestions are to disable ipv6, which I have done, but it made no difference.  It might be worth noting at this point that I have not manually set any network/internet settings, it simply worked out of the box!

3) I'm classing this as minor because I'd rather sort out the above problems first.  It seems to sometimes (not every time but most times) take significantly longer to boot Ubunutu than others.  Like quite a few mins - I normally watch TV for a few mins or do something else around the house.

There we are, the only problems I've had since getting Ubuntu install and booting on my PC.

If anyone would be kind enough to help me, it'd be very much appreciated.

Alien18

---

### Post by TenPlus1 on 2008-02-19
it would help if we knew the specs of your computer (memory, hard-drive, processor speed, graphics card)...

As for downloading, are you downloading from the browser only or are you nabbing a few torrents to test speed ?  I generally download the Ubuntu Iso as a torrent file to check bandwidth on my system...

---

### Post by Alien18 on 2008-02-19
Oh I probably should mention that everything else runs perfectly smoothly and it is only the keyboard typing that is very slow.  And should also mention that not only does it take a few secs to recognise the key press if I type too fast it actually misses the key presses too - it'd doesn't remember them, which I find odd.

---

### Post by Alien18 on 2008-02-19
Sorry I missed your reply then!

Off the top of my head: 
Intel Core 2 Duo
nVidia 7950GT (*stresses* I THINK!)
1Gb RAM (2*512Mb)
It's on an ~8Gb partition of the 2nd HDD 

I've downloaded using Firefox and Synaptic and when using the Terminal.

Just to briefly explain the small HDD partition it is installed on.  I'm using my current PC to learn the Linux basics and see if I can use it to stream/transcode videos (be they downloaded or ripped from my DVDs) to my PS3.  Eventually I plan to build a media server, with all my Photos, Music and Videos on it.

At first it'll be used to store files to be accessed by a laptop wirelssly and a desktop, and as I said, to stream to a PS3.  I'd also eventually like to set up a webserver making my Photos (at minimum) and hopefully my music available to me anywhere I can access the internet (e.g. friends PC, my phone, etc).

I'd start with a 500Gb HDD then hopefully expand that as required.  Not sure what I'd do about backups yet - might invest in a 500Gb external to backup at least my photos.

Anyway I ramble off topic. I hope this info helps.

---

### Post by Alien18 on 2008-02-20
Hi,

I thought I'd try another USB keyboard last night and lo-and-behold it works fine.  The USB keyboard that I normally use is a MS ergonomic natural 4000 (or something to that effect).  I found an old (very dusty!) USB keyboard under my bed! Is there a way I can get my MS keyboard playing nicely?

I also had another look into the slow internet issue, and while downloading a program/update (can't remember which) through Synaptic it only had two files to download both from different servers, the first file downloaded at my full speed of ~480kbps the second managed ~200kbps.

I did a little digging and changed a firefox setting to disable ipv6 in firefox, but it still didn't help - even when using DownThemAll!

So I tried Opera and that didn't work either! Browsing seems fine (because the ~70kbps I seem to average is fast enough for browsing) but downloading is an issue! I tried Axel (a download accelerator) but I'd like to something a bit more integrated into a browser and with a gui.

Does anyone have any advice with regards to the slow internet connection?

Many thanks in advance.

---

### Post by Alien18 on 2008-02-21
Hi,

Just thought I'd let you know that my internet is now much faster - left my PC installing 165 updates last night - lol.  Didn't realise they were there to download previously. and now using DownThemAll I seem to be getting better results.

Still not hte consistent ~480kbps that I get in Vista but is going up and down between ~300kbps and ~470kbps.  I can only hope that I don't have any probs when I build my media server, since it will be a new build and completely fresh install.

The only two things that remain are the fact my MS keyboard doesn't work properly and the slow boot up.  But I can live with both of them for the moment since I'm only using this dual boot option to "learn" the basics of Ubuntu.

Many thanks,
Alien18

---

### Post by hotmonkeyluv on 2008-02-21
The slow boot could be due to a fsck check every time it boots up. If you boot in verbose mode it might show what is taking forever. Also, if you have lots of server packages (like my ubuntu server) it takes forever to initialize/startup some of them. Try doing a verbose boot and looking at which ones take the longest and disabling/uninstalling them.

---

### Post by Alien18 on 2008-02-21
Thanks, I'll have a look into this verbose boot thing.

Shortly after my previous post I realised that the reason my internet connection was quicker but not solid is because DownThemAll was only creating one connection for the download (even though it's set to 5!).  I use DownThemAll in Vista and it works perfectly. Does anyone have any suggestions please?

Many thanks
Alien18

---

### Post by patrickfromspain on 2008-02-21
as for the keyboard problem.. could you try to plug it into the ps/2 keyboard connector? There are usb to ps/2 adapters, shouldn't be expensive (when I worked in a pc shop, we'd give them for free usually)

---

### Post by Alien18 on 2008-02-21
> **patrickfromspain said:**
> as for the keyboard problem.. could you try to plug it into the ps/2 keyboard connector? There are usb to ps/2 adapters, shouldn't be expensive (when I worked in a pc shop, we'd give them for free usually)

Never thought of that - i've got a couple of them lying around somewhere - thanks I'll give it a try.

---

### Post by Alien18 on 2008-02-21
Hi,

I don't suppose anyone has any ideas as to why DownThemAll would only be using 1 connection do they?

Alien18

---

### Post by MCrittenden on 2008-02-21
One VERY common reason for slow boot times in Gutsy (7.10) is that the usplash has the wrong screen resolution, causing it to freak out for a couple minutes and finally give up and move on.

Open a terminal, type:

sudo gedit /etc/usplash.conf

and change the values to your screen resolution, save and exit. Reboot.  That took my boot time from 3min to about 40sec. Hope that helps.

---

### Post by Alien18 on 2008-02-27
Hi All,

I have another problem now - quite an annoying one.  When I put a DVD Video in my DVD drive Ubuntu will work for a while, but then freeze (normally within a minute of inserting the disc).  It's a complete freeze, no Caps Lock light, Ctrl-Alt-Del doesn't work I have to press the reset button to get back to normality.  Any ideas?

If this is a common problem that has an easy fix then great, if not I hope it doesn't happen when I build my media server, because I'll be wanting to rip all my DVDs to it!

Many thanks,
Alien18

---

### Post by Alien18 on 2008-02-27
> **MCrittenden said:**
> One VERY common reason for slow boot times in Gutsy (7.10) is that the usplash has the wrong screen resolution, causing it to freak out for a couple minutes and finally give up and move on.

Open a terminal, type:

sudo gedit /etc/usplash.conf

and change the values to your screen resolution, save and exit. Reboot.  That took my boot time from 3min to about 40sec. Hope that helps.

Sorry I hadn't noticed this reply when I made my previous post.  I shall try that, but I recently installed bootchart and it seems that something called "modprobe" is taking the most time.  Is that related to your solution in any way?

Thanks,
Alien18

---

### Post by Alien18 on 2008-02-29
Hi All,

It's been a busy week and I haven't got to play with Ubuntu much, but I was wondering if anyone had any possible guesses with regards to the DVD/freezing issue?  It's really annoying! lol.

many thanks,
Alien18

---

### Post by Snyper64 on 2008-03-11
If you are using a sata dvd drive, that may be your problem with Ubuntu freezing. Last I heard Ubuntu was still a little testy with sata dvd drives and there were freezing and install problems.

---

### Post by RobJN on 2008-07-04
I'm also having the same problems with my keyboard.

If I type too fast ubuntu misses some of my key presses.  This includes both the space bar and backspace which makes things extremely annoying.  I have had to boot into Windows to write this message as I was getting nowhere in ubuntu.

Furthermore this has only started occurring after a few boot ups. not straight away. could it be one of the updates i added?? 

Did anyone come up with a fix as I would love to switch to ubuntu completely but with simple things like the keyboard not working there is no of that. :(

I have a laptop so really need to get it to work with this keyboard.  

Thanks in advance

---

