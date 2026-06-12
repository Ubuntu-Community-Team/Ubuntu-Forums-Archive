---
title: "shebang question"
date: 2007-04-14
forum: General Help
---

### Post by evaristegalois on 2007-04-14
Why does the shebang not work on my computer? How could I test it? Here is the situation:

I wrote an html form and put it on my server. Worked fine. The first line of my cgi file is #! /usr/bin/perl so that the shell (or the kernel) knows that the cgi script is a perl script. 

When I use exactly the same form on my local computer (mutatis mutandis file references, of course) I only get garble when I hit the submit button in the html form, presumably because instead of interpreting the perl file as a perl executable file (I changed the file permissions to make it executable, btw) it just seems to stupidly read it off the page despite the shebang #!/usr/bin/perl (which indicates the correct location of perl on my computer).

--evaristegalois

---

### Post by stylishpants on 2007-04-14
> **evaristegalois said:**
> Why does the shebang not work on my computer? How could I test it? Here is the situation:

I wrote an html form and put it on my server. Worked fine. The first line of my cgi file is #! /usr/bin/perl so that the shell (or the kernel) knows that the cgi script is a perl script. 


If that is actually the first line, then one of your problems is that you should not have a space after the "!".


> 
When I use exactly the same form on my local computer (mutatis mutandis file references, of course) I only get garble when I hit the submit button in the html form, presumably because instead of interpreting the perl file as a perl executable file (I changed the file permissions to make it executable, btw) it just seems to stupidly read it off the page despite the shebang #!/usr/bin/perl (which indicates the correct location of perl on my computer).

--evaristegalois


The problem could also be in your local computer's http server configuration.  

You can easily check whether your shebang is right by trying to run your script manually yourself, from the command line, rather than through the web interface.  

You could even comment out all your code and just put "print 'hello\n'"; right under the shebang line, if your script won't run easily from the command line.

---

### Post by evaristegalois on 2007-04-15
Thanks. That helped. I didn't realize you couldn't just type 

shebang.pl

on the command line if you were in the directory where shebang.pl was (existing of the hello world program). You have to type

./shebang.pl

or put shebang.pl in a directory that's in the path. 

In any case, my problem isn't quite solved yet because perl on my computer doesn't seem to know what to do with the line

print "Content-type: text/html\n\n";

which works perfectly fine on the server and is sort of crucial to the whole enterprise because the idea is that the website interacts with the user inside the browser. If anybody knows how to change that line to make it work on a local computer please let me know.

--evaristegalois

---

### Post by stylishpants on 2007-04-15
That line is absolutely basic perl code that should work in any and all perl versions.  You do not need to rewrite it.

You can prove it to yourself like this:  
```
perl -e 'print "Content-type: text/html\n\n";'
```


What error message or problem are you experiencing?

---

