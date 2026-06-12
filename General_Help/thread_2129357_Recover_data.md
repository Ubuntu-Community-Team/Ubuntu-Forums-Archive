---
title: "Recover data"
date: 2013-03-26
forum: General Help
---

### Post by Rakeshvijayan on 2013-03-26
Hi friends 

I accidentally deleted my file that is very urgent file from ubuntu os locations is /home/myshare/contents. how can i recover it from the location I need a frequent answer my friends because its very important for me .give me any solution

---

### Post by dino99 on 2013-03-26
you should use deja-dup to avoid such issue. 
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by slickymaster on 2013-03-26
Besides those mentioned on dino99's post, you could also try Scalpel.
```
sudo apt-get install scalpel
```
After installing it you just have to change it's configuration in **scalpel.conf**:
```
gksudo geany /etc/scalpel/scalpel.conf 
```
Remove the # sign from the beginning of the lines which contain the file types you want to recover.
After that please run the Scalpel:
```
sudo scalpel /dev/sdb1 -o /home/Recovered_Files/
```
**dev/sdb1** is the location of the device from where the files were deleted.
**/home/Recovered_Files/** is the place to accommodate the files that will be recovered from /dev/sdb1

---

### Post by Rakeshvijayan on 2013-04-01
hirance boot cd is the best thing

---

