---
title: "RSYNC Script/One liner"
date: 2013-03-02
forum: General Help
---

### Post by kg87 on 2013-03-02
Hi guys, hoping someone can help. 

The current command I'm using is

```
screen rsync -avh --exclude-from=/home/root/rsync-exclude --progress /media/MUSIC/ /media/MyBook/Music/rsync/ | egrep -E '/$' | sed 's/\/$//g'

```

which will list only directories that are due to transfer and output them on a detachable screen.

What i'd like to do is get the output of the rsync to display normally (eg show the percentage done on the file realtime) but append the directories created back to the rsync-exclude file. I think there'll be a 'tee' in there somewhere but im not sure on how to incorporate this. something like?

```
screen rsync -avh --exclude-from=/home/root/rsync-exclude --progress /media/MUSIC/ /media/MyBook/Music/rsync/ |  tee "'egrep -E '/$' | sed 's/\/$//g' | cat >> rsync-exclude" | ??? 
```

so that would produce

[table="width: 500"]
[tr]
	[td]screen[/td]
	[td]rsync-exclude[/td]
[/tr]
[tr]
	[td]foo/[/td]
	[td]foo[/td]
[/tr]
[tr]
	[td]foo/foo-bar.mp3[/td]
	[td]bar[/td]
[/tr]
[tr]
	[td]bar/[/td]
	[td][/td]
[/tr]
[tr]
	[td]bar/bar-foo.mp3  96% 130kB/s 0:00:00[/td]
	[td][/td]
[/tr]
[/table]


as always, thanks in advance

---

### Post by kg87 on 2013-03-04
bump - anyone?!

---

### Post by kg87 on 2013-03-04
found my own solution

```
 rsync -avh --exclude-from=/rsync-exclude --progress /dira/MUSIC/ /dirb/Music/ |  tee **>( **egrep -E '/$' | sed 's/\/$//g' | cat >> rsync-exclude **)** 
```

All i was missing was the ">" and the brackets :D

---

### Post by schragge on 2013-03-04
> **kg87 said:**
> ```
rsync -avh --exclude-from=/rsync-exclude --progress /dira/MUSIC/ /dirb/Music/ |  tee **>( **egrep -E '/$' | sed 's/\/$//g' | cat >> rsync-exclude **)**
```It probably could be further simplified like this
```
rsync -avh --exclude-from=/rsync-exclude --progress /dira/MUSIC/ /dirb/Music/ | [COLOR=red]tee >(sed -n 's:/$::p' >>rsync-exclude)[/COLOR]
```
or even like this
```
rsync -avh --exclude-from=/rsync-exclude --progress /dira/MUSIC/ /dirb/Music/ | [COLOR=red]sed 's:/$::w/dev/stderr' 2>>rsync-exclude)[/COLOR]
```

---

### Post by kg87 on 2013-03-05
Awesome, thanks for that ... the /dev/stderr looks interesting.

---

