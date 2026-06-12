---
title: "rc.local rc.local rc.local"
date: 2007-11-13
forum: General Help
---

### Post by mrashley on 2007-11-13
First of all: ARGH!

Okay now that's off my chest, sorry for being so frustrated, but whenever I do a search for "rc.local" in all forums it's as if it's a new word from an alien language ne'er spoken by a human. I get no results. I get results for pretty much any other vague search term, but not that one. I've attached a screenshot of my results so anyone can feel free to point out that I've somehow managed to select the "don't actually give me results" tickbox.

So two questions: Before I toss myself to the ground screaming like an unruly child in a supermarket please would someone advise me what on earth I am doing wrong in searching for this particular term. I am *CERTAIN* someone since the dawn of Ubuntu has referred to this file in the forums.

Secondly how do I get this painfully elusive file to run during login on a gutsy machine? I thought it was just supposed to run like the autoexec.bat. There is some cryptic message about making sure the execution bits being set, but if I look at the file permissions it's x's all across.

---

### Post by jfinkels on 2007-11-13
When in doubt, Google: [http://www.google.com/search?hl=en&q=rc.local+site%3Aubuntuforums.org&btnG=Google+Search](http://www.google.com/search?hl=en&q=rc.local+site%3Aubuntuforums.org&btnG=Google+Search)

Try changing "#!/bin/sh -e" to "#!/bin/bash"

---

### Post by mrashley on 2007-11-13
I did google the matter, which led me to the ubuntuforums. It was only when I refined my searches on the actual forum that I found this odd problem.

As for the bash vs sh I don't think that'll be a problem, because

```
which sh
/bin/sh      <--- path is right

sh
$                <--- see it runs. 

```

and according to the manpage sh -e is a valid flag

However I will post my rc.local in case that clears up anything.

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

ivtv-tune --device=/dev/video0 --channel=3
touch /bootdate
exit 0

```

Also 
```
-rwxr-xr-x 1 root root 365 2007-11-13 11:16 rc.local

```

---

### Post by jfinkels on 2007-11-13
Well, you can't say it doesn't work unless you try it! :)

---

### Post by geraldm on 2007-11-13
Locate the file on your system.  It should be a file with mostly comments, and "exit 0"

```

find /etc -name "rc.local" -print

```
replace the file with your edited file, or add your two edited commands
Correct the permissions if you replace the file.
That is all you should have to do.  The file gets executed by a link in each of the
/etc/rc?.d/S99rc.local
Those links should already point to where the rc.local file is.

Gerald

---

### Post by fragos on 2007-11-13
The file you want is /etc/rc.local.  When you make changes, make sure that the last line in the file is still "exit 0".

---

### Post by mrashley on 2008-02-03
Does anyone know why nobody can search for the term "rc.local" in the ubuntu forums?

It's kind of freeaking annoying!!

---

### Post by fragos on 2008-02-03
rc.local is a bash shell file which has comments about it's purpose and use.  Exactly what bash commands to use depends on what you're trying to accomplish.  In general, any file or folder with a ".local" extension is a place for users to add bash commands.

---

### Post by B'man on 2008-02-03
> **mrashley said:**
> Does anyone know why nobody can search for the term "rc.local" in the ubuntu forums?

It's kind of freeaking annoying!!

I'd assume the forum is using fulltext search indexing and is separating rc and local into two words, and that MySQL doesn't index words under 3 or 4 letters long.

---

