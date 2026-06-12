---
title: "skype binary file corrupted"
date: 2008-01-28
forum: General Help
---

### Post by sandclock on 2008-01-28
Hi
I am tring to install skype on 7.04. I installed in successfully but when i try to run it. It says "Binary file Corrupted" Please reinstall skype. I tried reinstall still same error. I believe all dependancies are installed because it didnt gimme any error while installing
Regards and thanks
nik

---

### Post by Helios38 on 2008-01-28
are you installing it from the repos? or compiling from source?

if u compiled from source something may have gone wrong

---

### Post by sandclock on 2008-01-28
> **Helios38 said:**
> are you installing it from the repos? or compiling from source?

if u compiled from source something may have gone wrong

How do i do that? sorry i am new to ubuntu
Regards
Nik

---

### Post by sandclock on 2008-01-28
Bump ??
Anyone?

---

### Post by plucky on 2008-01-28
Skype is in the Medibuntu repository.To add it to your **Sources** list for Feisty,use the following commands.
```
sudo wget http://www.medibuntu.org/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list
```
To add the GPG key ```

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

```

To install skype ```
 sudo apt-get install skype
```

Good luck

---

### Post by derivatizer on 2008-02-20
hi,

i have the same problem as sandclock. i am really desperate. i am using xandros on a asus eee. after i installed the skype update it doesn t work any more.

everytime i want to start skype i receive the message: "binary file corrupted" "please reinstall skype".

i already did reinstalled skype. but nothing changed. can you help me with this problem?

ps: i know that this is a ubuntu community. but i already tried to get help in eee communities. without succes. perhaps you can help me?!

thanks

---

