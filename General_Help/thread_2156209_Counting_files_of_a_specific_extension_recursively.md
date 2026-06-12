---
title: "Counting files of a specific extension recursively in a directory."
date: 2013-06-20
forum: General Help
---

### Post by HittingSmoke on 2013-06-20
I'm fine tuning the PHP cache on my web server and that involves telling APC approximately how many source files there are to cache.

Is there a way to recursively count files throughout all of my web root with the .PHP extension and possibly other extensions?

---

### Post by ahallubuntu on 2013-06-20
~

---

### Post by SeijiSensei on 2013-06-20
The number of files may not correspond to the number of different requests that might be cached.

For instance, all my sites use only one index.php file.  The content displayed depends on additional parameters in the URI.  The "welcome" page is represented as /index.php?go=welcome; the "contact us" page is /index.php?go=contact, and so forth.  So my one index.php file can generate literally dozens of different pages.  

If you are sure that only one page is generated per file, then you can use

```
cd /var/www
ls -lR *.php | wc -l

```

to get a count of all files ending in .php in /var/www and its subdirectories.

Otherwise you can use "wget -r http://www.example.com/" to generate a complete list of all URLs accessible from the home page and count those.  The "-r" ("recursive") parameter tells wget to follow all the links it finds.

---

### Post by HittingSmoke on 2013-06-20
> **SeijiSensei said:**
> The number of files may not correspond to the number of different requests that might be cached.

For instance, all my sites use only one index.php file.  The content displayed depends on additional parameters in the URI.  The "welcome" page is represented as /index.php?go=welcome; the "contact us" page is /index.php?go=contact, and so forth.  So my one index.php file can generate literally dozens of different pages.  

If you are sure that only one page is generated per file, then you can use

```
cd /var/www
ls -lR *.php | wc -l

```

to get a count of all files ending in .php in /var/www and its subdirectories.

Otherwise you can use "wget -r http://www.example.com/" to generate a complete list of all URLs accessible from the home page and count those.  The "-r" ("recursive") parameter tells wget to follow all the links it finds.

I don't believe that matters for opcode caching. It's not caching static pages. It's caching PHP scripts. Unless I'm drastically misunderstanding opcode caching and APC.

That would be pretty pointless for a forum app since literally every single post creates a new URL. It would be impossible to keep up with and my file hints setting would be up into the hundreds of thousands after not long.

---

### Post by SeijiSensei on 2013-06-21
Since I have never used "opcode caching" in my life, I bow to your greater expertise in this matter.

---

### Post by Vaphell on 2013-06-21
*find  | wc -l* is good in 99.99% cases but if there is even 1 file with newline in its name (which is allowed) the result will be wrong

rock solid way to do this is to print a single char for every matching item and count how many chars are there
```
find -printf "x" | wc -c 
```

---

