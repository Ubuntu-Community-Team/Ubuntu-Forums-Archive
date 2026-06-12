---
title: "My Kingdom For A Working Bittorrent Client!"
date: 2008-02-11
forum: General Help
---

### Post by sharpycore on 2008-02-11
I know lists of bittorrent clients abound on the forums but I have a specific question. I've tried every bittorrent client in the repos and I can't get any of them to behave. Deluge crashes without warning, Transmission causes kernel panics and azureus just sucks up so much resources.
So, does anyone have recommendations for a bittorrent client that doesn't use libtorrent (apparently the cause of the crashes in the first two clients listed) or java (sloooooooow)? I'm surprised at the number of torrent clients and the failure of any of them to work.
Thanks

---

### Post by s_h_a_d_o_w_s on 2008-02-11
Id run utorrent under wine

---

### Post by solitaire on 2008-02-11
I run KTorrent with the "Upnp" Plugin enabled!
Don't think that uses "libtorrent" 
Dunno about Java....

---

### Post by sharpycore on 2008-02-11
> **solitaire said:**
> I run KTorrent with the "Upnp" Plugin enabled!
Don't think that uses "libtorrent" 
Dunno about Java....

KTorrent is looking like the solution. Hasn't crashed in the last half hour or so which is a record so far. And it's a lot less resource intensive and MUCH faster downloading than Azureus. I can watch films again! Thanks!

---

### Post by apetresc on 2008-02-11
I'm glad you found a solution that works for you, but I'd be *really* concerned about the underlying cause of your symptoms. It is not a normal issue - me and everyone in my house (5 linux users) use Transmission and Deluge on a very very regular basis and have never experienced a crash or kernel panic from them.

1) You should run a memtest86 session to make sure you don't have  bad RAM
2) How long has your system been installed for? There may be linkage issues

---

### Post by solitaire on 2008-02-11
> **sharpycore said:**
> KTorrent is looking like the solution. Hasn't crashed in the last half hour or so which is a record so far. And it's a lot less resource intensive and MUCH faster downloading than Azureus. I can watch films again! Thanks!

Glad i was of some help ;)

Happy Torrents :-\" ;)

---

### Post by sharpycore on 2008-02-12
> **AdrianP said:**
> I'm glad you found a solution that works for you, but I'd be *really* concerned about the underlying cause of your symptoms. It is not a normal issue - me and everyone in my house (5 linux users) use Transmission and Deluge on a very very regular basis and have never experienced a crash or kernel panic from them.

1) You should run a memtest86 session to make sure you don't have  bad RAM
2) How long has your system been installed for? There may be linkage issues

You are right that I should be concerned. KTorrent has only slightly reduced the number of kernel panics and I think it might be because I am downloading fewer torrents concurrently. I'll have a look at doing a memtest but people making similar reports seem to think it might be something to do with the libtorrent package.
I'm going to test memory and then check to see if I can repeat semi-stable behaviour by only downloading a small number of torrents with other clients.

---

### Post by sharpycore on 2008-02-12
Oh, and what are linkage issues and how do I check for them?
Tom

---

### Post by Sammi on 2008-02-12
You should make sure you are using updated versions of Deluge and Transmission.

[http://deluge-torrent.org/downloads.php](http://deluge-torrent.org/downloads.php)
[http://www.getdeb.net/app/Transmission](http://www.getdeb.net/app/Transmission)

---

