---
title: "Have I Got Encryption?"
date: 2014-09-01
forum: General Help
---

### Post by Quarkrad on 2014-09-01
I have install encryption on my **\home** folder via instructions from a number of sites (the instructions have all been the same).  My last issue was a boot error to do with the swap partition mapping but I have sorted that out.  In my **\home** folder I have a folder called **.ecryptfs**  so 'things' have installed.  However, despite entering a passphrase during the install process I'm not convinced all is well.  Encryption is not working because I can copy a file to a memory stick and read it on another pc &#8211; how do I check encryption is installed and what do I  'see' that is different?  (I am running 14.04)

---

### Post by Quarkrad on 2014-09-01
I do not know whether this is a default action but I now have to log in manually when I boot the laptop (it was set to auto logon).  I can open the terminal and when I type **ecryptfs-unwrap-passphrase** I am asked for my passphrase.  When I type it in I can see the actual numeric passphrase.

---

### Post by 3rdalbum on 2014-09-01
When you copy files to another drive, they are not encrypted. That is normal.

To see if your /home is encrypted, boot a live CD or live USB and try to read the data on /home.

---

### Post by Quarkrad on 2014-09-02
Thank you - unfortunately I have had to rebuild my laptop so cannot answer your question.  Twice I tried to install encryption and each time when I encrypted the swap space my touchpad became virtually none functional (14.04 machine) - I guess it is a hardware (Dell) issue.  Tried all sorts of fixes but none worked - only solution so far is to rebuild and then install the touchpad driver.  Is there anywhere I can read how encryption is _used_, from the user perspective, and what is where when using it?  There is lots of data on how to install or uninstall but I have found nothing, so far, on what to do and what you see once it is installed.

---

### Post by mastablasta on 2014-09-02
you should encrypt the whole disk then. I am not sure what hardware issue would have to do with encryption.

btw make sure you don't lose the key...

---

### Post by 3rdalbum on 2014-09-04
From the user perspective? Encryption is totally seamless. You log in as normal, your home directory appears as normal, but behind-the-scenes the data is encrypted as it goes onto the disk and decrypted as it gets read from the disk. Not even your programs will realize what is happening. It is all automatic and it "just works".

The only time you will notice any difference is if you try and boot from a different disk and then mount your encrypted drive. Filenames will be gobbledygook and files will be seemingly random data. You will see a plaintext file, though, which explains that the drive is encrypted and tells you how to mount it with the passphrase.

---

