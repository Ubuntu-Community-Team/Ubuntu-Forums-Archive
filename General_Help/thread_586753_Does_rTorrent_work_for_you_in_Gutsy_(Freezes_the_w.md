---
title: "Does rTorrent work for you in Gutsy? (Freezes the whole computer)"
date: 2007-10-22
forum: General Help
---

### Post by emil.s on 2007-10-22
I reinstalled my Edgy server with Gutsy for some days ago. Everything works great, with one exception: rTorrent
After some hours it freezes the whole computer!

I have tried with todays SVN, and the one from the reps.

When it craches the only way to solve it is to press the resetbutton (or Magic SysRq key shutdown).
No services like SSHd, Apache, SMB works, but I can reach the internet from the computer behind the server (I'm using it as Router/Firewall).
And I can't find some information in the logs. But i don't know what to look for...

Does anybody have simlar problems, or is my installation broken?

```
root@Sandnabba.se: ~ # lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 7.10
Release:	7.10
Codename:	gutsy
root@Sandnabba.se: ~ # uname -a
Linux Sandnabba.se 2.6.22.10-emil.s #2 Wed Oct 17 22:54:47 CEST 2007 i686 GNU/Linux
```

---

### Post by emil.s on 2007-10-25
*bump*

---

### Post by bodyhead on 2007-10-31
I'm doing a new server installation on a very old computer to just use rtorrent on it.  If I have the same symptoms, I'll report back here.  It would also be helpful if you would list what versions of libtorrent and rtorrent you are using.

---

### Post by emil.s on 2007-10-31
> **bodyhead said:**
> I'm doing a new server installation on a very old computer to just use rtorrent on it.  If I have  same symptoms, I'll report back here.  It would also be helpful if you would list what versions theof libtorrent and rtorrent you are using.

Ok, thanks. But it seems as the torrent client doesn't matter:
[http://ubuntuforums.org/showthread.php?p=3652582](http://ubuntuforums.org/showthread.php?p=3652582)
[http://ubuntuforums.org/showthread.php?t=587561](http://ubuntuforums.org/showthread.php?t=587561)
[http://ubuntuforums.org/showthread.php?t=587905](http://ubuntuforums.org/showthread.php?t=587905)

But when asking in Ubuntu Swedens forum, it works perfect for everybody, except of me... :(
Btw: "*** rTorrent 0.7.8/0.11.8", but it doesn't work with the one from APT either.

---

### Post by lamnk on 2007-11-02
rtorrent works fine for me, even in x86_64

I think your problem is related to network settings. When i ran feisty fawn on my box, i've experienced strange problem that everytimes i torrent (with rtorrent, azureus, deluge, ktorrent ... probably every linux torrent client under the sun), the browser doesn't work and I can't ping anything.

Now upgraded to gutsy and the problem is just ... gone.

---

### Post by eagletip on 2007-12-11
Yo, and a ho ho ho 
     I also have installed gutsy. since I went wireless Ktorrent worked just fine.Now that I am wireless Ktorrent, Bittorrent, Azureus all freezes my putter. Only way out is reset button. Cant figure it out. Seems like the poroblem lies in wireless. But I dont know how to get info on it as I am not as advanced as some of you true believers lol.
Anyone can help it would be most appreciated.

---

### Post by emil.s on 2007-12-16
> **eagletip said:**
> Yo, and a ho ho ho 
     I also have installed gutsy. since I went wireless Ktorrent worked just fine.Now that I am wireless Ktorrent, Bittorrent, Azureus all freezes my putter. Only way out is reset button. Cant figure it out. Seems like the poroblem lies in wireless. But I dont know how to get info on it as I am not as advanced as some of you true believers lol.
Anyone can help it would be most appreciated.

Hm, ok. But i'm of course not running my server with wireless connection. ;)
One TP with the internet IP, and one TP the the LAN.

But i have reported this as a bug...
[https://bugs.launchpad.net/ubuntu/+bug/158037](https://bugs.launchpad.net/ubuntu/+bug/158037)

---

### Post by l03wn3 on 2008-02-27
This happens to me as well. Also swedish, coincidence?

anyway:
lsb_release -a:
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 7.10
Release:	7.10
Codename:	gutsy

uname -a
Linux ruttputte 2.6.22-14-server #1 SMP Sun Oct 14 22:09:15 GMT 2007 x86_64 GNU/Linux

Tried svn version of libtorrent/rtorrent, and also
libtorrent-0.12.0 + rtorrent-0.8.0.

Guess they really were unstable. Have you tried the stable release?

Seems to only happen for me if i actually transfer anything, not if rtorrent is running but idling. Perhaps something in the library?

/Loon

---

### Post by emil.s on 2008-03-10
My problem is caused by a bug in the "tulip" driver in the vanilla kernel.

Se:
[https://bugs.launchpad.net/ubuntu/+bug/158037](https://bugs.launchpad.net/ubuntu/+bug/158037)

Maybe you're using the same driver?

---

