---
title: "How do I know if Secure Boot was actually turned off?"
date: 2018-04-06
forum: General Help
---

### Post by kregg2 on 2018-04-06
I ask, because;

I installed xubuntu, during installation I selected the option to disable secure boot, added a password, and installed.

After booting in for the first time, I was presented with an option screen, I selected 'continue boot' I believe. There wasn't an 'disable secure boot' option and I was never asked for the password.

Whatever right? 

So I modeset nouveau and head into the additional drivers, I can see the option to revert to the nvidia driver, and it begins to install. Right near the end, it of course questions the fact that UEFI secure boot is active, and asks me to set a password AGAIN.

The password fields were not *asterisk, which strikes me as weird, and I was confused as to why I needed to do this again. 

I press back a couple times, un-check the 'disable secure boot' option, and continue.

To my surprise, xubuntu starts normally and the nvidia driver is working?

Is this normal then? Did xubuntu not actually NEED to disable secure boot, or has secure boot been disabled (despite being turned ON in the bios)???

Any clarification from the experts would be massively appreciated :)

-----------------------------

Dell XPS-15 9560, i5 etc

---

### Post by oldfred on 2018-04-06
What does this show? Mine shows disabled, but I turned it off in UEFI settings.

fred@Z170N:~$ mokutil --sb-state
SecureBoot disabled

Since Ubuntu cannot confirm that proprietary drivers like nVidia or Wireless drivers are "secure" it has to turn off UEFI secure boot to use them.

 Why disabling &#8220;Secure Boot&#8221; is enforced policy when installing 3rd party modules
[http://askubuntu.com/questions/755238/why-disabling-secure-boot-is-enforced-policy-when-installing-3rd-party-modules](http://askubuntu.com/questions/755238/why-disabling-secure-boot-is-enforced-policy-when-installing-3rd-party-modules)

---

