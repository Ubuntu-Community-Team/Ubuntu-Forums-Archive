---
title: "VMWare Server stupid, simple problem"
date: 2006-07-05
forum: General Help
---

### Post by snellgrove on 2006-07-05
Well, I dont know if this is Ubuntu's fault or not..

But, when downloading the [VMWare Server](http://www.vmware.com/download/server/) for Linux, which is around 100mb (strangely 50mb less than the Windows one)

It downloads just fine, but when I come to unpack it (its a tar.gz file) I get the following, if I view the 'command line output' of File Roller:

```
tar: Skipping to next header

gzip: stdin: invalid compressed data--crc error

gzip: stdin: invalid compressed data--length error
tar: Child returned status 1
tar: Error exit delayed from previous errors

```

Does this happen for other people? did VMWare post a dud? or is my File Roller borked.

I tried clearing my internet cache (Firefox, ctrl+shift+delete) just in case a corrupt download was being brought from the cache.

---

### Post by peter72 on 2006-07-05
It looks like the download never completed, or was corrupt.

---

### Post by scxtt on 2006-07-05
i just downloaded it, extracted fine for me (w/ File Roller 2.14.3) ... i didn't install it, i'm waiting til my current version expires ...

---

### Post by snellgrove on 2006-07-05
how odd.

it does complete though, no errors during download.

damn Firefox :( 

I cant figure out how to WGET it, because the link re-directs. you dont end up with the correct file if you copy the address of the file on the website. very annoying.

oh well, i'll keep trying :)

---

### Post by mbeierl on 2006-07-05
I've seen firefox automatically decompress the file, yet still save it with the .gz extension.  Have you tried tar xvf instead?

---

### Post by snellgrove on 2006-07-06
I eventually gave up on damn Firefox, and downloaded it with Epiphany.

I used file-roller and it extracted just fine

now have the ol' VMMon problem - it cant build itself a module for my kernel or something. plenty of threads to look at, I think I need to export CC and use a different GCC

need to know what version of GCC my kernel (latest one, the 25-386) was built with before I can do that though.

---

### Post by scxtt on 2006-07-06
it should tell you in the error message ...

---

