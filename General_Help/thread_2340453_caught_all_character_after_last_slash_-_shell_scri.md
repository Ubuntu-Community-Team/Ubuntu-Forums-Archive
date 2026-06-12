---
title: "caught all character after last slash - shell script"
date: 2016-10-18
forum: General Help
---

### Post by sed_faster on 2016-10-18
hello folks,

I pretend copy all characters after last slash from this string "sdfsdsfdf/sdfsdfsfasf/sdfgsdfgsgf/qwert"
According to this site: [http://stackoverflow.com/questions/9532654/bash-expression-after-last-specific-character](http://stackoverflow.com/questions/9532654/bash-expression-after-last-specific-character) or [http://stackoverflow.com/questions/3162385/how-to-split-a-string-in-shell-and-get-the-last-field](http://stackoverflow.com/questions/3162385/how-to-split-a-string-in-shell-and-get-the-last-field)
I need use this command 
```

${var#*/}

```

According to my understanding I need use parameter % if I want all values it was on right of the slash, right?
But I use this parameter but didn't put this works.

How should I use this command?
This command or expression, it is expression regular?

thanks

---

### Post by steeldriver on 2016-10-18
If you want to copy the characters to the right of the last / then you need to remove the **longest **substring matching */ from the left:

```
$ str="sdfsdsfdf/sdfsdfsfasf/sdfgsdfgsgf/qwert"
$ echo "${str##*/}"
qwert
```

It is different from regular expressions - see for example [Bash FAQ #100 'Extracting parts of strings']("http://mywiki.wooledge.org/BashFAQ/100#Extracting_parts_of_strings")

---

### Post by sed_faster on 2016-10-19
Thanks,
See the script in my github: [https://github.com/EdgarOliveira/scriptlinux/blob/master/exsh38.sh](https://github.com/EdgarOliveira/scriptlinux/blob/master/exsh38.sh)

---

