---
title: "Apt-Get update message on AppGrid"
date: 2016-05-21
forum: General Help
---

### Post by checoimg on 2016-05-21
Today I did ```
sudo apt-get update
``` and got his message, should I do anything ? or just write to the ddevelopers :

```
/usr/share/appgrid/appdata/helpers.py:9: PyGIWarning: Soup was imported without specifying a version first. Use gi.require_version('Soup', '2.4') before import to ensure that the right version gets loaded.
  from gi.repository import GLib, GObject, Soup
Reading package lists... Done
W: http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg: Signature by key 4CCA1EAF950CEE4AB83976DCA040830F7FAC5991 uses weak digest algorithm (SHA1)
W: There is no public key available for the following key IDs:
1397BC53640DB551
W: http://download.videolan.org/pub/debian/stable/Release.gpg: Signature by key 8F0845FE77B16294429A79346BCA5E4DB84288D9 uses weak digest algorithm (SHA1)
W: http://debian.yeasoft.net/btsync/dists/unstable/InRelease: Signature by key 06ABBEA18548527F04A2FC2840FC0CD26BF18B15 uses weak digest algorithm (SHA1)

```
TY

---

### Post by Bashing-om on 2016-05-21
checoimg; Hello;

Not to sweat it.
You are on release 16.04, correct ?

We find the owner of the key " 1397BC53640DB551 " :
```

gpg --search-key 1397BC53640DB551

```
And lo and behold it is Google. We do trust Google, right ?
We tell the system we trust this source:
```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1397BC53640DB551

```
As Google has recently re-configured their servers .

The other notices ( warnings) are because the security at that end is not equal to the security that ubuntu 16.04 expects. Until they tighten up their security; you will get this notice, there is nothing, you, as the user can do; other than not trust the source and remove the source and the software from your system . Ping on the originator to tighten it up ?

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by checoimg on 2016-05-22
> **Bashing-om said:**
> checoimg; Hello;

Not to sweat it.
You are on release 16.04, correct ?

We find the owner of the key " 1397BC53640DB551 " :
```

gpg --search-key 1397BC53640DB551

```
And lo and behold it is Google. We do trust Google, right ?
We tell the system we trust this source:
```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1397BC53640DB551

```
As Google has recently re-configured their servers .

The other notices ( warnings) are because the security at that end is not equal to the security that ubuntu 16.04 expects. Until they tighten up their security; you will get this notice, there is nothing, you, as the user can do; other than not trust the source and remove the source and the software from your system . Ping on the originator to tighten it up ?[INDENT][INDENT]all in the process
[/INDENT]
[/INDENT]


This is what I get

```

gpg --search-keys 1397BC53640DB551
gpg: no keyserver known (use option --keyserver)
gpg: keyserver search failed: bad URI

```

```
gpg --keyserver 1397BC53640DB551
gpg: Go ahead and type your message ...
^C
gpg: Interrupt caught ... exiting

```

---

### Post by checoimg on 2016-05-22
Update[URL="http://imgur.com/YeeuZ1y"]

http://imgur.com/YeeuZ1y[/URL]

[IMG]http://tinyurl.com/jayqhwq[/IMG]

---

### Post by Bashing-om on 2016-05-22
checoimg; Hummm ..

Strange and unforeseen result from " gpg --search-key 1397BC53640DB551 "

My result:
```

sysop@1404mini:~$ gpg --search-key 1397BC53640DB551
gpg: searching for "1397BC53640DB551" from hkp server keys.gnupg.net
(1)     Google Inc. (Linux Packages Signing Authority) <linux-packages-keymast
          4096 bit RSA key D38B4796, created: 2016-04-12
Keys 1-1 of 1 for "1397BC53640DB551".  Enter number(s), N)ext, or Q)uit > q
sysop@1404mini:~$

```
Which now begs the question: Do you have internet connectivity ?
What results:
```

ping -c3 8.8.8.8
ping -c3 ubuntu.com

```
[INDENT][INDENT]sometime I wonder
[INDENT][INDENT][INDENT]other times I just do not know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by checoimg on 2016-05-22
```
ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=52 time=56.0 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=52 time=46.7 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=52 time=46.9 ms


--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 46.799/49.942/56.060/4.333 ms

```

```
ping -c3 ubuntu.com
PING ubuntu.com (91.189.94.40) 56(84) bytes of data.
64 bytes from ovinnik.canonical.com (91.189.94.40): icmp_seq=1 ttl=45 time=155 ms
64 bytes from ovinnik.canonical.com (91.189.94.40): icmp_seq=2 ttl=45 time=153 ms
64 bytes from ovinnik.canonical.com (91.189.94.40): icmp_seq=3 ttl=45 time=147 ms


--- ubuntu.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 147.433/151.935/155.058/3.277 ms



```

---

### Post by Bashing-om on 2016-05-22
checoimg; Yuk.

Beats me at the present time:
gpg --search-key 1397BC53640DB551
and
gpg --search-keys 1397BC53640DB551
both return for me. I do not know at this time why it fails on your end.

Lemme get caught up and get some time for homework .
I will return .

[INDENT][INDENT]the chase is on
[/INDENT][/INDENT]

---

### Post by vasa1 on 2016-05-22
```
06:28 AM ~ $  gpg --search-key 1397BC53640DB551
gpg: no keyserver known (use option --keyserver)
gpg: keyserver search failed: bad URI
06:28 AM ~ $  gpg --search-keys 1397BC53640DB551
gpg: no keyserver known (use option --keyserver)
gpg: keyserver search failed: bad URI
06:28 AM ~ $ gpg --search-key --keyserver keyserver.ubuntu.com 1397BC53640DB551
gpg: searching for "1397BC53640DB551" from hkp server keyserver.ubuntu.com
(1)	Google Inc. (Linux Packages Signing Authority) <linux-packages-keymast
	  4096 bit RSA key D38B4796, created: 2016-04-12
Keys 1-1 of 1 for "1397BC53640DB551".  Enter number(s), N)ext, or Q)uit > q
06:29 AM ~ $ 
```is what I see.

---

### Post by Bashing-om on 2016-05-23
vasa1; Huhhhh ... 

What is magic about my system :
```

sysop@1404mini:~$ gpg --search-key 1397BC53640DB551
gpg: searching for "1397BC53640DB551" from hkp server keys.gnupg.net
(1)     Google Inc. (Linux Packages Signing Authority) <linux-packages-keymast
          4096 bit RSA key D38B4796, created: 2016-04-12
Keys 1-1 of 1 for "1397BC53640DB551".  Enter number(s), N)ext, or Q)uit >

```

Some times
[INDENT][INDENT]in need of an explanation
[/INDENT][/INDENT]

---

### Post by QLee on 2016-05-23
> **Bashing-om said:**
> 

What is magic about my system :

Some times
[INDENT][INDENT]in need of an explanation
[/INDENT][/INDENT]

When I try the plain command ```
QLee@Atlas-Ubu16:~$ gpg --search-key 1397BC53640DB551
gpg: searching for "1397BC53640DB551" from hkp server keys.gnupg.net
?: keys.gnupg.net: Host not found
gpgkeys: HTTP search error 7: couldn't connect: Success
gpg: key "1397BC53640DB551" not found on keyserver
gpg: keyserver internal error
gpg: keyserver search failed: keyserver error

```

The command appears to be coded to go to a "pool" (presumably organised loosely by location in the world or some other paradigm) The magic of which you speak, Bashing-om.

When I issue```
QLee@Atlas-Ubu16:~$ gpg --keyserver keyserver.ubuntu.com --search-key 1397BC53640DB551
gpg: searching for "1397BC53640DB551" from hkp server keyserver.ubuntu.com
(1)	Google Inc. (Linux Packages Signing Authority) <linux-packages-keymast
	  4096 bit RSA key D38B4796, created: 2016-04-12
Keys 1-1 of 1 for "1397BC53640DB551".  Enter number(s), N)ext, or Q)uit > q

```

Note that in that instance I included the "--keyserver keyserver.ubuntu.com" address and get the correct response.

Perhaps there is a problem with one or more of the mirrors in the pool.

This is the type of problem that might clear up on its own over time. However, if it's still failing Bashing-om, maybe you can get the OP running by using the discrete keyserver.ubuntu.com address with the command.

HTH

---

### Post by Bashing-om on 2016-05-23
@QLee; Yeah :)

Thanks, that clears up the mystery to a large degree . Noted !

[INDENT][INDENT]meanwhile,
[INDENT][INDENT][INDENT]back at the ranch
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by checoimg on 2016-05-26
This are all the Warnings by now when I do apt-get update :

```


/usr/share/appgrid/appdata/helpers.py:9: PyGIWarning: Soup was imported without specifying a version first.

Use gi.require_version('Soup', '2.4') before import to ensure that the right version gets loaded.


(typos here in error messages, I've never noticed such a thing before. I could fix this bug XD)


  from gi.repository import GLib, GObject, Soup


W: http://debian.yeasoft.net/btsync/dists/unstable/InRelease: Signature by key 06ABBEA18548527F04A2FC2840FC0CD26BF18B15 uses weak digest algorithm (SHA1)


W: http://download.videolan.org/pub/debian/stable/Release.gpg: Signature by key 8F0845FE77B16294429A79346BCA5E4DB84288D9 uses weak digest algorithm (SHA1)


W: http://www.cyvoc.net/novo-repo/dists/stable/Release.gpg: Signature by key 5892575186356FBEFDF1A4E1BD1E393D4D915797 uses weak digest algorithm (SHA1)




```

---

### Post by Bashing-om on 2016-05-26
checoimg; K;

what distribution and release are you running ? 
" [http://debian.yeasoft.net/btsync/dists/](http://debian.yeasoft.net/btsync/dists/) "
No longer supported ?
" http://download.videolan.org/pub/debian/" same, no longer supported ?

 " http://www.cyvoc.net/novo-repo/dists/" Not able at this time to verify as valid in ubuntu ?

[INDENT]not supported then not a thing we can do
except remove the source
[/INDENT]

---

### Post by checoimg on 2016-05-27
Ok, no biggie. And AppGrid ?

---

### Post by checoimg on 2016-05-27
How can I purge all PPA's and take all of them out of the software sources ? (I'm using Ubuntu MATE-16.04)

---

### Post by checoimg on 2016-05-27
Found [this]("http://askubuntu.com/questions/646884/how-can-i-remove-all-ppa") and went on to detox the system

---

