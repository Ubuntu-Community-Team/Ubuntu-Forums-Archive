---
title: "Fprint and authorisation problems"
date: 2008-06-01
forum: General Help
---

### Post by _DD_ on 2008-06-01
I have fprint installed (for use with the fingerprint reader on my laptop) with the pam module referenced in common-auth.

It works fine for logging on, unlocking, sudo, etc, but when I try to open administrative apps then everything falls apart.

The apps which are launched with gksu (Synaptic, etc) show as loading down in the window list until I scan my finger and  then they appear. It took me a while to work this out because at first I thought they were taking ages to load then crashing.

For apps such as the network manager or users+groups where they run as a normal user and then there's an unlock button, the app loads but clicking on the unlock button just freezes until, I'm guessing, the authorisation request 'times out' and an 'unexpected error' message appears.

I've had error messages like this if I run things from the terminal...
```
** (users-admin:6899): CRITICAL **: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
```

I'm ok with the first, but the latter gets annoying as to use that app I have to remove the line from /etc/pam.d/common-auth, and then add it back to re-enable the fingerprint reader.

I'm running 8.04.
Any potential fixes?
Thanks.

---

### Post by _DD_ on 2008-06-02
One day later bump?

---

### Post by _DD_ on 2008-06-03
Shameless daily bump
Should this be in Laptops?

---

### Post by _DD_ on 2008-06-04
*cries*

:-({|=

^ He looks kinda solemn playing the violin, or is it a viola? Head sizes of yellow smilies are relatively unknown.

---

### Post by _DD_ on 2008-06-06
*bump*

---

### Post by siennalizard on 2008-06-21
If you can help me get to where you are with the setup of fprint on my HP TX2130, I'd be grateful.

Many thanks in advance,
J.

---

