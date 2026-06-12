---
title: "Rsync include/exclude list"
date: 2008-01-14
forum: General Help
---

### Post by spupy on 2008-01-14
Hi!
I'm trying to write a very simple script to back up my home directory to my server. Here is my rsync line:
```
rsync -e ssh -varuzPL --max-size=10M --list-only --exclude-from excludes.list --include-from includes.list --stats --log-file="$today.log" /home/spupy/* zion:/home/spupy/backups/
```
(--list-only is there for the testing only). The problem is that i haven't written the includes.list file quite right and it's not working. Here is (a part of excludes.list):
```
*
*Downloads/PROGRAMS*
*Downloads/Pics*
*Music*
```
...and includes.list:
```
*/Desktop/*
*/Downloads*
*/home/uibxn/.conkyrc*
*.fluxbox*
*.gtkrc-2.0*
*.mpd*
*.mpdconf*
*.thunderbird*
*.bashrc*
```
I want to exclude everything first, so i put '*' in excludes. And it does exclude all. But then the stuff i listed in includes don't get included. For example, i want to include the stuff i have in my "Downloads" folder, but without the "Pics" and "Programs" subfolders.
What am I missing here? The syntax of the list files? Or maybe the logic for the lists is different than i think? Please tell me!
Thanx for reading, double thanks for answering! ;)

---

