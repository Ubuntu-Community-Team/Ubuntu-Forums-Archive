---
title: "Ubuntu (and opensuse) ignore one ram stick all of a sudden"
date: 2019-02-21
forum: General Help
---

### Post by brodriguesco on 2019-02-21
Hi all

I have a dual boot system with Ubuntu and Opensuse and all of a sudden both OSes ignore one of my ram sticks. I have to Corsair 16gb ram sticks that were working perfectly fine up until now. I removed them, re-seated them, tested them one by one; everything works.
This does not seem to be a hardware fault; I did not change anything to my setup, nor did I update the bios nor anything.

Here's some info:

```
(base) cbrunos@ubantoo:~$ free -m
              total        used        free      shared  buff/cache   available
Mem:          16035         797       14330          81         907       14809


```

dmesg output: [https://gist.github.com/b-rodrigues/207c9a45bbcdea57f421e781339c2751](https://gist.github.com/b-rodrigues/207c9a45bbcdea57f421e781339c2751)
lshw output: [https://gist.github.com/b-rodrigues/29e052ecf5f81c8f9692391bdcc52e4d](https://gist.github.com/b-rodrigues/29e052ecf5f81c8f9692391bdcc52e4d)

Nothing seems to be out of the ordinary.

I see both sticks in the BIOS, and as mentioned above, both work individually. I will try running memtest from a live cd and come back with updated results, but I fear that memtest won't help.

---

