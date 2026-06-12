---
title: "Can I latex a file encrypted with vim?"
date: 2013-01-03
forum: General Help
---

### Post by jsmidt on 2013-01-03
I would like to make an encrypted file that I can latex.  vim has a nice blowfish encryption built in that I would like to use to encrypt the file.  However if I run latex on the file it fails because it sees gibberish.

Anyone have any ideas how I could use vim to encrypt the file but still have a way of compiling the file with latex?

---

### Post by hawthornso23 on 2013-01-03
The bottom line is that if the file is encrypted then it must be decrypted before latex can compile it. You could perhaps construct a single commandline instruction to do this by using a pipe to send the output of decryption to latex.  It does seem like a very odd thing to want to do though. Usually when people want to do such odd things I find that they have a perfectly sane objective in mind but have chosen to go about it in a strange way. So could you perhaps explain why you want to do this.  What are you hoping to achieve? I suspect there is likely to be an alternative means of achieving your real objective in a simpler fashion.

---

### Post by conradin on 2013-01-03
For your scripting pleasure:
[http://manpages.ubuntu.com/manpages/dapper/man1/bcrypt.1.html](http://manpages.ubuntu.com/manpages/dapper/man1/bcrypt.1.html)

---

