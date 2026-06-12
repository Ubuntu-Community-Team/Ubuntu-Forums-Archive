---
title: "ca keyboard layout (french canada) problem"
date: 2015-07-13
forum: General Help
---

### Post by palipeaublasee on 2015-07-13
Hi,

While working on an unrelated (I think) problem, I did something that made my 'é,É'
 key stop working.  It produces '?' in the terminal, and nothing in mousepad (default
 text editor in Xubuntu).  Also my "Alt Car" (Alt Gr or AltGr on other keyboards)
does not work on some keys.

Physically it is a qwerty bilingual keyboard, which was working fine in XP, Xubuntu
12.04, and Xubuntu 14.04 which is my current o/s.  I even had both fr_CA and en_US
working properly and was able to switch between them.  Now I only have fr_CA, which
is all I want, and it's giving me this problem.

What I find strange is that it is working fine in Firefox and in Abiword.  I don't have
LibreOffice installed but since it works in Abiword I assume it would be also in
LibreOffice Writer.

[TABLE="class: grid, width: 500, align: left"]
[TR]
[TD][SIZE=4]keys pressed
[/SIZE][/TD]
[TD="align: center"][SIZE=4]displayed output
[/SIZE][/TD]
[TD="align: center"][SIZE=4]displayed output[/SIZE][/TD]
[/TR]
[TR]
[TD][SIZE=4]
[/SIZE][/TD]
[TD="align: center"][SIZE=4]terminal
[/SIZE][/TD]
[TD="align: center"][SIZE=4]mousepad
[/SIZE][/TD]
[/TR]
[TR]
[TD][SIZE=4][é]  (between '.' and right-shift)
[/SIZE][/TD]
[TD="align: center"][SIZE=4]?
[/SIZE][/TD]
[TD="align: center"][SIZE=4]*nothing*
[/SIZE][/TD]
[/TR]
[TR]
[TD][SIZE=4]Shift+[é]
[/SIZE][/TD]
[TD="align: center"][SIZE=4]?
[/SIZE][/TD]
[TD="align: center"][SIZE=4]*nothing*
[/SIZE][/TD]
[/TR]
[TR]
[TD][SIZE=4][¸] (2nd row from top, extreme right)
[/SIZE][/TD]
[TD="align: center"][SIZE=4][I]nothing,
*nothing*[/I] after [c]
should give ç
[/SIZE][/TD]
[TD="align: center"][SIZE=4][I]nothing,
*nothing*[/I] after [c]
should give ç
[/SIZE][/TD]
[/TR]
[TR]
[TD][SIZE=4]Shift+[¸]
[/SIZE][/TD]
[TD="align: center"][SIZE=4]" (after [Space]),
*nothing* after [e]
should give ë
[/SIZE][/TD]
[TD="align: center"][SIZE=4]" (after [Space]),
*nothing* after [e]
should give ë
[/SIZE][/TD]
[/TR]
[TR]
[TD][SIZE=4]Alt Car+[1] (top row)
[/SIZE][/TD]
[TD="align: center"][SIZE=4]?
should give ±
[/SIZE][/TD]
[TD="align: center"][SIZE=4]*nothing*
should give ±
[/SIZE][/TD]
[/TR]
[/TABLE]

[Alt Car]+ any top row key, exept [#] (extreme left-> \ ) and [2](-> @), do not work.

The unrelated problem I was working on, in case anyone is curious, had to do
with locale.  I was told that locale and keyboard issues were independent of
each other, but just in case, my locale is "en_US.UTF-8" for LANG, LC_CTYPE,
LC_COLLATE, and LC_MESSAGES.  LC_ALL is null.  Everything else is "en".

Any suggestion on how I could fix this ?

Xubuntu 14.04
3.16.0-43-generic

localectl status:
   System Locale: LANG=en_US.UTF-8
                  LANGUAGE=en
       VC Keymap: n/a
      X11 Layout: ca
       X11 Model: pc105

cat /proc/version:
Linux version 3.16.0-43-generic (buildd@brownie)
 (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) )
 #58~14.04.1-Ubuntu SMP Mon Jun 22 10:21:20 UTC 2015


Thanks in advance.

---

### Post by palipeaublasee on 2015-07-13
Should this post be in the hardware section?  I chose not to put it there because
my physical keyboard works just fine, in Firefox and Abiword for example, but
maybe it would be better there.

---

