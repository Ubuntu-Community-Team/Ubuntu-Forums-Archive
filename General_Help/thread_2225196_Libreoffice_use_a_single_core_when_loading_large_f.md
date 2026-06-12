---
title: "Libreoffice use a single core when loading large files"
date: 2014-05-20
forum: General Help
---

### Post by gabbello on 2014-05-20
When I try to open larger files (ods, xls, csv) only 1 core (out of 4) goes to 100% and the rest stay at 0. This means that for files of 10-50 MB I have to wait a lot of time to have it opened. Is there a way to fix this?
thank you

---

### Post by Impavidus on 2014-05-20
Reading the file from disk doesn't max out the CPU, so, as these are spreadsheet formats, I assume this time is needed to recalculate all derived values. If the application you use to open these files has been designed to use multiple threads to do so, it will automatically use all cores. If the application has not been designed like that, it will use a single core. There not much to do about that, apart from changing the source code of the application.

For comparison, when I open a 492kB gnumeric file (spreadsheet with 25000 entries), opening takes 2.3 seconds, using a single core. Opening the application without opening the file takes 0.4 seconds, in both cases program and file where cached already. For larger spreadsheets (up to 10[SUP]8[/SUP] lines) I use self-made special purpose code.

---

### Post by The Cog on 2014-05-20
I agree with Impavidus - if LO is not written to use multiple cores while loading documents (and it seems not to be) there is nothing you can do about that.

---

### Post by Lars Noodén on 2014-05-20
It's an ongoing question:

[http://ask.libreoffice.org/en/question/5371/is-lo-calc-capable-for-smp/](http://ask.libreoffice.org/en/question/5371/is-lo-calc-capable-for-smp/)

looking around, I couldn't find any obvious bug report on the problem:

[https://www.libreoffice.org/bugzilla/buglist.cgi?quicksearch=smp](https://www.libreoffice.org/bugzilla/buglist.cgi?quicksearch=smp)

maybe you could look around there in bugzilla and either add your 2 cents to an existing report or, if you can't find one, start one.

---

### Post by bapoumba on 2014-05-20
[https://bugs.freedesktop.org/show_bug.cgi?id=65046](https://bugs.freedesktop.org/show_bug.cgi?id=65046)
[http://nabble.documentfoundation.org/Libreoffice-multiple-cores-problem-td4057938.html](http://nabble.documentfoundation.org/Libreoffice-multiple-cores-problem-td4057938.html)

---

### Post by gabbello on 2014-05-20
Sad news. Any other spreadsheet that is closely compatible with Excel and handle better large files?

---

### Post by Lars Noodén on 2014-05-21
You'd have to try them to know one way or the other.  There are at least Gnumeric and Calligra Tables (or Sheets, the name changes) to try out.

---

### Post by Impavidus on 2014-05-21
I have noticed that when I convert my 492kB gnumeric file to .ods format, it expands to 6.2MB and suddenly takes more than twice as long to open in gnumeric (5s instead of 2s). In .xls format it's still 3.2MB, but loads quite fast (2s). I don't have libreoffice to compare.

I thought, 50MB, that is a huge spreadsheet, that must have millions of entries. But it appears that the gnumeric files I used for comparison are just more space efficient than .ods.

---

### Post by Lars Noodén on 2014-05-21
> **Impavidus said:**
> I have noticed that when I convert my 492kB gnumeric file to .ods format, it expands to 6.2MB and suddenly takes more than twice as long to open in gnumeric (5s instead of 2s). In .xls format it's still 3.2MB, but loads quite fast (2s). I don't have libreoffice to compare.

I thought, 50MB, that is a huge spreadsheet, that must have millions of entries. But it appears that the gnumeric files I used for comparison are just more space efficient than .ods.

Gnumeric does not use OpenDocument Format as its native format so there is probably some conversion going on behind the scenes.  It could also be that Gnumeric is saving a lot of extra stuff in the OpenDocument version.  However, not knowing the internals, it's just a guess.  Both are zipped XML so it would be possible to open them up and look at the insides and see what is taking all that space.

---

