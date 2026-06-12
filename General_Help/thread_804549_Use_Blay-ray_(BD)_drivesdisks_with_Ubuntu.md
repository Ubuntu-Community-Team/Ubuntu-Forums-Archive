---
title: "Use Blay-ray (BD) drives/disks with Ubuntu?"
date: 2008-05-23
forum: General Help
---

### Post by johann_p on 2008-05-23
It seems that Blue-Ray DVDs are becoming the de-facto standard for High-definition DVDs. 
Is it / will it be possible to use Ubuntu to 1) play DB movies 2) use BD RWs for data backup, 3) use BD RWs to create own HD movies playable in a BD player?

As far as I understand even current DVD playing solutions are unlicensed, illegal or not supported by Ubuntu ... will this be even worse with BD movies?

Is there a roadmap that describes whether this will be supported and how?

---

### Post by Nepherte on 2008-05-23
I thought ubuntu did not include dvd playback capability because of regional country policies. But of course you can enable the playback capability by intalling the correct packages. I *assume* this will be the same for Blue-Ray.

---

### Post by Trollslayer on 2008-05-23
> **Nepherte said:**
> I thought ubuntu did not include dvd playback capability because of regional country policies. But of course you can enable the playback capability by intalling the correct packages. I *assume* this will be the same for Blue-Ray.

If you do happen to find [FONT="Courier New"]libdvdcss[/FONT] and [FONT="Courier New"]libdvdread[/FONT] somewhere life gets a lot easier. :KS

---

### Post by johann_p on 2008-05-23
The point I want to make is this: the content of commercial BD Movie disks is protected by an ecryption system that only allows decryption according to certain rules and only to licensees of the technology. 

So there are the following possibilites:
1) Ubuntu tries to get a license and follow the licenese requirements in order to be able to play content. This is extremely unlikely for many reasons, most importantly because open-source development will be incompatible with the license requriements, and because a license fee must be paid for every installation.
2) some commercial closed source program is developed that can play BD movies.  This is only possible however if the OS can make some guarantees about how the HD video stream is handled. Again, these guarantees are unlikely to be fulfilled with open-source software. 
3) Somebody finds a way to crack BD and provides a library, similar to libdvdcss. This is more unlikely than for CSS because the encryption is much better. I also assume that there will be harsh legal action about any such library.

The bottom is: will Ubuntu (like Linux in general) work towards solving these issues in some way or will Linux be increasingly an OS that will be unusable with protected media and other form of protected content? The times of simple and easily breakable algorithms like CSS are over, I think.

A totally separate but interesting issue is whether BD technology will be supported as a reading/writing medium and whether there will be drivers that support reading unencrypted data or writing unencrypted data to BD-RW media.

---

### Post by solitaire on 2008-05-23
Thought Blu-ray BD+ encryption was cracked ages ago??

---

### Post by Nepherte on 2008-05-24
There are already Blue-Ray readers + writers (pc only) for sale.

As you stated before, it is most unlikely ubuntu will get a license. Of all the options, number three is the most likely one.

---

### Post by speedsix on 2008-05-24
[https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD?highlight=(ray)|(blu](https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD?highlight=(ray)|(blu))

The biggest problem is going to be hardware i.e having something powerful enough to decode the content. I believe Intel are working on Linux apis to provide hardware assisted decoding (what I'm waiting for)

---

