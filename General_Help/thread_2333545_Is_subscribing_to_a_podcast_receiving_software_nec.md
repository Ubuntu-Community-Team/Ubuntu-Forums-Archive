---
title: "Is subscribing to a podcast receiving software necessary?"
date: 2016-08-11
forum: General Help
---

### Post by AbleTassie on 2016-08-11
Is there a safe subscription podcast receiver software for Lubuntu? 

I am using Lubuntu 14.04 LTS. I have downloaded and manipulated various MP3 files for a while. For example, I have copied MP3 files from audio CDs and split them, etc. Then played them on my PC or burned a new audio CD. 

But particular websites seem to require a subscription to a "podcast receiver" software. Do I need to subscribe to such a podcast receiving software?  See, for example, 
[http://books.mcgraw-hill.com/podcast/acm/](http://books.mcgraw-hill.com/podcast/acm/)   or    [http://www.cmecorner.com/podcasthelp.asp](http://www.cmecorner.com/podcasthelp.asp)

 One such advertised podcast software is "Juice," see [http://juicereceiver.sourceforge.net/index.php](http://juicereceiver.sourceforge.net/index.php) 

Another one is itunes, see [http://www.apple.com/itunes/download/](http://www.apple.com/itunes/download/)[URL="http://www.apple.com/itunes/download/"]
[/URL]

Does it really have to be so complicated? I want to be able to just get whatever content is available and download it as MP3 files (or maybe wav files) and burn audio CDs or play it on an MP3 player.

Does anybody have any comments?

Thanks,

A.[URL="http://www.apple.com/itunes/download/"]



[/URL]

---

### Post by CantankRus on 2016-08-11
In some cases you can find an actual page where you can download mp3s.
From one of your links you can go to this page to download an mp3.... [http://books.mcgraw-hill.com/podcast/](http://books.mcgraw-hill.com/podcast/)

It's better to use a podcast client though, as you can see what you have played and what's new and easily update and transfer to an mp3 player.

You can install gpodder to do this.
```
sudo apt install gpodder
```

Eg I added the podcast link from one of your page links to gpodder.
[ATTACH=CONFIG]270654[/ATTACH]

---

### Post by AbleTassie on 2016-08-11
Thanks CantankRuss, 

I got Gpodder working and have subscribed to a couple of sites and downloaded MP3 files. I guess each of these files is a "podcast." In looking at the Gpodder manual it is clear that I can play each podcast on my PC using, for example, VLC media player. And it appears I can use (or "sync") to an external MP3 player. 
But I am wondering:

QUESTION: Can I burn individual podcasts (MP3 files) to a CD so that I can play on a CD player?

Thanks,

A.

---

### Post by howefield on 2016-08-11
> **AbleTassie said:**
> QUESTION: Can I burn individual podcasts (MP3 files) to a CD so that I can play on a CD player?.

Yes, by default the downloaded podcasts will be downloaded to...

```
~/gPodder/Downloads/name_of_feed/file_name.mp3
```

I believe xfburn is included in a default Lubuntu installation and will burn an audio cd from mp3 files.

---

### Post by AbleTassie on 2016-08-11
Thanks Howefield. I actually have Brasero too for burning CDs. In addition, I can split large MP3 files using MP3splt-gtk audio splitter before burning. This allows me to stop a CD during listening on a CD player and then leter find my way back to the approximate area of the CD that I stopped at. 

Unless anybody had any more comments (which would be appreciated) I will mark this thread as SOLVED.

Thank you again, CantankRus and Howefield

A.

---

### Post by howefield on 2016-08-12
> **AbleTassie said:**
> Thanks Howefield. I actually have Brasero too for burning CDs.

Cool, sounds like you know what you are doing and are good to go :)

> In addition, I can split large MP3 files using MP3splt-gtk audio splitter before burning. This allows me to stop a CD during listening on a CD player and then leter find my way back to the approximate area of the CD that I stopped at. 

Just one thought, K3B (default Kubuntu optical media burning application) allows for tracks to be split prior to burning. Whilst I wouldn't necessarily suggest installing K3B in a Lubuntu installation due to it's size and Kde dependencies, perhaps Brasero has the same option ?

---

### Post by AbleTassie on 2016-08-13
Howefield,

I have been burning CDs using Brasero after having split a large MP3 file into shorter MP3s lasting 3 minutes each (using for MP3splt-gtk audio splitter) for a couple of years without problems. I do this because if I stop the CD midway, I can go back to the place I stopped and finish listening. The most I will repeat is 3 minutes. 

I have continued using Brasero in this manner recently and it has worked, but recently Brasero has "hung up" a couple of times and has not finished with the burn. So I have switched to Xfburn and Xfburn seems to work fine at burning CDs with split MP3 files.

If anybody has any more comments I will be glad to accept them, but will likely mark this post as SOLVED soon.

Thanks again,

A.

---

### Post by howefield on 2016-08-14
> **AbleTassie said:**
> I have been burning CDs using Brasero after having split a large MP3 file into shorter MP3s lasting 3 minutes each (using for MP3splt-gtk audio splitter) for a couple of years without problems. I do this because if I stop the CD midway, I can go back to the place I stopped and finish listening. The most I will repeat is 3 minutes. 

I have continued using Brasero in this manner recently and it has worked, but recently Brasero has "hung up" a couple of times and has not finished with the burn. So I have switched to Xfburn and Xfburn seems to work fine at burning CDs with split MP3 files.

+1 for xfburn.

Just to add that if you find yourself back with Brasero, it can also split tracks, only mention it as it might quicken the task by using the one application rather than two. You have your workflow so it may not be for you, but just mention it for other casual readers.

---

### Post by AbleTassie on 2016-08-17
Thanks Howfield,

I will mark this thread as SOLVED.

A.

---

