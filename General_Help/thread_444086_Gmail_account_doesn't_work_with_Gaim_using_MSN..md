---
title: "Gmail account doesn't work with Gaim using MSN."
date: 2007-05-15
forum: General Help
---

### Post by OpticalIllusion on 2007-05-15
I use MSN Messenger on Windows using my Gmail account and used to be able to do the same with Gaim.  I used to be able to use the MSN protocol and use my Gmail account to log in.  It no longer works that way.  What's going on?  How can I fix this?

---

### Post by thelinuxguy on 2007-05-15
Use the following. Works on 2.0.0beta3.1

BASIC:
======
Protocol: Jabber
Screen name: Your gmail account (without @gmail.com)
Server: gmail.com
Resource: Gaim
Alias: I have kept it same as my screen name. Didn't try using something else.

ADVANCED:
===========
Use TLS if available
Require TLS
Connect port: 5222
Connect server: talk.google.com

Hope this works for you.

---

### Post by OpticalIllusion on 2007-05-15
Yes, it appears as if it's working, but no one is appearing as online.  I usually always have one or two people that stay signed in 24/7.  I could be wrong, I'll see how it works out tomorrow.  Thanks!

---

### Post by wariomvc on 2007-05-16
Hi guys, I have same problem, with amsn i can connect to a gmail account that is registered in .Net Passport but with Gaim it doesn't connect.

Could you help me?

---

### Post by fragos on 2007-05-16
Worked for setup on Ubuntu 7.04 with Gaim 2.0.0beta6 that's part of the distro.  There were no TLS specific parameters with this version and I didn't change the few that weren't mentioned in the post above.  I was informed of buddies I've seen in the gmail interface.  No ones available online to talk with but it looks like it will work.

---

### Post by OpticalIllusion on 2007-05-17
Yeah, still no one appearing online even though I know of some that are online.  What's going on?

---

### Post by azidtripz on 2007-05-17
your logging in to gmail chat, not the msn protocol, which i think your wanting to use ??

---

### Post by thelinuxguy on 2007-05-17
> **OpticalIllusion said:**
> Yeah, still no one appearing online even though I know of some that are online.  What's going on?

Strange!!! I am using it and can see and chat with my friends when they are online. Even at this very moment.

---

### Post by DarkN00b on 2007-05-18
This is the same thing thelinuxguy posted, but with pics. These settings (with your info of course) **will** get you connected. See pix below.

---

### Post by Proximo1 on 2007-10-10
I am having the same issues.  

I have a question.  How is it that Jabber will get this to work.  I have a Live Messenger Account with a gmail address.  It works fine when I am on my Windows XP box.

It&#347; not working with gaim no matter what options I try.  I am running 7.04 and the default gaim that comes with the OS.

Any suggestions?

Why is something so simple not working in Linux?

---

