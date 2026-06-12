---
title: "shell script question"
date: 2016-03-27
forum: General Help
---

### Post by Old Jimma on 2016-03-27
Hi Community:

I want to write a shell script and execute it using cron.

Among the things that shells script needs to do is to create a new director with today's date.

How do I do that?

I've tried
> 
set TODAY='date +%F'
##
mkdir $TODAY


but that doesn't work!


Thanks,
Old Jimma

---

### Post by nerdtron on 2016-03-28
it's not single quotes. it should be backticks (the key left of number 1 on the keyboard, above the tab key)

```
 
#!/bin/bash
set TODAY=`date +%F`
##
mkdir /full/path/$TODAY

```

Also it's better to use full paths on your script since cron will execute the script on a different directory. (i'm not sure where).

---

### Post by Old Jimma on 2016-03-28
Thanks, nderdtron:

Here is my script:

> 
#!/bin/bash
##
cd "/mnt/TVA/Music2/Radio/Jazz24"
## 
set TODAY=`date +%F`
##
mkdir /mnt/TVA/Music2/Radio/Jazz24/$TODAY


when I use this mkdir command it says
> 
mkdir: cannot create directory ‘/mnt/TVA/Music2/Radio/Jazz24/’: File exists


However, when I do an [COLOR="#FF0000"]**ls**[/COLOR]... there is nothing in that directory.

What am I doing wrong?

Thanks,
Old Jimma

---

### Post by sudodus on 2016-03-28
In ***bash*** you do not use ***set***. Instead use ***typeset*** or even better simply

```
TODAY=`date +%F`
```

---

### Post by Old Jimma on 2016-03-28
Thank you!

I'm setting up directories to rip streaming radio with streamripper.

I'm going to retire soon and will brush up on linux commands then ... I'll read a book!

Many thanks!
Old Jimma from the Old Country

---

### Post by SeijiSensei on 2016-03-28
I suggest using "mkdir -p $TODAY" so that mkdir will not complain if the directory already exists.

Also while backticks still work to reference the output of the command they contain, they have been deprecated in favor of the $() syntax.  So I'd use
```

TODAY=$(date +%F)
mkdir -p $TODAY

```

If you don't need the TODAY variable for any other purpose in your script, you can just use
```
mkdir -p $(date +%F)
```

---

