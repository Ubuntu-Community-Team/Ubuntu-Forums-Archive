---
title: "picasa login in 14.04"
date: 2014-05-12
forum: General Help
---

### Post by kurja on 2014-05-12
I previously used 12.04 but have now 14.04, and I've used google picasa for browsing my photos for a long time, since the linux support got dropped I've had it on wine and it has worked just fine- until now:

I installed picasa and ie8 with wine, and both start and run as expected, but the picasa login just returns "there was a problem authenticating your account", it doesn't ask for my password or anything, just says that. Has anyone got this working in 14.04??

---

### Post by kumaryukuma on 2014-05-13
> **kurja said:**
> I previously used 12.04 but have now 14.04, and I've used google picasa for browsing my photos for a long time, since the linux support got dropped I've had it on wine and it has worked just fine- until now:


I installed picasa and ie8 with wine, and both start and run as expected, but the picasa login just returns "there was a problem authenticating your account", it doesn't ask for my password or anything, just says that. Has anyone got this working in 14.04??


I've been trying to get this to work as well... 


I've tried the following installation order:


1. Install WINE
2. Switch to 32bit
rm -rf ~/.wine
export WINEARCH=win32
wineboot --update
3. Install IE
4. Install Picasa


Using the following combinations:


WINE 1.4 with IE6
WINE 1.4 with IE7
WINE 1.4 with IE8


WINE 1.7 with IE6
WINE 1.7 with IE7
WINE 1.7 with IE8


WINE 1.8 with IE6
WINE 1.8 with IE7
WINE 1.8 with IE8


Between each tries, I've deleted the .wine directory.


Any comments would be much appreciated.

---

### Post by coffeecat on 2014-05-13
*Thread moved to **General Help**.*

---

### Post by kurja on 2014-10-12
I found this: [http://tsdgeos.blogspot.fi/2014/07/logging-in-into-picasa-39-under-linux.html](http://tsdgeos.blogspot.fi/2014/07/logging-in-into-picasa-39-under-linux.html)

> [FONT=Arial]when logging in, Picasa writes a few entries in HKEY_CURRENT_USER\Software\Google\Picasa\Picasa2\Preferences namely GoogleOAuth, GoogleOAuthEmail, GoogleOAuthServices and GoogleOAuthVersion, so I copied these over to the wine installation (with "wine regedit")[/FONT]

Maybe that will help some people. Better yet, maybe someone more knowledgeable can wield this information to come up with a solution for people who no not have windows ;)

---

### Post by Andrew_Young on 2014-10-27
"GoogleOAuth"=hex:12,7a,etc  66 2-digit hex numbers comma separated
"GoogleOAuthEmail"="my gmail email address"
"GoogleOAuthServices"="mail,lh2,cp,cp.manager,mailrelay,plus.stream.write,plus.circles.read,plus.profiles.read,plus.me,plus.media.upload,plus.media.readonly,plus.settings,youtube,"
"GoogleOAuthVersion"=dword:00000005


I hope this helps.

---

### Post by daniel224 on 2014-12-02
Hi, in my Windows past I have used Picasa and wanted to use it again on Ubuntu. 
I had the problem with logging in, but with this posts I was able to get Picasa to log in.
Unfortunately the next time I opened Picasa, the problem was back. Where to put the above mentioned settings in the register to have the system save this?

Is this possible, thanks in advance.
Daniel

---

