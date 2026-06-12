---
title: "gui for postscript ??"
date: 2007-10-06
forum: General Help
---

### Post by delfick on 2007-10-06
hello

I was wondering if there is a gui out there for postscript

say a program where you choose a file (i.e. pdf, odt, etc) and then you choose options like wether you want it many pages on one, two sides (even though you don't have a duplex printer, so when you print it, it prints one side for all pages, then it tells you to flip the pages, and then it continues with the other side for all pages)

so that say I had quite a few pdfs, some I want 4 pages per page, others, 2 per page, others 1 page per page, all of which are dupelx on a non-duplex printer, all I'd have to do was load those pages in this gui and then edit the options for each job, the gui then converts each job to a postscript and then prints it all at once so I only have to flip everything once for all sides to be done... 

?? :D

or am I just dreaming ?? :p

thnx

---

### Post by por100pre1 on 2007-10-06
Check if Evince does the trick:

```
sudo apt-get install evince
```

---

### Post by delfick on 2007-10-06
already use evince, It's a good program :D

But for printing many pdfs (and other file types) at the same time, It's such a hassle having to print them individually (I'm too used to fineprint)

and if such a gui existed, I'd imagine it'd also take advantage of other features provided by postScript :D

---

### Post by delfick on 2007-10-07
maybe say, a gui frontend to a2ps ?? :D

---

### Post by delfick on 2007-10-07
out of interest how can I print duplex without a duplex printer using the commandline ?
I can first change the pdf to the appropiate postScript file
for i in $(ls);do a2ps $i --columns=2 --rows=2 --portrait --chars-per-line=80 --major=columns -o ../ps/$i.ps;done

but when it comes to printing, I run into issues, I use
lpr -o page-set=odd -o outputorder=reverse <file.ps>
and then swap the put those pages back in and do 
lpr -o page-set=even <file.ps>

but I have no idea how to make it work with many at once
lpr -o page-set=odd -o outputorder=reverse *
lpr -o page-set=even *

because if a page doesn't have another side to it, then it doesn't print anything on that second side...

for example, if say I have a three page document, it will print page 1 and page 3,
then when I put it back in, it will print page 2 , leaving page 3 still in the printer.

So if I do many at once using the wildcard * then page 3 is used for page 2 of the next job, and it doesn't really work............

thnx :D

edit : also, with fineprint, the pages are dynamically sized so that if you have more than one page per page, then those pages are sized as to waste as little room as possible....

---

