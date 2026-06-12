---
title: "How to grep an online directory?"
date: 2013-01-15
forum: General Help
---

### Post by GnuKian on 2013-01-15
I need to extract all "*.ogg" links from [http://dl.tehranmusic239.com/t/Sal91/Dey/](http://dl.tehranmusic239.com/t/Sal91/Dey/)

I hoped the below link work, but didn't worked!
```
grep -rl "*.ogg"  http://dl.tehranmusic239.com/t/Sal91/Dey
```


How can I grep an online directory?

---

### Post by SlugSlug on 2013-01-15
you can use wget to download them all

```
wget --recursive -P ~/ -A ogg http://dl.tehranmusic239.com/t/Sal91/Dey/
```

Pretty sure you would be able to have wget log them all to a textfile without actually downloading and then you could grep that file

```
man wget 
```

---

### Post by GnuKian on 2013-01-15
> you can use wget to download them all

```
wget --recursive -P ~/ -A ogg http://dl.tehranmusic239.com/t/Sal91/Dey/
```A new question: Can I limit wget to download files less than 10MB?

> **SlugSlug said:**
> 
Pretty sure you would be able to have wget log them all to a textfile without actually downloading and then you could grep that file

```
man wget 
```
Yes, I don't want to download ogg files, I just need their actual links! wget man pages won't help me! however wget is a downloder!

---

### Post by SlugSlug on 2013-01-15
Am not sure of the correct syntax play around untill some one else can help

the wget command will be something like

```
wget -q  http://dl.tehranmusic239.com/t/Sal91/Dey/05 -O -  | grep -i 'ogg"' 

```

---

### Post by erind on 2013-01-15
> **GnuKian said:**
> [...]

Yes, I don't want to download ogg files, I just need their actual links! wget man pages won't help me! however wget is a downloder!

To avoid downloading the links' content, you can try* wget* with *--spider* option:

```
wget --recursive --spider -A ogg http://www.example.com 2>&1 | egrep 'http.+\.ogg'

```From the man pages the *--spider*  option just cheks the links:

> --spider
    When invoked with this option, **Wget will behave as a Web spider, which means that it will not download the pages, just check that they are there**. For example, you can use Wget to check your bookmarks: wget --spider --force-html -i bookmarks.htmlBased on your example the code produces:

```
 wget --recursive --spider -A ogg http://dl.tehranmusic239.com/t/Sal91/Dey/ 2>&1 | egrep 'http.+\.ogg'

--2013-01-15 20:31:08--  http://dl.tehranmusic239.com/t/Sal91/Dey/05/Ali%20Kia%20-%20nisti%20inja.ogg
--2013-01-15 20:31:08--  http://dl.tehranmusic239.com/t/Sal91/Dey/05/Ali%20Lohrasbi%20-%20Hanooz%20Bahatam.ogg
--2013-01-15 20:31:09--  http://dl.tehranmusic239.com/t/Sal91/Dey/05/Danial%20Shohrati%20-%20Aroose%20Ziba.ogg
...

```> A new question: Can I limit wget to download files less than 10MB?

[...]Afaik *wget  *doesn't support per file size limits, but this link has a patch for that:

[http://yurichev.com/index.php?title=Wget_patches](http://yurichev.com/index.php?title=Wget_patches)

See also this:
[http://superuser.com/questions/121193/make-wget-not-download-files-larger-than-x-size](http://superuser.com/questions/121193/make-wget-not-download-files-larger-than-x-size)

The file size can also be parsed from the *wget*'s output run with *--spider* option, look at the "*Length:* ..." line:  

 ```
wget --force-html  --recursive --spider -A ogg  http://dl.tehranmusic239.com/t/Sal91/Dey/ 2>&1 | egrep 'Length|http.+\.ogg'

--2013-01-15 21:12:09--  http://dl.tehranmusic239.com/t/Sal91/Dey/05/Ali%20Kia%20-%20nisti%20inja.ogg
**Length: 1801346 (1.7M)** [application/octet-stream]
--2013-01-15 21:12:09--  http://dl.tehranmusic239.com/t/Sal91/Dey/05/Ali%20Lohrasbi%20-%20Hanooz%20Bahatam.ogg
**Length: 1361977 (1.3M) **[application/octet-stream]

```Other good alternatives to explore are *curl   *and* lynx  *too.

---

