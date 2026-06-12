---
title: "I am getting error messgae at the end whenever I use apt-get or aptitude for update"
date: 2007-06-22
forum: General Help
---

### Post by applegrew on 2007-06-22
Whenever I use aptitude update or apt-get update I get the following message at the end.

```
Hit http://archive.ubuntu.com feisty-security/multiverse Packages
Hit http://archive.ubuntu.com feisty-security/multiverse Sources
Get:4 http://archive.ubuntu.com feisty/multiverse Sources [63.5kB]
99% [4 Sources gzip 0]
[COLOR="Red"]gzip: stdin: not in gzip format
Err http://archive.ubuntu.com feisty/multiverse Sources
  Sub-process gzip returned an error code (1)
Fetched 194B in 5s (34B/s)[/COLOR]
Reading package lists... Done

```

What is the meaning and source of the above message?

---

### Post by applegrew on 2007-06-22
Will somebody pls solve my problem.:( ](*,)

---

### Post by ezrollers on 2007-06-22
m8, it's only been an hour since your original post. chill out.

Do you get the same problem when running synaptic or any other front end?

---

### Post by applegrew on 2007-06-22
> **ezrollers said:**
> m8, it's only been an hour since your original post. chill out.

Do you get the same problem when running synaptic or any other front end?
yup

---

### Post by Qu4k3R on 2007-06-22
Can you install software (even with that bug? with apt-get or synaptics or aptitude)

Try to reinstall gzip

> 
sudo aptitude update
sudo aptitude install gzip
sudo aptitude upgrade


Do you have got "build-essentials" package installed?

---

### Post by applegrew on 2007-06-22
> **Qu4k3R said:**
> Can you install software (even with that bug? with apt-get or synaptics or aptitude)

Try to reinstall gzip



Do you have got "build-essentials" package installed?
ok. I am first goin to reformat and install Ubuntu again.

---

### Post by applegrew on 2007-06-22
@Qu4k3R
Why will I need build-essentials? Furthermore when I try to install that I get the "package not found" message. I do remember that I installed it when I had ubuntu. Is the package sources different for ununtu and kubuntu?

And for your 1st question. Yes, I can still install softwares inspite of the error.

---

### Post by bapoumba on 2007-06-23
This error often comes from a problem between your apt and the repos. Usually some kind of proxy time out (from your ISP?). Please try changing http --> ftp in your sources.list.

---

### Post by applegrew on 2007-06-24
> **bapoumba said:**
> This error often comes from a problem between your apt and the repos. Usually some kind of proxy time out (from your ISP?). Please try changing http --> ftp in your sources.list.
Ok. Thanks I will try this out. BTW I tried to acces the erring link in my browser and it got downloaded instantly and I could successfuly extract it. 

Also I saw that the file lists are in bz2 format too. How can I tell apt to download the bz2 version instead of gz format.

---

