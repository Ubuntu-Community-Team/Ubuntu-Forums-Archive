---
title: "Windows problems with firefox"
date: 2005-05-12
forum: General Help
---

### Post by bioS on 2005-05-12
Hi all,

I updated my Hoary install today, and noticed there was security updates related to firefox.

Since this update, I have problems with firefox as soon as it needs to open a window. For instance, the download window, the extensions window or the print window crash. It gives an XML error, saying it is not valid.

Any idea what is happening ?

Synaptic installation:
- firefox 1.02
- gnome-support
- locale-fr-fr

Installed extensions:
- adblock
- mouse gesture
- webdevelopper

Thanks a lot

---

### Post by defkewl on 2005-05-12
Why is yours still FF 1.0.2? Mine is 1.0.4 :D Perhaps that's the problem. There's still some bugs in 1.0.2

---

### Post by harryc on 2005-05-12
There's a couple of bugs in bugzilla about xml errors in Firefox. Delete the following file and restart Firefox.

 /home/user/.mozilla/firefox/***/XUL.mfasl

Substitute 'user' with your username, and *** with your unique directory name.

---

### Post by bioS on 2005-05-17
It has been corrected in the new update packages. 
I've just made an update, and the problem has disappeared.

---

