---
title: "Which ssh key is which? (~/.ssh and /etc/ssh)"
date: 2008-05-16
forum: General Help
---

### Post by sparrowkc on 2008-05-16
I believe the one in my home folder was generated through the passwords and encryption dialouge, but then I don't know what the other ones are for.  I do have the ssh server from the ubuntu repos, and after the update talking about regeneration, I went ahead and deleted all my keys just to be sure.  Might not have been the best way to go about it, but whatever.  

Also a general ssh tutorial would be nice!

---

### Post by Gunman1982 on 2008-05-16
mhh did you already look at the manual file of ssh?
open a console and write 'man ssh' explains pretty much

---

### Post by sparrowkc on 2008-05-16
I think I regenerated everything, and I did read the man file, but I guess I still don't understand the difference between what I think is called the host key in /etc/ssh and the key in the ~/.ssh folder.  Is it just the /etc one is used for incoming and the ~/.ssh one used for outgoing?  So you can have a passphrase on one but not the other?

---

### Post by Gunman1982 on 2008-05-16
Found a tutorial that might explain ssh a little bit better [http://www.securityfocus.com/infocus/1806]("http://www.securityfocus.com/infocus/1806")
the keys stored in /etc/ssh or used by the sshd (the ssh server) the keys stored in your home directory ~/.ssh or used as the client keys so every user can have different ones.
Whether the update "regenerated" just the host keys or your private keys I don't know. You can however do that manually with ssh-keygen

---

