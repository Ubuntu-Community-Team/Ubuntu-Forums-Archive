---
title: "Compile and install to a folder in home without sudo"
date: 2008-05-11
forum: General Help
---

### Post by Osvaldo on 2008-05-11
Hi.

I need to compile gnuchess to a local folder.

I don't have an administrator account. Can I compile and install to a folder in home ?


./configure
make
make install 

doesn't work because I don't have permissions...

I've tried to google but didn't found an howto.

Thanks,

Best,

Osvaldo

---

### Post by didooofidooo on 2008-05-11
you can compile whatever you want but the problem is in installation.
you can't install applications for security.

---

### Post by spec-chum on 2008-05-11
The final part of that needs root permissions as it won't be able to write the binaries to the required directories for the install, so you should issue
```

sudo make install

```
to do the installation, so the process would be
```

./configure
make
sudo make install

```

---

### Post by Osvaldo on 2008-05-11
Hi.

Isn't it possible to install gnuchess inside the home, without administrator previleges ?

I need to install it in a ubuntu server, shared hosting.


Thanks, 

Best

Osvaldo

---

### Post by Winawer on 2008-05-11
I think that you should be able to replace ./configure with ./configure --prefix=/target/dir and then do make and make install without sudo.  


That's if I recall correctly, anyways...

---

### Post by Osvaldo on 2008-05-11
Hi,

It worked very well, thank you very much.


B--

Osvaldo

---

