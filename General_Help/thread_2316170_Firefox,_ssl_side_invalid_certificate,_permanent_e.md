---
title: "Firefox, ssl side invalid certificate, permanent exception"
date: 2016-03-05
forum: General Help
---

### Post by kaweka on 2016-03-05
Searching for firefox AND exception matches in hundreds of irrelevant findings.
Problems described here were not seen in no of known Windows based Firefox installations,
so from this perspective the reason seems to be located in Ubuntu, not Firefox.

For SSL URLs secured by a private certificate (certificate not issued by recognized certification centre)
- "Your connection is not secure" - Firefox offers to use an exception, it offers to save that exception non-volatile (self-signed sides)
- Advanced > Add Exception > Permanently store this exception. 
The option of permanently storing exception do not never work.
Every time the exception must be done again.
Ubuntu 15.10 64Bits Desktop.

Ubuntu 14.04 does not offer exception permanently storage at this moment. No idea why.

---

### Post by howefield on 2016-03-05
Moved to the "*General Help*" forum.

---

### Post by pissedoffdude on 2016-03-05
Hi,

Is it actually adding it to the firefox trust store, or does it just proceed to let you view the page?  Head over to the settings next time this happens and check the list of trusted CA certs for the self-signed cert.  If it's not in there, does manually adding it as a trusted ca cert work after restart?  If there's still an issue after manually adding it as a CA cert, try on the latest firefox and file a bug report with mozilla if it's present in the latest release

---

### Post by kaweka on 2016-03-06
Affected site is a device in local network, a modem/switch/router/wifi/etc combo.
If to open Firefox Preferences > Advanced > Certificates > View Certificates it is  listed on Servers list,
lifetime permanently, expires never.
Despite this every time a administration page of this device is opened the message as
described in initial post is displayed and user has to activate the exception.

---

### Post by kaweka on 2016-03-06
Well, exception addition seems to work if to do it from Firefox Preferences > Advanced > Certificates > View Certificates > Servers > Add Exception...
After Firefox restart and url reopening it is no more alerting about invalid certificate  and no more asking for exception creation.
It does not work if the enquires are made by Firefox on url opening.

---

### Post by pissedoffdude on 2016-03-07
Is there a button to "permanently store this exception." I tried on my end with the latest firefox but wasn't able to reproduce this.  If you're checking that for sure, try on the latest version, as it could be a bug in whatever version of firefox you're using.

[ATTACH=CONFIG]267686[/ATTACH]

---

### Post by kaweka on 2016-03-08
Thanks for your proposal. Yes ,this tick filed is present and checked every time.

In the meantime new conclusions. One day after my last report it turned out, even the manual setting in Firefox Preferences does not help. The system new start next day and
the effect is back, Firefox is alerting and asking for exception allowance. Our another Ubuntu virtual machine, 14.04LTS, shows this too. We get confronted with the problem for long time.

Reg. used Firefox versions, we use only those offered by Ubuntu package management. Recommended and security updates only are enabled. Rest is disabled.
I refrain from back porting newer Firefox version as I am not practised in doing that (no knowledge, no experience).

---

### Post by Habitual on 2016-03-08
Wednesday 24 Feb 2016 had a ca-certificates update. Maybe it affected the certificate.

---

### Post by kaweka on 2016-03-09
However, we are confronted with these problems since several years ago.

---

### Post by pissedoffdude on 2016-03-12
You can get the latest from [https://www.mozilla.org/en-US/firefox/new](https://www.mozilla.org/en-US/firefox/new), create an apps folder in your home directory, unpack it there and run the executable.  This method also allows firefox to auto update itself as it does on Windows and Mac

---

### Post by kaweka on 2016-03-13
Please apologize my asking for purpose of your proposal. I see two.
1) Firefox installed in special folder might use own settings, not the Ubuntu specific, stuff might work better
2) New version new luck 
If latter applies please note, we confronted with this problem since several years ago. Firefox on this machine got lot of updates 
that time. No one helped. I don't understand why should the update last from current point of view help.

---

### Post by kaweka on 2016-06-24
Firefox does still lose the setting to save the exception non-volatile. 
Every time the router's  gui url is opened in Firefox one has to activate the exception to accept non-verified certificate.
Selecting the option "remember this exception" does not help.

---

