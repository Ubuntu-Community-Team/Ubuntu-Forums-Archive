---
title: "Linux that supports Broadcom"
date: 2007-11-24
forum: General Help
---

### Post by statue12 on 2007-11-24
Im just wondering if there is any version of linux that supports Broadcom wireless without having to configure it yourself.  I have installed linux but i am unable to get the wireless going tidy to get it going i got to put the lan cable into the laptop, then extract the fireware, take it out and the wireless will then work.  As soon as i restart it will go off and i will have to do the same again.

Thanks

---

### Post by HermanAB on 2007-11-24
Hmm, Ubuntu is not the easiest distro around.  It is middle of the road, so some things are a bit clunky or difficult and WiFi (actually ethernet networking in general) is one of those things that still needs a lot of work.

Mandriva has a ndiswrapper feature built into their networking wizard.  So provided that you have a Broadcom Windoze driver CD handy it is really easy to get to work:
[http://torrent.mandriva.com/public/](http://torrent.mandriva.com/public/)

Cheers,

Herman

---

### Post by AdamWill on 2007-11-26
Actually, the easy method on Mandriva does not use ndiswrapper (for Broadcom). It uses the native driver, bcm43xx. See:

[http://wiki.mandriva.com/en/Releases/Mandriva/2008.0/Notes#Required_firmware_for_Broadcom_wireless_adapters](http://wiki.mandriva.com/en/Releases/Mandriva/2008.0/Notes#Required_firmware_for_Broadcom_wireless_adapters)

This works great *so long as the particular Broadcom chipset you have works well with bcm43xx*. Some do, some don't. Ones newer than 4318, particularly, seem to have trouble with bcm43xx. If you have a newer Broadcom chipset that doesn't work well with bcm43xx, switching to ndiswrapper is not quite straightforward, and probably no easier than any other distro. Just a word of warning.

overall, it's rather difficult for distros to support Broadcom chips seamlessly. The problem is that you need a Windows driver. For ndiswrapper, obviously, the Windows driver is needed to work. For bcm43xx, it's needed to extract firmware the card needs. This firmware is under very tough license terms which make it impossible for any Linux distributor to legitimately redistribute it. So any distributor who has to respect licenses like this is basically forced to require the user to provide a Windows driver, one way or the other.

The only distros who can include the bcm43xx firmware and have it all working transparently are small community-based distros who choose not to care about the license for the firmware on the basis it's likely not worth Broadcom's time to chase them about it.

---

