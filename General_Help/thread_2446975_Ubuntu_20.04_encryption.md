---
title: "Ubuntu 20.04 encryption"
date: 2020-07-10
forum: General Help
---

### Post by jkmaloney on 2020-07-10
I chose to erase disk when installing Ubuntu 20.04. Then I chose "Use LVM with the new Ubuntu installation" and "Encrypt the new Ubuntu installation for security".


What type of encryption is used, and how secure is it? Is it full disk encryption?

---

### Post by grahammechanical on 2020-07-10
Your post is written in invisible font type. Are you testing a form of encryption on us? :)


Regards.

---

### Post by jkmaloney on 2020-07-10
Hahahaha, I hope it is visible now?

---

### Post by TheFu on 2020-07-10
dmcrypt+luks.

How secure it is would be highly dependent on you not doing non-secure things like using standby or hibernation or having passphrases along without 2FA devices involved.  
You have the responsibility to control the boot environment completely or have risks from the evil maid attack.
You have the responsibility to mitigate any and all network attack vectors since the encrypted data is only safe when the system is completely powered off.

How much security do you need?
How many hassles are you willing to put up with for that security?

There isn't a "100% secure" button.  Mitigation for every, each, all attack vectors is something you'll need to address.  The most difficult is ensuring a clean boot environment.

---

### Post by Ranbunta_Bantubunt on 2020-07-11
These threads may be of interest to you

[https://discourse.ubuntu.com/t/can-we-get-real-full-disk-encryption/8802](https://discourse.ubuntu.com/t/can-we-get-real-full-disk-encryption/8802)

[https://ubuntuforums.org/showthread.php?t=2444360](https://ubuntuforums.org/showthread.php?t=2444360)

---

