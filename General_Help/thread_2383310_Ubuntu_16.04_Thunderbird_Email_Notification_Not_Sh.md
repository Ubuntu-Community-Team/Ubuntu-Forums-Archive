---
title: "Ubuntu 16.04 Thunderbird Email Notification Not Showing"
date: 2018-01-23
forum: General Help
---

### Post by anspectrum on 2018-01-23
Hello,

I am using Ubuntu 16.04 and Thunderbird 52.5.0. I have a Microsoft Exchange Account created in there through ExQuilla Add-On and its working awesome.

However, when I receive Email, I do not get The Email icon in the Notification area to be turned to Blue. It just stays the same (white). Moreover once I click on the icon (Envelope) it does not show me any Unread messages link. I have searched for this particular issue with solutions ranging from changing config Editor to installing different Add Ons. In all honesty, I am not into installing any Add On if basic functionality is already built-in. I've enabled the settings for "Show an Alert when New Mail Arrives". **Can someone point out how to get that envelope icon turn to blue upon reception of new email ?**

P.S. I've also put in filters which immediately MOVE the new Email arriving into my Exquilla Account to Local Folders as the Email Account does not have much capacity at the server level.

Thanks.

---

### Post by anspectrum on 2018-01-28
bump.

---

### Post by anspectrum on 2018-02-04
Ok so here is the update.

I installed VM for Ubuntu 18.04 (Bionic Beaver) daily build just to get the feel of this upcoming release and tried to test my Exquilla Account in there. With same Email Move settings. And it worked flawlessly. Even if the Emails are moved to Local Folders the Email notification icon (envelope) stays blue as long as you don't read the email. I am sure it has to do something with the indication applet but don't know how to fix it.

Any thoughts ???

---

### Post by anspectrum on 2018-02-04
The Thunderbird version that is pre installed in Ubuntu 18.04 (64-bit)  is 52.6. I upgraded my Ubuntu 16.04 (32-bit) thunderbird from 52.5 to  52.6 but the problem is still there. Interestingly, in preferences there  is difference in the options "When New message arrives". Here are the  two screenshots.

32-bit SS:   [https://i.imgur.com/TgQgyVv.png](https://i.imgur.com/TgQgyVv.png)

64-bit SS:   [https://i.imgur.com/p3O17kW.png](https://i.imgur.com/p3O17kW.png)

---

### Post by anspectrum on 2018-02-06
After continuously analyzing and testing I have been successfully able  to diagnose and fix the issue. Here is what you need to have.

1. Thunderbird Addon "Messaging Menu and Unity Launcher Integration" should be installed and Enabled. (Mine was already there)

2.  Thunderbird package "thunderbird-gnome-support" should be installed.  (Mine was missing. After installing and restarting TB now my envelope  turns blue for new unread Emails [IMG]http://forums.mozillazine.org/images/smilies/icon_razz.gif[/IMG])

Hopefully someone might find this useful.

Cheers.

---

