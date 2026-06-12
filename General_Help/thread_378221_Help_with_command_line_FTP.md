---
title: "Help with command line FTP"
date: 2007-03-07
forum: General Help
---

### Post by mlissner on 2007-03-07
I'm trying to be intelligent about my ftping. Is there a way to ftp only html files in a directory, leaving out jpgs and the like? I can do this manually, but I'd like to be able to do this recursively for a number of directories via command line. 

I've been playing with FTP (the utility), but I can't for the life of me find a good tutorial on making it work, so I guess that's question number one.

Question two is, how do I do something like 'put -R *.html', (R for recursive), if that makes sense?

---

### Post by ewankho on 2007-03-07
Have you tried the mput and mget commands?

---

### Post by mlissner on 2007-03-07
Yeah, but they don't seem to work. I would think that if I did something like mget pics/* (where pics is a directory), it would get everything in it, and if I did mget pics/*.html, it would get only the html docs, but neither seem to work. 

Apparently ftp doesn't deal in regular expressions, but this must be doable.

---

### Post by ewankho on 2007-03-08
Maybe you can try a series of commands (cd's, mget's).  I've tried it before where ftp accepts a file containing a series of commands. Not sure if this is dependent on the ftp client you are using but you can check if it is available.

---

### Post by mlissner on 2007-03-08
That sounds like a pain. There must be a way to do this, right? Linux is designed for this kind of configurability, right?

---

### Post by Mr. C. on 2007-03-08
FTP is a very old protocol, and the command utility is as welll; it does not do recursion, regular expressions, or other things you take for granted today.

You can use * as a wildcard, such as:

mget *.html

and will allow

mget dir/*.html

but dir must already exist on the local system.

Use wget if you want to ftp an entire directory:

wget -r --ftp-user YourUSERNAME --ftp-password YourPASS ftp://FTPSITE//dir/'*.html'

MrC

---

### Post by mlissner on 2007-03-08
Asterisks weren't working for me, but I suppose this is my answer: It can't be done. It looks like wget will work for getting, but it'd be nice if we had a command line program with real features for uploading. 

Strange that we don't. Perhaps I'll write a note to the FTP people.

---

### Post by Mr. C. on 2007-03-08
Use lftp.  I didn't understand that you wanted uploads; I assumed download only.  I now see that you wanted to "put" files.

MrC

---

### Post by JermainWijnhard on 2007-03-08
Okay im i'm a newborn when it comes to cli commands but wouldnt it be possible to something like

```
ls *.html | ftp
``` (the code is sucky but you get the idea :) ) if it can be piped, ftp's lack of a wildcard could be bypassed

---

### Post by mlissner on 2007-03-08
> **JermainWijnhard said:**
> Okay im i'm a newborn when it comes to cli commands but wouldnt it be possible to something like

```
ls *.html | ftp
``` (the code is sucky but you get the idea :) ) if it can be piped, ftp's lack of a wildcard could be bypassed


Yeah, that's kind of the idea I'd be looking for, but the problem is googling doesn't really work for this from what I can figure out. FTP just isn't the best search term.

So, is my impression that ftp is to lftp as vi is to vim pretty much correct - Is lftp the usurper of ftp as far as features and such go?

I'll give it a whirl the next time I'm ftping and see what I get.

---

### Post by Mr. C. on 2007-03-08
No, you would have to write a script to call FTP for each subdirectory.

Take a look at this:

[http://www.linux.com/article.pl?sid=06/03/08/1716219](http://www.linux.com/article.pl?sid=06/03/08/1716219)

which leads to:

[http://www.ncftp.com/ncftp/](http://www.ncftp.com/ncftp/)

MrC

---

### Post by JermainWijnhard on 2007-03-08
> **mlissner said:**
> Asterisks weren't working for me, but I suppose this is my answer: It can't be done. It looks like wget will work for getting, but it'd be nice if we had a command line program with real features for uploading. 

Strange that we don't. Perhaps I'll write a note to the FTP people.

We have FTP people? Sweet, crack the whip!

---

### Post by JermainWijnhard on 2007-03-08
double posted, sorry :(

---

### Post by z33k3r on 2007-06-23
> **Mr. C. said:**
> Use wget if you want to ftp an entire directory:

wget -r --ftp-user YourUSERNAME --ftp-password YourPASS ftp://FTPSITE//dir/'*.html'

MrC

OMG, I have been looking for this command sequence for ever! Thank you!!! This is the only real way of doing recursive downloading for me downloading from a cPanel login that uses the @ symbol in the user name... again thank you!

:popcorn:

---

### Post by Mr. C. on 2007-06-23
Glad to be of service.

MrC

---

