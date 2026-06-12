---
title: "Terminal Log Recording"
date: 2019-01-31
forum: General Help
---

### Post by Redalien0304 on 2019-01-31
Is there Log Specific for Terminal Last Commands & Output? Mostly for the Output?
Or way to Record what the Terminal Command & out is?
Do not not really want a Recording App like Screenshot Video, more like Record To a txt file?

---

### Post by again? on 2019-01-31
You can append commands with tee.
eg 
```
sudo apt update |& tee -a term.txt
```
  
There is also the command "script" to record terminal.
eg
To start recording (use the --append option if you do not want to overwrite the log)
```
script ~/.terminal.log
```
Then use terminal as usual.
To stop recording type "exit" or close terminal.

To view...
```
cat ~/.terminal.log
```

Example...
```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] script ~/.terminal.log**
Script started, file is /home/glen/.terminal.log
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] ls**
Audio  Desktop    git             MEGAsync      operatransfers     Projects    scripts  Templates
bin    Documents  gPodder         Music         package-lock.json  Public      Sounds   term.txt
conky  Downloads  http_server.js  node_modules  Pictures           Recordings  Steam    Videos
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] exit**
exit
Script done, file is /home/glen/.terminal.log

**[COLOR="#006400"]glen@Bionic:~$[/COLOR] cat ~/.terminal.log**
Script started on 2019-02-01 01:38:05+0800
glen@Bionic:~$ ls
Audio  Desktop    git             MEGAsync      operatransfers     Projects    scripts  Templates
bin    Documents  gPodder         Music         package-lock.json  Public      Sounds   term.txt
conky  Downloads  http_server.js  node_modules  Pictures           Recordings  Steam    Videos
glen@Bionic:~$ exit
exit

Script done on 2019-02-01 01:38:16+0800
```

---

### Post by Redalien0304 on 2019-01-31
Ok Cool Thanks. I noticed in the output of [COLOR=#000000][FONT=&quot]script ~/.terminal.log produces [/FONT][/COLOR] this in the log like Boxes?

---

### Post by again? on 2019-01-31
From the script manual page....
> script places everything in the log file, including linefeeds and backspaces. This is not what the naive user expects.

Needs to be viewed in terminal using cat.
If you wanted a readable text file you could....
```
cat ~/.terminal.log > term.txt
```

Can I ask why/what you want to record.
I may have another method.

---

### Post by Redalien0304 on 2019-02-01
Mostly to Record from the terminal. I recently Installed Catfish File Search form Tar Source & was giving me Errors so Wanted to Record the Errors.
I ended up Copy/Paste to txt file. Thought there would be easier way automatically log Everything from that terminal session.

Here is the Link from the Catfish Install with Errors if you like to look?
[https://ubuntuforums.org/showthread.php?t=2411497&p=13834612#post13834612](https://ubuntuforums.org/showthread.php?t=2411497&p=13834612#post13834612)

---

### Post by Redalien0304 on 2019-02-01
Just Tried Using [COLOR=#000000][FONT=&amp]script ~/.terminal.log & exit & now cannot find [/FONT][/COLOR][COLOR=#000000][FONT=&amp].terminal.log. used [/FONT][/COLOR][COLOR=#000000][FONT=&amp]cat ~/.terminal.log > term.txt
could not find in my home Dir.
Found it Weird was not there earlier, even did file search for it?
K Found it, had to select search hidden files?[/FONT][/COLOR]

---

