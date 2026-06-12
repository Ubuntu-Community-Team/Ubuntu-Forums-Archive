---
title: "chmod erases files!!! -ripper doesn't set read bit"
date: 2006-12-27
forum: General Help
---

### Post by Mike-97470 on 2006-12-27
For some reason or another that is now ancient history, the files of my mp3 music albums don't always have the "Group" read bit set, and my music player namely a Sqeezebox can't access them.

So I thought I would run chmod -R 644:

mike@MikesPavillion:~/Desktop/Music--mp3$ chmod -R 644 /home/mike/Desktop/Music--mp3
chmod: `/home/mike/Desktop/Music--mp3': Permission denied

So I ran as sudo--
mike@MikesPavillion:~/Desktop/Music--mp3$ sudo chmod -R 644 /home/mike/Desktop/Music--mp3
Password:
mike@MikesPavillion:~/Desktop/Music--mp3$

And Presto-Change'o all of my files were gone with only a whiff of the artist names left in /Music--mp3. So I've copied a copy from my backup, but now I am clueless!  What do I do Now?

Please somebody tell me what I did wrong . . .
. . . Thanks . . . Oh, and if anyone can shed any light on why the Group Read permission isn't set consistently, it varies by album, that would be good. I own all of the CDs and used one of the usual Ubuntu rippers (I don't remember which) and then sound converter to convert to mp3. And there is only one Linux user account on my system and that's the one I use. I'm guessing now that one of the rippers doesn't set all the read bits . . .

---

### Post by taurus on 2006-12-27
Are your mp3s under ~/Desktop/Music--mp3?  Therefore, ~/Desktop/Music--mp3 need to have permissions of 744 so you can change directory to it (that's why you got the permission denied earlier).

```
cd ~/Desktop
chmod 755 Music--mp3
cd Music--mp3
chmod 644 *
```

---

### Post by Mike-97470 on 2006-12-27
Yes, /Music--mp3 contains all of my mp3 files. . .  organized in directories of artists then albums under /Music--mp3--the normal way.  I spot checked a few of them and they all are permitted as 755 including /Music-mp3.  But the files that the Squeezebox can't play are 640 and the ones it can are 644. . . which led to chmod -R 644 erasing everything!  How did that happen?

---

### Post by Mike-97470 on 2006-12-27
Ok Taurus, I ran chmod 644 * on my /Music--mp3 and oops, all the files erased.  This time the Artist folders look ok, but the Album folders have the "binary footprint" icon and there is no additional info.  I.e.: the Album folders are gone and all of the files.  Is this strange or what?

---

### Post by taurus on 2006-12-27
What's the output of this command, from a terminal?

```
ls -la ~/Desktop/Music--mp3
```

---

### Post by Mike-97470 on 2006-12-27
Thanks Taurus, for helping with this--here's the first few lines of output...consistent with what I reported earlier, ie: the Albums and .mp3 files have vanished;

mike@MikesPavillion:~$ cd /home/mike/Desktop
mike@MikesPavillion:~/Desktop$ cd Music--mp3
mike@MikesPavillion:~/Desktop/Music--mp3$ ls -la /home/mike/Desktop/Music--mp3
total 520
drwxr-xr-x 130 mike mike 4096 2006-12-26 14:24 .
drwxr-xr-x  19 mike mike 4096 2006-12-26 14:24 ..
drw-r-----   3 mike mike 4096 2006-03-18 22:14 10,000 Maniacs
drw-r-----   3 mike mike 4096 2006-03-19 05:52 Aaron Copland
drw-r-----   6 mike mike 4096 2006-12-26 14:24 Andres Segovia
drw-r-----   4 mike mike 4096 2006-03-19 13:58 Andrew Lloyd Webber
drw-r-----   3 mike mike 4096 2006-03-20 05:23 Angel Romero
drw-r-----   3 mike mike 4096 2006-03-20 05:37 Astrud Gilberto
drw-r-----   6 mike mike 4096 2006-03-20 06:42 Bach
drw-r-----   3 mike mike 4096 2006-03-20 06:43 Berlin
drw-r-----   4 mike mike 4096 2006-03-20 07:43 Billie Holiday
drw-r-----   3 mike mike 4096 2006-03-20 09:02 Billy Joel
drw-r-----   3 mike mike 4096 2006-03-20 09:12 Blondie
drw-r-----   3 mike mike 4096 2006-03-20 09:24 Bob Dylan

---

### Post by taurus on 2006-12-27
Okay, try this

```
chmod -R 755 ~/Desktop/Music--mp3
ls -la ~/Desktop/Music--mp3
```

p.s.  Andrew Lloyd Webber, huh!!!  I just watched The Phatom of the Opera (the movie) on Monday--xmas day...

---

### Post by Mike-97470 on 2006-12-27
I didn't know there was a movie (my CD is the Phantom), I'll watch for it.

Ok, here's the output--

mike@MikesPavillion:~/Desktop/Music--mp3$ chmod -R 755 ~/Desktop/Music--mp3
mike@MikesPavillion:~/Desktop/Music--mp3$ ls -la ~/Desktop/Music--mp3
total 520
drwxr-xr-x 130 mike mike 4096 2006-12-26 14:24 .
drwxr-xr-x  19 mike mike 4096 2006-12-26 14:24 ..
drwxr-xr-x   3 mike mike 4096 2006-03-18 22:14 10,000 Maniacs
drwxr-xr-x   3 mike mike 4096 2006-03-19 05:52 Aaron Copland
drwxr-xr-x   6 mike mike 4096 2006-12-26 14:24 Andres Segovia
drwxr-xr-x   4 mike mike 4096 2006-03-19 13:58 Andrew Lloyd Webber
drwxr-xr-x   3 mike mike 4096 2006-03-20 05:23 Angel Romero
drwxr-xr-x   3 mike mike 4096 2006-03-20 05:37 Astrud Gilberto
drwxr-xr-x   6 mike mike 4096 2006-03-20 06:42 Bach
drwxr-xr-x   3 mike mike 4096 2006-03-20 06:43 Berlin
drwxr-xr-x   4 mike mike 4096 2006-03-20 07:43 Billie Holiday
drwxr-xr-x   3 mike mike 4096 2006-03-20 09:02 Billy Joel
drwxr-xr-x   3 mike mike 4096 2006-03-20 09:12 Blondie
drwxr-xr-x   3 mike mike 4096 2006-03-20 09:24 Bob Dylan
.
.
.
.

---

### Post by taurus on 2006-12-27
Now you can change into those directories (Berlin and Blondie, eh)!!!

[http://www.amazon.com/Phantom-Opera-Full-Screen/dp/B0007TKNIS/sr=11-1/qid=1167247682/ref=sr_11_1/105-8432754-2994003](http://www.amazon.com/Phantom-Opera-Full-Screen/dp/B0007TKNIS/sr=11-1/qid=1167247682/ref=sr_11_1/105-8432754-2994003)

---

### Post by Mike-97470 on 2006-12-27
Well, everything is set to 755 now, but I'm still missing why I managed to erase everything doing what I thought was the same, ie: chmod -R 644 ~/Music--mp3?

Berlin and Blondie?  Hey, ya gotta be balanced.  Thanks for the Phantom DVD link, now I'm really curious.  Did Webber teach Gerald Butler to sing as well as Michael Crawford?
[http://www.amazon.com/Phantom-Opera-Original-1986-London/dp/B00004YTY2/sr=8-2/qid=1167250675/ref=pd_bbs_sr_2/104-1918376-1972766?ie=UTF8&s=music](http://www.amazon.com/Phantom-Opera-Original-1986-London/dp/B00004YTY2/sr=8-2/qid=1167250675/ref=pd_bbs_sr_2/104-1918376-1972766?ie=UTF8&s=music)

---

### Post by Adramelech on 2006-12-27
Not sure but avoid using '-' in file names cause it can confuse the commands and think they got parameters.

---

### Post by taurus on 2006-12-27
> **Mike-97470 said:**
> 
Berlin and Blondie?  Hey, ya gotta be balanced.  Thanks for the Phantom DVD link, now I'm really curious.  Did Webber teach Gerald Butler to sing as well as Michael Crawford?
[http://www.amazon.com/Phantom-Opera-Original-1986-London/dp/B00004YTY2/sr=8-2/qid=1167250675/ref=pd_bbs_sr_2/104-1918376-1972766?ie=UTF8&s=music](http://www.amazon.com/Phantom-Opera-Original-1986-London/dp/B00004YTY2/sr=8-2/qid=1167250675/ref=pd_bbs_sr_2/104-1918376-1972766?ie=UTF8&s=music)

Sorry but nobody sings like Michael Crawford!!!  (And nobody sings like Sarah Brightman, either...)

---

### Post by LenzM on 2006-12-27
If you disallow execute 'x' on a diirectory then you can't "go into" that directory.  So I don't think you really deleted the files, you just made it so that you couldn't view anything in each of the artist directories.

---

