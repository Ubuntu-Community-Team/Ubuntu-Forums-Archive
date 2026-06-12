---
title: "Queries!"
date: 2015-04-22
forum: General Help
---

### Post by Yezinki on 2015-04-22
Care to reply to the following:

1. Tried installing Ubuntu 14.04 64 bit LTS,  Does one have to unplug all usb devices like cooler tray?

2. Installation stalled at installing language packs?

3. Key board got warm and fans running high?

4. Hope it wont fry up my Nvidia 7900 GTX 512 MB....Been burnt 3 time earlier with W7 Pro 32 bit despite I use Dell Fan utility app and a cooler tray?

5. is this drive partitioning fine for Ubuntu only.........Guided > root 25 GB Primary beginning of the drive ext4, > Swap 4 GB end of the drive and > /home all the rest...... approx 270 GB Logical beginning of the drive ext4?

Thanks.

---

### Post by Holger_Gehrke on 2015-04-22
> **Yezinki said:**
> 
1. Tried installing Ubuntu 14.04 64 bit LTS,  Does one have to unplug all usb devices like cooler tray?

No. A cooler tray should only use USB for getting current, so it should not even show up as a device on the bus.
> **Yezinki said:**
> 
2. Installation stalled at installing language packs?

"Stalled" as in "took a while" or stalled as in "hung there and didn't finish" ? If the former, it might have downloaded them if they were not on the installation media. Or perhaps - if installing off a DVD - it had trouble reading. Or they might have been very well compressed (they are basically text ...) and this took a moment. If the latter, I'd think bad media or corrupted Download.
> **Yezinki said:**
> 
3. Key board got warm and fans running high?

Lots of decompressing getting done. It does give the cpu a work-out :) .
> **Yezinki said:**
> 
4. Hope it wont fry up my Nvidia 7900 GTX 512 MB....Been burnt 3 time earlier with W7 Pro 32 bit despite I use Dell Fan utility app and a cooler tray?

I don't think it will. I've seen reports of the fan on these cards going full tilt all the time until the right (proprietary) driver was installed. So basically, until software takes control of the card, the hardware is playing it safe and making sure it stays cool. 
> **Yezinki said:**
> 
5. is this drive partitioning fine for Ubuntu only.........Guided > root 25 GB Primary beginning of the drive ext4, > Swap 4 GB end of the drive and > /home all the rest...... approx 270 GB Logical beginning of the drive ext4?

I'd make the root partition bigger, about 50 GB perhaps, since programs, libraries and their data go there, but I'm running - among a lot of other things - mysql and it's data goes to /var on the root partition. For the basic install it's more than ample, though.

---

### Post by Yezinki on 2015-04-22
Thanks for your reply and expert thoughts.

I think too it was a bad download......there is mds check?

50 GB for /........thanks again........

Apologize for my simple questions........am a senile newbie to Ubuntu.

---

### Post by Yezinki on 2015-04-22
One more question does Ubuntu carry drivers for Nvidia 7900 GTX 512 MB?

Thanks.

---

### Post by Holger_Gehrke on 2015-04-22
You can find the checksums (md5,sha1,sha256) at [http://releases.ubuntu.com/14.04](http://releases.ubuntu.com/14.04) .

---

### Post by Yezinki on 2015-04-22
> **Holger_Gehrke said:**
> You can find the checksums (md5,sha1,sha256) at [http://releases.ubuntu.com/14.04](http://releases.ubuntu.com/14.04) .


Thanks for posting the link.

I have Ubuntu 14.04 LTS 32 bit and 64 bit and Kubuntu 14.04 LTS 32 bit.

What would there checksums be?

---

### Post by flaymond on 2015-04-22
You can find those md5 key at the official site. Ubuntu and Kubuntu is good looking, with the 3d transitions
and features. At leaet both of them, are lighter than W7

---

### Post by Yezinki on 2015-04-22
Matched for both Ubuntu versions.......... 1b305d585b1918f297164add46784116 *ubuntu-14.04.2-desktop-amd64.iso

                                                         a8a14f1f92c1ef35dae4966a2ae1a264 *ubuntu-14.04.2-desktop-i386.iso

Probably the burn isnt good........what media should I use......DVD-R or DVD-RW?

Thanks.

---

### Post by Yezinki on 2015-04-22
1b305d585b1918f297164add46784116 *ubuntu-14.04.2-desktop-amd64.iso

a8a14f1f92c1ef35dae4966a2ae1a264 *ubuntu-14.04.2-desktop-i386.iso

---

### Post by Holger_Gehrke on 2015-04-22
Towards the end of that page is a directory listing of the download server. At the beginning of that listing are text files with the checksums.

---

### Post by Yezinki on 2015-04-22
> **InterProg said:**
> You can find those md5 key at the official site. Ubuntu and Kubuntu is good looking, with the 3d transitions
and features. At leaet both of them, are lighter than W7


Woh really even the 64 bit is lighter than W7  Pro 32 bit?

Thanks for your expert views.

---

### Post by Holger_Gehrke on 2015-04-22
> **Yezinki said:**
> 
Probably the burn isnt good........what media should I use......DVD-R or DVD-RW?


If your machine can boot from USB I'd use unetbootin or something like that and make a bootable flash drive ... Installation is a lot faster from that than from a DVD.

---

### Post by Yezinki on 2015-04-22
> **Holger_Gehrke said:**
> If your machine can boot from USB I'd use unetbootin or something like that and make a bootable flash drive ... Installation is a lot faster from that than from a DVD.

You mean a usb flash drive.........how to make it bootable?

---

### Post by nerdtron on 2015-04-22
> **Yezinki said:**
> One more question does Ubuntu carry drivers for Nvidia 7900 GTX 512 MB?

Thanks.

Isn't that an old card? I believe it will work out of the box. not sure though if you install the proprietary drivers.

---

### Post by nerdtron on 2015-04-22
> **Yezinki said:**
> You mean a usb flash drive.........how to make it bootable?

Here's a video for that [https://www.youtube.com/watch?v=l8l6UdrMBIM](https://www.youtube.com/watch?v=l8l6UdrMBIM)

---

### Post by Yezinki on 2015-04-22
> **nerdtron said:**
> Isn't that an old card? I believe it will work out of the box. not sure though if you install the proprietary drivers.


Yes its an old card.......Thanks for confirming.

---

### Post by Yezinki on 2015-04-22
> **nerdtron said:**
> Here's a video for that [https://www.youtube.com/watch?v=l8l6UdrMBIM](https://www.youtube.com/watch?v=l8l6UdrMBIM)


Thanks again for posting the YT link.

---

### Post by flaymond on 2015-04-22
[QUOTE=Yezinki]1b305d585b1918f297164add46784116 *ubuntu-14.04.2-desktop-amd64.iso

a8a14f1f92c1ef35dae4966a2ae1a264 *ubuntu-14.04.2-desktop-i386.iso[/QUOTE]

I don't understand, are you trying to compare md5 hash with different version of bit? (e.g 32 bit and 64 bit).

DVD-RW (rewriteable) is good for me. No need to waste a DVD if something bad happened, in case you need to delete the copies (DVD-R [I think it's read-only])

---

### Post by flaymond on 2015-04-23
[QUOTE=Yezinki]Woh really even the 64 bit is lighter than W7  Pro 32 bit?

Thanks for your expert views.[/QUOTE]

Woa, that ironic.

* You can see the installation size, and the resource it using on RAM. 64 bit is faster than 32 bit, so no doubt. Anyway, it depends on where the system stand on(hardware).

---

### Post by Yezinki on 2015-04-24
> **InterProg said:**
> I don't understand, are you trying to compare md5 hash with different version of bit? (e.g 32 bit and 64 bit).

DVD-RW (rewriteable) is good for me. No need to waste a DVD if something bad happened, in case you need to delete the copies (DVD-R [I think it's read-only])


True I agree. Thanks.

---

