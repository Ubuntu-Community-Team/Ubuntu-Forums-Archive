---
title: "Cisco WebEx screen sharing not working since Ubuntu 14.04 upgrade"
date: 2014-04-28
forum: General Help
---

### Post by crooked_smile on 2014-04-28
Hello all,

Back when I was running Ubuntu 13.10 x64, I was able to participate in Cisco WebEx sessions, including the ability to view others desktops and share my own, by installing the following packages:

openjdk-6-jre
icedtea-6-plugin
libxmu6:i386
libgcj12-awt:i386

Since moving to a clean install of Ubuntu 14.04, it appears I've lost many of these functions. I'm able to join sessions, but can't see the participants' desktops or share my own any more. 

I'm able to install all but the libgcj12-awt:i386 package, as it appears it's been pulled from the Ubuntu repositories:

[https://launchpad.net/ubuntu/trusty/i386/libgcj12-awt](https://launchpad.net/ubuntu/trusty/i386/libgcj12-awt)

I believe this missing package is what's breaking WebEx on Ubuntu 14.04 x64.

Anyone else having similar issues? Is there a workaround available to let me get these features working on 14.04? Thanks!

---

### Post by matt.lawrence on 2014-04-29
What browser are you using? Or are you using a desktop app?

---

### Post by crooked_smile on 2014-04-29
I'm using Firefox 28.0. Starting/ joining WebEx sessions launches the WebEx Java applet independent from my browser, it seems, which is how it worked back in 13.10. My only issue is not being able to see shared desktops or share my own. Everything else seems to be working ok.

---

### Post by mark-markciecior on 2014-04-29
I'm having the same issue with WebEx since I upgraded from 12.04 to 14.04 last week.  I can join meetings, but no additional windows appear, including Audio information, shared desktops/apps, etc.

---

### Post by mark-markciecior on 2014-05-01
I resolved this by installing this package: libgcj14-awt:i386

[https://launchpad.net/ubuntu/trusty/i386/libgcj14-awt](https://launchpad.net/ubuntu/trusty/i386/libgcj14-awt)

---

### Post by crooked_smile on 2014-05-01
Hmm, still not working for me after installing libgcj14-awt. To be clear, I've installed the following packages:

openjdk-6-jre
iceatea-6-plugin
libxmu6:i386
libgcj14-awt:i386

and still have the same issues: Can join WebEx sessions, can't see shared desktops or share my own.

Can you explain what exactly you did to get it working on your install?

---

### Post by mgieparda on 2014-05-26
Hello,

I have the same issue and cannot resolve it... Did you solve it somehow?

regards,
M.

---

### Post by Habitual on 2014-05-26
When I have trouble with WebEx, I usually just rm ~/.webex and re-launch the browser.
Seems to do the trick for me.

---

### Post by crooked_smile on 2014-05-30
> **Habitual said:**
> When I have trouble with WebEx, I usually just rm ~/.webex and re-launch the browser.
Seems to do the trick for me.

Nope, I just tried it and same issues as before. I've for the meantime just gotten around this issue by running WebEx sessions through a Windows VM, which really sucks but honestly there's much else I can do. It's a shame because in 13.10 it worked perfectly fine.

If someone has been able to get this working properly under 14.04, PLEASE post a step-by-step guide on what you did to make it work!

---

### Post by regis-sarle on 2014-06-10
Hello,

Did you resolve this issue ? I am experiencing the same problem.

Thanks.

---

### Post by LostShootingStar on 2014-06-17
This worked for me on 14.04. I remember doing something similar in 13.X but I guess you have to do it again.

[http://linuxsagas.digitaleagle.net/2014/02/07/webex-on-64-bit-ubuntu-13-10/](http://linuxsagas.digitaleagle.net/2014/02/07/webex-on-64-bit-ubuntu-13-10/)

---

### Post by crooked_smile on 2014-06-19
> **LostShootingStar said:**
> This worked for me on 14.04. I remember doing something similar in 13.X but I guess you have to do it again.

[http://linuxsagas.digitaleagle.net/2014/02/07/webex-on-64-bit-ubuntu-13-10/](http://linuxsagas.digitaleagle.net/2014/02/07/webex-on-64-bit-ubuntu-13-10/)

Wow! This actually worked for me! I was able to track down the missing packages using the linked guide, installed them, and was finally able to share and see shared desktops. Thank you!

In case anyone is wondering, I was required to installed these additional packages to finally get everything working:

libpangoxft-1.0-0:i386
libxv1:i386
libpangox-1.0-0:i386 

Again, thank you! I can finally remove one more need for my Windows VM.

---

### Post by mehturt on 2014-10-27
Thanks, I needed to do the same!

---

