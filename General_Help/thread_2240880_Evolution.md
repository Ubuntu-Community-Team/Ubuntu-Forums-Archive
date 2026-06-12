---
title: "Evolution"
date: 2014-08-22
forum: General Help
---

### Post by gordon99 on 2014-08-22
I am using Evolution email client in Xubuntu 14.04. When I go to use it each day it asks for a password which, to me, seems unnecessary unless one is sharing a computer. How can I stop the requirement to give a password please?

---

### Post by ian-weisser on 2014-08-22
My Evolution has never asked for a password in 8 years...unless something was wrong.

Does it ask for a password when you start evolution? When checking e-mail? When sending e-mail?
Does it say why it's asking for a password?

It is asking for your user password? Networking password? Keyring password? e-mail account password?

---

### Post by gordon99 on 2014-08-25
Hello ian-weisser. I removed and re-installed Evolution, on reading your post, thinking I may have made an error at the start. No such luck however. Immediately on installing Evolution it downloaded my mail. However, on each subsequent occasion I go into Evolution it comes up with a Mail Authorisation Request for each of my email providers viz. gmail and gmx. I have to enter my **email account **passwords before my email shows up. The M.A.R. also asks if I want to add the passwords to my keyring (which is another source of annoyance as I do not know the purpose of a keyring and have so far managed without one). Any further thoughts what I should do to avoid having to give passwords?

---

### Post by ian-weisser on 2014-08-25
> **gordon99 said:**
> I do not know the purpose of a keyring and have so far managed without one.

A keyring is software that securely stores your passwords for you, so  you don't have loads of passwords stored (perhaps insecurely) all over  your system. Applications use the keyring to store passwords and other 'keys' securely. Secure storage of critical data (like passwords) is a big headache, and most applications are quite happy to offload the burden to a keyring.

Evolution will not remember your password. It uses a keyring for the purpose.
Without a keyring, you will be prompted for the password each time.

---

### Post by gordon99 on 2014-08-25
I have spent a large part of the day reading posts on different sites to try and pin down a solution to my problem. It seems there is a long running problem getting Keyring to work in Xubuntu, or it maybe applicable to the XCFE desktop only, though I do not know if XCFE is found in other Distros. I have read a number of "solutions" but non are very explicit and many give variable results. Anyway, I am going to post the problem under Desktops to see if I can get a response that is specific to XCFE. Thank you for your interest.

---

