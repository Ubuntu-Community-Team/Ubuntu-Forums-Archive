---
title: "transferring settings from evolution to evolution"
date: 2007-05-07
forum: General Help
---

### Post by diskotek on 2007-05-07
hello

i was using edgy eft before, than i made a fresh install with feity fawn. i copied my home directory and than put it back when feisty installed. but when i' opening "evolution" it begins with starting wizard. however i see evolution config files at my home directory it's not recognizing and asking me question "your name, email address, server type.." etc

for more infor evolution config files are under "~/.evolution". i straightly copied it back. do you have any idea?

---

### Post by ohgod on 2007-05-07
The actual mail store is stored in ~/.evolution, but the account settings & passwords are stored elsewhere.  This burned me too :(.

From [http://www.go-evolution.org/FAQ#Where_does_Evolution_store_my_data.3F](http://www.go-evolution.org/FAQ#Where_does_Evolution_store_my_data.3F)

> 
 Where does Evolution store my data?

Evolution stores your data in $HOME/.evolution/, your account settings in $HOME/.gconf/apps/evolution and your passwords in $HOME/.gnome2_private/Evolution. The passwords are not stored encrypted, just base64 encoded. SSL Certificates are stored in $HOME/.camel_certs, and if Evolution crashed while you were writing an email, there could even be a file $HOME/.evolution-composer.autosave-123456 (where 123456 is some string). 


---

### Post by diskotek on 2007-05-07
ah thank you for quick response, i'll keep that in mind. because i deleted those files! so i need to create sattings again, at least i would have my old emails (i hope).

thank you again.

---

### Post by ayoli on 2007-05-07
> **ohgod said:**
> The actual mail store is stored in ~/.evolution, but the account settings & passwords are stored elsewhere.  This burned me too :(.

From [http://www.go-evolution.org/FAQ#Where_does_Evolution_store_my_data.3F](http://www.go-evolution.org/FAQ#Where_does_Evolution_store_my_data.3F)

hey, that's learn me some tings, thanks :)

---

### Post by poobuntu on 2007-05-10
This has burned me as well, and now that I am attempting to switch machines (and OS), I am faced with it once again.

I'm attempting to transfer my Evolution emails, contacts and email identity/accounts from SuSE 10.2 to a machine running LinuxMint.

I've followed everything as described above and everything transfers except my email account information - I have several different identities and signatures. The only Identity/email account that shows up is the one I had to create with the wizard. Can anyone offer any insight here?

Also, I should point out that in SuSE,  there is absolutely nothing stored in $HOME/.gnome2_private/Evolution. What am I missing here??

Thanks in advance for any and all advice.

---

### Post by oomingmak on 2007-07-02
I just experienced the exact same issue.

I wanted to create a Data partition for my files (separate to my Home partition) but Gparted messed up the partition order (which Fdisk could not fix) so I ended up having to wipe the disk and start from scratch.

At first I tried to restore a backup of my home partition, but it wouldn't work because the partitions had changed. So I then tried to manually restore the 3 folders that are meant to store all the Evolution files and settings, but **none **of my 5 POP3 accounts were created and so I now have to dig up the various passwords and mail server settings for all of them and enter them again manually.

---

