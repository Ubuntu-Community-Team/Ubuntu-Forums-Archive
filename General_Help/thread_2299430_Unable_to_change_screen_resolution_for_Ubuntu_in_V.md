---
title: "Unable to change screen resolution for Ubuntu in VirtualBox"
date: 2015-10-18
forum: General Help
---

### Post by dave_h2 on 2015-10-18
This has happened through multiple versions and installs of Ubuntu on VirtualBox for Windows (7 in my case), and when I boot up, the screen resolution is too small and I've found no way to increase it; if I go to Settings in Ubuntu, I can only choose 640x480, any other resolutions are grayed out or not selectable. Here's the best screenshot I could get (I had to have a Windows Explorer window open and tucked away to get a full screenshot as tapping the PrintScrn button on my laptop just takes a screenshot in Ubuntu):

[IMG]http://imgur.com/i6bYjp6[/IMG]

Link to screenshot in case Insert Image doesn't work: [http://imgur.com/i6bYjp6](http://imgur.com/i6bYjp6)

---

### Post by jim_deadlock on 2015-10-18
It's most likely because you don't have Guest Additions installed. Right-click on the CD icon at the bottom of the Vbox window and make sure VboxGuestAdditions.iso is enabled, then install Guest Additions via the Devices menu on the Vbox window. Reboot the guest and you should then have more resolution choices.

---

### Post by dave_h2 on 2015-10-18
OK I did install Guest Additions and it worked, but I don't get why I have to do this now when I don't remember having to do it before.

---

### Post by josh166 on 2016-02-25
> **dave_h2 said:**
> OK I did install Guest Additions and it worked, but I don't get why I have to do this now when I don't remember having to do it before.

I had the same issue. This isn't that big of a deal for intermediate or expert users, but new ubuntu users deserve to have the ability to change their screen resolution out of the box.

---

### Post by QIII on 2016-02-25
This is an issue you will need to take up with Oracle or ask about at virtualbox.org.  Canonical does not maintain or develop VirtualBox.

---

### Post by SeijiSensei on 2016-02-25
The Extension Pack, as the "Guest Additions" are now known, contains some items that are proprietary and are not licensed under the General Public License that covers VirtualBox.  USB support is one such item, since USB technology is patented.

---

