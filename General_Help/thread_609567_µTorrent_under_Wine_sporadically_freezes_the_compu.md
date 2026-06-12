---
title: "µTorrent under Wine sporadically freezes the computer during fast download speeds"
date: 2007-11-11
forum: General Help
---

### Post by Meroigo on 2007-11-11
I don't want to use any other torrent client than µTorrent under Wine since many private trackers I'm on only allow µTorrent or Azureus, and Azureus uses to much CPU and RAM for my computer. So no need for you to tell me to use another client, thank you.

Before I upgraded to 7.10, when I had 7.04, I didn't have the following problem. I haven't changed my Wine or µTorrent configuration at all since 7.04, and Wine haven't had any updates since it worked like it should. I believe there's something stupid in 7.10 causing the problem.

I THINK this only happens when I save files over the network, using this computer to download it, but the download destination folder is located on another computer. I do this because the computer I use doesn't have very much free disk space.

When downloading fast in µTorrent under Wine, like 2-4 MB/s, the whole computer freezes for a couple of seconds, then it starts to work again as if nothing happened. It does this a couple of times during the download until it's 100% downloaded. I don't get any error messages in the terminal if i run it through there. Each time it freezes, there's data loss, so I have to do "force re-check" on a torrent when it says 100% is complete, and it changes to like 98,5% or something around that. Really annoying, takes alot of extra time. Anyone know what the problem could be?

---

### Post by yopnono on 2007-11-11
I know you like to use utorrent, but.. have you tried deluge?
[http://deluge-torrent.org](http://deluge-torrent.org) or you may hae it the synaptic repo.
or det it from getdeb

---

### Post by Meroigo on 2007-11-11
Deluge is not allowed on some of the private trackers I use so I cannot use it... I really hope someone knows what I can do so my µTorrent will work like before.

---

### Post by Meroigo on 2007-11-12
Woho! I THINK the problem was solved when wine got updated today. I could download 2,3 GB in constant 4-5 MB/s and the computer didn't freeze. Well, yes, some seconds around 90%, but when I rechecked it, it was still 100%, so there were no data loss during the freeze. =) Before, it used to freeze often when only downloading about 300 MB in 2 MB/s... Well, I HOPE I won't experience more of the problem. :]

---

### Post by weblordpepe on 2007-11-12
I am puzzled. I have been running uTorrent in Wine for like a zillion years. And it has always performed extremely well - far better than any native linux bittorrent client I've installed.

You mentioned that you were saving a file over the network. What speed is your network connection? Also, what method are you using to save the file over the network?

It might be a bad idea to download a file using bittorrent on one machine and network save it to another. That will increase the bandwidth/cpu usage a whole lot I amagine.

---

### Post by Meroigo on 2007-11-12
> **weblordpepe said:**
> What speed is your network connection? Also, what method are you using to save the file over the network?

It might be a bad idea to download a file using bittorrent on one machine and network save it to another. That will increase the bandwidth/cpu usage a whole lot I amagine.

My WAN speed is theoretically 100/100 Mbps and so is my LAN, but it never comes up in those speeds of course, it downloads/uploads at a maximum around 5 MB/s (which I think may be my budget router's fault, I don't think it's fit for 100 Mbps WAN).

When I choose were to save my stuff, I simply choose a folder in my file system where I have mounted a network share. I think I experience better performance this way, strangely enough, because it writes the data to the other computer directly, the hard drive in this computer isn't working as much. :)

And with a 100/100 Mbps connection, I wouldn't notice very much if something was using up my bandwith alot. Oh, right, yes, I notice. The computer works alot when I download in a couple of megabytes per second, but because of that, the downloads finish fast and the computer becomes "calm" again, so I can live with it. :P

As I said before, I think the problem was solved with the lastest Wine version. I downloaded alot today and never did any data get lost (it used to before, every time I was downloading fast). =) But there were still some sporadical freezes. Oh well, the important thing is that no data was lost.

---

### Post by weblordpepe on 2007-11-12
Well your network connection is 100Mbits.
You say you are downloading at 5 megabytes/second?

5 * 8 = 40. Twice that is 80. So you're using 80mbits/second to save the file. Ethernet is typically full-douplex, but if its not and you download at 6 megabytes pers second, then you have maxed out your LAN connection. Who knows what latencies are involved when your filesystem/drivers come into it.

Maybe you should run the bittorrent client on the machine you're actually saving the data to. I would, just for the network's sake.

---

