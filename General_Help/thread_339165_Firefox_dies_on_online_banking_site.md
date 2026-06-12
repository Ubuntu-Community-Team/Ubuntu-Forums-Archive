---
title: "Firefox dies on online banking site"
date: 2007-01-15
forum: General Help
---

### Post by c-m on 2007-01-15
Every time i try to log into my online banking firefox quits. whenever i try to use an online store using oscommerce and try to check out firefox quits. 

Below is the error i am getting.

Note i am using flash9 not flash-nofree etc...

Why is it doing this? 

```
carl@carl-desktop:~$ firefox
Segmentation fault

```

---

### Post by fragos on 2007-01-15
Are you running Firefox 2.0? Ubuntu 6.10? How about URLs on that crash on?

---

### Post by c-m on 2007-01-16
> **fragos said:**
> Are you running Firefox 2.0? Ubuntu 6.10? How about URLs on that crash on?

version 1.5.0.9 ubuntu 6.06 it is crashing on the barclays login [https://ibank.barclays.co.uk/olb/t/LoginMember.do](https://ibank.barclays.co.uk/olb/t/LoginMember.do) after i enter my details on this page and click next, the second page begins to load then quits.

The thing is I worked once yesterday, then staight after when i tried again it quit.

---

### Post by fragos on 2007-01-16
Not having a Barclays account I couln'd try to duplicate your problem.  I'm inclined to think that your problem isn't in the basic Firefox but in extensions.  You could try disabling extensions to see if the problem goes away and then one at a time to identify the culprit.

---

### Post by c-m on 2007-01-16
> **fragos said:**
> Not having a Barclays account I couln'd try to duplicate your problem.  I'm inclined to think that your problem isn't in the basic Firefox but in extensions.  You could try disabling extensions to see if the problem goes away and then one at a time to identify the culprit.



are there options in firefox to do that?

This only happens with firefox, epiphany works perfectly fine.

---

### Post by hikaricore on 2007-01-16
> **c-m said:**
> are there options in firefox to do that?

This only happens with firefox, epiphany works perfectly fine.

Flash is known to crash firefox at random sites as of late, if you have the flash 9 beta installed try removing it temporarily and test your banking site.  You may also want to try removing flash 7 if you have it installed instead.  If neither is the case see if you're using any firefox addons and disable them then restart and check again.  Usually comes down to some simple little thing that can normally be avoided.

---

### Post by eplans on 2007-01-17
I just wanted to confirm, I'm having exactly the same problem with barclays quitting the firefox at the second login page.  I've just tried to use synaptic to see if I have flash 9 installed, but it didn't look like it,  In fact it didn't seem to show any flash addons at all.  I apologise if I'm being terribly slow, and this isn't where I would find the addons anyway.  I tried re-installing firefox, but this didn't solve the problem.

I'm running firefox version 1.5.0.9 on Ubuntu 6.06.1 LTS \n \l .

(P.S I don't know what LTS \n \l means, so I've quoted this too!)

---

### Post by fragos on 2007-01-17
> **eplans said:**
> I just wanted to confirm, I'm having exactly the same problem with barclays quitting the firefox at the second login page.  I've just tried to use synaptic to see if I have flash 9 installed, but it didn't look like it,  In fact it didn't seem to show any flash addons at all.  I apologise if I'm being terribly slow, and this isn't where I would find the addons anyway.  I tried re-installing firefox, but this didn't solve the problem.

I'm running firefox version 1.5.0.9 on Ubuntu 6.06.1 LTS \n \l .

(P.S I don't know what LTS \n \l means, so I've quoted this too!)

Open Firefox and in the address area type "about:plugins" to see what plugins are installed and what are their versions.

---

### Post by fragos on 2007-01-17
> **c-m said:**
> are there options in firefox to do that?

This only happens with firefox, epiphany works perfectly fine.

I've been running Firefox 2.0 and Ubuntu 6.10 which does provide the disable feature.  In Firefox 2.0 select "Tools" then "Add-ons".  Select any extension and you'll see the disable button.  In 1.5.0.9 I believe that extensions and themes are still separate picks in the tools menu.  Look there.

---

### Post by flyingbrass on 2007-01-17
A couple weeks ago I had that problem with Bank of America.  Firefox would quit after entering the passphrase.  Clearing cache and cookies fixed it.

---

### Post by mal on 2007-01-18
There is a bug in the latest update of Firefox (1.5.0.9) that causes it to crash when connecting to a page that has a remembered password.  This is detailed [in Launchpad]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/77859").

The solution seems to be to go back to the previous version of Firefox, or to disable the password saving feature in Firefox (Edit/Preferences/Privacy/Passwords...).

Hope this helps.

Mal

---

