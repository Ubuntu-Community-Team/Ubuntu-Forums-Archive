---
title: "Directory starting with -"
date: 2007-02-13
forum: General Help
---

### Post by endfx on 2007-02-13
I've found a directory that starts with a - on my fileserver (thanks Windows users!)
I can't cd into it. Does anybody have any ideas of how I can cd into it?

Renaming isn't an option.

I've tried the following:

cd -dirName
cd '-dirName'
cd "-dirName"
cd \-dirName
cd \-\dirName

Any ideas?

Thanks.

---

### Post by MCSE_Crossover on 2007-02-13
Just to get the easy questions out of the way

Can you list the permissions on the directory? What are they?

---

### Post by dcstar on 2007-02-13
> **endfx said:**
> I've found a directory that starts with a - on my fileserver (thanks Windows users!)
I can't cd into it. Does anybody have any ideas of how I can cd into it?

Renaming isn't an option.

I've tried the following:

cd -dirName
cd '-dirName'
cd "-dirName"
cd \-dirName
cd \-\dirName

Any ideas?

Thanks.
Try: 

cd *dirName

---

### Post by endfx on 2007-02-14
No, I can't get the permissions.
I did an "ls -ld *" on the directory and it complains about the '-' in the filename.

More info: The directory is actually called -55
and so this is the error I get:

# ls -ld *
ls: invalid option -- 5
Try `ls --help' for more information.

Now when I do a cd *55 I get similar thing :
# cd *55
bash: cd: -5: invalid option
cd: usage: cd [-L|-P] [dir]

Any more ideas?

---

### Post by MCSE_Crossover on 2007-02-14
I have a Unix/Solaris expert here at work. I will hit him up about this question when he comes in.

---

### Post by highneko on 2007-02-14
cd -- -55

---

### Post by MCSE_Crossover on 2007-02-14
New idea...can you access it from a Windows box on the network? What exactly are you trying to do with the directory? Get rid of it or just list the contents? Created on Windows through Samba or something, you should be able to access it through a Windows medium I would assume.

---

### Post by reclusivemonkey on 2007-02-14
If all else fails, install Midnight Commander

```

sudo apt-get install mc

```

and you should be able to look inside it that way, and rename/delete it as necessary.

---

### Post by ~LoKe on 2007-02-14
> **highneko said:**
> cd -- -55

Correct.

---

### Post by MCSE_Crossover on 2007-02-14
Spoke with the Unix guy -

from the command line, type "bash" or "tcsh" to go into one of the shells

then, type "cd \-" and then hit the TAB key to make sure there aren't additional spaces or extra characters that aren't being displayed. It will auto complete if necessary.

Then hit enter. See if that works.

---

