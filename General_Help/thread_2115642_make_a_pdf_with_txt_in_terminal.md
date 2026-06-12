---
title: "make a pdf with txt in terminal"
date: 2013-02-13
forum: General Help
---

### Post by rimzai on 2013-02-13
to print the manual page of a command in pdf, i will type in terminal (for eg. with the avconv command)

```
 man -t avconv | ps2pdf - > avconv.pdf
```now i want to print the list of audio codecs used by avconv in pdf, that is

```
 avconv -codecs | grep A
```how can i manage this ?

---

### Post by schragge on 2013-02-13
I guess there are many ways to do it. I usually filter text through [mpage(1)]("http://manpages.ubuntu.com/manpages/precise/en/man1/mpage.1.html") like this
```
echo some text|mpage -2|ps2pdf
```

---

### Post by Maheriano on 2013-02-13
I use a HTML -> PDF converter called mPDF for generating quotes for my clients. You could try going that route.

---

### Post by rimzai on 2013-02-13
> **schragge said:**
> I guess there are many ways to do it. I usually filter text through [mpage(1)]("http://manpages.ubuntu.com/manpages/precise/en/man1/mpage.1.html") like this
```
echo some text|mpage -2|ps2pdf
```

thx for your response !

but i didnt succeed that way.... 

```
mpage 'avconv -codecs' -2 | ps2pdf - > test.pdf
```

returns

```
mpage: cannot open avconv -codecs
```

i did it graphically with gedit but hey this is not a geekclass solution lol

---

### Post by schragge on 2013-02-13
No, you should did it like this
```

avconv -codecs|mpage -2|ps2pdf - >test.pdf

```

---

### Post by rimzai on 2013-02-13
yeah great thx !

```
avconv -codecs|**grep A** | mpage -2|ps2pdf - >test2.pdf
```

worked as well

---

