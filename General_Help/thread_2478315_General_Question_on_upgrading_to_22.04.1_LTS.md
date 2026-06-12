---
title: "General Question on upgrading to 22.04.1 LTS"
date: 2022-08-22
forum: General Help
---

### Post by us-palermo on 2022-08-22
I'm following a guide on upgrading my xubuntu 20.04.4 lts to 22.04.1 lts and need to make sure on the commands which I used previously when upgrading from 18.04 lts to 20.04 lts.
$ cd /etc/apt/sources.list.d/
$ sudo find . -type f -readable -writable -exec sed -i 's/xenial/bionic/g' {} \;
 Finally, use the rename command to also rename all these /etc/apt/sources.list.d/ files all at once:

 $ sudo apt install rename
$ sudo rename 's/xenial/bionic/' *

Do I replace the following commands with the following


sudo find . -type f -readable -writable -exec sed -i 's/bionic/jellyfish/g' {} \;

and 

sudo rename 's/xenial/jellyfish/' *

I just want to make sure before I upgrade.

---

### Post by TheFu on 2022-08-23
That's how debian does it.  Ubuntu has a tool.

```
$ sudo do-release-upgrade
```

Run that, but make 100% certain that you backup anything on the system before beginning AND that you read the 22.04 release general notes AND the release notes for your specific DE (Lubuntu, Kubuntu, ....). Each have their own release notes. Google finds them easily.

---

### Post by Impavidus on 2022-08-23
In addition to TheFu's comments, the short name of 22.04 is jammy, not jellyfish. Just as the short name of 20.04 is bionic, not beaver.

---

### Post by us-palermo on 2022-09-02
thank you for your help

---

