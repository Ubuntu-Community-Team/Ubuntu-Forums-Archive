---
title: "errors in terminal are in chinese"
date: 2014-10-09
forum: General Help
---

### Post by maxinstuff2 on 2014-10-09
So in a terminal I am getting error messages returned in Chinese. Which is very annoying.

Chinese langauge is installed so other users of the machine can use pinyin. That's it. I don't use it myself, and I have checked the locale settings and English has priority over chinese. Everything is in English apart from errors in a terminal (as far as I can tell).

Interestingly, it does NOT occur in the virtual console screens (Alt+f1-f6), only in the full desktop environment.
It happens in both Konsole and Xterm so I don't think it is a bug with a particular terminal app. 

A simple example is to just type rubbish in, I get chinese which means "command not found" instead of the english error:
```
max@max-Z87-D3HP:~$ sdfgndsg
sdfgndsg&#65306;&#26410;&#25214;&#21040;&#21629;&#20196;
max@max-Z87-D3HP:~$ dkjbd
dkjbd&#65306;&#26410;&#25214;&#21040;&#21629;&#20196;
max@max-Z87-D3HP:~$ lzsknfv
lzsknfv&#65306;&#26410;&#25214;&#21040;&#21629;&#20196;
```

---

### Post by bashiergui on 2014-10-11
Check both pam_environment and /etc/default/locale . Make sure they're both set to english.

 /etc/default/locale
LANG="en_US"
LANGUAGE="en_US:en"

 ~/.pam_environment
LANG=en_EN
Language=en_EN

---

### Post by maxinstuff2 on 2014-10-14
Looks fine to me.... both set to Australian english:
/etc/default/locale
```
LANG="en_AU.UTF-8"
LANGUAGE="en_AU:en"
```

I don't have ~/.pam_environment, but that might be because I am on kubuntu - I did find this:
~/.kde/env/setlocale.sh
```
export LANG=en_AU.UTF-8
export LANGUAGE=en:zh:en
export LC_NUMERIC=en_AU.UTF-8
export LC_TIME=en_AU.UTF-8
export LC_MONETARY=en_AU.UTF-8
export LC_PAPER=en_AU.UTF-8
export LC_IDENTIFICATION=en_AU.UTF-8
export LC_NAME=en_AU.UTF-8
export LC_ADDRESS=en_AU.UTF-8
export LC_TELEPHONE=en_AU.UTF-8
export LC_MEASUREMENT=en_AU.UTF-8
```

Which the only possible thing I see in there is the second line "export LANGUAGE=en:zh:en" which may or may not be an issue??
**EDIT:** I can resolve the issue by setting that line to "export LANGUAGE=en:en:en". HOWEVER, I now realise that either way pinyin is not even working in the first place!
Now I need to mess around with that to make sure it's set up properly....
**EDIT2:** So I ran ibus-settings and ibus was all chinese! I went into locale and removed chinese as a language and when I go back into ibus-settings it is now english again, as are all my terminal outputs - however I am unable to enable pinyin now... Not that it was working before.....

I'm at a loss really - any advice is appreciated.

---

### Post by bashiergui on 2014-10-14
I'm at a loss too. You might have a look at this guy's posts, it seems he's done some troubleshooting. You didn't say which version of Ubuntu you're using, I would recommend looking at his bug workarounds for your particular version

[http://www.pinyinjoe.com/linux/ubuntu-12-chinese-setup.htm](http://www.pinyinjoe.com/linux/ubuntu-12-chinese-setup.htm)

---

### Post by papibe on 2014-10-14
Hi maxinstuff2.

Have you custumize your shell config files?

Could you open a terminal, run these commands, and post back the results (you can copy/paste the output)?
```
diff ~/.bashrc /etc/skel/.bashrc 

diff ~/.profile /etc/skel/.profile

env | grep -i lang
```
Regards.

---

### Post by maxinstuff2 on 2014-10-15
Hi papibe :)

> **papibe said:**
> Have you custumize your shell config files?
Not for the terminal apps themselves (Xterm and Konsole) nor for bash. 
I am running kubuntu 14.04 (updated daily) and am using whatever the defaults are in terms of config for them.
I added chinese (simplified) language as 2nd priority through the gui in kde and then added pinyin in ibus-setup (also gui).

[QUOTE=papibe;13143596]
Could you open a terminal, run these commands, and post back the results (you can copy/paste the output)?
**diff ~/.bashrc /etc/skel/.bashrc** 
there was no output....

**diff ~/.profile /etc/skel/.profile**
also no output....

I guess at least one of the files in both diff comparisons don't exist on kubuntu/kde?
Or does diff only report DIFFerences? :)

**env | grep -i lang**
```
LANG=en_AU.UTF-8
GDM_LANG=en_AU
LANGUAGE=en:zh:en
```
en:zh:en, same as in my locale file.

terminal errors happen like above, but as stated, ibus is crapping out and doesn't know what language it is as well. The only other place I have found this is terminal errors.....
[IMG]http://i.imgur.com/Y1qIpse.png?1[/IMG]

---

