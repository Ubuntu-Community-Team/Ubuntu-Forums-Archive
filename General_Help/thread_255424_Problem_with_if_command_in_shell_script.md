---
title: "Problem with if command in shell script"
date: 2006-09-11
forum: General Help
---

### Post by jamadagni on 2006-09-11
I have attached a shellscript and a couple of associated files. This script is meant to collect the latest additions to the apt cache and make an archive copy of it in a directory under /home wherever this script is placed. This was made for Kubuntu 6.06.1 but might possibly work without modifications on other *buntu-s as well.

Now the if block:

```
if ["$(ls)" = ""]; then
	echo "There are no extra packages in the apt cache."
fi
```

is meant to give a meaningful error if no new packages are found in the cache. However, if there are new packages, the if block gives an error:

```
./collect-latest-additions: line 22: [bind9-host_1%3a9.3.2-2ubuntu1.1_i386.deb
dnsutils_1%3a9.3.2-2ubuntu1.1_i386.deb
xserver-xorg-core_1%3a1.0.2-0ubuntu10.4_i386.deb: command not found
```

I understand I've done some mistake in the if block within the brackets but don't know how to correct it. Please help.

P.S: I'm new to shellscripting so I'd appreciate any help and useful pointers as to how to improve the script. In particular, the trick with the symlinks seems to be somewhat awkward. Is there a better way?

P.P.S: Crazy forum rules don't allow files with .sh or no extension as attachments. But actually Photoshop files are allowed. Seriously!? Photoshop files are allowed on a Linux forum but shell scripts are not? Crazy!

---

### Post by ruedu on 2006-09-11
Try modifying the if block to look like this

```
 if [ "$ls" = "" ]; then
    echo "There are no extra packages in the apt cache."
fi
```

EDIT: Notice that the [ and ] have spaces surrounding them, they must with only exception being the ];  You can, optionally, leave out the ; and instead put then on the next line, it would then read as follows

```

if [ "$ls" = "" ]
then
   echo "..."
fi

```

---

### Post by moma on 2006-09-11
```
if [ -z  "$(ls)" ]; then
	echo "There are no extra packages in the apt cache."
	exit 1
fi
```

---

### Post by jamadagni on 2006-09-11
Thanks people! I really need to learn a lot. What do you recommend as reading to get a good (if not thorough) knowledge of shell-scripting?

---

### Post by moma on 2006-09-12
The ABS guide
o---> [http://howtos.linux.com/guides/abs-guide/index.shtml](http://howtos.linux.com/guides/abs-guide/index.shtml)
+
o---> [http://cfaj.freeshell.org/shell/](http://cfaj.freeshell.org/shell/)

---

### Post by amo-ej1 on 2006-09-12
Bash guide for beginners:

[http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html)

Perhaps a better start than the abs ?

---

### Post by jamadagni on 2006-09-12
Thanks people.

---

