---
title: "Portable Mp3 Players"
date: 2007-12-29
forum: General Help
---

### Post by CheeseQueen452 on 2007-12-29
I'm looking for a new mp3 player, since the one I have hasn't worked too well from the start. Can anyone recommend a good AAA powered 2 GB mp3 player under $50? Money is rather tight..... Also, If the player has an INTERNAL rechargable battery(charges via USB), does that mean I'd have to use the (window$)software to charge it?

---

### Post by CheeseQueen452 on 2007-12-29
Anyone?

---

### Post by CheeseQueen452 on 2007-12-29
*bump*

---

### Post by Southwind on 2007-12-29
I like the Sandisk Sansa mp3 player.  Mine is a little older and is only 512 meg, but will give be about 10-15 hours on AAA battery(claim is 15 hours).  I use rechargable batteries that I can put in a slow charger.  I like to listen to audio files such as podcasts or audio books.  I plug the Sansa in to USB port and transfer files like it was another drive or file folder.  Drag and drop. 


Larry
LInux user 197889
ubuntu user 18239

---

### Post by AndyCooll on 2007-12-29
[ Looking for an mp3 player that will 100% surely work with Ubuntu.]("http://ubuntuforums.org/showthread.php?t=165978&highlight=mp3+player")
[ What kind of portable audio player do you have? ]("http://ubuntuforums.org/showthread.php?t=622922&highlight=portable+player")

:cool:

---

### Post by CheeseQueen452 on 2007-12-29
Thanx for the input, guys.... I've been eyeing the Sansa M250, but there are some reviews that make me wonder if it's the right choice. I'll keep my eyes open.....

---

### Post by BlastOButter42 on 2007-12-29
Just plugging into a USB port should charge the player, no matter what OS the computer is running. You won't have to use any Windows software to charge it -- it should start as soon as you plug it in.

---

### Post by dixonstalbert on 2007-12-29
I have a Coby 2 gig player that cost about $40. 

Linux does not have reliable high speed USB support for all cheap USB hardware like these mp3 players and many will not work out of the box- but there is an easy workaround.

I have no problems with my old ipod and the Coby if I first temporarily removed high speed USB by typing sudo rmmod ehci_hcd then plugging it in and Ubuntu immediately mounts it and opens it  with nautilus file manager without a problem.
 I use Amarok, and you can set up the rmmod command, and the modprobe command (sudo modprobe -f ehci_hcd) as pre- and post-mount commands to disable and then restore high-speed USB support automatically.  Or, if you dont use any high speed devices like cameras or printers you can just set up a start up script that disables ehci_hcd

With Amarok, I found that if I mounted it as 'Generic Audio Player' as opposed to 'mtp player' it works without a problem.

The file transfers do take longer than under windows, but the sync option in Windows Media player hiccuped one time and I lost all my mp3s, but I have never had a problem with amarok

---

### Post by smartboyathome on 2007-12-29
I have an Insignia MP3 which I got for christmas and works great. I had to learn how to convert videos for it, but once that was done everything just worked (except playlists).

---

### Post by dixonstalbert on 2007-12-29
x

---

### Post by CheeseQueen452 on 2007-12-30
Thanx for the input. I have a $40 2 GB Coby as well, & as I stated in my original post, it doesn't work well. My computer almost never detects it, & even my mother's winxp system won't see it when I plug it in. One of the buttons on the player doesn't work well, either. For these reasons, I'm looking for another mp3 player. As for your suggestion of disabling the high speed usb, I do use a camera which works fine when I plug it in. So, I really don't want to disable the usb. I'm afraid of messing something up.... Anywho, thanx again for your input.

> **dixonstalbert said:**
> I have a Coby 2 gig player that cost about $40. 

Linux does not have reliable high speed USB support for all cheap USB hardware like these mp3 players and many will not work out of the box- but there is an easy workaround.

I have no problems with my old ipod and the Coby if I first temporarily removed high speed USB by typing sudo rmmod ehci_hcd then plugging it in and Ubuntu immediately mounts it and opens it  with nautilus file manager without a problem.
 I use Amarok, and you can set up the rmmod command, and the modprobe command (sudo modprobe -f ehci_hcd) as pre- and post-mount commands to disable and then restore high-speed USB support automatically.  Or, if you dont use any high speed devices like cameras or printers you can just set up a start up script that disables ehci_hcd

With Amarok, I found that if I mounted it as 'Generic Audio Player' as opposed to 'mtp player' it works without a problem.

The file transfers do take longer than under windows, but the sync option in Windows Media player hiccuped one time and I lost all my mp3s, but I have never had a problem with amarok

---

### Post by CheeseQueen452 on 2007-12-30
Thanx for letting me know, that opens up my options a bit.

> **BlastOButter42 said:**
> Just plugging into a USB port should charge the player, no matter what OS the computer is running. You won't have to use any Windows software to charge it -- it should start as soon as you plug it in.

---

### Post by CheeseQueen452 on 2008-01-05
Ok, I bought the 2 GB Sansa Clip. I plugged it into my computer, & it *appears* to be charging, but I'm not certain that's what it's doing. If anyone has experience with this model, can you please tell me EXACTLY what I should see on the display when it's charging, & how do I know when it's done charging?

---

### Post by Southwind on 2008-01-06
Hi, I have a Sandisk Sansa with 512Meg of memory.  I open the case in the back and there is a 'AAA' battery that I replace.  I can use a throwaway or a rechargable  that I recharge in a charger that I plug into the wall plug in. I don't know about the clie. but if it charges by the usb port, that would seem to me to be a change in Sandisk's policy.  My son has a sandisk 256 meg which also uses a 'AAA' battery. I hope this helps.
Larry

---

### Post by CheeseQueen452 on 2008-01-06
I initially wanted one that uses a AAA battery, but the reviews for the Sansa M250(the one I *was* considering) made that model sound a bit sketchy. So, I opted for the newer Sansa Clip. I wouldn't say that charging via usb is a change in Sandisk's policy. Most portable mp3 players now use a rechargable/replaceable lithium ion battery. The Sansa Clip has a built-in/NON-replaceable battery. Since rechargable batteries can last for years before needing a replacement, I'm not worried about it. Sure, a AAA battery is more convenient, but I'd rather have a more reliable mp3 player that won't break down within a few days or weeks, as some of the reviews for the M250 claim. And I didn't want to take that chance..... I did with a Coby C895, & I'm sorry I did. I hope my Sansa Clip doesn't disappoint me! It took roughly 3 1/2 hrs to charge last night, which isn't bad compared to others that take 6 hrs to charge. I put all of my mp3s on it... over 1 GB... which only took a few minutes. The Coby took more than twice as long.... I'll be playing around with my Sansa a bit today, & I'll see how it goes.

> **Southwind said:**
> Hi, I have a Sandisk Sansa with 512Meg of memory.  I open the case in the back and there is a 'AAA' battery that I replace.  I can use a throwaway or a rechargable  that I recharge in a charger that I plug into the wall plug in. I don't know about the clie. but if it charges by the usb port, that would seem to me to be a change in Sandisk's policy.  My son has a sandisk 256 meg which also uses a 'AAA' battery. I hope this helps.
Larry

---

### Post by sugarland2k on 2008-01-07
Use a music player that supports Open Source!  Ogg is better than MP3.
Check out [http://www.rockbox.org/](http://www.rockbox.org/)

I love my Sansa e240 running Rockbox!  

:)

---

### Post by CheeseQueen452 on 2008-01-07
How is ogg better than mp3? Just asking, as I'm not familiar with ogg....

I needed an affordable mp3 player, & I chose the Sansa Clip... under $50(ebay). I've had it for 2 days, & so far so good.... No major issues, as of yet. I'm keeping my fingers crossed....

I can't find any info on the e240.... interesting....

> **sugarland2k said:**
> Use a music player that supports Open Source!  Ogg is better than MP3.
Check out [http://www.rockbox.org/](http://www.rockbox.org/)

I love my Sansa e240 running Rockbox!  

:)

---

### Post by sub2007 on 2008-01-07
OGG Is an open source format whereas MP3 is proprietary. Given that we are all running an operating system that is founded on open source then ethically (I feel) we should try to use open source alternatives if possible. Every Linux distro can play OGG Vorbis out of the box whereas in order to play MP3 you have to install a restricted codec. You also have to install lame to create MP3 files whereas Linux can create OGGs out of the box.

On a more practical note, OGG has better compression than MP3 and so you can either rip your music at a better quality for the same file size (128kbps OGG should sound better than 128kbps MP3) or if you're happy with the quality of your MP3s then you can rip them at a lower bitrate so you would create a small OGG file without sacrificing quality.

On the other hand though:
1. it's a pain to re=rip your music if your whole music collection is already in MP3
2. not all portable devices can support OGG whereas every player under the sun (I'd assume) can play MP3 files.
3. on a Windows note, every media player can play MP3 files whereas not all players can play OGG files (I think WMP and Real Player don't). Therefore if you use Windows then you may find that your favourite player doesn't play OGG.
4. MP3 files are so abundant on the Internet that you may not be able to live without the MP3 codec anyway, which you may feel eliminates the need for re-ripping your collection into OGG.

So it's a trade off really, as with all things in Linux it's the freedom for you as the user to choose.

More info on OGG Vorbis: [http://www.vorbis.com/](http://www.vorbis.com/)

---

### Post by CheeseQueen452 on 2008-01-08
Thanx for the explanation. I've heard of the ogg format, I just never researched it. I do prefer mp3, as it is the most common (& popular) format. As for the codec, I don't recall having to install it the last time I set up a fresh copy of Ubuntu. I don't mind installing the codec if I have to. Not a big deal.... I don't remember window$ being pre-packaged with *every* codec or plugin we need, so there really isn't much difference. You still have to install real player for .rm files, quicktime for .qt files, etc.... If I'm not mistaken, Audacity now includes lame, so there's no need to install it seperately. I can record any sound coming through my speakers & save it as an mp3 without a hitch. The quality would make an audiophile cringe, but it's ok for me.....

> **sub2007 said:**
> OGG Is an open source format whereas MP3 is proprietary. Given that we are all running an operating system that is founded on open source then ethically (I feel) we should try to use open source alternatives if possible. Every Linux distro can play OGG Vorbis out of the box whereas in order to play MP3 you have to install a restricted codec. You also have to install lame to create MP3 files whereas Linux can create OGGs out of the box.

On a more practical note, OGG has better compression than MP3 and so you can either rip your music at a better quality for the same file size (128kbps OGG should sound better than 128kbps MP3) or if you're happy with the quality of your MP3s then you can rip them at a lower bitrate so you would create a small OGG file without sacrificing quality.

On the other hand though:
1. it's a pain to re=rip your music if your whole music collection is already in MP3
2. not all portable devices can support OGG whereas every player under the sun (I'd assume) can play MP3 files.
3. on a Windows note, every media player can play MP3 files whereas not all players can play OGG files (I think WMP and Real Player don't). Therefore if you use Windows then you may find that your favourite player doesn't play OGG.
4. MP3 files are so abundant on the Internet that you may not be able to live without the MP3 codec anyway, which you may feel eliminates the need for re-ripping your collection into OGG.

So it's a trade off really, as with all things in Linux it's the freedom for you as the user to choose.

More info on OGG Vorbis: [http://www.vorbis.com/](http://www.vorbis.com/)

---

