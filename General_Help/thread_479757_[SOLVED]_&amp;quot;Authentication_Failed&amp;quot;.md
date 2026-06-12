---
title: "[SOLVED] &amp;quot;Authentication Failed&amp;quot; at login"
date: 2007-06-20
forum: General Help
---

### Post by sci-fi guy on 2007-06-20
I get this error whenever I try to login.  I would appreciate some help, as I am forced to resort to my Vista dual-boot to do anything.

---

### Post by ashz on 2007-06-20
at a guess i would say its because your a) not using correct user id b) using correct password or c) both the above!!

sorry i cannot be of any more help, unless someone else comes up with an answer then i would suggest reinstalling.

make sure u didnt have ur caps lock on at the time!!!

laters
ash

---

### Post by sci-fi guy on 2007-06-20
I don't even get a chance to enter my password. I enter my username (Caps Lock is off), press enter or tab, and get the error message.
I had this issue once before, and did reinstall then.  But considering that I got it again, I would like to avoid this in the future.

---

### Post by SimonHickling on 2007-06-22
If you reboot and from grub go into recovery mode, that will start you up as root.  From there you can get to the /etc/pam.d directory.  If you post the contents of the file starting common-* this may give some indication as to the problem. 

It looks like it is trying some non-normal authentication method.  I have seen this before when trying to setup authentication to AD or LDAP and getting the entries wrong.

---

### Post by sci-fi guy on 2007-06-25
I have already reinstalled, so I do not think that this command line will do any good. Thanks anyways

---

### Post by 5of0 on 2007-07-18
> **SimonHickling said:**
> If you reboot and from grub go into recovery mode, that will start you up as root.  From there you can get to the /etc/pam.d directory.  If you post the contents of the file starting common-* this may give some indication as to the problem. 

It looks like it is trying some non-normal authentication method.  I have seen this before when trying to setup authentication to AD or LDAP and getting the entries wrong.

Ah, thanks for the tip - I was starting to get a bit worried when I couldn't even log on as root after trying to join it to a Win2k3 domain.  This is definitely the case, as I was messing with common-* to get LDAP set up.  I'll keep you posted on how it goes, currently it's taking forever to Configure network interfaces :/

---

