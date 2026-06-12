---
title: "how to encrypt a file , shell script"
date: 2008-06-25
forum: General Help
---

### Post by dapim on 2008-06-25
i would like to encrypt a file,
for example a shell script, and then execute it, is that possible?

---

### Post by utsuprainfra on 2008-06-25
if you write something interpreted, like perl maybe, and called your encrypted data through a perl encryption call.  i couldn't tell you how, i just feel like it's possible?

---

### Post by ghostdog74 on 2008-06-26
you usually don't need to do that. Assign the proper permissions to users that's going to use your script. Otherwise, provide an interface that requires authentication and limited functionality.

---

### Post by dapim on 2008-06-26
it is possible or no?

---

### Post by ghostdog74 on 2008-06-26
yes you can encrypt a shell script. its possible. However, i would advise against doing it.

---

### Post by spupy on 2008-06-26
This encrypts/decrypts files with GPG. The script needs the programs "zenity" and "gpg" installed.

```
#!/bin/bash
#GPG encryption
basename=`basename $1`
ext=`echo $basename | grep -o 'gpg$'`
if [[ $ext != "gpg" ]]
then
	dirname=`dirname $1`
	basename=`basename $1`
	cd $dirname
	zenity --question --title="GPG Encryption" --text="Encrypt this file now?\n$1" && (gpg -cq --force-mdc -o $1.gpg --yes $1 || zenity --error --title="Mismatch" --text="The passphrases you entered does not match!")
else
	zenity --question --title="GPG Decryption" --text="Decrypt this file now?\n$1" && (gpg -q --force-mdc --yes $1 || zenity --error --title="Mismatch" --text="Wrong password!")
fi
```

EDIT: Or perhaps you want to encrypt a shell script and run it? No way that I know. In that case your best bet is to compile a binary in some other language (C/C++/Java).

---

### Post by ghostdog74 on 2008-06-26
and then you have to spend time thinking about how to protect this script.  The best way is to get the security policy right.

---

### Post by dapim on 2008-06-26
how can i encrypt a shell script, some say possible others says to do it in another language??/

---

### Post by ghostdog74 on 2008-06-26
[if you are still wanting to do this]("http://aplawrence.com/Linux/shc.html")

---

