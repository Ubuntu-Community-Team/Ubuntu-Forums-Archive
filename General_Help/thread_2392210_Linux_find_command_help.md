---
title: "Linux find command help"
date: 2018-05-17
forum: General Help
---

### Post by COKEDUDE on 2018-05-17
I am trying to find "php.ini". So I do the command:

```
find / "php.ini" 2>/dev/null
```
It is giving me thousands of files that do not contain "php.ini". What am I doing wrong?

---

### Post by yancek on 2018-05-17
Run the command:  ```
php --ini
```

This will output the information you want/need plus a number of additional ini files.  The good news is the file you want is at the top of the output as shown in my Ubuntu 16.04 below which shows the first two lines of output of the command. .  Yours of course, may be different.

```
Configuration File (php.ini) Path: /etc/php/7.0/cli
Loaded Configuration File:         /etc/php/7.0/cli/php.ini
```

---

### Post by papibe on 2018-05-18
Hi COKEDUDE.

Try this:
```
find / -name "php.ini"
```
Regards.

---

