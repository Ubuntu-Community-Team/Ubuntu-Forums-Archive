---
title: "What exactly does #! /bin/bash do?"
date: 2018-08-31
forum: General Help
---

### Post by webmiester on 2018-08-31
Hi everyone,

I made a bash script which starts with "#! /bin/dash" (instead of #! /bin/bash)

It was accidental but it works!  So it makes me wonder, 

1) Can I put just about anything after "#!"  
2) How important is that it is "/bin/bash"?
3) What exactly does the /bin/bash line do?

Thanks so much.

---

### Post by Holger_Gehrke on 2018-08-31
That line tells the system what interpreter to use to execute the script. '/bin/dash' is another shell that like bash is compatible to 'sh'. So as long as a script does not use any of the capabilities of the bash that go beyond 'sh' (arrays, for-loops with arithmetic expressions instead of "in list", ... ) it does not matter. 

Holger

---

### Post by webmiester on 2018-08-31
Thanks so much Holger.

It was really accidental.  So I accidentally found another interpreter which was more or less compatible with bash... I think that is so cool!

thanks again!

---

### Post by webmiester on 2018-09-01
Hi Holger,

Im sorry to bother you, but I was just curious, aside from bash and dash, what other interpreters can we call upon after #! and which one do you recommend to use?  Does this mean we can also call on python or something like visual basic?

---

### Post by The Cog on 2018-09-02
Ones I know of are:
/usr/bin/python
/usr/bin/python3
/usr/bin/perl
/usr/bin/js
but there will be lots of others - each one a different interpreter for different language text files. Most are in /usr/bin, only ones needed to boot are in /bin.

P.S.: 
js isn't there until you install package **nodejs**. And then there is a trail of symlinks:
/usr/bin/js -> /etc/alternatives/js
/etc/alternatives/js -> /usr/bin/nodejs
/usr/bin/nodejs -> /usr/bin/node
So the javascript interpreter /usr/bin/node also has aliases of nodejs and js.

Also:
/usr/bin/python -> /usr/bin/python2.7
/usr/bin/python2 -> /usr/bin/python2.7
/usr/bin/python3 -> /usr/bin/python3.6
but of course the specific versions may change with each release of Ubuntu while the generic versionless links will remain. One day in the dim and distant future, I guess python may change to link to python3 instead of python2.

---

### Post by Holger_Gehrke on 2018-09-02
Yes, you can put '#!/usr/bin/python' as the first line of a python script, chmod the file to be executable and expect the system to call python to run it. You can use a shebang line for any interpreted language that uses '#' as a mark for a comment, which includes all the various shells (bash, dash, ash, tcsh and other c-shell variants, pdksh ...), python, perl, tcl, awk and probably dozens more. And I recommend using the language that best fits the problem you're trying to solve.

Holger

---

### Post by webmiester on 2018-09-02
Thanks so much.  This is very nice.  I wonder if there is a visual basic interpreter available too.

---

### Post by Holger_Gehrke on 2018-09-02
> **webmiester said:**
> I wonder if there is a visual basic interpreter available too.

Yes - No - well, almost. Take a look at [gambas]("http://gambas.sourceforge.net").

Holger

---

### Post by webmiester on 2018-09-02
Thanks.  This sounds very exciting.  I used to code some simple programs way back in high school.  Well, Im a doctor now, so I havent coded anything in the past 20 years or so.  The bash script I made was kind of fun :)

Thanks so much.  Ill go take a look at gambas too.

---

