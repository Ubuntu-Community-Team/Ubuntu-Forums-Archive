---
title: "SCP, Cron Jobs And Variable Filenames"
date: 2014-09-02
forum: General Help
---

### Post by Maheriano on 2014-09-02
Hi, I have a cron job which runs nightly at midnight. It dumps a MySQL database to a file with the date as the filename and then attempts to transfer it to a remote server via SCP. My problem is I don't know the filename since it's the date. How do I specify this in the SCP command for the cron job?

Here is my cron job:

```
#!/bin/bash

echo "Dumping production database..."
mysqldump -u admin -p******** --databases production > production-$(date +%y%m%d).sql

scp -p -P 2201 [filename-here] deemar@***********:/home/deemar/Desktop/.

rm [filename-here-also]
```

---

### Post by andrew102 on 2014-09-02
NOW=$(date +"%Y-%m-%d.%H-%M-%S")
FILE="production-$NOW.sql"
touch $FILE

---

### Post by Maheriano on 2014-09-02
Great, I'll try that tonight.
Another question: how do I save only X copies of the database dump? Like say I want the last 10 days worth so the script will delete the 10th oldest file and save a new copy. I don't want this to run nightly and fill up my hard drive with backups I don't need.

---

### Post by sotiris2 on 2014-09-02
```
number=$( ls -l | wc -l)  #get number of files in directory
if (( "$number" > "10" )) #check if more than 10 
then
	old=$(ls -t | tail -n 1) #list by modification time (newest first) and get the last line which is the oldest modified line
	echo "removing $old" #message if wanted
	rm "$old" #remove the old #actual removal
fi
```

Try this. If you have more than 10 files in directory it will remove the oldest. Note that if you have 13 it will still only remove one. Didn't make it more complicated since you 'll probably have it running after each backup

---

### Post by Maheriano on 2014-09-02
Thank you very much!
I guess if I only want a couple of versions I could also do this:

- cp file2 to file3
- cp file1 to file2
- save new dump as file1

And that will give me the last 3.

---

### Post by sotiris2 on 2014-09-02
You confused me if you want to keep only 3 files change the second line of my script to this 
```
if (( "$number" > "3" )) #check if more than 3
```
or change the 3s to 2s if you need 2 versions. Remember this script should run after each backup and if there are more than whatever you put in this line it will delete ONE file. If you already have more than you want you should first get them under that limit manually and then have that script run after each backup.

---

### Post by Maheriano on 2014-09-02
> **sotiris2 said:**
> You confused me if you want to keep only 3 files change the second line of my script to this 
```
if (( "$number" > "3" )) #check if more than 3
```
or change the 3s to 2s if you need 2 versions. Remember this script should run after each backup and if there are more than whatever you put in this line it will delete ONE file. If you already have more than you want you should first get them under that limit manually and then have that script run after each backup.

Oh yes I know I can change the number of files in your script but I'm saying an alternative would be to do it the way I posted as well. If you only want a small number of files to keep. I like your way better though, thanks for that.

---

### Post by Vaphell on 2014-09-03
> ```
number=$( ls -l | wc -l)
old=$(ls -t | tail -n 1)
```

very lame. *ls* is NEVER a good idea in scripts.

if you want to count files you should use something like this

```
number=$( find -type f -printf 'x' | wc -c )
```

also if you want to get rid of stuff older than X you could just use *find *with appropriate criteria
```
find -iname '*.sql' -type f -mtime +10
``` should return .sql files older than 10 days.
if you combine it with -delete flag or -exec rm {} you are golden

```
find -iname '*.sql' -type f -mtime +10 -delete
find -iname '*.sql' -type f -mtime +10 -exec rm {} \;

```

---

### Post by SeijiSensei on 2014-09-04
I posted a script to do MySQL backups here:  [http://ubuntuforums.org/showthread.php?t=2195496&p=12882235&viewfull=1#post12882235](http://ubuntuforums.org/showthread.php?t=2195496&p=12882235&viewfull=1#post12882235)

It has some of the features you're looking for like rotations. Maybe it will give you some ideas.

---

### Post by sotiris2 on 2014-09-05
A bit off-topic can Vaphell point me to a somewhat detailed explanation of what could go wrong with ls? I don't doubt it is a bad idea if you say so but I would like to also understand it.

---

### Post by Vaphell on 2014-09-05
linux filesystems accept everything except / (path separator) and null char \0. Some chars are unprintable and ls is unable to represent them (because it is used to print to the screen), destroying original names. Using ls output is like taking a picture of original text and then running it through OCR to restore the text. It doesn't make sense to depend on passing data through a potentially destructive tool if you can use a non-destructive workflow. Also newlines introduce unsolvable ambiguosity.

just for kicks: create a dir and run this in it:
```
touch a.txt $'b\nc.txt'
```
now try to loop over files and count them using *ls* based hack. I will be very surprised if you get number other than 3.

[http://mywiki.wooledge.org/ParsingLs](http://mywiki.wooledge.org/ParsingLs)

it all boils down to having a dirty hack that can fail in your toolset, but not having actual dependable, true solutions and perpetuating the use of dirty hack.

---

### Post by sotiris2 on 2014-09-05
Thanks now understand better.

---

