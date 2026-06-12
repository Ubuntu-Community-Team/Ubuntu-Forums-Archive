---
title: "Install Kompozer?"
date: 2007-02-08
forum: General Help
---

### Post by Mookawaka on 2007-02-08
I would like to install Kompozer on my 6.06 system after trying out Nvu.   I liked the Nvu program but its bugs make it rather unresponsive and tend to crash on my computer.

The source code tarball found at kompozer.net is something of a mystery to me.  I am not very familiar in how to compile programs from source to begin with, and this particular one seems to be packaged differently.

If anyone who has insight into this could walk me through the process it would be much appreciated.  I am a big fam of commands that could be cut and pasted into the terminal.

---

### Post by Mookawaka on 2007-02-10
[http://www.getdeb.net/]("http://www.getdeb.net/")

I found this page which has helped me greatly in my efforts to get programs outside of the repositories.

---

### Post by srf21c on 2007-02-26
Here's how I did it manually

1)  Download and untar kompozer tarbal to your home directory.
```
wget http://prdownloads.sourceforge.net/kompozer/kompozer-077-i686.tgz?download
tar xzvf kompozer-077-i686.tgz

```
2)  Rename it to nvu-1.0 and move it under /usr/lib
```
sudo mv kompozer /usr/lib/nvu-1.0

```
3)  Copy the file /usr/lib/nvu-1.0/kompozer to /usr/bin
```
sudo mv /usr/lib/nvu-1.0/kompozer /usr/bin

```
4)  [Create a shortcut]("http://www.ubuntuforums.org/showthread.php?t=366475&highlight=kompozer") to /usr/bin/kompozer.  

 You can find a purty icon for the shortcut under /usr/lib/nvu-1.0/icons

---

### Post by vigi1 on 2007-04-18
It works!!!!!!!!!! Thank you very much.

---

### Post by aysiu on 2007-04-18
For future reference, I've written a page on this:
[https://help.ubuntu.com/community/Kompozer](https://help.ubuntu.com/community/Kompozer)

---

