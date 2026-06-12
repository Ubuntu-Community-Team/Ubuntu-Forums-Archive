---
title: "Terminal problem with UTF-8"
date: 2013-04-23
forum: General Help
---

### Post by nkauppila on 2013-04-23
Hello everybody!

I have this really weird problem with my terminal. I want to use UTF-8 and that works everywhere else in my system, also with different users. Problem is that when I'm launching terminal (urxvt / xterm) UTF-8 is not working. If I launch new terminal from that terminal (typing urxvt or xterm) UTF-8 works fine. So new terminal inherits right settings from parent terminal. If I go to for example tty1 (pressing ctrl+alt+f1) UTF-8 is working fine, so apparently this problem is only when using terminal from X.

I have tried this using two different users and with other terminal works fine. Both users have same locale settings and I have tested also with bash and zsh. I even tried different desktop environments, awesome and xfce.

We also have Likewise-open which we are using for domain authentication.

Here is output when running locale
```

LANG=en_US.UTF-8
LANGUAGE=
LC_CTYPE=en_US.UTF-8
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=

```

As fas as I know LC_CTYPE should be environment variable that defines locale for urxvt.

And here is list of steps
[LIST=1]
[*]Launch terminal (from menu, mod4 + enter or any method)
[LIST=1]
[*]UTF-8 is not working
[/LIST]

[*]Write in that terminal urxvt or xterm to launch new terminal
[LIST=1]
[*]UTF-8 is working correctly
[/LIST]
[/LIST]

I really don't have any idea what might be wrong, but hopefully someone else knows :) And please ask more information if needed.

---

### Post by SifGrey on 2013-04-24
[SIZE=2][FONT=arial]In case the terminal you're using is lxterminal:

I found this on a Dutch blog: "In plaats van de standaard terminal emulator, lxterminal, gebruik ik inmiddels rxvt-unicode (urxvt) omdat lxterminal geen UTF-8 karakters aankan."
It basically states that the regular terminal (lxterminal) doesn't support UTF-8 characters and that he uses rxvt-unicode instead, so I think that would explain why it works when you run urxvt in a new terminal.

src= [/FONT][/SIZE][http://linux.autostatic.com/2011/12/13/een-maandje-met-lubuntu](http://linux.autostatic.com/2011/12/13/een-maandje-met-lubuntu)

---

### Post by nkauppila on 2013-04-24
Thaks for post, but I'm using urxvt as my terminal.

---

