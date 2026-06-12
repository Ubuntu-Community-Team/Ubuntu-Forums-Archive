---
title: "Adobe 8.1"
date: 2008-05-01
forum: General Help
---

### Post by Audrey on 2008-05-01
My bank insisted that I get Adobe 8.1 so that I can print an e-application form.  I downloaded one and yes I had to pay for it, but I don't have a program to install it with.  Can anyone tell me what program I need and where to get it?  Audrey

---

### Post by FuturePilot on 2008-05-01
You can find Adobe Reader in the Medibuntu repositories. 
First add the repo
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list

```
Then 
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```
And to install it
```
sudo apt-get install acroread acroread-escript acroread-plugins mozilla-acroread
```

---

### Post by warp99 on 2008-05-01
> **Audrey said:**
> My bank insisted that I get Adobe 8.1 so that I can print an e-application form.  I downloaded one and yes I had to pay for it, but I don't have a program to install it with.  Can anyone tell me what program I need and where to get it?  Audrey

The medibuntu repositories already have Adobe Acrobat 8.1 available for install:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

So you can enable them per the instructions and install Acrobat Reader 8.1.

---

