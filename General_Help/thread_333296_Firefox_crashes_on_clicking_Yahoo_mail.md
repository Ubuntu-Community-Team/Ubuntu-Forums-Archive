---
title: "Firefox crashes on clicking Yahoo mail"
date: 2007-01-07
forum: General Help
---

### Post by satimis on 2007-01-07
Hi folks,

Ubuntu-6.06.1-LAMP-server-amd64
Xfce4 desktop

After login Yahoo website and clicking mail Firefox crashes.  This happened after running "apt-get update" and then "apt-get update".  It seems only happening on Yahoo website.

Tried starting Firefox on terminal as user.  It also crashed on clicking "mail" with a warning "segmentation fault".

Please advise how to fix this problem.  TIA

B.R.
satimis

---

### Post by louistan3 on 2007-01-07
hmm,

mine used to crash with yahoo too.. but it was coz of flash player.. maybe you should check if sumthns wrong with ur flash.. :)

hope this helps..

---

### Post by satimis on 2007-01-07
> **louistan3 said:**
> hmm,

mine used to crash with yahoo too.. but it was coz of flash player.. maybe you should check if sumthns wrong with ur flash.. :)

hope this helps..
Hi,

Tks for your advice.

IIRC I haven't installed Flash.  However before Firefox worked on Yahoo website without problem.  Problem only happened after running "apt-get update and upgrade".  Besides crash only happens on clicking the mail link, other links w/o problem

B.R.
satimis

---

### Post by brainlag on 2007-01-08
I had the same problem and it was flash related. It was a real pita!!

A solution I found here, but can't seem to find now, was changing color depth to "24".

/etc/X11/xorg.conf

near the bottom: 

> Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82915G/GV/910GL Express Chipset Family Graphics Controller"
	Monitor		"EN7750"
	DefaultDepth	16



change to
> 
Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82915G/GV/910GL Express Chipset Family Graphics Controller"
	Monitor		"EN7750"
	DefaultDepth	**24**



I really hope that helps you.

---

### Post by rdoolen on 2007-01-08
I have the same problem when I load the login page for gmail. Firefox crashes with a 'segmentation fault' error. It works on a new pfofile, but if I sync the new profile using the Google browser sync extention it crashes agian. So, it seems to be caused by some that syncs. Maybe that could give you a hint on where the problem is.

I am using the Firefox version 1.5.0.9 with Ubuntu 6.06.

---

### Post by satimis on 2007-01-08
Hi brainlag,

Tks for your advice.

Herebelow is on /etc/X11/xorg.conf
```

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-64
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV43 [GeForce 6600]"
        Monitor         "Generic Monitor"
        DefaultDepth    24

```
I have Philips 190B LCD display.  I tried changing;
```

Herebelow is on /etc/X11/xorg.cong
[code]
Section "Monitor"
        Identifier      "Philips 190B"
        Option          "DPMS"
        HorizSync       28-64
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV43 [GeF"orce 6600]"
        Monitor         "Philips 190B"
        DefaultDepth    24

```
Restarted Xfce4 and Firefox.  Firefox still crashed on clicking yahoo mail.

B.R.
satimis

---

### Post by satimis on 2007-01-08
Hi rdoolen,

Tks for your advice.

The amaizing here is clicking other links on Yahoo.com Firefox did not crash.  Only clicking Yahoo mail then Firefox crashed.

I am also running Firefox version 1.5.0.9.


B.R.
satimis

---

### Post by el_baby on 2007-01-09
I'm having the same problem... I think it started after upgrading firefox to 1.5.0.9 (I'm using Dapper)... I'l try uninstalling flash when I get back home...

FWIW,  Mine crashes when it's trying to open the login verify screen in Yahoo! Mail...

---

### Post by rdoolen on 2007-01-09
I read in an other forum that Firefox for Ubuntu Dapper (6.06), version 1.5.0.9 causes Firefox to crash when using a saved password field on a Mailman admin login screen. 

[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/77859](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/77859)

There is a patch, but it is beyond my skills to understand or apply it. I am going to live with it and hope they fix and update Firefox soon. If it get too annoying, I will either downgrade to 1.5.0.8 or upgrade to 2.x

Hope this helps.

---

### Post by el_baby on 2007-01-09
Thanx for the pointer, rdoolen.

This is exactly what's happening to me... the patch at [https://bugzilla.mozilla.org/attachment.cgi?id=185577](https://bugzilla.mozilla.org/attachment.cgi?id=185577) is not for mortals (like you and I)... you have to have a complete development environment, get the original source package, apply the patch, recompile and repackage (i.e. generate the binary .deb)...

What's more... this patch is for an old version of firefox... I'd definitively leave this to the package maintainers... If this gets annoying enough, I'll either disable stored passwords (and try to overcome my Alzheimer) or downgrade to 1.5.0.8... for now, I'm reading Yahoo! mail with Opera :)

Regards.

---

### Post by fortran01 on 2007-01-10
I got the crash when I cleared my cache and I have to relogin to Gmail. I have a saved password for Gmail. Firefox crashes after it loads the Gmail login page. So I deleted the saved password for Gmail, then went back to Gmail login page. This time it did not crash. I think this is a problem with saved passwords as mentioned in some bug reports. HTH

I am using Firefox 1.5.0.9 in Ubuntu Dapper.

---

### Post by robertinvanc on 2007-01-11
My first Linux post (!).  I am having the same problem (crashing) on Yahoo and I think it happened after I selected "remember password";  I don't have this problem with Gmail although I have noticed that recently Firefox frequently logs me out of Gmail whereas before it would remember me.

---

### Post by Stryker777 on 2007-01-11
I installed 2.0.0.1 and it runs fine.  Here are the instructions if anyone wants to try
[http://kb.mozillazine.org/Installing_Firefox](http://kb.mozillazine.org/Installing_Firefox)

---

