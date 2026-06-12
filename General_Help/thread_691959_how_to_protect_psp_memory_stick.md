---
title: "how to protect psp memory stick"
date: 2008-02-09
forum: General Help
---

### Post by porloporlo on 2008-02-09
hello am a newie here and i have a problem
HOW CAN I MAKE THE CONTENT OF MY MEMORY STICKS TO BE READ ONLY FILES ie i dont want them to be copyable

thanks

---

### Post by pytheas22 on 2008-02-09
simply changing the file permissions isn't going to protect much, especially since your stick is probably formatted as FAT, which I think doesn't have any kind of permissions implemented in the filesystem.  Even if you were using a better kind of filesystem, it wouldn't be that hard to get past permissions.  Even if files are read-only they can still be copied and accessed.

For real protection you should simply encrypt the drive, which is pretty easy.  Take a look at Truecrypt [http://www.truecrypt.org/](http://www.truecrypt.org/) .  Then the files could only be read by someone with the password, and Truecrypt is really hard to crack if implemented properly.

Keep in mind that if you use a program like Truecrypt, you will not be able to access your encrypted files on a computer to which you don't have root/administrator privileges, because you need to install a driver to make it work.  Truecrypt does have a "traveller mode"  that allows it to work without actually installing anything permanently, but it still requires you to have administrator privileges.  There's no way around this if you want to have encrypted files.

---

### Post by porloporlo on 2008-02-11
thanks pytheas .thanks for your advice.but wat i want exactly was that the psp games i download which are in ISO flie .and are the content i dont want people to copy from my memory stick.

---

### Post by pytheas22 on 2008-02-11
ok, sorry, I was confused about what you meant.  I don't know anything about psp's but if you're storing these files on a regular memory stick (I guess that's what you mean?), encrypting it would still be the best way to protect it, probably.

---

### Post by porloporlo on 2008-02-11
thanks pyteas but if i encrypt it will the memory stick be able to read when insetred into the psp machine

---

### Post by pytheas22 on 2008-02-11
it would only work if you could install Truecrypt onto your psp.  I don't know anything about psp...I don't even understand what operating system they run (apparently you can install Linux on them, but you haven't done that, have you?)...so I can't tell you whether or not you could install Truecrypt on them, but a quick search for "truecrypt psp" doesn't look like you can.  There might be other encryption options that will work on psp, or NTFS has some decent encryption features that can be implemented through Windows, and maybe the psp could read them, since I think it does support NTFS, at least unencrypted.  Or perhaps psp has its own built-in encryption mechanisms that you could use to protect your flash drive.

Sorry I can't be of more help, but I'm sure you can find a better answer if you keep researching.  Or you could try a psp forum, since people there will probably know more about this than Ubuntu users.

---

