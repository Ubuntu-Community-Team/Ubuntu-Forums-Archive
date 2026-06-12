---
title: "wine audio tab problem"
date: 2006-10-22
forum: General Help
---

### Post by pay on 2006-10-22
Whenever I select the audio tab I get this error
```
daniel@daniel-desktop:~$ winecfg
*** glibc detected *** winecfg.exe: free(): invalid pointer: 0x7c2d30a8 ***

```It's got some backtrace information so if you need that as well just ask.

I've read on this forum about people with the same problem and "sudo modprobe snd-seq" seemed to be the magic answer but that didn't work for me. Chessmaster 8000 says ```
daniel@daniel-desktop:/opt/chessmaster$ wine Chessmaster.exe 
err:wave:DSDB_MapBuffer Could not map sound device for direct access (Input/output error)
err:wave:DSDB_MapBuffer Please run winecfg, open "Audio" page and set
"Hardware Acceleration" to "Emulation".

```which is why I want to get to that audio tab so badly
Thanks for reading.

---

### Post by Ales~ on 2006-10-22
I have the same problem, I did "sudo modprobe snd-seq" and the message about snd-seq dissappeared, but still crashes. In the Terminal can be read:
```

Creating link /home/ales/.kde/socket-ales-desktop.
can't create mcop directory

```

I'm with Ubuntu 6.10.

---

### Post by pay on 2006-10-22
Try ```
mkdir /home/ales/.kde/socket-ales-desktop.
```

---

### Post by pay on 2006-10-22
Okay, I renamed the file "/usr/lib/wine/winearts.drv.so"and now it's working.

---

### Post by joshgtv6 on 2006-10-22
> **pay said:**
> Okay, I renamed the file "/usr/lib/wine/winearts.drv.so"and now it's working.

you have any ideas for this error.  I haven't been able to get an answer yet.  


I get this error when clicking the audio tab.  

ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
Creating link /home/jpeifley/.kde/socket-jpeifley-desktop.
can't create mcop directory
jpeifley@jpeifley-desktop:~$

EDIT: ok, i did the sudo modprobe snd-seq   
now i'm getting 

Creating link /home/jpeifley/.kde/socket-jpeifley-desktop.
can't create mcop directory
jpeifley@jpeifley-desktop:~$

---

### Post by pay on 2006-10-22
Try creating the directory that it's having trouble with ```
mkdir -pv $HOME/.kde/socket-$HOSTNAME
```

---

### Post by joshgtv6 on 2006-10-22
> **pay said:**
> Try creating the directory that it's having trouble with ```
mkdir -pv $HOME/.kde/socket-$HOSTNAME
```

ok, i can access the audio tab now but i get a few warning dialogue boxes about not having selected an audio driver and this is what appears in the terminal window

fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack


Also, i read elsewhere about renaming the winearts.drv.so file to winearts1.drv.so    

You heard anything about that?

Also, if creating that directory appears to cause more issues how would i go about deleting it.  i see that mkdir is the make directory command, what is the delete directory command?

Sorry for all the questions, but i figured if i can kill a few birds with one stone why not.

---

### Post by pay on 2006-10-22
> **joshgtv6 said:**
> ok, i can access the audio tab now but i get a few warning dialogue boxes about not having selected an audio driver and this is what appears in the terminal window

fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
You need the jack library, I forget what it's called in Ubuntu but you can select a different audio type like Alsa or Oss. Both should work
> **joshgtv6 said:**
> Also, i read elsewhere about renaming the winearts.drv.so file to winearts1.drv.so

You heard anything about that?
No
> **joshgtv6 said:**
> Also, if creating that directory appears to cause more issues how would i go about deleting it. i see that mkdir is the make directory command, what is the delete directory command?
to remove files it's```
rm file
```to remove directories it's ```
rm -r directory/
```

---

### Post by joshgtv6 on 2006-10-23
thanks, the error message isn't coming up anymore so that's a good thing.

---

### Post by markba on 2007-01-10
Problem is known under:
[https://bugs.launchpad.net/ubuntu/+source/wine/+bug/42169](https://bugs.launchpad.net/ubuntu/+source/wine/+bug/42169)

Apart from the so renaming, no other solutions or workaround.

---

