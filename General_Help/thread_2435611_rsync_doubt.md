---
title: "rsync doubt"
date: 2020-01-23
forum: General Help
---

### Post by giobaxx on 2020-01-23
Hello all

I need an additional clarification about the use of rsync. Normaly i use to backup Home Folder from an old Linux Workstation to an new one, and i use this  command:

> *rsync -avz /home/username/     username@hostname:/home/username --exclude=".*"  *  


[LIST]
[*]if i need to exclude all the hidden files/folders is correct the option *--exclude=".*"*
[*]Sometimes it happened like today#-o, that the new workstation is never used(for weeks or months) and we would need to re-run an rsync to update the "backup" running again:
[/LIST]

> *rsync -avz /home/username/     username@hostname:/home/username --exclude=".*"  *

I thought it was going to copy only the difference, basically all the modified files in the source(the new workstation was never touched) but i have the suspect that it copying again all the file, because the Rsync it has been running for 15 hours.

Where am I doing wrong?

---

### Post by TheFu on 2020-01-23
*--dry-run* is very helpful.

I would start by testing something like this if not getting dotfiles is desired.
```
rsync -avz  --dry-run --exclude="/home/*/.*"      /home/username/     username@hostname:/home/username/
```
Note the order and trailing slash on the target. In theory, the trailing slash on the target shouldn't matter, but ...

.* alone matches much more than just config files.

If you need more exact control, using the *--exclude-from=list-o-exclude-files.txt* is handy.

For the target to be just like the source, might need to add *--delete* to the options.  rsync is additive unless explicitly told to delete any files in the target that do not exist in the source. There are a few different --delete-.... options, depending on how much excess storage the target directory has and whether deleting after, before or during is needed.

---

### Post by giobaxx on 2020-01-23
Wth the --exclude option sometimes we want to exclude configuration files because it can happend to pass from an ubuntu 14.04 to an 18.04 and also from Fedora to ubuntu 18.04 and we don't want overwrite configuration files over the new Workstation with the new software installed.

we have also a scenario where a user has two old workstation and we need to rsync two home over the new workstation and normally we back the younger with the command i mentioned before:


[LIST=1]
[*]> *rsync -avz /home/username/ username@hostname:/home/username --exclude=".*"*
[/LIST]

Then we create an additional folder on the new workstation where to copy the home folder of the older computer:


[LIST=1]
[*]> *rsync -avz /home/username/ username@hostname:/home/username/Older_Workstation --exclude=".*"*
[/LIST]


[I]To use the --delete option is dangerous unfortunately  i have to run the 1st command again it will delete the Older_Worlstation folder, right?

but apart the --exclude option what i really feel is that the rsync is copying everything again......maybe it could be  the  missing / on the destination......i don't know....

[/I]

---

### Post by cmcanulty on 2020-01-23
I do an grsync every week. One with /home and one with / but here are the excludes I put in
```
--exclude '/cdrom'
--exclude '/dev'
--exclude '/home'
--exclude '/lost+found'
--exclude '/media'
--exclude '/mnt'
--exclude '/proc'
--exclude '/run'
--exclude '/sys'
--exclude '/tmp'
--exclude '/.cache'
--exclude '/.Trash-0'
```
I am also posting 4 pics of the options I put which seem to work real well and the excludes setup

---

### Post by HermanAB on 2020-01-24
Hmm, I'm not sure about that '.*'

In Bash, '*' includes a '.', therefore '.*' will expand to '..', which may indicate the previous directory and not do what you want.

---

### Post by TheFu on 2020-01-24
Exactly Herman.  That's why I used the path with multple wildcards.

Never underestimate the utility of **--dry-run** either.

---

### Post by giobaxx on 2020-01-27
Hello Guys just some update

I've made some test with two very simple virtual Machine and the *exclude =".*"* seems to work but to be sure i want to try to run the rsync with the --dry-run as advised by ***@TheFu*** to try to understand the behavior of the Rsync with the option  *exclude =".** about the problem mentioned by[I]** HermanAB**.
[/I]
About the problem to run a second or a third rsync to update modified files/folders on the source i asked to a collegue that is an advanced linux user and he told me to use the following option *rsync -auvz sources destination,* even if i tried to run rsync in the two simple VM created by me and the *rsync -avz sources destination* work perfectly.

I have added a file in the sources VM and Running a second rsync only that file was copied from the source to the destination...i will try again this week...

[COLOR=#000000]HermanAB[/COLOR]

---

