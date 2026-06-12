---
title: "pdftk"
date: 2018-05-31
forum: General Help
---

### Post by sed_faster on 2018-05-31
Hllo folks,

How can I installed pdftk?
```

$ sudo apt-get install pdftk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package pdftk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'pdftk' has no installation candidate

```

Maybe is related to this:
```

$ sudo apt-get update
Hit:1 http://pt.archive.ubuntu.com/ubuntu bionic InRelease
Hit:2 http://pt.archive.ubuntu.com/ubuntu bionic-updates InRelease                                                                                                                           
Hit:3 http://pt.archive.ubuntu.com/ubuntu bionic-backports InRelease                                                                                                                         
Get:4 http://security.ubuntu.com/ubuntu bionic-security InRelease [83,2 kB]                                                                                                                                       
Ign:5 http://ppa.launchpad.net/webupd8team/sublime-text-2/ubuntu bionic InRelease                                                                                                                                 
Err:6 http://ppa.launchpad.net/webupd8team/sublime-text-2/ubuntu bionic Release                                                                                                                 
  404  Not Found [IP: 91.189.95.83 80]
Hit:7 http://archive.canonical.com bionic InRelease                                                                                           
Hit:8 https://download.sublimetext.com apt/stable/ InRelease                                               
Get:9 http://security.ubuntu.com/ubuntu bionic-security/main amd64 DEP-11 Metadata [204 B]
Get:10 http://security.ubuntu.com/ubuntu bionic-security/universe amd64 DEP-11 Metadata [2456 B]
Reading package lists... Done                                         
E: The repository 'http://ppa.launchpad.net/webupd8team/sublime-text-2/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```

How can I execute this command:
```

$ lsb-release -v

Command 'lsb-release' not found, did you mean:

  command 'lsb_release' from deb lsb-release

Try: sudo apt install <deb name>

```

```

$ uname -a
Linux xxx 4.15.0-22-generic #24-Ubuntu SMP Wed May 16 12:15:17 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

```

Thanks

---

### Post by deadflowr on 2018-05-31
pdftk is now gone from the repos
[https://ubuntuforums.org/showthread.php?t=2390293&highlight=pdftk]("https://ubuntuforums.org/showthread.php?t=2390293&highlight=pdftk")
And you need to disable the webupd8 sublime ppa as that hasn't yet been updated for bionic, yet.
Maybe it will, but as of now, it is not.

---

### Post by sed_faster on 2018-05-31
This means I can't installed pdftk, at least for now?
(sorry, but my level english is not the best).

Which alternative have I to the pdftk through terminal? I am trying PdfShuffler I am felling like a windows user :)

---

### Post by monkeybrain20122 on 2018-05-31
> **Edgar_Oliveira said:**
> This means I can't installed pdftk, at least for now?
(sorry, but my level english is not the best).

Which alternative have I to the pdftk through terminal? I am trying PdfShuffler I am felling like a windows user :)

The last post from deadflower's link tells you how to install pdftk in 18.04. 

I never used pdftk with command line, I used pdfchain which is a gui for pdftk. I can use the cmd but I would rather use my brain  and time for something else than remembering cryptic options and commands or googleling for something that I use only once in a blue moon :).  I only use it for spliting and merging pdf files so pdfchain is good enough for me,--it doesn't have all the pdftk options. pdfshuffler would meet my needs.

---

### Post by dragonfly41 on 2018-05-31
I found this tip to merge multiple pdf files in lieu of pdftk

[https://stackoverflow.com/questions/2507766/merge-convert-multiple-pdf-files-into-one-pdf](https://stackoverflow.com/questions/2507766/merge-convert-multiple-pdf-files-into-one-pdf)

```
gs -dBATCH -dNOPAUSE -q -sDEVICE=pdfwrite -sOutputFile=merged.pdf mine1.pdf mine2.pdf
```

---

### Post by vanadium on 2018-06-01
qpdf (command line) can probably do all pdftk could.

---

### Post by sed_faster on 2018-06-02
Hello,

When I was reading this thread ([https://ubuntuforums.org/showthread.php?t=2390293&highlight=pdftk](https://ubuntuforums.org/showthread.php?t=2390293&highlight=pdftk)), share by deadflowers and also vanadium, I just know qpdf. I am enjoying this software.
I still trying install pdftk. I like their syntax. My level english it is low, someone wants help me guide in what I lockup and which commands/script/software I should use to fix this issue?

Thanks

---

### Post by sed_faster on 2018-06-18
Hello,

I was trying install pdftk on my 18.04 bionic but I can't handle this. Due to my level of english and the difficult with the system. Anyone can help me with this situation? I downloaded this archive "https://launchpad.net/ubuntu/+source/pdftk/2.02-4build1/+build/10581759/+files/pdftk_2.02-4build1_amd64.deb" but this return this message when I tried execute [https://snag.gy/RDZap1.jpg](https://snag.gy/RDZap1.jpg)

Thanks

---

### Post by nlee2 on 2018-06-18
To install pdftk from artful on bionic, you need to install **libgcj17-dev And gcc-libs first**

+1 I needed these for deps.
**libgcj17-dev And gcc-libs** Found here: [https://packages.ubuntu.com/artful/libgcj17-dev](https://packages.ubuntu.com/artful/libgcj17-dev)

---

### Post by sed_faster on 2018-06-18
Finally I got resolve the problem! I followed the tip Claus7:

```

sudo dpkg -i gcc-6-base_6.4.0-8ubuntu1_amd64.deb
sudo dpkg -i libgcj-common_6.4-3ubuntu1_all.deb
sudo dpkg -i libgcj17_6.4.0-8ubuntu1_amd64.deb
sudo dpkg -i pdftk_2.02-4build1_amd64.deb

```

Thanks you all

---

