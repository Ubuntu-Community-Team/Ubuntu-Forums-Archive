---
title: "help piping to xargs rm"
date: 2012-10-20
forum: General Help
---

### Post by moorsey on 2012-10-20
Hi all,

I am trying to write a little script that removes the oldest backups, keeping just the latest 2.  This is what I have:

ls -t | tail -n +3 | xargs rm -f

I have checked each bit by bit and all the correct output is given, but it never removes the files.

I have tried with "xargs echo rm -f" and it shows the correct output as well, choosing the file that should be removed, but does not remove it.

Anyone got any ideas what I might be doing wrong?!

Cheers!

---

### Post by Habitual on 2012-10-20
```
ls -t | tail [COLOR=Red]-3[/COLOR]...
```

---

### Post by moorsey on 2012-10-20
that just lists the first 3, not from 3 onwards

the -n +3 works fine and outputs correctly, but when passed to rm, it does nothing

---

### Post by Habitual on 2012-10-20
moorsey:

ls output *may* be behave differently on different systems/OSs

Here, I get this:
ls -t | tail -n +3
```
env.out
set.out
VirtualBox VMs
Documents
Downloads
Pictures
Desktop
Public
Videos
Music
Templates

```but -3 gives me
```
ls -t | tail -3
```Videos
Music
Templates

please type 
```
type ls
```and post that output,

Thank you.

Edit:
You ONLY keep 5 backups?
"keeping just the latest 2"

---

### Post by moorsey on 2012-10-20
ah interesting, my apologies.

I get the following output:

```
ls is aliased to `ls --color=auto'
```

many thanks

---

### Post by sisco311 on 2012-10-20
ls prints its output in human readable format. Its a great tool for looking at file informations interactively, but it will cause bugs in scripts. You should use globs or find instead. See: 

[http://mywiki.wooledge.org/ParsingLs](http://mywiki.wooledge.org/ParsingLs)

and

BashFAQ 003 (link in my signature).

---

### Post by Lars Noodén on 2012-10-20
> **Habitual said:**
> 
ls -t | tail -n +3


The plus is in the way, an alternative to writing 'tail -3' would be to write 'tail -n 3'

---

### Post by Vaphell on 2012-10-20
sisco speaks the truth. Create a file with a newline in the middle (it's allowed) and tell us how the ls approach works for you ;-)

```
$ > $'xyz\nxyz'
$ echo xyz*
xyz
xyz
$ ls xyz* | xargs rm
rm: cannot remove `xyz': No such file or directory
rm: cannot remove `xyz': No such file or directory
```

---

### Post by Lars Noodén on 2012-10-20
> **Vaphell said:**
> sisco speaks the truth. Create a file with a newline in the middle (it's allowed) and tell us how the ls approach works for you ;-)


It gets complicated quickly.  What is the best way to do what he was originally trying to do which was getting rid of the oldest 3 files?

---

### Post by sisco311 on 2012-10-20
I would recommend one of the backup tools to backup your files: [https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

or logrotate to keep backups of log files.

But if you want to write your own script, then here is how I would print the name of all files but the two latest from a directory:
```

i=0
while IFS= read -rd '' file
do
    ((i++))
     if ((i>2))
     then
         **echo** "${file#* }"
     fi
done< <(find ./ -type f -printf '%T@ %p\0' | sort -znr)

```

Test it and if it works as intended, then you can replace the **echo** command with **rm**.

---

### Post by moorsey on 2012-10-22
wow, great, thanks for all the tips, apologies for not getting back here sooner.

I did find another alternative, one liner, that seems to work:

```
ls -t * | awk 'NR>2 {system("rm \"" $0 "\"")}'
```

Although I will admit to not being 100% sure how it works.

sisco311, I will give yours a try this weekend, many thanks for taking the time for that.  I will also give the bash stuff a read, been getting into these basic scripts recently.

Find it odd that the original command does not work, but looking around, it does seem to echo thoughts here, that ls causes problems.

Anyway, got some stuff to go on here, many thanks all!

---

### Post by Lars Noodén on 2012-10-23
I'd look into logrotate as sisco311 hinted at.  It already solves the problem of rotating log files and has a lot of capabilities.  It's very easy to set up.

---

### Post by moorsey on 2012-10-23
I did indeed look into logrotate, but couldn't find any mention of using it on something other than log files, guess it is the same in principle, just point it at the directory with the files in.

Will take a look and experiment, better to use a script made for the job?!

cheers

---

