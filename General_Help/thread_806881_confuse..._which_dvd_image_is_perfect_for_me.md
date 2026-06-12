---
title: "confuse... which dvd image is perfect for me"
date: 2008-05-25
forum: General Help
---

### Post by miteshanand1729 on 2008-05-25
I want to download a DvD image of Ubuntu 8.04(Hardy) via bittorrent but i got confuse seeing many ver.here
[[http://torrent.ubuntu.com:6969/]](http://torrent.ubuntu.com:6969/]).
Earlier i downloaded this image Info Hash-a479656de1c06dc78f4205356f160432ceb7ba20	ubuntu-7.04-dvd-i386.iso	3.97GiB	13	1	0	0B

I install it but i want to add this dvd image in synaptic manager but it does not accept it.
So i want to download a fresh dvd image of Hardy.Can any one suggest me a dvd image which i can add in Synaptic???

Or which is the org DVD image of Hardy??? {Torrent}.

---

### Post by chewearn on 2008-05-25
This one:
[http://torrent.ubuntu.com:6969/file?info_hash=l/%27%7E%AD%CFTR%1AO%3C%11%97%04%DB%E6%F3%BCh%B2](http://torrent.ubuntu.com:6969/file?info_hash=l/%27%7E%AD%CFTR%1AO%3C%11%97%04%DB%E6%F3%BCh%B2)
[URL="http://torrent.ubuntu.com:6969/file?info_hash=z%82i%D1%80%1B%20%3F%96%EE%FB%D6%8C%BC%D6%80V%F8%CC%84"]
[/URL]

---

### Post by miteshanand1729 on 2008-05-25
> **AstalaVista said:**
> This one:
[http://torrent.ubuntu.com:6969/file?info_hash=l/%27%7E%AD%CFTR%1AO%3C%11%97%04%DB%E6%F3%BCh%B2](http://torrent.ubuntu.com:6969/file?info_hash=l/%27%7E%AD%CFTR%1AO%3C%11%97%04%DB%E6%F3%BCh%B2)
[URL="http://torrent.ubuntu.com:6969/file?info_hash=z%82i%D1%80%1B%20%3F%96%EE%FB%D6%8C%BC%D6%80V%F8%CC%84"]
[/URL]
Thanx for reply But i already download this one ,i can't able to add it synaptic manager. Since i have a slow internet connection i want to add it to synaptic manager.
So when i want to add it to synaptic it cant scan the dvd and hence i can't able to add dvd in synaptic.
NOte-I check the dvd for damage its correct.

---

### Post by shifty_powers on 2008-05-25
not sure i understand.

you want to download and burn a live-dvd of ubuntu, and add it to your repo list in synaptic so that synaptic will install software from it, yes?

---

### Post by miteshanand1729 on 2008-05-25
> **shifty_powers said:**
> not sure i understand.

you want to download and burn a live-dvd of ubuntu, and add it to your repo list in synaptic so that synaptic will install software from it, yes?
Yes i want to download a dvd image which i can add it to Rep list in Synaptic so that i've to download less amount of data when i install something...

---

### Post by miteshanand1729 on 2008-05-25
Or can any one help me how i can add a DVD image in Rep list in Synaptic...???

---

### Post by shifty_powers on 2008-05-25
system>admin>synaptic>settings>repositories>third party software>add cd rom

(alos works for dvd ;))

---

### Post by chewearn on 2008-05-25
If you don't want to burn a DVD, you can mount the iso image directly to /media/cdrom, and the system will think that a real DVD is in the drive.

Run this command in terminal to mount (replace /path/file.iso with the actual iso file):

```
sudo mount -o loop /path/file.iso /media/cdrom
```To dismount:
```
sudo umount /dev/cdrom
```

---

### Post by miteshanand1729 on 2008-05-25
> **AstalaVista said:**
> If you don't want to burn a DVD, you can mount the iso image directly to /media/cdrom, and the system will think that a real DVD is in the drive.

Run this command in terminal to mount (replace /path/file.iso with the actual iso file):

```
sudo mount -o loop /path/file.iso /media/cdrom
```To dismount:
```
sudo umount /dev/cdrom
```
By using this command or by using Gmount iso i m not able to mount dvd iso image.It say E:Fail to mount the cdrom.I don't know why... Any help..???

---

### Post by zvacet on 2008-05-25
I´m not sure it will work but try with 

```
sudo mount -o loop /path/file.iso /media/cdrom0
```

---

