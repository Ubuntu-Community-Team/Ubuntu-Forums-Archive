---
title: "pdftk &quot;Error: Unable to find file.&quot; on ubuntu 20.04"
date: 2020-09-04
forum: General Help
---

### Post by me-xghozt on 2020-09-04
```
# pdftk test.pdf
Error: Unable to find file.
Error: Failed to open PDF file:
   test.pdf
Done.  Input errors, so no output created.


```

The file exists for sure. This also works fine on centos and ubuntu 18.04 (Other test servers I have).

I tried both the snap install and installing from package manager (current install): ```
sudo apt install pdftk
```

No matter what I do, I cannot get it to work. My guess is that it has something to do with the /tmp directory but I'm not sure. I'm running it as root from ~/

Everything I have found online is talking about 18.04 and none of those fixes seem to work either.

---

### Post by me-xghozt on 2020-09-04
Actually my problem seems to be a corrupt PDF. So it is working fine.

---

### Post by me-xghozt on 2020-09-04
If anyone else runs into this and you were the one making the PDF file. pdftk needs to be saved with "adobe/Acrobat 5.0".

---

### Post by monkeybrain20122 on 2020-09-05
I don't think pdftk is even available for Ubuntu20.04.

---

### Post by Impavidus on 2020-09-05
> **me-xghozt said:**
> I'm running it as root from ~/

This is unclear. ~ is your home directory, but when using sudo, it can be two different things, depending on the options you use for sudo (and on the release of Ubuntu, as sudo changed its behaviour in 20.04). When you run a command with sudo in your normal shell, the ~ gets expanded by the shell before it's passed on to sudo, so it refers to the home directory of the normal user, /home/username. If you run a root shell, it may refer to root's home directory instead, /root.

BTW, if the tool can find the file, but sees it's corrupted, I expect a different error message.

---

### Post by me-xghozt on 2020-09-14
> **Impavidus said:**
> This is unclear. ~ is your home directory, but when using sudo, it can be two different things, depending on the options you use for sudo (and on the release of Ubuntu, as sudo changed its behaviour in 20.04). When you run a command with sudo in your normal shell, the ~ gets expanded by the shell before it's passed on to sudo, so it refers to the home directory of the normal user, /home/username. If you run a root shell, it may refer to root's home directory instead, /root.

BTW, if the tool can find the file, but sees it's corrupted, I expect a different error message.

I tried both a user and root home directory. And I also expected a different error if the PDF was corrupt, but turns out it was due to the acrobat version the PDF was saved with. The error basically meant that it couldn't read/create any files.

> **monkeybrain20122 said:**
> I don't think pdftk is even available for Ubuntu20.04.

It is: [https://packages.ubuntu.com/search?keywords=pdftk](https://packages.ubuntu.com/search?keywords=pdftk)

I'm not able to build from source though.

---

