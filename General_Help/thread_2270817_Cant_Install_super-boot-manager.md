---
title: "Cant Install super-boot-manager"
date: 2015-03-25
forum: General Help
---

### Post by dannyboyinpy on 2015-03-25
Im running Ubuntu 14.10. I want to install super-boot-manager. I added the repo with

```
sudo add-apt-repository ppa:ingalex/super-boot-manager
```

then did

```
sudo apt-get update
```

this went fine but at the end it said

```
W: Failed to fetch http://ppa.launchpad.net/ingalex/super-boot-manager/ubuntu/dists/utopic/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/ingalex/super-boot-manager/ubuntu/dists/utopic/main/binary-i386/Packages  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.



```

I tried to install anyway but it didnt work. I went in my browser to the repo and saw why. Inside /ubuntu/dists they only have up to Raring (13.04). How can i make this install anyway?

thanks in advance

---

### Post by Holger_Gehrke on 2015-03-25
Just feeding "super-boot-manager" to google gave me this:
[http://askubuntu.com/questions/449807/how-do-i-install-super-boot-manager](http://askubuntu.com/questions/449807/how-do-i-install-super-boot-manager)
But are you really sure you want this program this badly ? It's just a GUI on top of tools you've already got and from what little information I could find on it, it barely scratches the surface of what these tools can do.

---

### Post by dannyboyinpy on 2015-03-25
> **Holger_Gehrke said:**
> Just feeding "super-boot-manager" to google gave me this:
[http://askubuntu.com/questions/449807/how-do-i-install-super-boot-manager](http://askubuntu.com/questions/449807/how-do-i-install-super-boot-manager)
But are you really sure you want this program this badly ? It's just a GUI on top of tools you've already got and from what little information I could find on it, it barely scratches the surface of what these tools can do.

Thanks Holger. I think i'll try the tools manually first and if i cant figure them out i'll go for super-boot-manager. Thanks again for your help.

---

### Post by uchihitachi on 2015-06-17
Try editing the software sources. Select the 
ppa:ingalex/super-boot-manager

press Edit and change the distribution from vivid to raring.

Update again and install.

Hope it helps

 :guitar:

---

