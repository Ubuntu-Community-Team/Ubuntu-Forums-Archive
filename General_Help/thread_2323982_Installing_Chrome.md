---
title: "Installing Chrome"
date: 2016-05-09
forum: General Help
---

### Post by Donnie Love on 2016-05-09
I can't figure out how to install Chrome browser in Lubuntu.

---

### Post by oldrocker99 on 2016-05-09
Here's a link with instructions. Ubuntu MATE has a Welcome screen that installs Chrome with one click, by the way.

[http://www.ubuntuupdates.org/ppa/google_chrome](http://www.ubuntuupdates.org/ppa/google_chrome)

---

### Post by Impavidus on 2016-05-10
Keep in mind that you must have a 64 bit system to make chrome work.

---

### Post by Donnie Love on 2016-05-10
The last command is:

```

sudo apt-get install <package name>
```

and then there is a list of packages. I tried all of them and I get this:

```
E: Unable to locate package google-chrome-beta
```

---

### Post by Donnie Love on 2016-05-10
Ubuntu MATE is a whole operating system, isn't it? I don't want to go through all that. Unlike most Ubuntu users I get no thrill out of installing whole operating systems every other week. I'm still trying to recover from the last one.

---

### Post by Donnie Love on 2016-05-10
> **Impavidus said:**
> Keep in mind that you must have a 64 bit system to make chrome work.

Please explain.

---

### Post by Impavidus on 2016-05-11
> **Donnie Love said:**
> Please explain.

Google stopped support for the 32 bits version of chrome. But if you run 64 bit Lubuntu that doesn't matter.

---

### Post by Donnie Love on 2016-05-11
> **Impavidus said:**
> If you run 64 bit Lubuntu that doesn't matter.
How would I find out which I'm using?

---

### Post by vasa1 on 2016-05-11
> **Donnie Love said:**
> How would I find out which I'm using?

Run **uname -a** and post the output here.

---

### Post by Donnie Love on 2016-05-11
Here is the output to that:
```
Linux R103 3.19.0-58-generic #64~14.04.1-Ubuntu SMP Fri Mar 18 19:05:42 UTC 2016 i686 athlon i686 GNU/Linux
```
But it doesn't matter now; I got it to work. I found something called "GDebi Package Installer" and I was able to use that.
So never mind all my dumb questions. :0>

---

### Post by Bucky Ball on 2016-05-11
Please mark the thread as solved to help others. See the link in my signature at the bottom of this post for how if you are unsure. Thanks.

---

### Post by deadflowr on 2016-05-11
> **Donnie Love said:**
> Here is the output to that:
```
Linux R103 3.19.0-58-generic #64~14.04.1-Ubuntu SMP Fri Mar 18 19:05:42 UTC 2016 i686 athlon i686 GNU/Linux
```
But it doesn't matter now; I got it to work. I found something called "GDebi Package Installer" and I was able to use that.
So never mind all my dumb questions. :0>

What it's worth: your running 32-bit.
i686 is 32-bit

---

