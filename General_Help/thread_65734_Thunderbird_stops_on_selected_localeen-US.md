---
title: "Thunderbird stops on selected locale:en-US"
date: 2005-09-14
forum: General Help
---

### Post by josir on 2005-09-14
Hi folks,
after an apt-get update, Thunderbird stops to run with 

$mozilla-thunderbird
selected locale: en-US

I tried to reset locale, removing en-US with configure-debian:

Generating locales...
  pt_BR.UTF-8... done
  pt_BR.ISO-8859-1... done
Generation complete.
Done.

but it didn't work.
Does someone has any clue on how to fix it??

Thanks in advance,
Josir Gomes
Rio - Brasil

---

### Post by josir on 2005-09-14
Just to notice: I found the problem. 
When I did the last upgrade, mozilla-firefox-gnome was not installed correctly.

So I run apt-get install mozilla-thunderbird and apt-get fix and install the pending packages and everything started to work again.

Ubuntu is great ! It fixes itself...

---

