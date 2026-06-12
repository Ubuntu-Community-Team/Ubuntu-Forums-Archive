---
title: "LANG Environment Variable Is Blank"
date: 2014-03-20
forum: General Help
---

### Post by boot3r on 2014-03-20
Hello All,

I have a program that is expecting a certain format in the LANG env. var. provided by the system and as the title says this env. var. is blank.  Output from the locale command:

```

[PROMPT]:~$ locale
LANG=
LANGUAGE=
LC_CTYPE="POSIX"
LC_NUMERIC="POSIX"
LC_TIME="POSIX"
LC_COLLATE="POSIX"
LC_MONETARY="POSIX"
LC_MESSAGES="POSIX"
LC_PAPER="POSIX"
LC_NAME="POSIX"
LC_ADDRESS="POSIX"
LC_TELEPHONE="POSIX"
LC_MEASUREMENT="POSIX"
LC_IDENTIFICATION="POSIX"
LC_ALL=

```

I have tried looking online but no where has any help.  Currently I don't have a ~/.pam_environment file so the info for that was useless.  Both of the files **/etc/default/locale **and **/etc/environment** have the following set.

```

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANGUAGE="en_US:en"
LANG="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"

```

Any help would be greatly appriciated.

Thanks!

EDIT:  I also noticed that something is obviously overriting the values from the files **/etc/default/locale **and **/etc/environment** but I have no idea where that is....

---

### Post by coldcritter64 on 2014-03-21
> **boot3r said:**
> Hello All,

I have a program that is expecting a certain format in the LANG env. var. provided by the system and as the title says this env. var. is blank.  Output from the locale command:

```

[PROMPT]:~$ locale
LANG=
LANGUAGE=
LC_CTYPE="POSIX"
LC_NUMERIC="POSIX"
LC_TIME="POSIX"
LC_COLLATE="POSIX"
LC_MONETARY="POSIX"
LC_MESSAGES="POSIX"
LC_PAPER="POSIX"
LC_NAME="POSIX"
LC_ADDRESS="POSIX"
LC_TELEPHONE="POSIX"
LC_MEASUREMENT="POSIX"
LC_IDENTIFICATION="POSIX"
LC_ALL=

```

I have tried looking online but no where has any help.  Currently I don't have a ~/.pam_environment file so the info for that was useless.  Both of the files **/etc/default/locale **and **/etc/environment** have the following set.

```

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANGUAGE="en_US:en"
LANG="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"

```

Any help would be greatly appriciated.

Thanks!

EDIT:  I also noticed that something is obviously overriting the values from the files **/etc/default/locale **and **/etc/environment** but I have no idea where that is....

Try adding the 2 lines below to the end of your ~/.profile file, save the file, log out then log back in again and the variables will be set for your user profile,

```
export LANG=en_US.UTF-8
export LANGUAGE=en_US.UTF-8
```

To check open a terminal and issue the code
```
echo $LANG && echo $LANGUAGE
``` both should return "en_US.UTF-8" with the 2 export commands in place and active. Or alternatively run the "locale" command again and check the difference. Cheers.

---

### Post by boot3r on 2014-03-21
Thanks coldcritter64!  This worked like a charm!

---

