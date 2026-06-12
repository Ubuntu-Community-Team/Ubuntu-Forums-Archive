---
title: "washed out colors on hp laptop with ubuntu"
date: 2023-05-15
forum: General Help
---

### Post by tomposton on 2023-05-15
After a recent firefox update, the colors of all internet images are washed out or skewed on my HP laptop running Ubuntu 22.04.1 LTS.

---

### Post by yancek on 2023-05-16
Were you using firefox installed from the Ubuntu repositories or had you downloaded a newer version from the Mozilla site?  
How was the update done? 
What graphics card do you have?  Have you had previous problems with graphics on this machine, not necessarily just firefox?

---

### Post by tomposton on 2023-05-16
Firefox from the repository. Firefox updated itself automatically. This machine has no hardware problems.

---

### Post by idmbe on 2023-05-16
type:
```
 snap list
```
then see if firefox there type:
```
 snap refresh firefox
```
if firefox not in the list type:
```
 snap install firefox
```

I guess that better if work with snap store in 22.04

---

