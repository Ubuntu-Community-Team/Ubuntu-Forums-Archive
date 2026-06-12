---
title: "Bluetooth between Ubuntu and Nexus 7"
date: 2013-05-14
forum: General Help
---

### Post by Marzata on 2013-05-14
Bluetooth connection between laptop with Ubuntu (Xubuntu 12.04.2 LTS) and Nexus 7 (Android 4.2.2) tablet. The devices are paired. When transferring files from the tablet to the laptop it works. The opposite is not possible. Any idea why and how to solve it? Thank you!

---

### Post by Irihapeti on 2013-05-14
There are a couple of long-term bugs with 12.04 and bluetooth transfers. I have a similar problem with two older Nokia Symbian phones.

My workaround is to install obexfs and mount the phones to a folder in my home directory.

```

obexfs -b xx:xx:xx:xx:xx:xx <folder>

(Replace xx:xx:xx:xx:xx:xx with the identifier for the phone/tablet.)
```

Unmount it with
```
fusermount -u <folder>
```

I've found that it gives a good, solid connection. I can drag and drop files from one device to the other in the usual way with no problems. I've even had both the phones mounted at once (to different folders) and transferred files from one to the other.

---

### Post by Marzata on 2013-05-14
obexfs -b  xx:xx:xx:xx:xx:xx <folder> 

where xx:xx:xx:xx:xx:xx is the HW address of the tablet? 
<folder> is a folder on the local linux machine? 

I did this but nothing appeared in that folder. Both devices are paired.

Idea?

---

### Post by Irihapeti on 2013-05-14
Yes, you've understood the command correctly.

It's been a while since I set this up, and I didn't make notes at the time, so my memory is a bit hazy on some of the details, so some of this is guesswork.

Run the command:
```
sdptool browse <hw address>
```

and check for Obex File Transfer in the output.

---

### Post by Marzata on 2013-05-15
Thank you! It is too slow. Back to good old ssh.

---

### Post by phamthanhnam on 2013-05-21
It looks like the same problem [here]("https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/1148033").
As many people said, installing blueman solved the problem. Try it.

---

