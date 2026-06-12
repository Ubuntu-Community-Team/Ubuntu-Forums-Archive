---
title: "Locale problem"
date: 2016-03-30
forum: General Help
---

### Post by WDYSUN on 2016-03-30
Dear All

I have the following problem with a Ubuntu 14.04 system.

When I do 

```

$ locale
LANG=en_US.utf8
LANGUAGE=en_US
LC_CTYPE="en_US.utf8"
LC_NUMERIC=en_US.utf-8
LC_TIME=en_US.utf-8
LC_COLLATE="en_US.utf8"
LC_MONETARY=en_US.utf-8
LC_MESSAGES="en_US.utf8"
LC_PAPER="en_US.utf8"
LC_NAME="en_US.utf8"
LC_ADDRESS="en_US.utf8"
LC_TELEPHONE="en_US.utf8"
LC_MEASUREMENT=en_US.utf-8
LC_IDENTIFICATION="en_US.utf8"
LC_ALL=

```


but when I inspect ```
/etc/default/locale
```

I get 

```

LANG=en_US.utf8
LC_NUMERIC=en_US.utf-8
LC_TIME=en_US.utf-8
LC_MONETARY=en_US.utf-8
LC_MEASUREMENT=en_US.utf-8
LC_ALL=

```

how is this be possible, what I should do in order to get consistency with my locale settings. I tried to do what is suggested in here

[https://help.ubuntu.com/community/Locale](https://help.ubuntu.com/community/Locale)

but it doesn't work. What else?

The other thing which is not realy clear is the role of the file ```
~/.pam_environment
```, I don't have any locale settings there but googling a bit I have seen users that suggests to set locale there. What I understood is that this will only affects the user not system, is that correct?


Thanks
Pierre

---

### Post by X-RED_Tech on 2016-03-30
I see "en_US" all over the place. What inconsistency?
Besides, in Ubuntu, you can just go to System Settings > Language support and set everything there as you wish. The first language in the language tab defines the language for the system and in the second tab you should also choose accordingly. Apply, done.

---

### Post by WDYSUN on 2016-04-01
Hello  X-RED_Tech

thanks, sorry but I had a small accident and I stayed away from my desk. The inconsistency I mentioned is about the fact that what I see with ```
$ locale
``` is not exactly what's in ```
/etc/default/locale
```. Why is that?

I know System Settings > Language support, however settings in  "Language support" do not allow fine tuning like having a format for monetary units and another for date. I always configured loacales by editing  ```
/etc/default/locale
```, but it seems there is something going on on 14.04.

Regards
Pierre

---

### Post by X-RED_Tech on 2016-04-03
Sorry, that's beyond my knowledge. I hope someone else joins the discussion.

---

### Post by him610 on 2016-04-03
Not an expert in this area, but if one considers the directory that the file "/etc/default/locale" resides in - "default". What does that suggest?
These are *_default_* files. 
Take a look at "/etc/default/grub" Does it look anything like the grub file one actually boots with? True, there is some similarity, but then again it is a *default* file. 
The designers could have called it the "directory where basic files to build upon reside", but they choose a simpler name, *default*.

---

