---
title: "Spyware"
date: 2008-05-30
forum: General Help
---

### Post by teixidoj on 2008-05-30
Could someone please recommend a good spyware program for Ubuntu?

---

### Post by kerry_s on 2008-05-30
there is no spyware in linux, none needed.

---

### Post by ibuclaw on 2008-05-30
Yep, spyware is a Windows-only phenomenon.

Although, Linux **can be a carrier** (You download a bunch of exes, only to find that they are really malicious binaries when you reboot into Windows).

Best choice to prevent that happening is clamav (UNIX version of clamwin). It's in the repositories.
```
sudo apt-get install clamav
```

Or if you prefer avast, there is also a Linux version for the app too.
```

wget http://files.avast.com/files/linux/avast4workstation_1.0.8-2_i386.deb
sudo dpkg -i avast4workstation_1.0.8-2_i386.deb
rm avast4workstation_1.0.8-2_i386.deb
cd /usr/lib/avast4workstation/share/avast/desktop
sudo ./install-desktop-entries.sh install

```
Then when you go into Applications>Accessories, a menu entry will be there.
It will ask you for a registration key, just enter in your current one and update the virus database.

Else, [go here for you free registration.]("http://www.avast.com/eng/home-registration.php#register-form")

Regards
Iain

---

### Post by LaRoza on 2008-05-30
> **tinivole said:**
> Yep, spyware is a Windows-only phenomenon.

Although, Linux **can be a carrier** (You download a bunch of exes, only to find that they are really malicious binaries when you reboot into Windows).

Best choice to prevent that happening is clamav (UNIX version of clamwin). It's in the repositories.
```
sudo apt-get install clamav
```

Technically, Clamwin is the Windows interface and version of Clamav.

You don't need it in general unless you are running some sort of file or mail server.

---

### Post by twright on 2008-05-30
basically while it is **technically** possible for ubuntu to be targeted by malware it is extremely unlikely

you might send viruses to other people by mistake though :)

---

### Post by Ioky on 2008-05-30
maybe I am an ignorant but I really wonder can you try to run a spyware with Wine? haha, I know that sound a be funny. and even it run, it still wouldn't do much because the architecture of Linux is difference from Windows but, really, what will happen if I run a spyware with wine, and wine actually allow the spyware work? haha

---

### Post by ibuclaw on 2008-05-30
That has already been tried and tested.

The worst thing that I have ever read from a virus in WINE is causing the system to slow down by 25-50%.

That is, until the person ran the command "**killall wine**"
Then it was stopped dead in it's tracks...

Viruses have been known to copy themselves in and around your home directory (If you are smart enough to have your home directory as one of your virtual WINE drives) and also in your main system (If you are smart enough to run the virus as root)!!!

But apart from that, there really is not damage done at all to your system. Viruses and Spyware are useless in Linux!!!

As for successfully spreading itself to other people through mailing accounts/etc.

That has so far proven not to work...

Regards
Iain

---

### Post by twright on 2008-05-30
still it is work backing up as while Ubuntu is immune to spyware it is not immune to failing hard drives

---

### Post by teixidoj on 2008-06-04
I probably ment tracking cookies like doubleclick.com and various others.

---

### Post by kerry_s on 2008-06-04
> **teixidoj said:**
> I probably ment tracking cookies like doubleclick.com and various others.

my cookies are not turned on, i've already setup a list of sites that can set cookies. i have mine set to ask, if i need a cookie from a site i turn it on, allow it, then turn cookies back off.(see pic)

everything else i use a hosts block list.

---

