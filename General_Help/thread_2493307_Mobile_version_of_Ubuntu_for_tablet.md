---
title: "Mobile version of Ubuntu for tablet"
date: 2023-12-11
forum: General Help
---

### Post by robert48 on 2023-12-11
Hello

I have read a lot of posts regarding 'mobile Ubuntu' which are all old.

Can you you tell me where we are (or not) with Ubuntu for mobile devices please?

I am currently running Android 12 on a tablet and the intrusion by Google is very alarming. I would like to wipe the device and load an os on it that does not want to control my life. I have been using the 64bit version of Ubuntu on a PC for years now. Thank you very much for that.

Robert

---

### Post by MAFoElffen on 2023-12-11
Just opinion. I would say Ubuntu, but with gnome-sessions as the DE. Very touchscreen friendly.

---

### Post by dragonfly41 on 2023-12-12
Since we are often pestered to install various apps (I do not use smart phones although we have an old Galaxy Tab mainly for ebooks) I looked around recently, exploring how to run Android within Ubuntu 20.04.

[https://www.howtogeek.com/760044/how-to-run-android-apps-on-linux/](https://www.howtogeek.com/760044/how-to-run-android-apps-on-linux/)


snap install --devmode --beta anbox


[https://askubuntu.com/questions/1732/can-i-run-android-apps-on-ubuntu](https://askubuntu.com/questions/1732/can-i-run-android-apps-on-ubuntu)

I have to say that anbox does launch but sits there dumb. I have not taken the experiment further but I intend to explore further how to install Android as a layer. But OP wants Ubuntu to run on Android tablet, I see.  I am pursuing Android on top of Ubuntu. Emulating tablet.

---

### Post by DuckHook on 2023-12-12
Ubuntu on a tablet is very hard to set up. I consider myself something of a power user, but I gave up on a number of different Samsung tablets after days of fruitless and cussed effort.

I hear you (and sympathize) about Android. Others have reported decent results with Librem and LineageOS. I have no idea if they will install on your tablet. Here's a link to some of the different alternatives: [https://itsfoss.com/open-source-alternatives-android/](https://itsfoss.com/open-source-alternatives-android/)

Plasma Mobile looks interesting as do a few others, but I have no idea if they work, how they work, or what problems/issues they might present.

---

### Post by Irihapeti on 2023-12-12
Samsung can be especially painful because it's got its own system for installing custom ROMs, unlike the rest of the Android world. Be aware also that recent Samsung bootloaders may make customisation completely impossible. (See xda forums for details.)

Depending on what model your tablet is, you might get lucky and discover that it will run lineageOS, or at least a GSI ROM. And if you're really adventurous/lucky, you might even find that it will run postmarketOS, which is a genuine Linux, not an Android variant.

Personally, my approach has been to get a x86_64 tablet and run bog-standard Ubuntu on it. I think there are also fairly standard ARM tablets out there, but I have no idea what they're like.

---

### Post by grahammechanical on 2023-12-12
The version of Ubuntu that you want is called Ubuntu Touch. It is no longer under development. It progressed to the point of a Chinese company releasing a tablet with Ubuntu Touch on it but the company discontinued production of the tablet. At that point Canonical discontinued development of the Ubuntu Touch operating system.

A group of developers took up the challenge of porting Ubuntu Touch on to various smartphones with a certain amount of success. They are call ubports.

[https://ubports.com/](https://ubports.com/)

These are the devices that they have had some success in getting working.

[https://ubuntu-touch.io/en_GB/get-ubuntu-touch](https://ubuntu-touch.io/en_GB/get-ubuntu-touch)

It is all experimental.

Regards

---

### Post by DuckHook on 2023-12-13
> **Irihapeti said:**
> Samsung can be especially painful…
Thanks Irihapeti. Did not know this about Samsung. Just like me to choose the worst HW to try something like this.

---

### Post by deadflowr on 2023-12-13
I put the ubports ubuntu-touch on an old nexus 7 2013, now a legacy device.
They have a snap package installer for it.
Easy to use.
Note that you may need to clear the cache or else it might bork the install. No OS, complete crash.
That's what happened to me so I had to find some compatible android rom then re-flash it and then clear the cache properly following some guide.
But once I cleared the cache it installed just fine.

Still have it, though the device is pure garbage so I cannot say if it's a good experience or not.
It works, so that's something.

---

### Post by Irihapeti on 2023-12-13
> **DuckHook said:**
> Thanks Irihapeti. Did not know this about Samsung. Just like me to choose the worst HW to try something like this.

That would depend on exactly which device it is. Devices before 2019 seem to be OK to modify. I have a 2019 Samsung 8in tablet which is currently running lineageOS, so it can be done. I think the big thing is to read, read, read before doing anything, even updating. So many of the individuals who get into difficulties seem to just rush into things and/or make assumptions. Anyway, this may be getting off-topic somewhat, so I'd better leave it at that.

---

### Post by DuckHook on 2023-12-13
> **deadflowr said:**
> It works, so that's something.
Something indeed!
> **Irihapeti said:**
> …Devices before 2019 seem to be OK to modify…
Okay, I have one or two older Samsungs laying around and may give them a try.

@OP

I actually don't have too many concerns about Android if it is strictly the FOSS version that has been detoxified of all the Google pollutants. The advantage to using Android instead of Linux proper is that Android is built for tablets while anything Linux&#8209;based has be be force&#8209;fitted into the form factor, with all of the attendant issues. Moreover, the app base for Android is far larger than that for portable Linux. If one sticks to F-Droid and just a few mainstream apps through Aurora, that is enough to bring in some amazingly useful apps for a pure Android experience with minimal tracking/privacy exposure. Not sure that you could get the same functionality using Linux (I know, I know… Android is Linux, but you know what I mean).

The problem that most people run into with Android is that they can't resist installing Google's ecosystem. Once you do that, you've given up the farm. But if you resolutely and strictly keep away from Google altogether, then Android is actually pretty good.

P.S. Also need to stay away from the OEM's ecosystem, so all of those Samsung applets and the store itself need to be nuked too. Pure Android doesn't have any of those either.

---

### Post by robert48 on 2024-02-20
Thanks for the advice. It has been a real struggle to pluck out Google from my Lenovo Tab P11 5G. I have a sim card in this one and I am still using Google Phone to make calls. The camera also has a life of it's own and won't let me save directly to Cx File Explorer. Can you recommend a phone app that I can keep my contacts free from Google surveillance?

---

### Post by DuckHook on 2024-02-20
I find 2 phone alternatives on F-Droid:

Welefon
Fossify Phone

Welefon claims that their phone app does not keep a separate contact database and just relies on the contact database already contained in your phone. I don't use either app, so cannot give you any guidance from personal experience. I do recall another very simple (i.e. primitive) phone app that I used to use, but can't find on the F-Droid store anymore. I assume that it has been dropped due to lack of support.

TBH, I use the phone app that comes with my phone. It tends to be the most properly integrated with the HW and gives me the fewest headaches. Every OEM swears up and down that their native app does not track you, but this is only as good as their word, which is suspect in most cases, especially so if you use some brand manufactured within a certain authoritarian nation state. Given this reality, Google Phone may be your best bet, as it at least carries the promise of a behemoth that has a lot to lose if they are caught outright lying to us. If you decide to give either of the above phone apps a try, please do report back to this thread. I for one would be very interested in your experiences.

I do not use Google for my contacts. I keep my contacts on my own Nextcloud database and access it via DAVx on Android. All of these platforms are available on F-Droid, but Nextcloud requires your own dedicated self&#8209;hosted server, which is a whole 'nuther level of commitment, maintenance and knowledge. Unless you are prepared to really geek out on your home setup, I do not recommend Nextcloud just for this.

You do not need Google for photo maintenance. Though I am unfamiliar with Lenovo (have never owned one) every brand of mobile that I've ever run across will store its photos locally and comes with its own gallery app. One of the other advantages of Nextcloud is that it allows synchronization of your phone photos/videos with your central server whenever you have a WIFI connection (hence acting as a fully featured Google Photos alternative). But again, this functionality should not be the driving force for installing Nextcloud. You can use other cloud based photo storage/mirroring services (though you will have to pay for such storage). Setting these up are far simpler than running your own Nextcloud instance.

---

