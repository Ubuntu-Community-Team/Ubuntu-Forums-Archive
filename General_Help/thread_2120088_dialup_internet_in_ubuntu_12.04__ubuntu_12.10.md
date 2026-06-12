---
title: "dialup internet in ubuntu 12.04 / ubuntu 12.10?"
date: 2013-02-25
forum: General Help
---

### Post by ramidavis on 2013-02-25
I am going to be installing either 12.10, because it is newer, or 12.04, because it is a LTS release, on a laptop.
I have **only** dial up internet.
Can some one please tell me what i need to get online with either of those 2 versions for dial up? I plan to download what ever i need ahead of time, and then install them on the new system.
I am using a USRobotics usb modem right now under ubuntu 11.04 .
To get it working, i had to install the following, after downloading them in windows:
gnome-ppp_0.3.23-1_i386
libuniconf4.6._4.6.1-1ubuntu1_i386
libwvstreams4.6-base_4.6.1-1ubuntu1_i386
libwvstreams4.6-extras_4.6.1-1ubuntu1_i386
wvdial_1.61-2_i386

What would i need to download in order to get online with dial up in either 12.04 or 12.10?

---

### Post by grahammechanical on 2013-02-25
There is another way to do this. At least it will get you on-line after Ubuntu is installed. For Ubuntu already has a text based dialer that is installed by default on each version of Ubuntu. I can confirm that it is still in 13.04.

```
sudo pppconfig
```

[https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer]("https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer")

See the section

**Alternative Way 2 (using pppconfig & pon/poff)**

I used to use this method a few years ago before I get broadband and a wireless router. If you are not sure what 'device' to set the COM port as, try /dev/tty0. That worked for me.

Regards.

---

