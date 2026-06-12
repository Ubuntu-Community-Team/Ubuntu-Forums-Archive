---
title: "Evolution &amp; Date format"
date: 2007-01-21
forum: General Help
---

### Post by mune on 2007-01-21
Hi all

A couple of days ago evolution started in american and not in italian.

I thought it wasn't a big deal.

The problem apperead when I tryed to add a new appointment (I sync it with the palm); say it was 18/01/2007 but the evolution calendar said "invalid date".

All depends that evolution is localized in american and not in italian.

How do I go back to italian?

Thanks

Fede

---

### Post by dcstar on 2007-01-21
> **mune said:**
> Hi all

A couple of days ago evolution started in american and not in italian.

I thought it wasn't a big deal.

The problem apperead when I tryed to add a new appointment (I sync it with the palm); say it was 18/01/2007 but the evolution calendar said "invalid date".

All depends that evolution is localized in american and not in italian.

How do I go back to italian?

Thanks

Fede

AFAIK Evolution uses the system Locale, it seems this has been changed/corrupted on some systems by a recent update.

---

### Post by mune on 2007-01-21
> **dcstar said:**
> AFAIK Evolution uses the system Locale, it seems this has been changed/corrupted on some systems by a recent update.

Thanks

The same as I thought...but firefox and other applications was localized correctly, so as half was working and half was not, I figured out that something was corrupted. I used the tool in System -> Administration -> Language support (I hope those are the correct names because they're in italian:)) to unselect the language and then select my own language again. Now evolution seems to work.

Goog hint

Fede

---

### Post by dcstar on 2007-01-21
> **mune said:**
> Thanks

The same as I thought...but firefox and other applications was localized correctly, so as half was working and half was not, I figured out that something was corrupted. I used the tool in System -> Administration -> Language support (I hope those are the correct names because they're in italian:)) to unselect the language and then select my own language again. Now evolution seems to work.

Goog hint

Fede

I think some other non-English users posted similar problems a day or so ago, it looks like someone was a little too "English-centric" in the latest updates!     ](*,)

---

### Post by sizzlor on 2007-01-27
indeed, same here..  i have my locale set to **en_GB.UTF-8**, but this seems to have no effect on Evolution.

version: 2.9.6
release: feisty

---

### Post by mune on 2007-01-28
All is ok now!:D 

I did a new update and some locale_someting packages shpw up; yes it was not my box.

Fede

---

