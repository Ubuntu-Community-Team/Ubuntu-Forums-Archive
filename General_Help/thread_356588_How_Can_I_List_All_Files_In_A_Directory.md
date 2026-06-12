---
title: "How Can I List All Files In A Directory"
date: 2007-02-08
forum: General Help
---

### Post by Keymaster on 2007-02-08
What command can I use to make a text file that lists every file in a specific directory one after the other?

ie:
```
Song A.ogg
Song B.ogg
Song C.ogg
```

---

### Post by ~LoKe on 2007-02-08
```
echo $(ls -la) > file.txt
```
Or, to skip hidden files...
```
echo $(ls) > file.txt
```
Or to only echo .ogg files..
```
echo $(ls|grep .ogg) > file.txt
```

---

### Post by Buelldozer on 2007-02-08
What is the purpose of the echo command?

I just test on Feisty and ls *.ogg > test.txt will write the output of the ls command (with args) to the specified file.

---

### Post by ~LoKe on 2007-02-08
I just like to make things complicated and inefficient.  So, yeah, assuming "Music" is your music directory.  **-R** assumes you want it to be recursive.
```
ls -R Music|grep .ogg > music.txt
```

---

### Post by david_2001 on 2007-02-08
For just the filenames:
```
find *.ogg > files.txt
```

---

### Post by Keymaster on 2007-02-09
The find command sounds familiar.  If I used the command from a different directory would it list the directory the files are in on each line as well?  If not, how could I make it do that?

ex:

the file playlist.txt in /opt/playlist contains

```
/opt/music/song a.ogg
/opt/music/song b.ogg
/opt/music/song c.ogg
```

---

### Post by david_2001 on 2007-02-09
> **Keymaster said:**
> The find command sounds familiar.  If I used the command from a different directory would it list the directory the files are in on each line as well?  If not, how could I make it do that?

To list without directory path I would use a "-printf" expression.  Here's a real example, omitting the " > files.txt":
```
david@darkstar:~$ find /home/media/Music/Albertos\ Y\ Lost\ Trios\ Paranoias/Mandrax\ Sunset\ Variations\ CD1/*.ogg -printf "%f\n"
01 Torture You.ogg
02 Pavlov.ogg
03 I Like Girls.ogg
04 Dead Jaws.ogg
05 Follow The Guru.ogg
06 Dead Meat.ogg
07 Anadin.ogg
08 645.ogg
09 Jesus Wept.ogg
10 Mandrax Sunset Variations Pts 1 2  3.ogg
11 Old Trust.ogg
12 Brrrr.ogg
13 Ill Come If You Let Me.ogg
14 Invocation Of The Fundamental Orifice Of St Agnes.ogg
15 No Change.ogg
16 Peon In The Neck.ogg
17 Happy To Be On An Island Away From Demis Roussos.ogg
18 Teenager In Schtuck.ogg
19 Italians In Outer Space a The Ballad Of Colonel Callan b A Fistfull Of Spaghetti.ogg
david@darkstar:~$ 
```
To list with the path, omit the -printf expression.  The find manual page contains many more possibilities.

---

