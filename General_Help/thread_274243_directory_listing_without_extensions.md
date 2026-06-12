---
title: "directory listing without extensions"
date: 2006-10-09
forum: General Help
---

### Post by evaristegalois on 2006-10-09
I want to create a file from the command line (!) that lists all the files in my directory without extensions. I know that

ls > filename

will do this with extensions. How can I get rid of the extensions? For example, the list of files

song.mp3
reading.wav
list.txt

needs to be

song
reading
list

--evaristgalois

---

### Post by ayoli on 2006-10-09
try this:
```
#!/bin/bash
for i in `ls .` 
    do echo ${i%.*} >> output.file
done
```
more useful:
```
#!/bin/bash
for i in `ls $1` 
    do echo ${i%.*} >> output.file
done
```
then call your script like that:
```
script_name /path/you/want/to/list
```

---

### Post by MikeBenza on 2006-10-09
```
ls -p | grep -v / | sed "s/\.[a-zA-Z0-9~_-]*$//"
```That will chop off the last period and alphanumerics after it, including ~, _, and -.  **It will not list direcories.**  If you want directories, use this:

```
ls | sed "s/\.[a-zA-Z~_-]*$//"
```
- Mike

---

### Post by evaristegalois on 2006-10-09
Thanks. Works. Great.

--evaristegalois

---

