---
title: "Root access and setting ups nfs"
date: 2007-05-31
forum: General Help
---

### Post by stevesheldon on 2007-05-31
Apologies for missing the obvious.. but :) 
I have just installed Ubuntu Feisty Fawn on my AMD64. Everything went smooth as silk with the install - but - I don't have access to the root account, and cannot setup fstab to include an nfs share on my file server.
I have obviously missed something obvious here.. can anyone please help?
Regards,
Steve
[email]steve.sheldon@solidlinux.co.uk[/email]

---

### Post by uterrorista on 2007-05-31
Open the Terminal [Applications » Accessories » Terminal ] and type:
```
sudo gedit /etc/fstab
```

note:
to be root privilege, write:
```
 sudo <command>
```
in this case:
```
sudo gedit /etc/fstab
```

---

### Post by stevesheldon on 2007-05-31
Thanks for that - I am used to working with SuSe, and RedHat and with always having root access through su - I guess it is reassuring from a security angle that root access is locked here :) Thanks again, nfs server now accessible :)
Steve

---

