---
title: "Firefox Problem"
date: 2005-06-29
forum: General Help
---

### Post by Cerbz on 2005-06-29
I have a problem with firefox. I go to the theme and extension page but i cant access it due to my firefox apparently being out of date. Here is something written on that page..


"Firefox on Ubuntu

You appear to be using the Firefox package provided by Ubuntu Linux. Ubuntu distributed a new version of Firefox which contains the security fixes from Firefox 1.0.4, however, they did not update the version number, so we have no way to tell whether your copy of Firefox contains the security fixes or not. A request to Ubuntu to update the version number has been filed at Ubuntu Bug 10681. A workaround you can use to get access to addons.mozilla.org is given in comment 3 on that bug. Please ensure you have updated to the latest Firefox package using apt-get, Synaptic, or the Ubuntu Update Manager before trying the workaround."

I'm pretty sure i have the correct version of firefox installed, but i may not have? How do i check apart from going to the help tab in firefox? I wanna get themes and extensions but i cant get to the page :( Thanks for anyone who helps me!

---

### Post by Lunde on 2005-06-29
[QUOTE=Cerbz]I have a problem with firefox. I go to the theme and extension page but i cant access it due to my firefox apparently being out of date. Here is something written on that page..


"Firefox on Ubuntu

You appear to be using the Firefox package provided by Ubuntu Linux. Ubuntu distributed a new version of Firefox which contains the security fixes from Firefox 1.0.4, however, they did not update the version number, so we have no way to tell whether your copy of Firefox contains the security fixes or not. A request to Ubuntu to update the version number has been filed at Ubuntu Bug 10681. A workaround you can use to get access to addons.mozilla.org is given in comment 3 on that bug. Please ensure you have updated to the latest Firefox package using apt-get, Synaptic, or the Ubuntu Update Manager before trying the workaround."

I'm pretty sure i have the correct version of firefox installed, but i may not have? How do i check apart from going to the help tab in firefox? I wanna get themes and extensions but i cant get to the page :( Thanks for anyone who helps me![/QUOTE]
 OK if you have the latest version of Firefox from ubuntu:

In the message you just posted here, there is refered to a comment 3, here it tells you how to fix this bug. You only have to type in the 1.04 version number in the firefox config. 

This bug is listed here:
[https://bugzilla.ubuntu.com/show_bug.cgi?id=10681](https://bugzilla.ubuntu.com/show_bug.cgi?id=10681)

Comment 3:
Setting general.useragent.vendorSub to 1.0.4 in about:config seems to let me
access addons.mozilla.org

---

### Post by Lunde on 2005-06-29
[QUOTE=Lunde]OK if you have the latest version of Firefox from ubuntu:

In the message you just posted here, there is refered to a comment 3, here it tells you how to fix this bug. You only have to type in the 1.04 version number in the firefox config. 

This bug is listed here:
[https://bugzilla.ubuntu.com/show_bug.cgi?id=10681](https://bugzilla.ubuntu.com/show_bug.cgi?id=10681)

Comment 3:
Setting general.useragent.vendorSub to 1.0.4 in about:config seems to let me
access addons.mozilla.org[/QUOTE]
 Sorry, forgot to tell you how to do this. open Firefox, in the address bar type
**about:config **

I big list of configurations will show in the main window, in search type in:
**general.useragent.vendorSub**

Doubble click and set the value to 1.0.4 instead of 1.0.2

Have fun

---

### Post by Cerbz on 2005-06-29
[QUOTE=Lunde]Sorry, forgot to tell you how to do this. open Firefox, in the address bar type
**about:config **

I big list of configurations will show in the main window, in search type in:
**general.useragent.vendorSub**

Doubble click and set the value to 1.0.4 instead of 1.0.2

Have fun[/QUOTE]
 Thank you, you have helped me solve my problem!! :D These forums are dead helpfull. thankyou lots ^_^

---

### Post by Lunde on 2005-06-29
[QUOTE=Cerbz]Thank you, you have helped me solve my problem!! :D These forums are dead helpfull. thankyou lots ^_^[/QUOTE]
 No problem, glad to help..

---

