---
title: "Need recommendation for contemporary browser on OLD ubuntu (xubuntu 16)"
date: 2023-09-26
forum: General Help
---

### Post by wb0gaz on 2023-09-26
I wish to find a contemporary browser that can be installed in an existing Xubuntu 16 based system (a repurposed chromebook.)  

An attempt to install current firefox version fails due to unmet dependencies.

Opera 40.0 did install and does run, but appears to have some javascript limitations/compatibility issues that make use inconvenient.

The system is currently using firefox 88 (which was the last version that appeared to directly support Xubuntu 16), however, wish to replace this if possible (likely high vulnerability exposure.)

Thanks for any advice (except for replacing the hardware or kernel, neither which are being considered at this point.)

Thank you

---

### Post by ne29914 on 2023-09-26
I expect you need a lightweight browser?
Firefox has become a resource hog.
Try Brave, use it myself.

---

### Post by QIII on 2023-09-26
Were I you, I would not risk using such an old version of Ubuntu on any machine that is connected to the web.  The risk of compromise is extremely high, no matter the browser.

I can't spend your money, of course, but I do *strongly* recommend a current release.  This is not only for your protection, but that of the community.  A compromising bot can cause problems for all netizens.

---

### Post by wb0gaz on 2023-09-26
ne22914 - thank you, I will investigate brave-browser

qiii - please re-read my original posting which specifically addressed your suggestion:
"Thanks for any advice (except for replacing the hardware or kernel, neither which are being considered at this point.)"

---

### Post by MAFoElffen on 2023-09-26
My recommendation? Upgrade to an OS that is in current support. If the Chromebook is 32bit, then Debian 32bit.

Ubuntu 16.04 LTS went EOL on 2021.04.30. 18.04 went EOL on 2023.07.31. Even if that machine is updated to it's last update before it lost support, then it hasn't had updates in about 2-1/2 years. 

FireFox will not update on it to current. And the web certs are out of date, so invalid. The OS itself hasn't had any security updates in over 2 years, so I would not risk going out to the internet with it.

I usually will support someone if they have a reason, like a old program that doesn't work on newer (ie, it was written on an early versio of something that didn't run on anything newer than Ubuntu 8.04), or a version of something that is no longer available (ie, OS for a development board)... I helped a municipality for a embedded system that had 14.04, and controlled Public Personal Monorails. Those all were on closed, open-gap systems... 

But for an every day user to play with a browser. No. That is just asking for troubles. I have to draw the line in the sand somewhere.

EDIT -- And yes I read your first post. I have adopted a saying (from a friend): "Just because something is possible, doesn't mean it's a good idea."

---

### Post by Frogs Hair on 2023-09-26
If Xubuntu was installed via [crouton]("https://github.com/dnschneid/crouton") your operating system choice may be limited. If not do as suggested in the previous post.

---

### Post by QIII on 2023-09-26
> **wb0gaz said:**
> qiii - please re-read my original posting which specifically addressed your suggestion:
"Thanks for any advice (except for replacing the hardware or kernel, neither which are being considered at this point.)"

Understood -- and I said I can't spend your money.  But my recommendations still stands.  Don't connect to the web with that release.

---

### Post by Dennis N on 2023-09-26
I have one Ubuntu MATE 16.04 in our computer museum. It's enrolled in the extended-support maintenance program, so still alive. There is hope there. It also has a lot of Flatpaks installed to get up-to-date software. However, if your system is 32-bit, I'm afraid there are no 32-bit Flatpak applications. The Flatpak Firefox is currently 118.0.

---

