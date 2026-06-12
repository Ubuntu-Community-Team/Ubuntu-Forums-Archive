---
title: "nautilus encrypt folder"
date: 2008-06-14
forum: General Help
---

### Post by nix4me on 2008-06-14
How do I encrypt a folder with naultils right click option?  When I try it, it seems to be looking for a key, however there are no keys to use.  How do I use this thing?

Thanks,
nix4me

---

### Post by wormser on 2008-06-17
Bump, I would also like to know.

---

### Post by geirha on 2008-06-17
Go to «Applications -> Accessories -> Passwords and Encryption Keys» and create a PGP-key.

EDIT: And make sure you don't forget the passphrase you choose, and always remember to backup the keys if you reinstall or similar. If you don't have the secret key and the correct passphrase, your files will be encrypted forever.

---

### Post by wormser on 2008-06-17
Thanks geirha.

I was looking for an option under System> Preference> Encryption and Keyring and for got about the option under accessories.  There should be a prompt to create a key when there are no keys.

---

### Post by nix4me on 2008-06-17
Brilliant.  I was looking at the keyring area too.  i agree about a prompt needed.

Oh well, all good now, thanks!

nix4me

---

### Post by mikey11 on 2008-07-24
More importantly, how can I back the keys up? Are they plain text? can I copy and paste the key into an email and store it on some server on the internet somewhere?

In addition to having a key generation prompt when no keys are made, there ought to be a thorough tutorial on how to use keys!

I mean I think I got it figured out, but you never know.

Anyhow, works for now.

---

### Post by Potatoj316 on 2008-07-24
You have 2 keys, public and  private. Public can encrypt but only private can dectypt.  I dont really know how to back it up but make sure you back up the private key, not just the public key.  Im pretty sure its in one of the menus, but I could be wrong.  I would check now but im not on my computer. (no the computer im on is not mine)

---

### Post by coreysk8wow on 2008-12-06
I use winPT ([www.gpg4win.org/](www.gpg4win.org/)) to creat and backup both secret and public keys in Windows XP. There are two options to export secret key or public key in winPT. Then I import the keys into Seahorse in ubuntu.

---

### Post by paste on 2009-04-04
For those of you who are interested, you can backup your keys by clicking on the "Export..." button at the top of the "Passwords and Encryption Keys" dialog, or by right-clicking on the key you want to backup and selecting "Export...."  You can then import the saved keys with "File->Import...", or by simply dragging the backed-up key file from Nautilus into the dialog.

---

### Post by aneganov on 2011-04-14
On 10.10 there is no "Encrypt..." in the right-click menu. Any ideas?

---

### Post by Geremia on 2011-05-31
> **nix4me said:**
> How do I encrypt a folder with naultils right click option?  When I try it, it seems to be looking for a key, however there are no keys to use.  How do I use this thing?I have generated an OpenPGP key pair, but I still don't see the option to encrypt a folder while right-clicking in Nautilus. Thanks

---

### Post by kavoura on 2011-06-24
I have the same problem, running Ubuntu 10.10. I created a PGP key, but I have no idea how to use it to encrypt a folder, there is no Encrypt option on the right-click menu. Surely it should be easy to encrypt files and with an obvious way of doing it? I must be missing something obvious.

---

### Post by haqking on 2011-06-24
> **kavoura said:**
> I have the same problem, running Ubuntu 10.10. I created a PGP key, but I have no idea how to use it to encrypt a folder, there is no Encrypt option on the right-click menu. Surely it should be easy to encrypt files and with an obvious way of doing it? I must be missing something obvious.


you might need to add seahorse plug in called decrypt file in synaptic or software centre or just sudo apt-get install seahorse-plugins will do same thing


also log out and log back in after making a key, occasionally you might need to restarts system but unikely, definately log out and log back in though

---

