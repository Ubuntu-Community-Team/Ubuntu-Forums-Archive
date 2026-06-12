---
title: "Trusty Nautilus copy operation reads file size wrong"
date: 2018-01-28
forum: General Help
---

### Post by kansasnoob on 2018-01-28
I wonder if anyone else has seen something like this. Right-clicking my Documents folder and selecting Properties shows the folder is under 600 MB, but I'm copying folders from Home as part of a regular backup and the file operation dialog shows it as being over 5 GB:

[ATTACH=CONFIG]278358[/ATTACH]

I'm sure it hasn't always been that way but I don't see any recent updates to nautilus in the changelog. I'm letting it complete to see what the size of the destination folder is but it sure is slow:

[ATTACH=CONFIG]278359[/ATTACH]

---

### Post by kansasnoob on 2018-01-28
Destination folder came out nearly the same size:

[ATTACH=CONFIG]278360[/ATTACH]

The slight reduction in size makes sense because I chose to "replace" duplicate files that exist within internal folders - yes, I need to clean that up some day :)

I've searched for a bug report to no avail.

---

### Post by kansasnoob on 2018-01-28
Copying my Pictures folder all is normal. So I decided to cd to /Documents and something is borked:

```
lance@lance-dg41ty:~$ du -sh ./*
40M	./Desktop
4.8G	./Documents
48G	./Downloads
12K	./examples.desktop
4.0K	./Music
480M	./Pictures
4.0K	./Public
4.0K	./Templates
15M	./Videos
lance@lance-dg41ty:~$ cd /Documents
bash: cd: /Documents: No such file or directory
lance@lance-dg41ty:~$ cd /Downloads
bash: cd: /Downloads: No such file or directory
lance@lance-dg41ty:~$ cd
lance@lance-dg41ty:~$ cd /Pictures
bash: cd: /Pictures: No such file or directory

```

Earlier I could cd to Pictures and Downloads but now they're borked too :(

---

### Post by mc4man on 2018-01-28
Don't know about your file size stuff but it's cd Pictures or cd Documents ect. when at your normal default prompt
/Pictures  /Documents  directories don't exist

---

### Post by kansasnoob on 2018-01-28
> **mc4man said:**
> Don't know about your file size stuff but it's cd Pictures or cd Documents ect. when at your normal default prompt
/Pictures  /Documents  directories don't exist

Oops. I should know that, I mean for crying out loud I use zsync for updating iso's all the time. A sure sign I've tipped over into dementia??????

---

### Post by mc4man on 2018-01-28
> **kansasnoob said:**
> Oops. I should know that, I mean for crying out loud I use zsync for updating iso's all the time. A sure sign I've tipped over into dementia??????

Nah, just one of those things. Did that myself a few days ago..

---

### Post by kansasnoob on 2018-01-28
Clearly something is borked:

[ATTACH=CONFIG]278361[/ATTACH]

I dunno what to look for next :redface:

---

### Post by kansasnoob on 2018-01-28
I found the problem by sorting by modification date. I'd needed a flash drive for backing up a Windows install before reinstalling and I copied all of the contents of that drive to a folder named PNY_BK. The thing is that drive contained a folder named Documents (as well as others) but after deleting that entire folder I'm back to normal:

```
lance@lance-dg41ty:~$ du -sh ./*
40M	./Desktop
529M	./Documents
48G	./Downloads
12K	./examples.desktop
4.0K	./Music
480M	./Pictures
4.0K	./Public
4.0K	./Templates
15M	./Videos

```

It's odd that the properties dialog showed a much smaller size though.

---

