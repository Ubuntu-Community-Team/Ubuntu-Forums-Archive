---
title: "clamscan show progress on 1 line in console"
date: 2014-08-11
forum: General Help
---

### Post by tubos2 on 2014-08-11
**Goal:** Show one line of output when running clamscan virusscan in console

Example live output:  Files scanned OK: 512 Files Infected : 3 File Errors : 3

**Question: **Any ideas on how to write a script to do that?

---

### Post by nerdtron on 2014-08-11
What command do you use to run clamscan and what is it's usual output?

---

### Post by tubos2 on 2014-08-11
```

sudo clamscan -r --bell --max-filesize=750M /mnt/seagate2tb/

```

Right now it gives out a line per checked file (see below) , it also has an option to suppress output
or only show infected files , none of which i really want.
```

./backupfs.sh.rsync: OK
./snow.py: OK
./backupfs.sh: OK
./clonedata.sh.old:  Joke.Snowman FOUND
./inf.sh: OK
./docsrotate.sh: OK
./clonedata.sh: OK
./vscan.sh: OK
./snow.sh: OK

```

---

### Post by nerdtron on 2014-08-11
You can extend your command by using pipe and grep to filter the output, but I don't see where you can get the lines "Files scanned OK: 512" and "Files Infected : 3" because these words don't appear on the output. You can't just create a script that will show these values if you don't have data to begin with.

---

### Post by SeijiSensei on 2014-08-11
> **tubos2 said:**
> ```

sudo clamscan -r --bell --max-filesize=750M /mnt/seagate2tb/

```

Pipe that command through grep like this:
```

sudo clamscan -r --bell --max-filesize=750M /mnt/seagate2tb/ | grep 'Files scanned'

```

I don't recall if the output is sent to "stdout," the usual output to the screen, or to "stderr" which handles errors and such.  If the latter, rewrite the command like this:
```

sudo clamscan -r --bell --max-filesize=750M /mnt/seagate2tb/ 2>&1 | grep 'Files scanned'

```
The "2>&1" parameter redirects stderr, represented as stream "2," to stream one, stdout.

---

### Post by tubos2 on 2014-08-11
If the line contains OK could it increase a counter and display it ?
if the line contains FOUND increase another counter and display it?

---

### Post by nerdtron on 2014-08-11
We can count the number lines with the word OK and FOUND and then store them on variables. Then use the echo command to the final output line

```
#!/bin/bash
#run the scanner and save the results to output.txt file
sudo clamscan -r --bell --max-filesize=750M /mnt/seagate2tb/ > output.txt

#count the lines that contains 'OK'
OK_COUNT=`grep 'OK' output.txt | wc -l`

#count the lines that contain 'FOUND'
FOUND_COUNT=`grep 'FOUND' output.txt |wc -l`

#now display them on a single line output
echo "The number of OK: $OK_COUNT The number of FOUND: $FOUND_COUNT"
```

---

### Post by tubos2 on 2014-08-11
Is it possible to do that live when it is running?

---

### Post by nerdtron on 2014-08-11
The script will wait for the scanning to be finished before showing the final output.

---

### Post by tubos2 on 2014-08-11
Yes i understand but my original question was if it could be done when it is running
in the console.
Clamscan has an option already to print the stats after it has finished scanning.

---

### Post by nerdtron on 2014-08-11
I find it hard to think on how to show the counting of OK and FOUND while the scan is running.
That's the best I can do. Maybe others have another solution?

---

### Post by steeldriver on 2014-08-11
maybe something like

```

*your command* | awk -F: '$2 ~ /OK/ {ok++} $2 ~ /FOUND/ {inf++} {printf "Files scanned OK: %d Files infected: %d\r", ok, inf}'

```

---

### Post by tubos2 on 2014-08-12
Pretty amazing , it really works thank you steeldriver.
It is not a continuous update sometimes it jumps 50 or more
but still is very useful to me.

---

### Post by steeldriver on 2014-08-12
Hmm... you could try playing with the buffering to see if that stops the 'jumps' e.g.

```

**stdbuf -oL** your command | awk -F: '$2 ~ /OK/ {ok++} $2 ~ /FOUND/ {inf++} {printf "Files scanned OK: %d Files infected: %d\r", ok, inf}'

```

---

### Post by tubos2 on 2014-08-12
I tried the stdbuf , made no change

---

