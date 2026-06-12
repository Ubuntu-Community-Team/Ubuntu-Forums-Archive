---
title: "chromium stopped loading https websites"
date: 2014-04-22
forum: General Help
---

### Post by Vedelaar on 2014-04-22
Hello,

Chromium worked until yesterday perfectly, but now, when I try to load an https site, it does not load it.
Other sites work good.

When starting it from the terminal, the errors I get are:

```
[772:802:0422/115717:ERROR:nss_util.cc(750)] After loading Root Certs, loaded==false: NSS error code: -8018
[902:902:0422/115717:ERROR:nss_util.cc(750)] After loading Root Certs, loaded==false: NSS error code: -8018
NVIDIA: could not open the device file /dev/nvidia0 (Operation not permitted).
NVIDIA: could not open the device file /dev/nvidia0 (Operation not permitted).
NVIDIA: could not open the device file /dev/nvidia0 (Operation not permitted).

```

google did not help much with the errors.

Any ideas on how to fix the https problem?

I tried to create a new user account in ubuntu and then run chromium, that works fine, so it must be something in my profile/home directory...

I run 12.04

Thanks

---

### Post by TheFu on 2014-04-22
I used chromium this morning trying to log into 3 websites.  My cell provider to change plans and a brokerage.  The cell provider didn't work. I could see the page, but was never able to login.  Tried Firefox and had the same issue.  Tried visiting a related website (same company @ [www.co.com](www.co.com)) and that failed too.  Inconvenient for me. Often, problems like this are on the server-side, not ours.  15 min later, the login worked.  

The login to the brokerage worked fine from the start in chromium.

Ok ... so if everything isn't working now "magically", looking at those errors leads me to a graphics driver issue, assuming you even have an nvidia GPU.  The root cert errors could be related to many, many, many certificates being revoked recently thanks to the [heartbleed bug]("http://arstechnica.com/security/2014/04/how-heartbleed-transformed-https-security-into-the-stuff-of-absurdist-theater/") in openssl.  So ... please ensure that your system is 100% updated and patched before doing anything else. 

If that doesn't solve it, you can move the ~/.config/chromium to ~/.config/chromium-old and start over with a new profile for that app. If you'd like to retain any settings like bookmarks, it is likely those are stored in a file and a file-based DB under there too.

BTW - I'm running 12.04 on almost all my machines too. I think that is an excellent choice for about another month. Then it is a second choice behind 14.04 (released last week). It will take me at least 18 months to migrate from 12.04 --> 14.04, so there isn't any real hurry, yet.  Heck, I'm still running (2) 10.04 servers which are fully patched and supported. THAT is the reason for LTS releases.

---

