---
title: "looking like a wget like program for http..."
date: 2007-01-03
forum: General Help
---

### Post by Mateo on 2007-01-03
i'm looking for a program like wget, but for http.  My only demands are:

1) console based

2) supports wildcards.

thanks!

---

### Post by Falcorian on 2007-01-03
What do you need to do with it? I really not sure what "for http" means, since the only thing I can think of is "gets from http sources" and wget does that.

---

### Post by bodhi.zazen on 2007-01-03
I'm not sure what you are asking either.

perhaps [curl](http://www.hmug.org/man/1/curl.php)

---

### Post by Mateo on 2007-01-03
i want it to download from http sources with wildcards.  such as [http://mysite.com/*.pdf](http://mysite.com/*.pdf)

wget doesn't accept wildcards in http.  Just for ftp.

---

### Post by Falcorian on 2007-01-03
> **Mateo said:**
> i want it to download from http sources with wildcards.  such as [http://mysite.com/*.pdf](http://mysite.com/*.pdf)

wget doesn't accept wildcards in http.  Just for ftp.
I think you can use wget to do something like that... But I'm no expert on it. I'd be a good thing to know though, so I'll be watching the thread for an answer.

---

### Post by Falcorian on 2007-01-03
As I said, I'm not wget expert, but I did remember reading an article on how to use it to scrape mp3s from a site.

Here's the link: [http://www.veen.com/jeff/archives/000573.html](http://www.veen.com/jeff/archives/000573.html)

Might be helpful for you...

---

### Post by bodhi.zazen on 2007-01-03
> Notes: http doesn't support downloading using standard wildcards, ftp does so you may use wildcards with ftp and it will work fine. A work-around for this http limitation is shown below:

**wget -r -l1 --no-parent -A.gif [http://www.website.com](http://www.website.com)**

This will download (recursively), to a depth of one, in other words in the current directory and not below that. This command will ignore references to the parent directory, and downloads anything that ends in “.gif”. If you wanted to download say, anything that ends with “.pdf” as well than add a -A.pdf before the website address. Simply change the website address and the type of file being downloaded to download something else. Note that doing -A.gif is the same as doing -A “*.gif” (double quotes only, single quotes will not work).

HTH 8)

---

### Post by kebes on 2007-01-03
Three options that I know of:
wget --recursive
curl
lynx -crawl

(wget is installed by default in Ubuntu but curl and lynx are not)

You'll have to read the manpages to get it right. I've done it before and it takes a bit of fiddling. As I recall wget works best. In all cases the best the program can do, however, is follow links like a web-crawler, since with HTTP you typically can't get a raw directory listing.

---

### Post by Mateo on 2007-01-03
I read about that A.gif method on the man page.  That's not what I'm trying to do, because I need more wildcards than just all of one file type.  Let me give an example.  Say you have 5 files named the following:

ubuntu-linux-guide.pdf
fedora-linux-guide.pdf
windows-xp-guide.pdf
windows-linux-comparison.pdf
ubuntu-fedora-comparison.pdf

And say you only wanted to grab the files about ubuntu.  So you'd want to use *ubuntu*.pdf in order to do that.  That would grab 2 of the 5 files.  As I understand it, that wget command just gets all of a specific file type.

what i'm *actually* trying to do is grab a daily newspaper.  I could just create a script to grab today's date and plug it into the file name.  But the problem is that they append a four digit random number (or at least appears random to me) to the end of the file.  so i need wildcards in order to ignore that random number.

---

### Post by Mateo on 2007-01-03
> **kebes said:**
> 
You'll have to read the manpages to get it right. I've done it before and it takes a bit of fiddling. As I recall wget works best. In all cases the best the program can do, however, is follow links like a web-crawler, **since with HTTP you typically can't get a raw directory listing**.

ohh, didn't know this.  will have to try a different way, i guess.

---

### Post by Mateo on 2007-01-03
for those curious, I figured it out.

The -r tag tells it to crawl the page. 

The --no-parent tag tells it not to get stuff from parent directories.

The --no-directories tag tells it not to maintain the directory structure

-A is where you tell it what type of file it is looking for.  This can have unlimited wildcards.  See my example.

-e robots=off was necessary in my case, because it kept downloading the robots.txt file.

-P is the destination.

wget -r -l1 --no-parent --no-directories -A "*2007_01_3*" -e robots=off -P ~/Books/ URL

thanks for the nudge in the right direction.

---

