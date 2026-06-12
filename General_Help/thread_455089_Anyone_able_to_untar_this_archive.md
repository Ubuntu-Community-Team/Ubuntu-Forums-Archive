---
title: "Anyone able to untar this archive?"
date: 2007-05-26
forum: General Help
---

### Post by Lucifiel on 2007-05-26
[http://www.melodymachine.com/sfark.htm](http://www.melodymachine.com/sfark.htm)

Hey, I'm trying to untar sfArkXTc but keep running into tar archive errors. Have downloaded it with 2 different browsers. And untarred using tar -zxvf and tar -xvf and tar -xvzf . 

So, anyone able to download and untar it?




Thank you! :)

---

### Post by Swab on 2007-05-26
No, it seems to be corrupted.

---

### Post by mips on 2007-05-26
I can gunzip it and then untar it but I get a file that is useless.

---

### Post by Lucifiel on 2007-05-26
> **Swab said:**
> No, it seems to be corrupted.

Blasted!!!! 

Oh, no!!! :p

---

### Post by Lucifiel on 2007-05-26
> **mips said:**
> I can gunzip it and then untar it but I get a file that is useless.

Really? *goes to find out more about gunzip*

---

### Post by GeneralZod on 2007-05-26
It's actually a tar.gz.gz - you need to gunzip it, gunzip the resulting file, then untar.  The result is an executable file:

```

[~/downloads]>./sfarkxtc
======================================================================
sfArkXTc 1.03 (using sfArkLib version: 224)
copyright (c) 1998-2004 melodymachine.com, free for non-commercial use
======================================================================
Please specify filename(s) on the command line, i.e:
./sfarkxtc <InputFilename> [OutputFilename]

```

---

### Post by Lucifiel on 2007-05-26
> **GeneralZod said:**
> It's actually a tar.gz.gz - you need to gunzip it, gunzip the resulting file, then untar.  The result is an executable file:

```

[~/downloads]>./sfarkxtc
======================================================================
sfArkXTc 1.03 (using sfArkLib version: 224)
copyright (c) 1998-2004 melodymachine.com, free for non-commercial use
======================================================================
Please specify filename(s) on the command line, i.e:
./sfarkxtc <InputFilename> [OutputFilename]

```

Yuppers, Yeah well, turns out that I don't need this program but still, I learnt a new command. :) 

Yup. Btw, ehhh.. sorry for posting in the wrong forum, guys! :p

---

