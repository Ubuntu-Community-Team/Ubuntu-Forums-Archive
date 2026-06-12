---
title: "copy old /home to new /home"
date: 2007-11-27
forum: General Help
---

### Post by m.musashi on 2007-11-27
I bought a new HD and did a clean 64 bit install. I want to copy all the files in my old /home to the new /home. However, I don't want to copy the hidden files since that mess up the settings. I figure rsync is the way to go but its syntax is a bit cryptic. Basically, I'm wondering if this will work and if not how to change it. I did copy some files I needed right away manually with two nautilus windows and I could probably do it all that way but I'm afraid I'll miss something. I want rsync to make sure I got everything.

rsync -r --exclude '.*' /media/old/home/musashi/ /home/musashi/

Oh, and it should preserve permissions, owners and such.

Thanks.

---

### Post by fatmano on 2007-11-28
If you are only worried about hidden files at the base of your old home folder.  This will keep hidden folders underneath none hidden directories e.g .svn directories which you would want.  If that sounds like what you are looking for try this:

for i in `find /oldHome -maxdepth 1 -name '[!.]*'`; do for j in `find $i`; do cp $j /newHome/$j; done; done 

HTH

-eo

---

### Post by x64Jimbo on 2007-11-28
What's wrong with copying the hidden files? I have had the same home directory since Dapper, and I've used Kubuntu AND Ubuntu. No problems whatsoever in the changeovers.

---

### Post by m.musashi on 2007-11-28
Thanks for the mini script, fatmano, but I'd really like to learn more about using rsync. I know it can do what I want, I just don't know how to make it do it. Or maybe I do know if my command above is good.

@x64Jimbo - i'm not sure anything is wrong with copying the hidden files but I like doing a clean install and some of the hidden stuff is junk I want to get rid of. For example, if I also set up kubuntu-desktop but no longer want it I don't want to copy the hidden stuff. Same for a lot of stuff I've installed but don't want. I manually copy the hidden files I do want (like firefox passwords).

Thanks.

---

### Post by m.musashi on 2007-12-02
Just wondering if anyone can verify that my syntax is correct or show me a correct version. I don't want to just try it as it could easily mess things up if wrong. Thanks.

---

### Post by cygnine on 2007-12-02
> **m.musashi said:**
> Oh, and it should preserve permissions, owners and such.

rsync's -pgo options will preserve permission, group, and owner, respectively. The archive option, -a, does all this plus -r plus some other stuff. That may be what you want. 

I'm with others in wondering why you'd want to exclude hidden files/directories. A lot of user data for programs is stored in hidden files and directories in /home/user. 

In any case, I guess the --exclude command would do what you want. In addition, you can do --exclude-from=somefile if there are lots of exclusion patterns and you want to store them in a file. Type `man rsync' into a terminal or Google to read up on this stuff.

> **m.musashi said:**
> I don't want to just try it as it could easily mess things up if wrong.

Why don't you just give it a trial run? You'll never know if it will do exactly what you want until you put it into practice first. A quick browse through rsync's manpage and I'd try:

```
rsync -av --include ".*/"  --exclude ".*" /media/old/home/musashi /media/old/temp/
```

I *think* that will include all hidden directories but exclude all hidden files in the parent directory. Just run that and see if everything you want is in /media/old/temp. The -v option is `verbose', meaning it will spit out to the terminal what it's doing. --include ".*/" includes all directories.

---

### Post by m.musashi on 2007-12-02
> **cygnine said:**
> I'm with others in wondering why you'd want to exclude hidden files/directories. A lot of user data for programs is stored in hidden files and directories in /home/user.
The main reason is that I did a fresh install of gutsy on the new drive and have been using it for a while. If I copy the hidden stuff, my current settings will get overwritten.

> ```
rsync -av --include ".*/"  --exclude ".*" /media/old/home/musashi /media/old/temp/
```

I *think* that will include all hidden directories but exclude all hidden files in the parent directory. Just run that and see if everything you want is in /media/old/temp. The -v option is `verbose', meaning it will spit out to the terminal what it's doing. --include ".*/" includes all directories.

I'll give this a go and see what happens. Thanks.

---

### Post by froy02 on 2007-12-02
Why don't you just use nautilus to copy all the unhidden file?
Open terminal window and type 'gksu nautilus' (assuming you installed nautilus-gksu). Now you are a nautilus super user. Go to nautilus edit>preference uncheck 'show hidden files then copy your home directory to the new one.

---

### Post by m.musashi on 2007-12-02
I used nautilus to copy many of the files so that I could get back to work with my new install. However, now I would like to copy over the rest and it would be really easy to let rsync figure out what is new and needs to be copied and what has already been copied. If I use nautilus I would have to co through almost 50GB of files on my own. I would prefer to use the power of the computer to do this work for me. I just want to make sure I do it right and not overwrite files that have been changed or folders that have been modified.

Thanks.

---

### Post by quixote on 2008-03-20
m.musahi: this rsync command preserves permissions, links, and so on:

```
rsync -avu /dir1/somefile/ /backup/somefile
```

-a archive, like the commenter above said, preserves settings.
-v verbose (you can leave this out if you don't want to watch all your neat files scrolling up the screen :)
-u update, tells rsync to write only changed files and to skip unchanged ones, which speeds up the process.  Unless it's a new backup, in which case they're all "changed"
/ trailing slash on source but not on target means that it will copy the *contents* of the source directory to the target, and not make a new subdirectory of the same name as the source dir.

I've been trying to find how to exclude hidden files, for the same reasons as you.  I haven't tried this yet, but this seems to make sense:

```
rsync -avu  --exclude ".*" /dir1/somefile/ /backup/somefile
```
(that's: quote, period, asterisk, quote)

I'll try to get back and leave another comment when I find out for sure if it works.

---

### Post by quixote on 2008-03-20
apparently it's ```
 --exclude ".*/"
```

the slash means you want to exclude hidden directories as well as hidden files.  Kind of the whole point! ;)

---

### Post by m.musashi on 2008-03-22
Thanks. I have tried with the ".*" before and it seemed to work but I never paid real close attention to the directories. I'll keep this in mind next time.

---

### Post by der_joachim on 2008-03-23
Another tip: with the -n and the -v  option you can 'test-drive' your sync. ```

rysnc -anvz /path/to/old/home /path-to-new-home

```
This command enables you to see what is actually being synced, without actually overwriting anything. Remove the -n option to exit the dry-run modus and the -v option to remove verbosity.

---

### Post by quixote on 2008-03-24
I've actually used it now and this was my result: 

 --exclude ".*/"  excludes all hidden directories and their contents, but not hidden files in the first-level directory itself (home in this case).  

--exclude ".*" excludes hidden files in the first-level dir, but not hidden folders.

---

