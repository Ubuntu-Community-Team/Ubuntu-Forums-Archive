---
title: "updating error: grub-efi-amd64-signed"
date: 2021-01-26
forum: General Help
---

### Post by ronjjjg8885 on 2021-01-26
```
This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.
Transaction failed: Package dependencies cannot be resolved
 The following packages have unmet dependencies:

grub-efi-amd64-signed: 
```

trying to update and now there is another error. in the past i hade more problems of updating.
let me know if u know a solution
thanks

---

### Post by ronjjjg8885 on 2021-01-27
anyone has a solution?

---

### Post by windryder on 2021-01-27
I have the same problem. The Warning screen is attached. 

- I prefer Xorg drivers for the graphic card, but in any case, changed to Nvidia (lates, tested) drivers but no use. [IMG]https://ibb.co/3FKPnGL[/IMG]
- Tried changing the update source from "Main Server" to "UK" servers, again, no use.

Regards,

---

### Post by habana on 2021-01-27
I had this problem a couple of days ago. I launched synaptic and found warning symbols next to that file and a few associated. It seems they were missing so I installed them and all now good.

---

### Post by ronjjjg8885 on 2021-01-28
> **habana said:**
> I had this problem a couple of days ago. I launched synaptic and found warning symbols next to that file and a few associated. It seems they were missing so I installed them and all now good.

can you explain how to do that?
i'm not even sure ive synaptic

edit:
no need. i think that the problem got solved by the last update. now it is not in the list anymore

---

### Post by habana on 2021-01-29
Yes, I saw the problem file in the latest update. Anyway, synaptic package manager is useful to have but is not installed by default.

```
sudo apt update
sudo apt install synaptic
```

---

### Post by ronjjjg8885 on 2021-01-30
ok i see

thanks

---

### Post by ronjjjg8885 on 2021-02-24
again after there was no problem for a while i get it again:
[ATTACH=CONFIG]288001[/ATTACH]

i really into having a secure os and it is very annoying that every once in a while i get these errors.

---

### Post by CelticWarrior on 2021-02-24
[https://askubuntu.com/questions/1294853/cannot-update-software-because-of-grub-efi-amd64-signed-unmet-dependency](https://askubuntu.com/questions/1294853/cannot-update-software-because-of-grub-efi-amd64-signed-unmet-dependency)

---

### Post by ronjjjg8885 on 2021-02-24
hi
thanks
checking your link now

---

### Post by habana on 2021-02-24
I had the error again too. Same response as last time.
Run synaptic
Enter grub-efi-amd64 in the search box.
Note exclamation mark on a few files
Click on the grub-efi-amd64-signed file. Mark to upgrade/install (I can't remember which!)
Click Apply and accept the offered changes
This should fix it.

---

### Post by ronjjjg8885 on 2021-02-27
tnx but i did what was suggested earlier and it worked at the end

---

