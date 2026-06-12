---
title: "bittorrent trouble"
date: 2007-06-24
forum: General Help
---

### Post by d_xtremw on 2007-06-24
So I've got bittorrent installed and everything already but wen i go to Applications-->Internet, it doesn't show up, yet when I go to applications->add/remove it shows bittorrent is installed and its checked. so why doesn't it show up???

---

### Post by iota on 2007-06-24
I think you need to install the bit torrent gui.

Trying searching for it in the packet manager :)

---

### Post by d_xtremw on 2007-06-25
it is installed. but i found out the solution. bittorrent is automatically hidden by default. had to right click applications go to edit menus and make sure that bittorrent is selected

---

### Post by TexMex657 on 2007-07-06
So I was having similar problems but did what you did and can now get BitTorrent to show up.  Problem is when I click on a torrent file and open it, I never see a download dialog box or anything else indicating that BitTorrent is actually running and downloading the file.  

Running the command:
```
ps -ef | grep BitTorrent
```
doesn't show anything either which means to me that its not actually running...

Do you need to save the torrent files in order for the file to actually download?

Thanks

---

### Post by Hallvor on 2007-07-06
> **TexMex657 said:**
> 

Do you need to save the torrent files in order for the file to actually download?

Thanks

No, if you download the torrentfile and open it, or if you open it directly from url, the file should download anyway.

You could always try a different client and see if it helps. Bittornado is a lot like the original client, small, lightweight and stable, but has a few more options.

kTorrent is also quite good, and a lot like uTorrent in Windows.

---

### Post by Lolicon on 2007-07-06
Why don't you Wine uTorrent? It works very well.

---

### Post by Hallvor on 2007-07-06
> **Lolicon said:**
> Why don't you Wine uTorrent? It works very well.

I`ll give you two reasons not to:

1. Closed source
2. Affiliated with the MPAA

It should be banned from trackers IMHO.

---

### Post by southernman on 2007-07-06
I've only used Azureus. It works pretty well (for me at least), though have read that others consider it bloated.

---

### Post by TexMex657 on 2007-07-07
Using kTorrent works.  Still don't know why the original BT client wouldn't work though.

---

