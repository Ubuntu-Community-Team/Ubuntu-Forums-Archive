---
title: "Where is php.ini ?"
date: 2005-05-23
forum: General Help
---

### Post by Blues- on 2005-05-23
Hi all .. installed Apache2 and PHP5 on my box with the help from [http://www.ubuntulinux.org/wiki/PHP5FromSource](http://www.ubuntulinux.org/wiki/PHP5FromSource) , everything works great but .. phpinfo() says that Configuration File (php.ini) Path points to -> /usr/local/lib.
But there is no php.ini file there .. I did a full system search for php.ini but no file seems to exist ...

Can anyone tell me what happened to the php.ini file or do i have to create the file myself ? On my old box running FC2 i build php from source and the php.ini got created like expected, I'm rather confused by this.

Thanks in advance,
Blues-

---

### Post by XDevHald on 2005-05-23
[QUOTE=Blues-]Hi all .. installed Apache2 and PHP5 on my box with the help from [http://www.ubuntulinux.org/wiki/PHP5FromSource]("http://www.ubuntulinux.org/wiki/PHP5FromSource") , everything works great but .. phpinfo() says that Configuration File (php.ini) Path points to -> /usr/local/lib.
But there is no php.ini file there .. I did a full system search for php.ini but no file seems to exist ...

Can anyone tell me what happened to the php.ini file or do i have to create the file myself ? On my old box running FC2 i build php from source and the php.ini got created like expected, I'm rather confused by this.

Thanks in advance,
Blues-[/QUOTE]
 You will need to download the file it's self, try using the following link and see if you can find the file inside the tar.bz2 or gz.

[http://www.php.net/downloads.php](http://www.php.net/downloads.php)

---

### Post by sassi67 on 2005-05-24
Didi you try to type:
find / -name php.ini
from command line?

---

### Post by Blues- on 2005-05-24
Followed BB's instructions and just created the file,
everything works as should now ..
Thanks for the help guys ..

---

### Post by Linkz57 on 2008-05-04
I found it at etc/php5/apache2/php.ini

---

