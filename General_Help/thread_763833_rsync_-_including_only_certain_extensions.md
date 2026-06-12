---
title: "rsync - including only certain extensions"
date: 2008-04-23
forum: General Help
---

### Post by chantron on 2008-04-23
Hi,

I run some backup scripts using rsync and after compression the backups are still over 50gb. I'd like to cut that down and to do that I want to include ONLY files with certain extensions (eg every file with a .bmp/.mp3/.pst etc.. extension)

My question is that if i use --include will it exclude all other files or will I have to use a combination of the --include and --exclude. Maybe there's an even easier way of doing it.

Any help you could give would be awesome.

Thanks a lot!

---

### Post by txcrackers on 2008-04-24
I'd use the
```
--include-from=FILE
```
option. Put the regular expressions of the files you want to backup, one per line, into a file and use that filename in the option. It may a bit of experimenting to get the names correct, but if you're trying to only include a certain subset of names, this will be the easiest to use (and maintain).

---

### Post by chantron on 2008-04-24
> **txcrackers said:**
> I'd use the
```
--include-from=FILE
```
option. Put the regular expressions of the files you want to backup, one per line, into a file and use that filename in the option. It may a bit of experimenting to get the names correct, but if you're trying to only include a certain subset of names, this will be the easiest to use (and maintain).

Thanks for the reply. I hate to sound noobish but do you have an example of the kind of expression I would use?

Also, will the include file force rsync to ONLY transfer files in the file?

---

### Post by chantron on 2008-04-28
Bumped.

---

### Post by thuerrschmidt on 2009-12-23
What you need is indeed a combination of --include and --exclude arguments. For example the following will replicate only mp3 files in a directory named source, or any of its subdirectories, to a directory named target:

```
rsync -a --include '*/' --include '*.mp3' --exclude '*' source/ target/
```

This will (1) include any directory or subdirectory, whatever its contents, (2) include all files with an mp3 extension, and (3) exclude all other files. Any number of other file types can be included by adding their one include pattern for each before the --exclude, e.g. --include '*.bmp'.

---

### Post by schneidexe on 2011-02-28
Thanks! :)

---

### Post by kermit666 on 2011-11-21
> **thuerrschmidt said:**
> What you need is indeed a combination of --include and --exclude arguments. For example the following will replicate only mp3 files in a directory named source, or any of its subdirectories, to a directory named target:

```
rsync -a --include '*/' --include '*.mp3' --exclude '*' source/ target/
```

This will (1) include any directory or subdirectory, whatever its contents, (2) include all files with an mp3 extension, and (3) exclude all other files. Any number of other file types can be included by adding their one include pattern for each before the --exclude, e.g. --include '*.bmp'.

Thanks a lot! I've been searching for this information all over the internet and rsync's manpage and couldn't find it :)

---

### Post by oldos2er on 2011-11-21
Closed, necromancy.

---

