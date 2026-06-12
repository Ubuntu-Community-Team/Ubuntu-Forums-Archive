---
title: "Gnormalize Installation"
date: 2005-07-12
forum: General Help
---

### Post by Beej on 2005-07-12
I have a lot of AAC files which I have managed to get to play on my favourite player Amarok. Amarok will recognise the files to play, but will not add them to my collection, or do any of the funky things it does with the rest of my music.

I have identified gnormalize as a program that would convert my AAC(m4a) files to mp3, but being a bit of a newbie, and the program not being in Synaptic I have been having difficulty getting the gnormalize-0.32.tar.gz to install. 

I have the file extracted on my desktop and have tried /Home/ben/Desktop/gnormalize-0.32/Install but it does not install correctly(Iwill post output later).

 I understand it has some dependancies, and I tried to install them all but I'm not sure whether they all installed correctly.

What I really could do with is some pointers as to where I may be going wrong.
Any help would be greatly appreciated. 

Congratulations to the community by the way. I've been using Ubuntu for 3 weeks and this is the first time I have found a problem that hasn't been answered by searching the forums, or on the ubuntuguide. 

Thankyou You have a convert.

---

### Post by runenes on 2005-07-12
You have to give the excact output, otherwise all we can do is guess :)

---

### Post by Beej on 2005-07-12
I'm at work at the moment, but when I get home i'll try again and post the output.

Thanks.

---

### Post by Beej on 2005-07-12
[B]ok, here we go.

On running /home/ben/Desktop/gnormalize-0.32/install, the following is displayed
[/B]
Homepage of this project:
[http://gnormalize.sourceforge.net](http://gnormalize.sourceforge.net)

This script will install gnormalize, CDDB_get, MP3::Info, Audio-CD, mppenc and mppdec in your system:

Install Audio-CD to play Audio CDs( you must have installed: libcdaudio,libcdaudio-devel, perl-devel )? Type (y/n): /home/ben/Desktop/gnormalize-0.32/install: line 43: =: command not found

Install Audio-CD:
tar: Audio-CD-0.04-changed.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
/home/ben/Desktop/gnormalize-0.32/install: line 49: cd: Audio-CD-0.04-changed: No such file or directory
Can't open perl script "Makefile.PL": No such file or directory
make: *** No targets specified and no makefile found.  Stop.

Could not install Audio-CD.


Install CDDB_get? Type (y/n):
[B]
Then after pressing Y[/B]

Install CDDB_get:
tar: CDDB_get-2.25.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
/home/ben/Desktop/gnormalize-0.32/install: line 69: cd: CDDB_get-2.25: No such file or directory
Can't open perl script "Makefile.PL": No such file or directory
make: *** No targets specified and no makefile found.  Stop.

Could not install CDDB_get.


Install MP3::Info? Type (y/n):

**After pressing Y**

IInstall MP3::Info:
tar: MP3-Info-1.13.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
/home/ben/Desktop/gnormalize-0.32/install: line 89: cd: MP3-Info-1.13: No such file or directory
Can't open perl script "Makefile.PL": No such file or directory
make: *** No targets specified and no makefile found.  Stop.

Could not install MP3::Info.


Install gnormalize, mppenc and mppdec? Type (y/n):
[B]
After pressing Y[/B]

Install MPC encoder and decoder:
cp: cannot stat `mpc/mppdec': No such file or directory
cp: cannot stat `mpc/mppenc': No such file or directory

Install gnormalize:
cp: cannot stat `gnormalize': No such file or directory
cp: cannot stat `gnormalize.png': No such file or directory
root@Home:/home/ben #

The files it refers to as "No such file or directory" are in the same folder as the install shell script, as downloaded from the website.

Hope you can help

Beej.

---

### Post by runenes on 2005-07-13
**cd** to the directory of the install file. 
```

$ cd /home/ben/Desktop/gnormalize-0.32/
$ ./install

```

---

### Post by Beej on 2005-07-13
Thanks, all worked fine and I am currently converting my AAC to mp3.

---

