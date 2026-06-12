---
title: "Clone web sites?"
date: 2007-07-03
forum: General Help
---

### Post by GabrielWolff on 2007-07-03
Hey, I have a web site that I'd like to download completely.
The website includes lots of documents and pix, all in different directories.
Is there any tool like webclone in windows, that makes it possible for me to download and save any file in a certain directory and underneath it?

Thanks

G

---

### Post by Steveway on 2007-07-03
You would like to check out wget.
Check it's man page for exact details on how to use it.

---

### Post by GabrielWolff on 2007-07-03
> **Steveway said:**
> You would like to check out wget.
Check it's man page for exact details on how to use it.


great, only problem is: How do I fill in a password and user for the site, it's protected. I tried: 
wget --http-user --http-passwd http:URL
but it gave me: unrecognized option

Why?

---

### Post by GabrielWolff on 2007-07-03
OK, solved that - next.

I get only html web sites.

And it's always only the one site I pointed at.

I want to download any file that is placed in the directory I pointed at, and in the directories beneath it. Mailny pdf and gif files/

How?

G

---

### Post by McNils on 2007-07-03
Should have been something like this...
```

wget --user=YOUR_HTTP_USER --password=YOUR_HTTP_USER_PASSWORD http:URL

```

---

### Post by McNils on 2007-07-03
> **GabrielWolff said:**
> OK, solved that - next.

I get only html web sites.

And it's always only the one site I pointed at.

I want to download any file that is placed in the directory I pointed at, and in the directories beneath it. Mailny pdf and gif files/

How?

G

Options from the man page.
> 
       -A acclist --accept acclist
       -R rejlist --reject rejlist
           Specify comma-separated lists of file name suffixes or patterns to accept or reject (@pxref{Types of Files} for more
           details).


---

### Post by GabrielWolff on 2007-07-03
Getting better.
But still it doesn't work recursively.
wget downloads the one file that is in the directory I pointed at, but none of the hundrets in the directories below.

Why?

G

---

### Post by McNils on 2007-07-03
You must add  a -r  to wget to enable recursion...

---

### Post by kpkeerthi on 2007-07-03
Try gwget

```
sudo aptitude install gwget
```

---

### Post by GabrielWolff on 2007-07-09
> **McNils said:**
> You must add  a -r  to wget to enable recursion...

OK, but now it doesn't only download anything below, but the whole website. Like: If I type in: wget -r [http://www.GabrielWolff.com/Gabriel/Wolff](http://www.GabrielWolff.com/Gabriel/Wolff) it downloads the files in [http://www.GabrielWolff.com/Gabriel](http://www.GabrielWolff.com/Gabriel) as well. Any way of avoiding that?

G

---

### Post by SpiritIsReality on 2007-08-21
bump

---

