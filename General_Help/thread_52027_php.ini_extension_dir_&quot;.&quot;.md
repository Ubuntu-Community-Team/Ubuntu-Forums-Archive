---
title: "php.ini extension_dir &quot;./&quot;"
date: 2005-07-26
forum: General Help
---

### Post by cage on 2005-07-26
Hello,

in the php.ini the extension_dir is set to "./"
I want to put a new module inside there (dbg-debugger), but I don't know which directroy is meant.
I tried /etc/php4/apache/ and /usr/lib/php4/... as well as /usr/lib/apache/1.3/ where the libphp4.so is located. Still no success.
Please give me a hint, which directory is meant by "./"

For the real linuxers this is probably a very stupid question, but I'm simply unable to find this (current = ./) path.

Thanks in advance,
Carsten

---

### Post by psysmic on 2006-10-12
new to *nix myself so take this with a grain of salt

extension_dir= "/usr/lib/php5/20051025"

yours should be a little different if you're running php4

then restart apache

/etc/init.d/apache2 restart

---

### Post by dboyer02 on 2006-10-22
I'm having the same problem, but this solution has not helped me for some reason. I did a LAMP install of Ubuntu Server 6.06, added only Xubuntu desktop, did an update on all programs and have been using the [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) guide slowly and carefully.

My default extension directory also shows "./" However when I do a "locate mysql.so" it returns 2 directories:

/usr/lib/perl5/auto/DBD/mysql/mysql.so (106.8kB) and
/usr/lib/php5/20051025/mysql.so (43.7kB)

I've tried using entering them both, one at a time, into php.ini, saving, then restarting Apache with "sudo /usr/sbin/apache2ctl restart". The only thing I noticed that someome above did differently was to use a different Apache restart command. (etc/init.d/apache2 restart)

Any idea why this isn't working for me?

---

### Post by aeon on 2006-10-22
someone hit me with a +20 sword of smithing if i'm wrong, but the ./ directory refers to the current directory of the referring file.

so, if /home/user/somedir/example.file refers to ./ that would be /home/user/somedir/ in this case.. 

i've been coding C++ for 10+ hours now and its 5 in the morning so i might be way off on this one...


-aeon

---

