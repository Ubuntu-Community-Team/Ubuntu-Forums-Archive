---
title: "App for Streaming Torrents"
date: 2012-12-02
forum: General Help
---

### Post by prince2689 on 2012-12-02
Hi Guys,

I need an application that can stream/play videos from torrent files while downloading, something utorrent/Bittorrent does in windows. Tried many torrent clients for linux but didn't find this functionality.

Please help me.

---

### Post by mungatsuma on 2012-12-02
Well You can try Miro. The Linux version is a powerful torrent client, a media player as well as a converter. This is something that was not there in the windows version (last time I checked). Good thing is once installed it associates torrent link file options hence no extra tweaking.

If you miss Utorrent so much, it is installable in Ubuntu, just follow the tutorial at this link
[http://askubuntu.com/questions/104094/how-to-install-utorrent-step-by-step](http://askubuntu.com/questions/104094/how-to-install-utorrent-step-by-step)

---

### Post by Lars Noodén on 2012-12-02
Torrents won't work that way.  Pieces of the file are downloaded as they become available.  So it is entirely possible to download the end of the file long before the beginning gets downloaded.  You'll have to wait for the torrent to finnish to be sure to have the pieces in the right order.

---

### Post by prince2689 on 2012-12-02
@mungatsuma

I have tried miro. It plays videos only after the entire video is downloaded. That is not what I am looking for, I am searching for an app that streams/plays videos in torrent files while it is being downloaded.

The only reason to miss utorrent is that they have added this new functionality in their latest version. I have already tried 'utorrent server' as mentioned in your link but that does not add that functionality.

@Lars

Now a days torrents do work in this way. They can download the files sequentially so that streaming/playing videos while downloading is possible. Check the latest utorrent client for window, if you can. You will find the button stream which plays videos that are currently being downloaded. Check this link [http://torrentfreak.com/utorrent-adds-video-streaming-support-091217/](http://torrentfreak.com/utorrent-adds-video-streaming-support-091217/)

---

### Post by haqking on 2012-12-02
> **Lars Noodén said:**
> Torrents won't work that way.  Pieces of the file are downloaded as they become available.  So it is entirely possible to download the end of the file long before the beginning gets downloaded.  You'll have to wait for the torrent to finnish to be sure to have the pieces in the right order.

ktorrent, qbitorrent both allow previewing, I have been doing it for years.

I am sure most torrent applications allow it, I currently use KTorrent and it allow preview.

Peace

---

### Post by prince2689 on 2012-12-02
@haqking

I have tried previewing in qBittorrent, its not working for videos that are still downloading. Its works flawless only for videos that are 100% downloaded.

---

### Post by Lars Noodén on 2012-12-02
> **prince2689 said:**
> @Lars

Now a days torrents do work in this way. They can download the files sequentially so that streaming/playing videos while downloading is possible. Check the latest utorrent client for window, if you can. You will find the button stream which plays videos that are currently being downloaded. Check this link [http://torrentfreak.com/utorrent-adds-video-streaming-support-091217/](http://torrentfreak.com/utorrent-adds-video-streaming-support-091217/)

Cool.  I'll have to check to see how to do that with Transmission.

---

### Post by haqking on 2012-12-02
> **prince2689 said:**
> @haqking

I have tried previewing in qBittorrent, its not working for videos that are still downloading. Its works flawless only for videos that are 100% downloaded.

been a while since i used QBittorrent I use Ktorrent now, but to be honest I rarely need to preview anymore as im on Fibre and its downloaded before i settled down to preview ;-) I will double-check with Dexter and Boardwalk Empire later ;-)

---

### Post by prince2689 on 2012-12-02
@haqking

Not everyone is as lucky as you..... :( 
So help me to complete my hunt, so that i can feel better :)

---

### Post by prince2689 on 2012-12-03
I found a solution with the help of @HalationEffect

Solution:

Install Media Player plugin into Ktorrent. Start downloading the video file from torrent. Add that file to the playlist of the media player. This makes libktorrent to switch to sequential mode. Then after appropriate download usually 5-10% of the file, click play and enjoy the video while it is downloading !!!! :P:P:P:P

KTorrent is the best Torrent client......

Thanks All.

---

### Post by haqking on 2012-12-03
> **prince2689 said:**
> I found a solution with the help of @HalationEffect

Solution:

Install Media Player plugin into Ktorrent. Start downloading the video file from torrent. Add that file to the playlist of the media player. This makes libktorrent to switch to sequential mode. Then after appropriate download usually 5-10% of the file, click play and enjoy the video while it is downloading !!!! :P:P:P:P

KTorrent is the best Torrent client......

Thanks All.

Sorry I forgot to respond, yeah Ktorrent is great, i have never needed to do anything with Media player though, but yeah i knew it worked.

Peace

---

### Post by pranjalsagar5 on 2013-07-02
I am sure there are others ways of doing this but somehow only qBittorrent worked for me

choose download in sequential order & wait for few % of file to download and finally open media file normally

---

### Post by lodp2 on 2013-12-31
> **prince2689 said:**
> Then after appropriate download usually 5-10% of the file, click play and enjoy the video while it is downloading !!!! :P:P:P:P

And you don't even have to use KTorrent's own player - after playing it in the Media Player Plugin for a few seconds Ktorrent will continue sequentially downloading the file. You can stop playback in Ktorrent and view the file in VLC or something.

It's weird they don't just provide an option "sequentially download" in the context menu, instead of offering it only through the media player plugin. I suspect most people would prefer using their regular media player, particularly as the ktorrent media player is a bit buggy (crashed on me three times, controls wouldn't go away in fullscreen etc..)

---

