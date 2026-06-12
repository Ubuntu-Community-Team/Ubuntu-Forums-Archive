---
title: "Terminal is echoing bash completion scripts"
date: 2014-12-17
forum: General Help
---

### Post by david.aldrich.ntml on 2014-12-17
Hi

I am running Ubuntu 10.04 LTS.  When I am in a terminal session and press the TAB key to do completion of directory names, I see the bash completion script echo'ed to the terminal:

```
[COLOR=#000000][FONT="Courier New"]-> cd lt++ _get_cword
++ '[' -n '4.1.5(1)-release' ']'
++ __get_cword4
++ local i
++ local LC_CTYPE=C
++ local 'WORDBREAKS=   
"'\''><=;|&(:'
++ WORDBREAKS='         
'\''><=;|&(:'
++ WORDBREAKS='         
><=;|&(:'


<snip>[/FONT][/COLOR]

```

What could be causing this?

Best regards

David

---

### Post by Habitual on 2014-12-17
look for "set -v" in your ~/.bashrc or possibly another hidden file sourced ("source /path/to/some/file") in it.

---

### Post by david.aldrich.ntml on 2014-12-17
Thanks for your answer. Then I think the reason is that I use set -x in an alias.

---

### Post by Habitual on 2014-12-17
Glad it worked out.

---

