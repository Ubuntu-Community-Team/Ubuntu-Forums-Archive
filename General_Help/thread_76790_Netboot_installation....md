---
title: "Netboot installation..."
date: 2005-10-15
forum: General Help
---

### Post by cheuschober on 2005-10-15
Hi all! First foray into linux so be gentle, please.

I had several half-successful and a few unsuccessful installation attempts off my ubuntu .iso but the cd/dvd-rom on my toshiba A45-S130 has been dying for over half a year now and it's showing - every installation has had some kind of error. If that isn't enough this computer doesn't boot from my usbdrive so I've spent the better part of my day (devoted as I am to trying to get this to work) figuring out how to get a netboot installation going from my second pc (WinXP Pro media center).

I've finally gotten my windows pc talking with my laptop and started the installer (all as described in the [Installation / Server Netboot Wiki]("https://wiki.ubuntu.com/Installation/WindowsServerNetboot"))

Unfortunately, now I'm running into a huge issue with being incapable of select an 'archive mirror' as directed by the installation engine, or rather, I can select one but always receive a 'Bad archive mirror' error. Now I'm typing on my windows pc right now so I can obviously access the net, and I don't have any proxy (though I do have two daisy-chained routers, but that shouldn't affect this and I really don't have an option on that end).

I've tried the mirrors list for cd images (as found in the [Archive Wiki]("https://wiki.ubuntu.com//Archive")) using the following format (each screen's text is included for identification and I have tried multiple mirrors, this is just an example)```
Please enter the hostname of the mirror from which Ubuntu will be downloaded. An alternate port can be specified using the standard [hostname] : [port] format.

Ubuntu archive mirror hostname:

**ubuntu.mirrors.tds.net**
```

and the following...

```
Please enter the directory in which the mirror of the Ubuntu archive is located.

Ubuntu archive mirror directory:

**/releases/**
```

and finally...

```
If you need to use a HTTP Proxy ... (left this one blank)
```

The official error returned is:
```
Bad archive mirror
The specified Ubuntu archive mirror is either not available, or does not have a valid Release file on it. Please try a different mirror.
```

Does anyone have an idea of what the problem could be, or a possible alternate solution? I do have room enough on my other server... is there a method whereby I could locally host the necessary installation files?

Any and all help is greatly appreciated!
~C

---

### Post by arctic on 2005-10-15
can you ping the web-address of the server you are contacting from your yoper installation anyhow?

---

### Post by cheuschober on 2005-10-15
Well ping isn't available to the command shell of the installation dialogue (or is it ? maybe I didn't find it?), but I can certainly do so from my media server...

I've suspected that maybe it's not communicating over the internet but I've disabled all my firewalls and given it about as clear a path as it could hope for.

Thanks,
~C

---

### Post by cheuschober on 2005-10-15
Okay, got it fixed but just for anyone who runs into the same, the Netboot Installation Wiki recommends not touching the WINS/DNS settings of Tftpd32 (which default to 0.0.0.0) but they have to be enabled and set--I thought it was a little odd. In most cases gateway-driven home networks your DNS server is your gateway address. So there you have it - hope this can help someone else!

~Chad

---

