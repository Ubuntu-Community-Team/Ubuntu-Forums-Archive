---
title: "--include-list    rdiff-backup"
date: 2021-11-05
forum: General Help
---

### Post by Quarkrad on 2021-11-05
I have been using rdiff-backup for backup  using scripts originated by TheFu. Part of the script includes:

```
sudo /usr/bin/rdiff-backup  --exclude-special-files \
 #          --include /home --include /root --include /etc
```

I have been experimenting using an --include-list as I do not want everything in /home so my new script looks like:

```
sudo /usr/bin/rdiff-backup  --exclude-special-files \
           --include-filelist '/usr/bin/includelist.txt' --include /root --include /etc
```

my /usr/bin/includelist.txt file lists a number of directories I want to backup - e.g.

```
/home/dad/Desktop/
/home/dad/Documents/
/home/dad/Downloads/
/home/dad/dvd/
/home/dad/Music/
/home/dad/Pictures/
```

All this works as I hoped - all the directories specified in the rdff-backup script are copied to my local backup.  However ..... there is something wrong with my /usr/bin/includelist.txt file.  In the backed up copy .... in /home I have all the right directories but they are empty.  Spent quite a few hours on this and seem to be almost there but I cannot find what extra commands/symbols I need to add.   E.g. my include list specifies /home/dad/Documents  and /home/dad/Documents is copied - but not it's contents.

---

### Post by Quarkrad on 2021-11-05
Solved, although to be honest I do not fully understand why (more learning!)  Added globbing to my script.

```
sudo /usr/bin/rdiff-backup  --exclude-special-files \
           --include-**globbing**-filelist '/usr/bin/includelist.txt' --include /root --include /etc
```

---

### Post by TheFu on 2021-11-05
Without seeing the entire command, I cannot say what is happening.  However, I don't think you can comment out a line in the middle of a multi-line command using continuation characters.

Regardless of the include/exclude stuff, there always, always, always has to be both a SOURCE and target TARGET in the command. I think those two have to be the last 2 arguments in the total command line.  My base command uses / as the source and excludes everything.  Then it specifically includes directories that I want backed up.  Order of the include/exclude arguments matters. The manpage explains that part.

---

### Post by softrabbit on 2022-10-22
No, there is no solution, but TheFu gives the solution. Quarkrad does not have source and target. Therefore, include-list just makes the listed directories. The reason why the 'solution' works is:

"we have used --include-globbing-filelist instead of --include-filelist so that the lines would be interpreted as if they were specified on the command line." ([https://rdiff-backup.net/docs/examples.html](https://rdiff-backup.net/docs/examples.html))

So, Quarkrad had made his command work by swithching the list to be cml-specifications that presumable were added to the end of the command. But, this is an ureliable method as it does not follow the syntax of rdiff-backup.

---

### Post by HermanAB on 2022-10-22
BTW, an include list always needs maintenance.  In my experience it is better to include everything and exclude certain things.  That way requires less or no maintenance, since anything new will be backed up.

---

### Post by QIII on 2022-10-22
Thanks for the late replies, but I'm putting this thread back to sleep.

RIP

---

