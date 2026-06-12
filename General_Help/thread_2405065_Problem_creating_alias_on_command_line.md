---
title: "Problem creating alias on command line"
date: 2018-10-31
forum: General Help
---

### Post by ubuntini2 on 2018-10-31
Hi
Trying to create an alias in the command line using the following

> alias houdini_run='pathold=$PATH; PATH=/home/jim/yt-conda/bin:/home/jim/yt-conda/sbin:/opt/hfs17.0.352:/opt/hfs17.0.352/bin:/usr/bin:/usr/sbin/;/opt/hfs17.0.352:/opt/hfs17.0.352/bin/houdini-bin; PATH=$pathold'

Then when I enter 'houdini_run' I get the following error
> bash: /opt/hfs17.0.352:/opt/hfs17.0.352/bin/houdini-bin: No such file or directory

However, if I navigate to the bin directory, and simply enter houdini-bin, I still get the 'No such file' error but the application correctly launches.

Can anyone tell me what is going on here?

---

### Post by TheFu on 2018-10-31
Check the : and ;   - something looks funny.
I think you want to use double-quote, not single-quotes around the whole thing too.

---

### Post by HermanAB on 2018-11-01
Yup, you need "double quotes" to expand "$variables".

---

### Post by ubuntini2 on 2018-11-01
Thanks.
Appreciated but the alias seems to work the same with single or double quotes.

If I edit the cmd slightly

alias houdini_run="pathold=$PATH; PATH=/home/jim/yt-conda/bin:/home/jim/yt-conda/sbin:/opt/hfs17.0.352:/opt/hfs17.0.352/bin:/usr/bin:/usr/sbin/;/opt/hfs17.0.352/bin/houdini-bin; PATH=$pathold" 

I can get houdini to launch when I enter houdini_run
but I still get all the 'not found' errors.

---

### Post by TheFu on 2018-11-01
So. ... the way I'd solve this is to put the commands into a shell script, run it with debug mode to see how things are really working.  That would mean each command on a separate line.

And I wouldn't completely replace the existing PATH - I would preprend the extra things needed, but there are likely to be other tools in the OS PATH that are still needed and probably the LD_LIBRARY_PATH needs to be fixed too.

And you should check that an export isn't necessary so that subshells will inherit the new PATH.

The original error;
```
 bash: /opt/hfs17.0.352:/opt/hfs17.0.352/bin/houdini-bin: No such file or directory 
```
is because there isn't a command in that line.  This is why I suggested that you check the ; and : already. Something is broken, probably because you have a : where a ; is needed.

But if you put everything into a bash script and put each command onto a new line, it will be OBVIOUS what the issue is.

And you still need to use double-quotes, not single quotes.  Herman and I have been doing this stuff for decades.

---

