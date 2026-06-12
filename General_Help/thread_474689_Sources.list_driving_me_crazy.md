---
title: "Sources.list driving me crazy"
date: 2007-06-15
forum: General Help
---

### Post by flat4 on 2007-06-15
I  have checked my sources file several time to comment out the cd-rom and cannot find it. When i try to install anything using the 

sudo apt-get install whatever, I keep getting the error E:  cannot find file. 

I also have ran the apt-get update, still asks for a cd.

Where else should I look at ? :?:

---

### Post by jasonlfunk on 2007-06-15
You can try looking in System->Preferences->Software Sources

---

### Post by mikewhatever on 2007-06-15
Post the output of the following command 
> sudo nano /etc/apt/sources.list

Also, what's the name of the file it can't find?

---

### Post by flat4 on 2007-06-15
I was trying to install zoneminder

---

