---
title: "why is it so difficult to install programs"
date: 2013-07-02
forum: General Help
---

### Post by philgo on 2013-07-02
I have tried lots of different versions of linux (now on xubuntu), however I always have the same problem.
I get to a link like [https://raw.github.com/dzach/nrfmon/master/binaries/nrfmon](https://raw.github.com/dzach/nrfmon/master/binaries/nrfmon) its supposed to be a binary file, I download it and it appears as a .txt file.
Now what, It seems like every version of linux has its own none standard way. Why can't we just have a standard installer instead of reading page after page of forums of instructions thats might work if you have the right version at the right time.
Dont get me wrong I want linux but why make its so hard?

---

### Post by tgalati4 on 2013-07-02
You need to add executable privilege to any file that you download and want to execute (run).  This is a security precaution.  Open a terminal:

```
cd Downloads
sudo chmod +x nrfmon
./nrfmon
```

Linux is not hard intentionally.  It just takes some time to learn it.  After 10 years of using Linux, it will be easy.

---

### Post by marianoa on 2013-07-02
You can also do it without using the terminal, right click on the file and select "Properties" in the popup menu. Then in the Permissions tab you can define the file as an executable file. At this point you can simply double click on the file to run the program.

---

### Post by grahammechanical on 2013-07-02
It is not difficult when we use the software centre.

---

