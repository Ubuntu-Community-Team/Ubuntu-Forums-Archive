---
title: "want checksum of xubuntu 20.04 iso"
date: 2020-05-03
forum: General Help
---

### Post by Skaperen on 2020-05-03
i would like to get a checksum (md5, sha256, etc) of the xubuntu 20.04 (focal fossa) LTS iso image to verify my download.  the xubuntu.org web site didn't have it.  otherwise i will download it from 3 or more sites and cross check it.

---

### Post by oldfred on 2020-05-03
[https://kubuntu.org/alternative-downloads](https://kubuntu.org/alternative-downloads)

Use zsync from the folder you have your ISO in.
You will need to find correct path for xubuntu. Probably:
[http://cdimage.ubuntu.com/kubuntu/releases/20.04/release/](http://cdimage.ubuntu.com/kubuntu/releases/20.04/release/)

this is my Ubuntu 
[noparse]zsync http://releases.ubuntu.com/focal/ubuntu-20.04-desktop-amd64.iso.zsync[/noparse]

I often change to a local repository once released. 

When they released Ubuntu, I changed daily name to release file name & zynced it.

> Rename daily from Monday & it was 91% the same:
fred@Z170N-focal:~/ISO$ zsync [http://releases.ubuntu.com/focal/ubuntu-20.04-desktop-amd64.iso.zsync](http://releases.ubuntu.com/focal/ubuntu-20.04-desktop-amd64.iso.zsync)

#################### 100.0% 2711.6 kBps DONE     

reading seed file ubuntu-20.04-desktop-amd64.iso: 

Read ubuntu-20.04-desktop-amd64.iso. Target 91.0% complete.      
downloading from [http://releases.ubuntu.com/focal/ubuntu-20.04-desktop-amd64.iso:](http://releases.ubuntu.com/focal/ubuntu-20.04-desktop-amd64.iso:)
#################### 100.0% 7988.2 kBps DONE      
**
verifying download...checksum matches OK
used 2471415808 local, fetched 244168352


---

### Post by Skaperen on 2020-05-04
i have already downloaded the xubuntu ISO.  i just need a checksum string so i don't need to do it all over, again.

---

### Post by sudodus on 2020-05-04
You find your MD5SUM at the following link (along with the other released Xubuntu files),

[cdimage.ubuntu.com/xubuntu/releases/20.04/release/](http://cdimage.ubuntu.com/xubuntu/releases/20.04/release/)

You can navigate to all released ISO files and other files of Ubuntu desktop and Ubuntu family flavours via the following link,

[**releases.ubuntu.com/**](http://releases.ubuntu.com/)

---

### Post by oldfred on 2020-05-04
The zsync automatically does the chksum. 
It only downloads changes, if you already have the ISO.

Used primarily for daily release of the next Ubuntu, so you an test.

---

### Post by Skaperen on 2020-05-04
i get no response from the cdimage.ubuntu.com (91.189.92.164) server.  not even a ping.  it must be way overloaded.

```

lt2a/forums /home/forums/iso 43> time zsync http://releases.ubuntu.com/focal/xubuntu-20.04-desktop-amd64.iso.zsync
failed on url http://releases.ubuntu.com/focal/xubuntu-20.04-desktop-amd64.iso.zsync
could not read control file from URL http://releases.ubuntu.com/focal/xubuntu-20.04-desktop-amd64.iso.zsync
[[ 0m0s real 0.690 - user 0.000 - sys 0.005 - 0.72% ]]
lt2a/forums /home/forums/iso 44>

```

looks like they don't have the *zsync* control file there for Xubuntu.

---

### Post by Skaperen on 2020-05-04
```

lt2a/forums /home/forums/iso 46> time sha256 /home/share/iso/xubuntu/20.04/xubuntu-20.04-desktop-amd64.iso
005a9450d16fe885132be9368a96c73910096b57cc1a67f03a97fca7af95f4a3  /home/share/iso/xubuntu/20.04/xubuntu-20.04-desktop-amd64.iso
[[ 0m7s real 7.913 - user 7.676 - sys 0.236 - 99.99% ]]
lt2a/forums /home/forums/iso 47> 

```

---

### Post by SeijiSensei on 2020-05-04
I've never had a problem going to cdimage.ubuntu.com and didn't just now.  All the checksums are on this page along with the ISOs:

[http://cdimage.ubuntu.com/xubuntu/releases/20.04/release/](http://cdimage.ubuntu.com/xubuntu/releases/20.04/release/)

The file [http://cdimage.ubuntu.com/xubuntu/releases/20.04/release/SHA256SUMS](http://cdimage.ubuntu.com/xubuntu/releases/20.04/release/SHA256SUMS) contains the same signature you report above.

```
005a9450d16fe885132be9368a96c73910096b57cc1a67f03a97fca7af95f4a3 *xubuntu-20.04-desktop-amd64.iso
```

---

### Post by oldfred on 2020-05-04
I see it here, but did not run it.

[noparse]zsync http://cdimage.ubuntu.com/kubuntu/releases/20.04/release/kubuntu-20.04-desktop-amd64.iso.zsync[/noparse]

---

### Post by Skaperen on 2020-05-05
so, i need a different site which has xubuntu (i'm not trying to get kubuntu) and that zsync file.  or just the plain sha256.  i have already downloaded the whole iso.  the sha256 of it is **005a9450d16fe885132be9368a96c73910096b57cc1a67f03a97fca7af95f4a3**.

---

### Post by Holger_Gehrke on 2020-05-05
I don't really understand the problem. On all the mirrors linked on [http://xubuntu.org/download](http://xubuntu.org/download) there are files MD5SUMS, SHA1SUMS and SHA256SUMS which contain the respective sums. You can just download the *SUMS files to the same directory as the iso and then do 'sha256sum --check SHA256SUMS' and the respective other checks. The sum you posted is identical to the one found in SHA256SUMS on one of the two German mirrors

Edit: And if you downloaded by torrent, then there were checksums in the .torrent file both for the file and for each and every block of the file. If the sums don't match, the mismatching parts are discarded and re-downloaded.

Holger

---

### Post by CelticWarrior on 2020-05-05
> **Holger_Gehrke said:**
> Edit: And if you downloaded by torrent, then there were checksums in the .torrent file both for the file and for each and every block of the file. If the sums don't match, the mismatching parts are discarded and re-downloaded.

Exactly. And that's one of the two main reasons why everybody should use torrents for this. The other is it offloads a lot of traffic from the repository servers. Please keep seeding it for as along as you can.

---

### Post by Skaperen on 2020-05-05
i didn't see the *SUMS files and i still get no response from cdimage.ubuntu.com.
```

lt2a/forums /home/forums 54> time ping -c 1024 cdimage.ubuntu.com
PING zaniah.canonical.com (91.189.92.164) 56(84) bytes of data.

--- zaniah.canonical.com ping statistics ---
1024 packets transmitted, 0 received, 100% packet loss, time 1044285ms

[[ 17m34s real 1054.290 - user 0.029 - sys 0.054 - 0.00% ]]
lt2a/forums /home/forums 55> 

```

---

### Post by oldfred on 2020-05-05
You are going to ubuntu, but it is a flavor. 
You have to go to that flavor's site.

per Holger_Gehrke link above & then go to the nearest Mirror:
[https://xubuntu.org/download](https://xubuntu.org/download)

When I click on USA mirror, I get this with everything.
[http://mirror.us.leaseweb.net/ubuntu-cdimage/xubuntu/releases/20.04/release/](http://mirror.us.leaseweb.net/ubuntu-cdimage/xubuntu/releases/20.04/release/)

---

### Post by sudodus on 2020-05-05
Is your system accepting HTTP or only HTTPS websites? Or is there some other blacklisting?

[http://cdimage.ubuntu.com/](http://cdimage.ubuntu.com/)

works all the time for me.

---

### Post by Skaperen on 2020-05-06
```

lt2a/forums /home/forums 59> time telnet cdimage.ubuntu.com 80;time telnet cdimage.ubuntu.com 443
Trying 91.189.92.164...
telnet: Unable to connect to remote host: Connection timed out
[[ 2m9s real 129.375 - user 0.001 - sys 0.005 - 0.00% ]]
Trying 91.189.92.164...
telnet: Unable to connect to remote host: Connection timed out
[[ 2m11s real 131.072 - user 0.006 - sys 0.000 - 0.00% ]]
lt2a/forums /home/forums 60> 

```
maybe they are blocking me.

---

### Post by sudodus on 2020-05-06
Why do you use telnet? You want to get a file and a file browser or wget might suit better from this task.

Try
```

wget http://cdimage.ubuntu.com/xubuntu/releases/20.04/release/SHA256SUMS

```

It works for me.

---

### Post by ActionParsnip on 2020-05-06
If you use torrents, the torrent protocol will check the data for you. Much better than HTTP downloading, and faster too.

---

### Post by Skaperen on 2020-05-06
why would i use torrents if i have already downloaded the ISO?  oh wait, you mean i should use torrents to do 2 more downloads to cross-check with what i already have.

---

### Post by Skaperen on 2020-05-06
i used telnet to show that i cannot get a connection to either port 80 (HTTP) or port 443 (HTTPS).

---

