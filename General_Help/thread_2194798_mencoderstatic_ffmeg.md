---
title: "mencoder/static ffmeg"
date: 2013-12-20
forum: General Help
---

### Post by mcgill.carpenter on 2013-12-20
Is there a way to use mencoder to make a mkv a mpg? I also have static ffmpeg but can't remember how to use it. I'm running 11.04 without internet. So right now I'm using mencoder to make a mkv an avi then making it mpg. Just want to cut out the extra step.

---

### Post by ajgreeny on 2013-12-20
Use avconv now instead of ffmpeg (unless you have compiled your own ffmpeg or have the static version) with command ```
avconv -i file.mkv -vcodec mpeg2video -q 5  -ab 128k file.mpg
```

If using static ffmpeg you need to run command from the folder where the ffmpeg is sitting ```
./ffmpeg -i file.mkv -vcodec mpeg2video -sameq -ab 128k outfile.mpg
``` Don't forget the ./ before ffmpeg at the start or the static version will not run.

---

### Post by mcgill.carpenter on 2013-12-20
Will the second command work if I replace that mp4 with mkv?

---

### Post by ajgreeny on 2013-12-20
> **mcgill.carpenter said:**
> Will the second command work if I replace that mp4 with mkv?

Yes, it should.  Sorry about that typo; I've edited and corrected it now.  I quickly copied that command from one I used a few days ago but forgot to edit it to fit your question.

---

### Post by mcgill.carpenter on 2013-12-20
Hmm. It says in red. Option 'sameq' was removed. If you are looking for an option to preserve the quality  (which is not what -sameq was for), use -qscale 0 or an  equivalent quality factor option.
Failed to set value '1' for option 'sameq' : Invalid argument
Error parsing global options: Invalid argument

I've no idea what this means. Unless I'm just suppose to replace it with -qscale 0.

---

### Post by FakeOutdoorsman on 2013-12-21
> **mcgill.carpenter said:**
> Is there a way to use mencoder to make a mkv a mpg? I also have static ffmpeg but can't remember how to use it. I'm running 11.04 without internet. So right now I'm using mencoder to make a mkv an avi then making it mpg. Just want to cut out the extra step.

```
./ffmpeg -i input.mkv -codec:v mpeg2video -codec:a mp2 -qscale:v 2 -b:a 192k -ac 2 output.mpg
```

"-qscale:v 2" should suffice for this encoder. Anything lower may cause many "buffer underflow" messages in the console output. "-qscale:v 2" may show the messages as well, but you can probably ignore them.

> **ajgreeny said:**
> If using static ffmpeg you need to run command from the folder where the ffmpeg is sitting ```
./ffmpeg -i file.mkv -vcodec mpeg2video -sameq -ab 128k outfile.mpg
``` Don't forget the ./ before ffmpeg at the start or the static version will not run.

Again, [-sameq does not mean "same quality"](http://superuser.com/a/478550/110524) and has been removed from ffmpeg (you must have missed my previous response to your -sameq recommendation). This option should not be used in 99% of cases.

---

