---
title: "Deluge update with .deb"
date: 2008-05-05
forum: General Help
---

### Post by Jojan on 2008-05-05
Started Deluge a few weeks ago and it claimed there was an update. It asked if I wanted to go to the site where it could be downloeaded, and I did.

[http://download.deluge-torrent.org/ubuntu/hardy/0.5.9.0/](http://download.deluge-torrent.org/ubuntu/hardy/0.5.9.0/)

But when I open it with my mouse and begin the installation, it first tells me that an older version excists and I should use that one. I try to ignore that fact and install anyway. [FONT="Courier New"]dpkg[/FONT] then tells me it doesn't want to because [FONT="Courier New"]deluge-torrent[/FONT] is depended of [FONT="Courier New"]deluge-torrent-common[/FONT].

How do I "fix" this or when will Ubuntu update Deluge for me?

---

### Post by fahadsadah on 2008-05-05
If you installed deluge via apt, updates will come automatically.
If they don't, type the following into a terminal please:
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by FuturePilot on 2008-05-05
You need to remove the old version first.
```
sudo apt-get remove --purge deluge-torrent
```
Then just double click on the new one and install it.

---

### Post by Jojan on 2008-05-05
Okej. I'll try that. Will my preferences be saved?

But why can't dpkg just do that for me? Is it dumb&#8253; xD

---

### Post by FuturePilot on 2008-05-05
Yes, all your settings will still be there. dpkg can't handle dependencies automatically like apt can.

---

### Post by Ux64 on 2008-05-19
It seems that there are also some other problems.

[http://forum.deluge-torrent.org/viewtopic.php?f=7&t=5905&start=10&st=0&sk=t&sd=a](http://forum.deluge-torrent.org/viewtopic.php?f=7&t=5905&start=10&st=0&sk=t&sd=a)

My current problem is here.

[http://forum.deluge-torrent.org/viewtopic.php?f=7&t=5905&start=10&st=0&sk=t&sd=a#p27305](http://forum.deluge-torrent.org/viewtopic.php?f=7&t=5905&start=10&st=0&sk=t&sd=a#p27305)

--

[http://download.deluge-torrent.org/ubuntu/hardy/0.5.9.1/deluge-torrent_0.5.9.1-1_amd64.hardy.deb](http://download.deluge-torrent.org/ubuntu/hardy/0.5.9.1/deluge-torrent_0.5.9.1-1_amd64.hardy.deb)

Most interesting. Now download is ok, package is ok, depencies are ok, but installation fails? Hmm... 
Now it's a new problem. Does anyone else have this problem?

And Terminal doesn't show anything...

I did clear FF cache and Synaptic Package Cache, didn't change anything.

Deluge installation simply fails.

Older versions are working just fine.

---

