---
title: "How do I make a Video CD"
date: 2006-12-08
forum: General Help
---

### Post by Coop on 2006-12-08
Hello everyone.:D 
I have a video file in mp4 format of about 3 mb.
I want to make a Video CD from it.
How do I do this?
I will be highly obliged for your help.

Regards Coop

---

### Post by der_joachim on 2006-12-09
Hmmm... You'll need ffmpeg. Make sure that all your repos are enabled and do an ```
sudo apitude install ffmpeg
```

ffmpeg is a command line tool, which has a huge load of options. You will have to read the documentation for the package. Your command will be something like ```
ffmpeg -i myfile.mpeg4 -target ntsc-vcd myvcd.mpg
``` if you use the ntsc standard.

---

### Post by kaamos on 2006-12-09
You should try the program devede - it can create dvd, svcd, vcd and so on.. Available in the repositories.

---

### Post by DWright on 2006-12-09
Agreed: DeVeDe is the easiest way to make video clips into VCD, SVCD or (video) DVDs.

---

### Post by Coop on 2006-12-13
Hello.
I tried devede and I chose to create a vcd,and it created .bin,.cue,.xml and .mpg files,and when I play the .mpg file it doesn't play properly which means it isn't converted properly.
Please tell me what to do.I will be highly obliged for your help.
Regards Coop:D

---

