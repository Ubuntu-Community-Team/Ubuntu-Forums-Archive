---
title: "Cryptsetup Edgy"
date: 2007-01-22
forum: General Help
---

### Post by QÉD² on 2007-01-22
I followed [https://help.ubuntu.com/community/EncryptedFilesystemHowtoEdgy]("https://help.ubuntu.com/community/EncryptedFilesystemHowtoEdgy") to encrypt swap, /, and /home. I assume they **are** encrypted, as there have been no error messages. I entered luks passphrase to unlock /boot, then user passwd to login. So far so good.

Problem is, I cannot see any difference in Nautilus. So how do I verify whether the partitions are really luks encrypted?

Also, can my box still be hacked now that the file system (hopefully) is encrypted? What if I just login but do not get online?

Thirdly, since the user passwd is used to mount crypthome, will changing it break any link in /dev/mapper?

And this very important one: I followed the article and edited my grub Recovery kernel line before urandoming the old boot and setting it up as crypthome.  Where is the Recovery kernel now?
 
I am a relative noob, so please, details in your answers.

---

### Post by High Roller on 2007-01-22
> **QÉD² said:**
> 
Also, can my box still be hacked now that the file system (hopefully) is encrypted? What if I just login but do not get online?


In a powered down state your system should be secure (in an ideal world).  Your system could technically be compromised by stealing your password through modifying the boot process or via hardware keyboard logging methods.  And that's just when you're in a powered down state.

When you're system is powered up it introduces a whole other realm of possibilities where your key could be compromised by either grabbing it from memory or again modifying the boot process should the user be tricked into running malicious code.  If the attacker were to somehow gain root access it would be game over encryption or not.  Your system is most secure in a powered down state where there is trust that the boot process hasn't been modified.

Defending against unauthorized access is totally dependent on your threat model.  Software encryption is a good idea if you want to protect against someone stealing your laptop for example.  The data won't be compromised as it is likely that the thief would only have access to the machine after it was stolen and lack the ability to set a trap.

These are just my opinions on securing a system.  Hope it helps!

---

