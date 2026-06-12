---
title: "MP3 Players on Dapper"
date: 2007-08-17
forum: General Help
---

### Post by Weta on 2007-08-17
Hello There

We recently tried to use a Samsung U3 MP3 player on our Ubuntu Dapper operating system, but the player wasn't recognised when we plugged it into the USB port. Does anyone know of any MP3 players - preferably cheap ones! - that work easily on Dapper?  I don't mind using Synaptic to download files to make the player work, but would prefer not to have to use the terminal much to do this (as our system has been excellent since I installed it).  Thanks

Weta

---

### Post by HermanAB on 2007-08-17
Pretty much anything works except Sony, although those can be made to work with some effort too.  The best devices are those that are USB Mass Storage Devices, since then you can just plug it in and drag and drop files to it.  

In my experience, the worst ones are Apple and Sony.  Anything else is easier, cheaper and work better.

---

### Post by heidfirst on 2007-08-17
Some Samsung MP3 players use MTP (Microsoft Transfer Protocol). Have tried installing libmtp, there are a number of threads on the forum indicating that this does work with a number of these devices.

---

### Post by Weta on 2007-08-17
Hello

Thank you. We found a nice small, and relatively inexpensive, iRiver T60 player which seems to work fine - it's recognised when we plug it into the USB port, we can drop Ogg Vorbis files into it, and it plays them!.

Weta

---

### Post by biengo on 2007-08-18
Interestingly enough, although the yp u3 is no longer available with ums-capable firmware, Samsung still won't pipe down about it. It seems to work with libmtp, but of a latest version, and there might be some tinkering involved with /etc/udev/rules.d/  . for more: google "amarok yp u3 site:anythingbutipod.com"

I for one went straight back to the store and got back the cash, and I feel I might have dodged a bullet there, still think it'd be a nice player though...

the i.beat organix works fine, if you like it, and if it is available in NZ. It hasn't quiete the quality of the samsung, and mine did hissing noises while playing back mp3 at very low volume, though as of ogg that wasn't the case.

I really like the iriver t20, although that is an older modell and iriver semms to go down the same mtp route that samsung does (e.g. clix). Does anyone know about a current iriver modell in that price-range that can take the pie?

---

### Post by strabes on 2007-08-18
iPods work perfectly because they're the most popular.
If you don't want apple (like me) I recommend getting one of the Sansa e200 series. They're great little players. Biggest one is 8gb. They appear as mass storage devices so they're platform independent. Just plop your music on it and it builds the database for you. They're kind of picky about tags, so just get easytag and remove all the id3v1 tags and make them id3v2.

---

