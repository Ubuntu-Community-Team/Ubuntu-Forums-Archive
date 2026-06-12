---
title: "Best encryption software (was using truecrypt on windows)"
date: 2015-06-18
forum: General Help
---

### Post by RayTomes on 2015-06-18
I have used truecrypt on windows for some time. I am now using dual boot with ubuntu 14.04.2 and would like to have encrypted containers that can hold very many files that are mountable and dismountable. Truecrypt allows me to mount a container (huge file) as a device on Windows.

Can anyone recommend software that is preferably in the USC? Ideally that is also available on Windows-XP and compatible across the two.

---

### Post by mastablasta on 2015-06-18
why not truecrypt then?

it's development was abandoned but there are forks and others picked it up.
[https://truecrypt.ch/](https://truecrypt.ch/)
or
[https://ciphershed.org/](https://ciphershed.org/)

...

[https://veracrypt.codeplex.com/](https://veracrypt.codeplex.com/)

---

### Post by dragonfly41 on 2015-06-18
There is [https://www.bouncycastle.org/](https://www.bouncycastle.org/)

---

### Post by lenzojake on 2015-06-18
I think that older versions of truecrypt are fine. The development team though had talked about certain government agencies asking politely for keys if you know what I mean. If you want my humble thoughts on the matter version 7.0 is pretty solid and otherwise you can just use the built in encryption of 7zip, it still uses AES 256, if they can break that you would be screwed with truecrypt or just about anything else...
cheers and good luck.;)

---

### Post by RayTomes on 2015-06-18
I am not particulary interested in strong encryption. Part of the point is that the files are not accessible to viruses etc when the container is not mounted. TrueCrypt works fine for me as it is on Win-XP, so I am happy to use TrueCrypt on Ubuntu. It is not clear to me how to get it installed as I don't see it in USC and have never installed anything any other way. Please treat me like a dummy in this. :)

---

### Post by wildmanne39 on 2015-06-18
This should install 7 onto ubuntu if it is not to old for the kernel.

Run the commands one line at a time and follow the directions in the terminal and watch for errors.
```
sudo add-apt-repository ppa:stefansundin/truecrypt
sudo apt-get update
sudo apt-get install truecrypt 
```
Thanks

---

### Post by RayTomes on 2015-06-18
WildMan I typed first line and it asked me "password for ray". What is that password to?

---

### Post by wildmanne39 on 2015-06-18
It is your user password that you created when you installed ubuntu, when you type it in the terminal it will be invisible for security reasons so after you type it just hit enter.
Thanks

---

### Post by RayTomes on 2015-06-18
Thank you sir! It is installed and I can look inside my encryted folders on Win-XP file system. Excellent.

---

### Post by wildmanne39 on 2015-06-18
Glad it is working!
Enjoy!

---

