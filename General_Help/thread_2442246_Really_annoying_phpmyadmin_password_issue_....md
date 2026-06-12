---
title: "Really annoying phpmyadmin password issue ..."
date: 2020-05-01
forum: General Help
---

### Post by dbee on 2020-05-01
No matter what i do I can't seem to satisfy the phpmyadmin database install access password requirements.

```

mysql said: ERROR 1819 (HY000) at line 1: Your password does not satisfy the current policy requirements . 

```

I've tried cutting and pasting the password, I've searched mysql db for password requirements. Which by the way are set to LOW.

```

dara@dara-HP-Pavilion-Notebook-15-bc5xxx:~$ mysql --version
mysql  Ver 8.0.19-0ubuntu0.19.10.3 for Linux on x86_64 ((Ubuntu))

```

phpmyadmin wasn't in the repo so I got it from the ppa like so ...

```

sudo add-apt-repository ppa:phpmyadmin/ppa

```

I presume it's the latest version. For apache, i seem to get two results, one of them is an error ...

```

dara@dara-HP-Pavilion-Notebook-15-bc5xxx:~$ apache2 --version
[Fri May 01 15:22:51.191315 2020] [core:warn] [pid 11237] AH00111: Config variable ${APACHE_RUN_DIR} is not defined
apache2: Syntax error on line 80 of /etc/apache2/apache2.conf: DefaultRuntimeDir must be a valid directory, absolute or relative to ServerRoot
dara@dara-HP-Pavilion-Notebook-15-bc5xxx:~$ apache2 -v
Server version: Apache/2.4.41 (Ubuntu)
Server built:   2019-08-14T14:36:32

```

my root pass works fine for the mysql command line. I've tried to satisfy the mysql password policy. I've even cut and pasted the pass to be sure it's not a mistype ..

also, the mysql password policy ,,,
```

mysql> SHOW VARIABLES LIKE 'validate_password%';
+--------------------------------------+-------+
| Variable_name                        | Value |
+--------------------------------------+-------+
| validate_password.check_user_name    | ON    |
| validate_password.dictionary_file    |       |
| validate_password.length             | 8     |
| validate_password.mixed_case_count   | 1     |
| validate_password.number_count       | 1     |
| validate_password.policy             | LOW   |
| validate_password.special_char_count | 1     |
+--------------------------------------+-------+
7 rows in set (0.00 sec)


```

what in god's name am i doing wrong ?

---

### Post by ActionParsnip on 2020-05-01
What is the output of:

```

lsb_release -a; uname -a

```

Thanks

---

### Post by ActionParsnip on 2020-05-01
It is in the repos:
[https://packages.ubuntu.com/search?keywords=phpmyadmin&searchon=names&suite=all&section=all](https://packages.ubuntu.com/search?keywords=phpmyadmin&searchon=names&suite=all&section=all)

---

### Post by ActionParsnip on 2020-05-01
What are you wanting to use PHPMyAdmin to achieve please? There may be a sleeker solution to your needs

---

### Post by dbee on 2020-05-01
I have an old wordpress site with blog posts in it. I downloaded a backup of the sql file and opened it my mysql cli.

But it's full of html/css etc... and isn't transferable to my new site. The only thing to do is install a lamp server on my laptop and do a staging version of my old wordpress site.

But i'm having a hell of a time a) setting up phpmyadmin (which will come in useful in the future anyway) and b) installing the wordpress site wp-config.php file. It doesn't accept my login details.

Bummer. The only thing i can do now is try windows.
```

dara@dara-HP-Pavilion-Notebook-15-bc5xxx:~/Downloads$ lsb_release -a; uname -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 19.10
Release:	19.10
Codename:	eoan
Linux dara-HP-Pavilion-Notebook-15-bc5xxx 5.3.0-51-generic #44-Ubuntu SMP Wed Apr 22 21:09:44 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

```
how exactly do i install the 'bionic' package ? 
```

sudo apt-get install bionic

```
doesnt' seem to work

it would seem that mysql is having issues with connection strings. but the command line works fine. 

Thanks everyone

PS: apache logs are giving me a timeout script error 408 ...
```

tail access.log 
::1 - - [01/May/2020:18:29:43 +0100] "-" 408 0 "-" "-"
::1 - - [01/May/2020:18:29:44 +0100] "-" 408 0 "-" "-"

```
error logs are clear...

---

