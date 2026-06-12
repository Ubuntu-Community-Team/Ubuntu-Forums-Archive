---
title: "VOB converter."
date: 2006-10-09
forum: General Help
---

### Post by Roasted on 2006-10-09
I've got a VOB file I want to convert to mpg. Is there any programs out there for linux that does such a thing?

---

### Post by Iandefor on 2006-10-09
Endersshadow does Vive, which sounds like just what you're looking for. You can get it [here]("http://vive.sourceforge.net/"). The thread on the forums he uses for support for Vive can be found [here]("http://www.ubuntuforums.org/showthread.php?t=114946"), in case you run into problems.

---

### Post by Roasted on 2006-10-09
I don't really understand the instructions here... Maybe I'm just having a brain fart.

./configure
make
make install

It says read the readme, and I did. But terminal says ./configure is no such file or dir. Can anyone clarify?

---

### Post by Iandefor on 2006-10-09
Wow. I just read the instructions. I'll talk to Eric about cleaning up the documentation. In the meantime, have you at least followed this instruction?:
> 
1. If you are running Ubuntu and have not followed the guide on ubuntuforums.org ([http://ubuntuforums.org/showthread.php?t=114946)](http://ubuntuforums.org/showthread.php?t=114946)) Knowing Eric, I'm pretty sure he's talking about the section entitled "Encoding Video for the iPod Video" 

In regards to the problem with the configure script, make sure you've CD'ed into the directory where the vive source files are kept before you try running the script.

---

### Post by Roasted on 2006-10-09
I don't need gtkpod and all that from the ubuntuforum link you sent me do I? I ran the installation and at the very end I got an error with the "make" line. Oh well. Now what? I can't seem to locate it. I guess it didn't install fully?

---

### Post by Iandefor on 2006-10-09
> **Roasted said:**
> I don't need gtkpod and all that from the ubuntuforum link you sent me do I? I ran the installation and at the very end I got an error with the "make" line. Oh well. Now what? I can't seem to locate it. I guess it didn't install fully? You *shouldn't* need it. 

What was the error you got?

---

### Post by koshari on 2006-10-09
i would just use the transcode option in vlc player.

very easy,

---

### Post by Roasted on 2006-10-09
I love using VLC. What's this transcode option?

---

### Post by anaconda on 2006-10-09
I would just use ffmpeg from the terminal.

type "man ffmpeg", one of the last exaples is howto convert vob to mpg..

And ffmpeg is propably already installed

---

### Post by Roasted on 2006-10-09
I didn't notice anything towards the end that would pertain to me. But I found this towards the beginning.

ffmpeg -i myfile.avi -target vcd /tmp/vcd.mpg

So I guess I could do ffmpeg -i AmericanBadAss.vob -target vcd /tmp/AmericanBadAss/mpg

Would that work? Or am I lost...

---

### Post by koshari on 2006-10-10
> I love using VLC. What's this transcode option?

```
file>wizard>transcode
```

---

### Post by Roasted on 2006-10-10
Yeah. But, sorry if I sound like an idiot, but what do I do now? How am I supposed to select the file and adjust it to convert to the new format?

---

