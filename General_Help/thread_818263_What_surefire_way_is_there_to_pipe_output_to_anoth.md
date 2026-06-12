---
title: "What surefire way is there to pipe output to another command?"
date: 2008-06-04
forum: General Help
---

### Post by ChameleonDave on 2008-06-04
I'm stuck on a certain problem in bash.

What I want to do is pipe the result of one command to another.

Let's say I want to get the result of "ls *" to "rm".  I was under the impression that the following code (either on the command line or in a script) would suffice:

```
$ ls * | rm
```

But it doesn't, so I must be missing something.

Let's say the current directory contains files called "foo" and "bar".  I want something that automatically does the equivalent of the following:

```
$ ls
foo bar
$ rm foo bar
```

What is the simplest way to get the output of the first command to carry over?

If you tell me to enter "rm *" you have completely missed the point.

---

### Post by ChameleonDave on 2008-06-04
Ah, it's with "xargs", isn't it?

---

### Post by bingoUV on 2008-06-04
The developer of rm program had a choice of accepting input in these 2 simple ways 
1. Command line arguments. e.g. rm arg1 arg2 ...
2. Standard input e.g. cat filename | rm

They chose 1. i.e. command line arguments. rm does not read its standard input i.e. stuff piped in like you did.

For a solution to your problem, do
```

rm `<command to run>`

```

If the <command to run> has output
```

outputline1
outputline2
outputline3

```

files outputline1, outputline2 and outputline3 will be deleted.

---

### Post by bingoUV on 2008-06-04
xargs is not bad, but I don't find it intuitive for these cases. Though, these are extremely personal things.

---

### Post by ChameleonDave on 2008-06-04
> **bingoUV said:**
> 
For a solution to your problem, do
```

rm `<command to run>`

```


Hmm, that doesn't seem to always work.

The following code successfully creates and deletes "deleteme".

```
mkdir test
cd test
touch deleteme
rm `ls`
```

But this code doesn't:

```
mkdir test
cd test
touch deleteme
rm `locate -e deleteme`
```

I think I'll use xargs.

---

### Post by lavinog on 2008-06-04
> **ChameleonDave said:**
> Hmm, that doesn't seem to always work.

The following code successfully creates and deletes "deleteme".

```
mkdir test
cd test
touch deleteme
rm `ls`
```

But this code doesn't:

```
mkdir test
cd test
touch deleteme
rm `locate -e deleteme`
```

I think I'll use xargs.

Quoted from man page of locate:
" locate can never report files created  after  the  most  recent update of the relevant database."

That might be the reason why

---

### Post by bingoUV on 2008-06-04
my locate man page says
```

       -e <dir1,dir2,...>
              Exclude directories from the slocate database.

```

Don't know what your locate does when given -e option.

EDIT : Anyway, you can always verify what rm `command` will do by running just command. Note that the output at standard error (STDERR) will not go to rm, just the output at standard output (STDOUT) will

---

### Post by roffles on 2008-06-04
I think for what you want to do the quickest way is to use find with the -delete switch

find . -name "foo*" -delete

or in general you can use -exec and pass the output of your find results to a command, in this case rm:

find . -name "foo*" -exec rm {} \;


hope this helps!

---

### Post by lavinog on 2008-06-04
> **bingoUV said:**
> my locate man page says
```

       -e <dir1,dir2,...>
              Exclude directories from the slocate database.

```

Don't know what your locate does when given -e option.


weird my locate many page says:
```
 -e, --existing
              Print only entries that refer to  files  existing  at  the  time locate is run.

```

---

### Post by bingoUV on 2008-06-04
> **lavinog said:**
> weird my locate many page says:
```
 -e, --existing
              Print only entries that refer to  files  existing  at  the  time locate is run.

```

I am not running Ubuntu, but RHEL4, so it is not that weird. I should have mentioned that. But still.

---

### Post by ChameleonDave on 2008-06-04
> **roffles said:**
> I think for what you want to do the quickest way is to use find with the -delete switch

find . -name "foo*" -delete

or in general you can use -exec and pass the output of your find results to a command, in this case rm:

find . -name "foo*" -exec rm {} \;


hope this helps!

That only works with "find" though, doesn't it?

Never mind.  The command "find" is probably better than "locate", really.  I just liked how fast "locate" was.

OK, here is what I have come up with:

```
find ~ -name "*gz" -size -5M -print0 -exec advdef -z4 {} \;
```

This runs through my user directory, gets all the gzipped files, and optimises them for size.  I've saved about 10% of the disk space previously occupied by those files.

With minor variations, I can optimise all my SVGZs, PNGs, ZIPs, etc.

If I'm feeling daring, I may run it on "/".

---

