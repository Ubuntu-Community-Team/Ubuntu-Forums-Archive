---
title: "encrypt or not encrypt?"
date: 2013-06-02
forum: General Help
---

### Post by mrsanna1 on 2013-06-02
Hello, I've installed the new raring ubutu, it's really awesome.
During installation it ask if I want or not encrypt my home.
I use the notebook, in which I've installed ubuntu, only at home.
Do you suggest to encrypt?

---

### Post by Impavidus on 2013-06-02
The advantage of encryption is that if your notebook gets stolen your data is still not in stranger's hands. On the other hand, it can be somewhat slower and if you lose your password or your system crashes it may be very difficult to recover any data.  You have to decide, how much sensitive data is in your home directory and how likely is it that your laptop gets stolen.

I think it's also possible to encrypt a single directory inside your home directory, instead of everything.

---

### Post by Mark Phelps on 2013-06-02
Personally, I would advise against encryption -- at least -- in terms of a whole partition or filesystem.  IF there are filesystem problems down the road, having it encrypted is going to seriously complicate repairs.

If you need to encrypt sensitive data, then encrypt a file -- that's what I do.

Realize that if someone steals your notebook, they're more likely to do that for the hardware, or to sell it.  IF your data is in an encrypted file on the drive, they still won't be able to get to it easily and would more likely, if they want to keep the notebook for their use, erase the file or replace the hard drive.

---

### Post by techvish81 on 2013-06-02
how to encrypt a file/folder?

---

### Post by Hekabe on 2013-06-02
I don't know if out-of-the-box Raring has a built-in program, but truecrypt has always worked decently well for me, and it's cross-platform.

---

### Post by dave0109 on 2013-06-03
To simply encrypt a file containing sensitive information, I use GPG.

To encrypt a directory where I put other files, I use Truecrypt.

---

### Post by HiImTye on 2013-06-03
encrypting your drive will give you better read/write speeds, but it is also more demanding on the CPU and requires more memory. it will also add a layer of complexity down the road. so, if you're concerned about read/write speeds, and have the CPU/memory to spare, or if you want to protect your data, then it's a good idea, just keep in mind that it will be more complicated to deal with later.

as others have said above, you can also encrypt individual files or folders. there's a pretty decent one in last weeks Linux Action Show but I can't for the life of me remember what it's called.

edit: i checked the show notes, it's called gnome-encfs manager [http://www.libertyzero.com/GEncfsM/](http://www.libertyzero.com/GEncfsM/)
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

