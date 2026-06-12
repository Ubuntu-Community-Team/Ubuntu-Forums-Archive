---
title: "Printing With CUPS on CLI Doesn't Make Margins"
date: 2014-07-09
forum: General Help
---

### Post by marjinal1st on 2014-07-09
I'm using Ubuntu 14.04 AMD64.

I'm trying to print a document in a special page size. Width 10 cm, Height 18 cm, left-right margins 2 cm and top-bottom margins 1 cm. I tried to create a page model in printer settings. Like this:

[IMG]http://i.imgur.com/6tJWQES.png[/IMG]

Priting with this page size works without a problem. But I need to do it on the command line. I found how can I do in CUPS documents. Like this:

```
lp -o media=Custom.100x180cm -o page-left=57 -o page-right=57 -o page-top=28 -o page-bottom=28 result.jpg
```

(Margin values are points which is 1/72 inch or 0.35 mm)

When I print the document (image actually), page sizes are OK but there are no margins :confused: I'm testing these on CUPS's virtual PDF printer.

Any ideas?

---

### Post by marjinal1st on 2014-07-09
Whoops, I found a mistake in command. I wrote 100x180cm instead of 10x18cm:

```
[COLOR=#000000][FONT=Ubuntu Mono]lp -o media=Custom.10x18cm -o page-left=57 -o page-right=57 -o page-top=28 -o page-bottom=28 result.jpg[/FONT][/COLOR]
```

Still, there's no margins.

---

### Post by tgalati4 on 2014-07-09
It's possible that lp does not support custom sizes:

>        -o media=size
            Sets the page size to size. Most printers support at least the size names "a4", "letter", and "legal".


It's also possible that the margins only work for text files, not image files:

>        -o page-top=N
            Sets the page margins when printing **text **files. The values are in points - there are 72 points to the inch.


There are several PDF-handling tools available, perhaps one of those will work:

```
apropos pdf
```

Write out the steps that you are trying to accomplish.  There are several ways of doing things in linux.

---

### Post by marjinal1st on 2014-07-09
Like I said before, if I print the image on GUI (using Shotwell) with custom page size, it prints without a problem, page sizes are margins are OK.

I tried the command with different options. For example;

```
lp -o page-left=57 -o page-right=57 -o page-top=28 -o page-bottom=28 result.jpg
```

With this command, page margins shows up fine. But page size becomes A4. When I add **"-o media=Custom.10x18cm"** option, page margins disappear :confused:

---

