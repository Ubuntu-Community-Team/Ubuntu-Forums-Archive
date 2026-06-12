---
title: "rsnapshot, backup size grew quickly"
date: 2019-01-05
forum: General Help
---

### Post by bradhaack on 2019-01-05
My rsnapshot backup has been growing very slowly, then quickly almost doubled in size.    How can I figure out what is taking so much space?  I didn't add a large amount of data, but I'm thinking somehow a bunch of directories got 'touched', and the time stamp changed or something like that.    I've cleaned up some things manually, but its really slow going.  
rsnapshot diff show this,   Note daily.8 and weekly.0
```
35G	/media/Maxtor/Backup/hourly.0/
37M	/media/Maxtor/Backup/hourly.1/
37M	/media/Maxtor/Backup/hourly.2/
101M	/media/Maxtor/Backup/hourly.3/
100M	/media/Maxtor/Backup/hourly.4/
103M	/media/Maxtor/Backup/hourly.5/
101M	/media/Maxtor/Backup/hourly.6/
101M	/media/Maxtor/Backup/hourly.7/
102M	/media/Maxtor/Backup/hourly.8/
100M	/media/Maxtor/Backup/hourly.9/
100M	/media/Maxtor/Backup/hourly.10/
100M	/media/Maxtor/Backup/hourly.11/
155M	/media/Maxtor/Backup/daily.0/
163M	/media/Maxtor/Backup/daily.1/
199M	/media/Maxtor/Backup/daily.2/
43M	/media/Maxtor/Backup/daily.3/
206M	/media/Maxtor/Backup/daily.4/
275M	/media/Maxtor/Backup/daily.5/
13M	/media/Maxtor/Backup/daily.6/
74M	/media/Maxtor/Backup/daily.7/
12G	/media/Maxtor/Backup/daily.8/
33G	/media/Maxtor/Backup/weekly.0/
161M	/media/Maxtor/Backup/weekly.1/
211M	/media/Maxtor/Backup/weekly.2/
230M	/media/Maxtor/Backup/weekly.3/
762M	/media/Maxtor/Backup/monthly.0/
83G	total
```

---

### Post by clementc on 2019-01-05
Hi [**[COLOR=#000000]bradhaack[/COLOR]**]("https://ubuntuforums.org/member.php?u=746386"),

Hopefully, one of these two commands will help you find out what changed and caused this increase in size:

rsnapshot-diff -v /media/Maxtor/Backup/daily.7 /media/Maxtor/Backup/daily.8

rsync -aHin /media/Maxtor/Backup/daily.8 /media/Maxtor/Backup/daily.7 2>&1 | grep -v '^\.d'

---

### Post by bradhaack on 2019-01-05
thx, that's very helpful

---

