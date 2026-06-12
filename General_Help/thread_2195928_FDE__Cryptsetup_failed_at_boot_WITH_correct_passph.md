---
title: "FDE : Cryptsetup failed at boot WITH correct passphrase"
date: 2013-12-27
forum: General Help
---

### Post by Igonelsy1920 on 2013-12-27
Hello,

I have a very strange problem with full disk encryption.

We have a small fleet of Thinkpads (X220 and T420s) running Lubuntu 13.04 with FDE. No problem until now.
Since yesterday, one of the Thinkpad X220 won't decrypt cryptsetup at boot. We are 100% sure the passphrase we enter is correct. We use french keyboards, so my first idea was that (for any reason) the system reset the keyboard layout to EN_US. We've tried to type the passphrase using this US layout, it doesn't work either.

The user of this laptop has NO admin privilege on the computer. So he couldn't have changed the passphrase.

What could cause this behavior ?

If I can't solve this by the end of the day, I'll do a fresh install during the week-end and restore the data from backup. But I'd like to understand what happened so it doesn't occurs too often :confused:

Thanks for your help !

---

### Post by Igonelsy1920 on 2013-12-27
Update :

I've re-installed Lubuntu 13.04. 

Everything was working fine on the new installation until I ran an apt-get upgrade and rebooted. The exact same problem occured : the correct passphrase won't unlock the LVM volume. 

Any help ?

Thanks.

---

### Post by Kopczyk on 2014-04-30
Ubuntu 14.04 LTS the same problem. I can't encrypt disk on boot with correct password. %#$@^#$%$^!^$

---

### Post by Viktor_Alakrkk on 2014-05-06
I have this issue to on my Thinkpad R400 with 14.04. Any one figured out the problem?

---

### Post by rbaleksandar on 2014-05-26
I can only concur to what the rest said in this post - fresh installation of Lubuntu 14.04 LTS (in VirtualBox however), correct passphrase given and still can't unlock the LVM volume. It's a good thing that at least people will find out about this after a freshly setup LVM. It would be a real pain if such problem occurs after you have accessed it a couple of times, stored some important data AND then found out that it won't let you in any more :D

---

