---
title: "Compilation aborted - ogg2mp3 script troubles"
date: 2007-11-16
forum: General Help
---

### Post by AxAeo on 2007-11-16
> Can't locate String/ShellQuote.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/bin/ogg2mp3 line 42.

So I tried to run ogg2mp3, and I got this error... I have no idea what the issue is. Any advice? I SHOULD have everything I need... LAME, perl, ogg123, ogginfo...

---

### Post by mccurly on 2008-07-04
try:
perl -MCPAN -e 'install String::ShellQuote'

---

### Post by tr333 on 2008-07-05
you would be better off installing it from the repositories (apt-get install libstring-shellquote-perl).

---

