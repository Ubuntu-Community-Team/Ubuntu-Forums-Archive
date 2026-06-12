---
title: "Help for shell-script on android"
date: 2013-09-13
forum: General Help
---

### Post by vonvic on 2013-09-13
I am trying to make a yes or no shell-script but it doesn't work on my rooted android phone. Right now it works on xubuntu but not on android.
Here's the script:

clear
echo Yes or no
Read answer

If [ $answer == yes ]; then
Echo you chose yes

elif [ $answer == no ]; then
echo you chose no

else
echo please pick yes or no

fi

But after that I get:
yn.sh[5]: syntax error: 'then' unexpected

---

### Post by Lars Noodén on 2013-09-13
What kind of error are you getting when you try to run it?

There are several typos involving capitalization, and *read* can be done differently, but the main problem looks like it is missing what it should run (#!)

```

#!/bin/sh
clear
read -p "Yes or No: " answer

if [ "yes" = "${answer}" ]; then
echo you chose yes

elif [ "no" = "${answer}" ]; then
echo you chose no

else
echo please pick yes or no

fi

```

Note that /bin/sh is the more standard, portable dash not the tricked out non-standard bash.

Edit: fixed string comparisons

---

### Post by vonvic on 2013-09-13
Now I get 
yn.sh[3] read: -p: no coprocess
yn.sh[5] syntax error: 'then' unexpected

---

### Post by Lars Noodén on 2013-09-13
My mistake, I rushed through that.  The [test comparison](http://manpages.ubuntu.com/manpages/raring/en/man1/test.1.html) for strings in the shell is = not ==  Also it should be wrapped in quotes.  So it should be written like this:
```

"yes" = "${answer}" 

```

See these links for more details:

[http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls)
[http://mywiki.wooledge.org/FullBashGuide](http://mywiki.wooledge.org/FullBashGuide)

---

