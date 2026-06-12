---
title: "Perl"
date: 2007-11-23
forum: General Help
---

### Post by poisonmushroom on 2007-11-23
Today i have decided i want to study Perl, i couldn't think of any other language so i just thought i'd pick this one. (hear it was supposed to be easier than others).

Before i start? do i need any HTML knowledge or such for it? just wondering...

anyway, I have LAMP set up on my server and perl is ofcourse installed, using a guide i have found, it said i should create a simple script with .pl extenstion and then copy it into the CGI-BIN directory, in the guide he put it in  /ftp/cgi-bin since he connected using FTP to his webhost.

what i don't get is, where am i supposed to put the file? i mean there is a cgi-bin directory in /usr/lib but im not sure its the right one... Apache2 is running great so i thought i would put it in /var/www but heard it's not safe...

Anyone here who can help me out? much appreciated, thanks :)

P.S: should i rather go for C++? (or maybe go through HTML not to look like a n00b?)

---

### Post by niteshifter on 2007-11-23
I wouldn't call Perl exactly easy to learn unless you already some experience with shell scripting and C. If what you are after is to learn programming I'd recommend the Python language.

Yes, a working knowledge of HTML is needed for CGI via Perl.

---

### Post by LaRoza on 2007-11-23
Perl isn't the easiest.

See my wiki....

I would recommend Python for now. Learning XHTML and CSS is easy, so you can learn that too.

Starting with CGI is not recommended. You have to already know how to program to do that.

Work with Python, learn the concepts of programming, and write small apps for now.

---

### Post by lakris61 on 2007-11-23
> **poisonmushroom said:**
> Today i have decided i want to study Perl, i couldn't think of any other language so i just thought i'd pick this one. (hear it was supposed to be easier than others).

Before i start? do i need any HTML knowledge or such for it? just wondering...

anyway, I have LAMP set up on my server and perl is ofcourse installed, using a guide i have found, it said i should create a simple script with .pl extenstion and then copy it into the CGI-BIN directory, in the guide he put it in  /ftp/cgi-bin since he connected using FTP to his webhost.

what i don't get is, where am i supposed to put the file? i mean there is a cgi-bin directory in /usr/lib but im not sure its the right one... Apache2 is running great so i thought i would put it in /var/www but heard it's not safe...

Anyone here who can help me out? much appreciated, thanks :)

P.S: should i rather go for C++? (or maybe go through HTML not to look like a n00b?)

I would say that if You need to use Perl as a cgi-tool, Yes, You must be very familiar with HTML, and also be aware of the pitfalls of using other libs/packages to present it, problems with quoting, etc. It is old style programming. 
Very powerful and competent for ordinary system admin tasks. I would say it's a powerful alternative to a Unix shell, such as bash or sh or zsh. I think that's where it started. It's sed/awk/grep/tr/cut/etc on steroids.
And then people started to use it for the web. Heck, I've whipped up a few web-apps myself in Perl, since I had my roots in C, and it works for reasonably sized apps and usage. But for larger apps? No, I don't think so.

So, Perl is a nice programming language, but if I would be programming for the Web, no. I don't do any web-app programming nowadays but I guess Java or .Net (any flavour really)  would be better alternatives. PHP may be, but I have no experience. And then You have Ruby, Python, etc, but do they really have a big user base? It's important if You want community support.

If You want to do some really nifty logfile, sysadmin, and database handling, Yes, Perl is a good choice. I actually like it! ;)


/Lakris

---

### Post by poisonmushroom on 2007-11-23
Thanks for the replies guys, so i guess Perl isn't easy afterall...

So i think it's the best programming language to start with is Python? the thing is that i simply want somewhere to start, I would love to start with the easy thing, something that does not require previous knowledge for programming, then move to different ones and expand my knowledge.

At the moment my knowledge is literally zero, so if anyone here can suggest some good e-books / books that can help me study Python (for example) from scratch i would really appreciate it!

Would it be good if i studied HTML before python? i mean, everybody seems to know exactly how html is written and i feel like the only one who doesn't know it... What kind of "plan" would you guys suggest me? first html, then python then C++? not to mention i don't even understand what's the purpose of each language, where do i write it or what kind of file extension does it become?

I'm trying to expand my knowledge everywhere so i won't have a hard time when i sign-up for college/university and might someday write a really elite program, open-source too :D

Thank you for taking the time to read this, i really appreciate it!

P.S: What in general does a programmer need to know before studying any language?

---

### Post by niteshifter on 2007-11-23
Some Python Tutorial links:

[http://www.python.org/doc/current/tut/tut.html]("http://www.python.org/doc/current/tut/tut.html")

[http://diveintopython.org/]("http://diveintopython.org/")

[http://www.greenteapress.com/thinkpython/]("http://www.greenteapress.com/thinkpython/")

Enjoy!

---

### Post by MrFSL on 2007-11-23
> 
So i think it's the best programming language to start with is Python? the thing is that i simply want somewhere to start, I would love to start with the easy thing, something that does not require previous knowledge for programming, then move to different ones and expand my knowledge.



Perl is wonderfully easy because it was programmed by a user who was fed up with obfusticated programming languages. I would suggest that as it has been said "if htlml is that language of the internet then perl in the duct tape" - 

Might I point you toward this book:

[http://www.oreilly.com/catalog/learnperl4/](http://www.oreilly.com/catalog/learnperl4/)

I still, after years of programming perl in professional environments use this book as a reference guide. 

Python is more liberal with the sytax and has good deal of libraries to simplify it's coding but perl can do whatever you can imagine. And CPAN is a HUGE resource - ever evolving, free, you name it... just wonderful... that's all I have to say.

EDIT:
Also, perl's syntax might be slightly more complex but it was written by a C programmer - so the syntax is at least close to a standard which can be adopted in future use to other popular languages such as C or C++.

EDIT:
WOW. Remind me never to post while drinking... my above post hardly makes sense... sorry ;)

---

### Post by LaRoza on 2007-11-23
> **poisonmushroom said:**
> 
So i think it's the best programming language to start with is Python? the thing is that i simply want somewhere to start, I would love to start with the easy thing, something that does not require previous knowledge for programming, then move to different ones and expand my knowledge.

At the moment my knowledge is literally zero, so if anyone here can suggest some good e-books / books that can help me study Python (for example) from scratch i would really appreciate it!

Would it be good if i studied HTML before python? i mean, everybody seems to know exactly how html is written and i feel like the only one who doesn't know it... What kind of "plan" would you guys suggest me? first html, then python then C++? not to mention i don't even understand what's the purpose of each language, where do i write it or what kind of file extension does it become?

P.S: What in general does a programmer need to know before studying any language?

Python, yes. See my wiki and get coding. Perl is not easy unless you live knee deep in it.

XHTML isn't a programming language, it is a markup language. Go to my site: [http://laroza.freehostia.com/home](http://laroza.freehostia.com/home) and view the source, that is XHTML. (I say my site because I don't mix ECMAScript and CSS with the markup.) My wiki has information on XHTML and CSS too.

Visiting the wiki, [http://laroza.pbwiki.com](http://laroza.pbwiki.com), would give you answers, just click on the right links.

Programmers don't need prerequisite knowledge. Math isn't needed (unless you are writing math programs). It doesn't matter if you are a "logical" person or a "creative" person. The only thing a programmer needs is the desire.

---

### Post by poisonmushroom on 2007-11-24
Thanks for everyones replies, i have decided to start with Python.

LaRoza, i visited your site then through that got to this link to start with the basic things: ```
http://hkn.eecs.berkeley.edu/~dyoo/python/idle_intro/
```
They were using some program on windows to write python code but since i thought since i have a putty session open to my other ubuntu box i thought i would use the already installed Python program there, so i opened it but i got an error when trying to do this command:
```
for i in range(10):
```
then i did
```
print i,
```
(also tried without ,) but i got this message:
```
File "<stdin>", line 2
    print i,
        ^
IndentationError: expected an indented block
```

Can you tell me if this has got to do with the fact that i'm writing the code on an ubuntu box through putty?

Thanks for reading!

P.S: Is coding in linux much different than windows? wondering which one to use since im trying to slowly move into using ubuntu (even though i only have the server edition only).

---

