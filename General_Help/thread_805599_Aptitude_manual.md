---
title: "Aptitude manual"
date: 2008-05-24
forum: General Help
---

### Post by jessejazza on 2008-05-24
I have been trying to find a way of printing out the manual - i've got a bit annoyed with having to read it on screen. As i've learnt aptitude is very powerful and in order to learn about it more effectively i wanted to print it out.

thanks

---

### Post by jjgomera on 2008-05-24
with this command you have a text plane file easy to print on desktop

man aptitude >Desktop/man_aptitude

you can change the output file

---

### Post by angry_johnnie on 2008-05-24
Alt + F2

```
yelp
```

Search:  **aptitude**

**File > Print this page**

Try that :-)

---

### Post by jessejazza on 2008-05-24
Thanks both of you for your replies - i'll give it a try. Angry_johnnie... you're not so angry there was a :) there.
:lolflag:

---

### Post by jessejazza on 2008-05-24
The manual i actually wanted to print out was the aptitude-doc-en - the help manual accessed from within aptitude. It has more info than the aptitude[8] from man pages in apt.

Is it possible? when i looked in the archives it seemed that it was an html with a lot of dependencies. Ideally i wanted to print it out so i could read it from cover to cover [i always find reading pdf's on a screen less effective].

---

### Post by angry_johnnie on 2008-05-25
:o HTML... I think you'll have to copy/paste everything into a text file, or print it one page at a time.

I'm at work right now, but I'll think about it.  There must be an easier way to do it... I think :-)

And, by the way, I'm not angry.  It's just an old song :-)

---

### Post by jessejazza on 2008-05-28
Many thanks - i wish they'd produce it as a pdf that is well presented and easy to read. I did email the author but hasn't replied yet.

---

### Post by jessejazza on 2008-06-03
I seem to have found it after a fair bit of hunting. I don't follow why they didn't put it in a nice pdf that could be easily readable but i did find a text version [which i thought must be somewhere!]

/usr/share/aptitude/README

---

### Post by geirha on 2008-06-03
In aptitude's sources ```
cd /tmp
apt-get source aptitude
cd aptitude-0.4.9/doc/en/

```
there's an xml-version of that document, which is apparently a docbook format (never used docbook before). I couldn't find a converter to pdf, but there is one that converts to odf, and from there it's easy to get an pdf if you like. Install [docbook2odf](apt://docbook2odf), and run ```
docbook2odf aptitude.xml
```

---

### Post by jessejazza on 2008-06-11
many thanks i'll try it.

---

