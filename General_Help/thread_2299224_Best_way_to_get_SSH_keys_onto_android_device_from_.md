---
title: "Best way to get SSH keys onto android device from Ubuntu"
date: 2015-10-16
forum: General Help
---

### Post by CaptainMark on 2015-10-16
There are many ways to get an SSH key generated from my PC onto my Android tablet. You could just place it in the cloud, but that seems stupidly insecure. You could take out the SD card from the tablet and put it on there, but not all tablets have SD card slots. You could use tools like ADB but this can often be hard to get to work on a lesser known device.

The option I'm left looking at is to encrypt the key and use the first option of cloud storage to transfer the key then decrypt it on the tablet.
Does anyone have any better ideas and if not does any one know of an encryption method that is reasonably secure and can still be decrypted on the tablet.

Regards
Mark

---

### Post by TheFu on 2015-10-16
ssh-copy-id
Same as pushing keys anywhere else.

Of course, if the tablet is the client, you need to ssh-keygen "on the tablet" and use ssh-copy-id from there to the remote server.

The public keys don't need the same level of security as the private keys.

---

### Post by SeijiSensei on 2015-10-16
Why can't you just plug the Android device into the client machine with a USB cable and copy the key from $HOME/.ssh to the device?

---

### Post by efflandt on 2015-10-16
When I first wanted to access my Android phone I was using Ubuntu 12.04 and could not get MTP (USB file access) to work at all. So I think I put my Linux openssh keys on microSD and copied them to internal storage on the phone (at least that is where they are now). So without MTP I used my keys for ConnectBot (ssh client), AndFTP (sftp client), and SSHServer Android apps, so I could sftp or scp from either end. Although MTP works fine in Ubuntu 14.04.

As long as your ssh key has a pass phrase, I am not sure how much it matters if someone gets your private key, because they cannot do anything with it unless they know your pass phrase.

---

### Post by CaptainMark on 2015-10-17
The android device is client only not server and most android devices will only let you write to the sdcard if you plug them directly into a pc not the internal storage. Additionally keys generated on the tablet cannot always be used interchangeably between applications requiring a whole bunch of keys for a whole bunch of connection types, most of which (depending on the application) cannot be made of a non default bit rate. The only decent secure way I've found to use one strong ssh key for all purposes on the tablet is to generate a key pair on the desktop and transfer both to my tablet without using cloud services. I've managed to get adb to work eventually but it was a bit of a work up.

---

### Post by TheFu on 2015-10-17
> **efflandt said:**
> As long as your ssh key has a pass phrase, I am not sure how much it matters if someone gets your private key, because they cannot do anything with it unless they know your pass phrase.

Let me fix that for you 
**As long as your ssh key has a long, random, pass phrase ....**

20+ characters, longer if they aren't random. I find it is easiest to just use a password manager for this stuff, which also has a long, random, passphrase.  At least this way the ssh-key passphrases can be 50 characters and really odd - basically with ZERO chance to be brute forced.

I would never consider using any cloud service to move this data around. That's what my LAN and rsync is for.

---

