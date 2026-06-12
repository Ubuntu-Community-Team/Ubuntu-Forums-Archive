---
title: "install curl extension?"
date: 2005-05-10
forum: General Help
---

### Post by MindSpore on 2005-05-10
Hi, I installed apache2/php4 using the instructions described in the Wiki @ [http://www.ubuntulinux.org/wiki/PHPDevelopmentHowTo](http://www.ubuntulinux.org/wiki/PHPDevelopmentHowTo)

My question is, how do I get the curl extension and install it so I can use it within php?

Thanks,
MindSpore

---

### Post by shakin on 2005-05-10
[QUOTE=MindSpore]Hi, I installed apache2/php4 using the instructions described in the Wiki @ [http://www.ubuntulinux.org/wiki/PHPDevelopmentHowTo](http://www.ubuntulinux.org/wiki/PHPDevelopmentHowTo)

My question is, how do I get the curl extension and install it so I can use it within php?

Thanks,
MindSpore[/QUOTE]
```

$ sudo apt-get install php4-curl

```

Search in Synaptic for "php4" and you'll find dozens of modules you can add.

---

### Post by MindSpore on 2005-05-10
Okay, I did that fine.  Now how do I get it to work for php?  I tried adding: extension=curl.so -- but, that did not seem to work.

Thanks,
MindSpore

---

### Post by MindSpore on 2005-05-10
Okay, well after getting permissions right, it works fine through apache via ([http://localhost/test.php)](http://localhost/test.php)).  However, it keeps giving me "call to undefined function curl_init" in Zend Studio when trying to debug.  Zend is set to use existing Apache2 installation... so I'm not sure why I'm getting that... any help?

I may have permission problems as I think I might have installed Zend as root.... any easy way to fix this without re-installing, if permissions/ownership is the problem?

---

### Post by Perro_Manson on 2008-05-11
> **MindSpore said:**
> Hi, I installed apache2/php4 using the instructions described in the Wiki @ [http://www.ubuntulinux.org/wiki/PHPDevelopmentHowTo](http://www.ubuntulinux.org/wiki/PHPDevelopmentHowTo)

My question is, how do I get the curl extension and install it so I can use it within php?

Thanks,
MindSpore

type in your terminal 

sudo apt-get install curl libcurl3 libcurl3-dev php5-curl php5-mcrypt

Regards, P M

---

