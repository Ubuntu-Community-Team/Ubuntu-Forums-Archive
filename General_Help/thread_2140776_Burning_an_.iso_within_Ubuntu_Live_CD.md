---
title: "Burning an .iso within Ubuntu Live CD"
date: 2013-04-30
forum: General Help
---

### Post by AmigaMind on 2013-04-30
I am trying to help a friend burn an .iso image (antivirus boot cd). He is using an Ubuntu 12.10 live CD on a Win-7 virus-infested laptop. Right-clicks on the .iso and write to disc, inserts the blank dvd and presses Burn, but he reports errors or inability to proceed (he's a total noob and on the phone, we can't do much). Is it possible to do this? I am thinking maybe Ubuntu relies on the live CD and when that is ejected, problems might arise.

---

### Post by CaptainMark on 2013-04-30
Yes, you've answered your own question.
Imagine it akin to removing your hard drive whilst running your normal operating system. You'll have to use a live usb to allow yourself access to the cd drive in a live session [https://help.ubuntu.com/community/Installation/FromUSBStick#live-usb](https://help.ubuntu.com/community/Installation/FromUSBStick#live-usb) or [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-window]("http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows")

---

### Post by ajgreeny on 2013-04-30
Or if that is not a possibility, if the computer will not boot from a USB, try downloading and using a live CD of puppy linux.

Puppy runs entirely from ram, and once booted, allows the live CD to be ejected, freeing the drive for burning an .iso image if wanted.  There may be other small sized live linux systems that can do the same, but puppy is the only one I know and have used in the past.

---

### Post by Impavidus on 2013-04-30
And to do that he would need to make a puppy live cd, and if he could do so he could as well make the anti-virus cd directly. I think he needs access to a second computer. Or an external cd burner, if he has one. Unless he can use the ubuntu live cd to burn the anti-virus .iso to usb and boot from usb.

---

### Post by AmigaMind on 2013-05-01
Many thanks for your helpful and interesting answers. I think the laptop can boot from USB so we will try that. Is a USB-installer included in the Ubuntu live CD? Most "how to create a Linux live-usb" guides I see online, talk about doing it within Windows. Same is true about the Avira rescue CD .iso he has, it seems a usb can only be created from Windows.

**edit: **ok, I saw it can be done from Ubuntu on CaptainMark's link.

---

