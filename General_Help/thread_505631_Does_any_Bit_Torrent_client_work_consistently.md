---
title: "Does any Bit Torrent client work consistently?"
date: 2007-07-20
forum: General Help
---

### Post by dkaddict on 2007-07-20
I have been trying to get Bit Torrent downloads to download at a reasonable speed. Up until this morning I had tried every Torrent client there is. 

I thought I had finally cracked it this morning as I had a file downloading at 500kbps by using Utorrent in Wine.
Alas, this only lasted for the end of that file download and now I am back to 10kbps MAX on any of the clients I have installed. Is this normal? I mean, what is an average download rate for Bit Torrents? The last torrent I was trying to download was connected to 75 Seeders & 70 peers but download was really slow and upload was around the same. i have been trying to find an answer to this problem but all I have found is stuff about trying different clients and listening on ports that have never made any difference to my speeds.

Is, therefore, the claim of 'faster downloads' that all of these clients make a lie?
Is the MAX download anyone can expect ~10kbps, regardless of how many seeders or leechers?

I am really confused as I had a fast dwnload earlier.

Should I just resign myself to the fact that fast Torrent downloads are not fully supported in Ubuntu and that there is no really decent, reliable, and consistent Bit Torrent client for Linux?

Any help on this very confusing and frustrating matter will be VERY welcomed

peace

dk

---

### Post by splintercellguy on 2007-07-20
It's not really Linux/BT client, it could be your ISP or your router port forward. Ubuntu and your client doesn't have much to do with connectivity I believe. Getting good torrents is also key.

---

### Post by rscott5 on 2007-07-20
There are lots of possible reasons but here are the two that I have personally run into:

1. If you are behind a router/firewall you may need to open the ports behind used by your torrent client. If your router supports UPnP (automatic port mapping) and your torrent client does as well then you can try that but otherwise you may just need to manually set your router to forward certain ports to your computer.

2. Your ISP may block/limit torrent file downloading. I found this link on the Azureus wiki with a list of ISPs telling which ones block bittorrent: [http://www.azureuswiki.com/index.php/Bad_ISPs](http://www.azureuswiki.com/index.php/Bad_ISPs) . I know there is a bigger list on Wikipedia somewhere, but I can't seem to find it. If your ISP is listed as blocking torrents then you may just be out of luck.

---

### Post by stchman on 2007-07-20
> **dkaddict said:**
> I have been trying to get Bit Torrent downloads to download at a reasonable speed. Up until this morning I had tried every Torrent client there is. 

I thought I had finally cracked it this morning as I had a file downloading at 500kbps by using Utorrent in Wine.
Alas, this only lasted for the end of that file download and now I am back to 10kbps MAX on any of the clients I have installed. Is this normal? I mean, what is an average download rate for Bit Torrents? The last torrent I was trying to download was connected to 75 Seeders & 70 peers but download was really slow and upload was around the same. i have been trying to find an answer to this problem but all I have found is stuff about trying different clients and listening on ports that have never made any difference to my speeds.

Is, therefore, the claim of 'faster downloads' that all of these clients make a lie?
Is the MAX download anyone can expect ~10kbps, regardless of how many seeders or leechers?

I am really confused as I had a fast dwnload earlier.

Should I just resign myself to the fact that fast Torrent downloads are not fully supported in Ubuntu and that there is no really decent, reliable, and consistent Bit Torrent client for Linux?

Any help on this very confusing and frustrating matter will be VERY welcomed

peace

dk

Do you have the proper port opened up om your router (if you use a router)?  500kbs(63kBs) is fairly slow.  I don't download too much using torrents as the speed is so hit or miss.

---

### Post by davidjmayo on 2007-07-20
In case it is your ISP blocking/restricting  torrents which they do sometimes have you tried running any of the bittorrent clients as "encrypted". This setting will obviously vary depending which app you use.

If you want to test download reliability try one of the ubuntu torrents (which have hundreds of seeds and few if any peers) and see what DL speed you get

[http://releases.ubuntu.com/feisty/](http://releases.ubuntu.com/feisty/) ubuntu torrents are near the end of the page

You may want to test this link with different bittorrent clients

---

### Post by dkaddict on 2007-07-20
Thanks a lot for all replies. I do appreciate the time you have taken to try and help.

I have tried forwarding the ports and my router does support UPNP apparently. I am gonna have a quick look to see if my ISP, British Telecom, throttles torrent downloads. I had resigned to simply not using torrents until I got the fast rate this mornng. Gonna keep trying I suppose.

dk

---

### Post by BlahMan_of.Doom on 2007-07-20
[KTorrent](www.ktorrent.org) works nicely.

---

### Post by dkaddict on 2007-07-20
Hold the phone!!!!!!!!

The link to 'bad torrent sites' has BT Broadband, my ISP as a 'bad' provider but says that it limits torrent downloads during certain times of the day, which makes sense now because I got the 500kbps+ rate at 7:30am. 

Big big thanx for that info and all of your help.

Now I need to work out how to really encrypt the downloads because it didn't work earlier.

Thanx again

DK

---

### Post by davidjmayo on 2007-07-20
> Now I need to work out how to really encrypt the downloads because it didn't work earlier.

there should be an option in your bittorrent client to do this

In ktorrent it's settings==>configure ktorrent==>general and then check the encrytption options.
there should be something similar in other torrent aps (I did it before with utorrent when I was on W2K)
EDIT: look at preferences or connection in the app

---

### Post by LadFromWales85 on 2007-07-20
BT shape certain services/protocols during peak times, which to them is 4PM through to midnight as far as I'm aware.  Bittorrent is one of them.  I was at a friends place (on the same exchange as me) using BT, and managed to download from a torrent with lots of seeds at a max of 12kB/sec.  The same torrent on a different ISP at my place got over 700kB/sec.  After midnight he was able to download faster.

---

### Post by dkaddict on 2007-07-23
My ISP is definitely using bandwidth shaping to limit the downloads of torrents and it seems that those times you mentioned, walesguy, are about right. I am using utorrent in Wine now and have been getting around 200kbps on average when the isp aren't playing silly buggers with my bandwidth. I am still trying to work out how to, a:succesfully encrypt incoming torrent downloads so as to beat the shaping and b:get the best speeds that I can.

A short while ago, I tried ktorrent and it looked really promising to begin with. It reached ~300kbps, stayed there for a couple of mins. then dropped instantly (it wasn't a gradual speed reduction) to ~40kbps. I fancy that my isp (British Telecom who charge me a bullseye a month for what is obviously *not* what they advertise their service to be) is shaping my bandwidth now, albeit not as severely as peak times. 

I tried turning 'encryption' on in ktorrent and it slowed the download to ~500bps (I do mean 'bytes' so it dropped to ~0.5kbps) which is just dismal-I would be a *lot* older by the time I got to watch that documentary.

I am back with utorrent in Wine and getting ~200kbps (max). I can live with those sort of speeds but would like to get my moneys worth out of my ISP and beat their bandwidth fascism.

I am relatively new still to Ubuntu so any help will be received with thanx.

peace

dk

---

### Post by kelvin spratt on 2007-07-23
Encryption as far as i know will only work if all seeds are participating  hence the poor download speeds itsi a sign of the times here in the uk, Bt is to interested in fleecing the public and not investing it has fallen so far behind and because we British just complain but take no action it does what it wants and can get away with it.
One small tip in the UK set your download speed 1000 and your upload speed to 20-25 this seems to give good download speeds, iv'e used all the torrent aps  utorrent gives no advantage to the frog, bitcomet, or Ktorrent when they are set up properly in fact Ktorrent regularly gives me 500+kbs download speeds so does the Blue frog and the Frog is not a resource hog when set-up correctly far from it

---

