---
title: "Need website scraper to Download an entire website"
date: 2007-11-20
forum: General Help
---

### Post by bliffle on 2007-11-20
I need a website scraper that can DL an entire website to my HDD. It sounds like piracy, I know, but I have what I feel is a legitimate use and If offered as an alternative I would pay for a CD or DVD from the website owners, but I can seldom find such an offer.

I'm equipping an IBM thinkpad with an 80gb HDD for a 9 yr. old who has great interest in biology (and has had for 5 years, so I don't think she's going to lose it anytime soon). I want to make this Thinkpad a useful reference system. Her mom doesn't want to turn her into an internet addict and wastrel, so she's got her daughter taught to go to the library if she doesn't have a suitable book on her bookshelves. Mom says a computer is OK if it doesn't clog up their telephone and turn the child into a zombie.You could only dream of having such a child.

So I need to download all the HTML and images, etc., into a convenient folder with all the appropriate URLs translated into appropriate new URLs. When I was using Windows and IE there was a way to synchronize bookmarks that, IIRC, downloaded that stuff into the browser cache so next reference would go there first. But I couldn't find anything just like that for Firefox. But there must be something. I remember that before IE did that one could get a shareware standalone program. 

Is there something for ubuntu or Firefox?



.

---

### Post by spupy on 2007-11-20
Two options:
1. wget. Read the man page. It can recursively download websites (how deep you say), follow links, skip some file types, can resume interrupted downloads, the links in the mirror get updated to point correct files on the disk. Lots of options. 
2. httrack. It has a windows version, too. I don't know how it works in Linux, but i was satisfied with it when i used it with windows.

Since both are command line tools, i would choose wget, because it offers more options. The syntax will be something like
```
wget -r -l 3 http://www.example.com/
```

---

### Post by bliffle on 2007-11-21
> **spupy said:**
> Two options:
1. wget. Read the man page. It can recursively download websites (how deep you say), follow links, skip some file types, can resume interrupted downloads, the links in the mirror get updated to point correct files on the disk. Lots of options. 
2. httrack. It has a windows version, too. I don't know how it works in Linux, but i was satisfied with it when i used it with windows.

Since both are command line tools, i would choose wget, because it offers more options. The syntax will be something like
```
wget -r -l 3 http://www.example.com/
```

You are so right!

"wget" just got me everything I wanted from the 2 websites of HTML and photos (basically) that I wanted to make available on my granddaughters machine. That way she doesn't have to tie up her mothers phoneline.and she can use it as a reference library.

I'd used 'wget' a few years ago for a rather narrow purpose so I didn't realize the power that is intrinsic in it's design. For example, if I found that I hadn't recursed far enough to get everything I wanted, I could run the 'wget' again with an improved "-r -l 3" to go 3 levels, and also append the new log info with "-a wget1.log" which I could scan for errors later, and if, for example, I was still getting errors increase the retry count with say "-t 3". 

"wget" swings, man!

As an interesting side issue, one ought to notice that this is made possible by the (often-criticized) Command Line Interface (CLI). Windows and Mac people who encounter CLI for the first time ALWAYS complain about the seemingly obscure syntax of CLI and the fact that they, poor dears, have to RTFM! And maybe even THINK, a loathsome burden, apparently, for many computer users.

By separating implementation of a function from the parameter parsing it sets the software developer free to develop the vital hidden code that brings something to life without bogging down in UI considerations until later when the functionality is settled down. As a longtime software developer I can attest that this is a BIG reduction in development time and effort.

Thanks again for the reference.

---

