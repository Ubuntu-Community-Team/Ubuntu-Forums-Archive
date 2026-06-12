---
title: "Open Broadcaster Software trouble"
date: 2015-05-06
forum: General Help
---

### Post by devdlp on 2015-05-06
I just downloaded and install OBS on my computer but cant find it and dont know how to start it from the terminal how do i do this?

---

### Post by QDR06VV9 on 2015-05-06
Not sure witch method you used to install?
But see here [http://www.cupoflinux.com/SBB/index.php?topic=1604.0](http://www.cupoflinux.com/SBB/index.php?topic=1604.0)

---

### Post by devdlp on 2015-05-06
deven@deven-Satellite-L455:~/Desktop$ sudo apt-add-repository ppa:jon-severinsson/ffmpeg
Cannot add PPA: 'ppa:jon-severinsson/ffmpeg'.
Please check that the PPA name or format is correct.
deven@deven-Satellite-L455:~/Desktop$ sudo apt-add-repository ppa:btbn/obs-studio
Cannot add PPA: 'ppa:btbn/obs-studio'.
Please check that the PPA name or format is correct.
deven@deven-Satellite-L455:~/Desktop$

---

### Post by howefield on 2015-05-06
Have you looked at the OBS website ?

[https://obsproject.com/download#linux](https://obsproject.com/download#linux)

---

### Post by devdlp on 2015-05-06
yes, im even asking someone in their forums and hes saying thats odd it should just show up in the dash but it isnt

---

### Post by QDR06VV9 on 2015-05-06
Try this.
```
If you do not have FFmpeg installed (if you're not sure, then you  probably don't have it), you can get it with the following commands: 								

								sudo add-apt-repository ppa:kirillshkrogalev/ffmpeg-next
								sudo apt-get update && sudo apt-get install ffmpeg 								

								**14.04+**: You can install OBS with the following commands: 								

								sudo add-apt-repository ppa:obsproject/obs-studio
								sudo apt-get update && sudo apt-get install obs-studio
```
Crap howefield already posted that link:D
Sorry howefield I should have looked at that first!
Regards

---

### Post by devdlp on 2015-05-06
omfg i feel like the biggest dumbo! I installed the ffmpeg but not the actual obs. Thank you so much.

---

### Post by QDR06VV9 on 2015-05-06
Got it done though success!
I know I have my share of brain segfaults! LOL
Good Job.
Regards

---

### Post by devdlp on 2015-05-06
Im sorry i thought we were done here but now it crashes when i start it.

---

### Post by QDR06VV9 on 2015-05-06
This from the site howefield posted.
> [COLOR=#ff0000]Alpha release. Not all features have been implemented and stability is not guaranteed.[/COLOR]
Should become better with time and patience.(Maturity) Sorry Its not going so good for you.

---

### Post by devdlp on 2015-05-07
Is that why everytime i try to start OBS 0.9.1 it automacially crashes and shows a splash report.

The title of the splash report is: OBS CRASHED WITH SIGABRT in_libc_message()

ill leave the splash report open in case you need it

---

### Post by QDR06VV9 on 2015-05-07
Not trying to brush you off by any means but perhaps you would be more likely to get the help you need from their support forums.
I do not think it has anything to do with Ubuntu.
Just had a peek on their site, and there were a lot of crash or segfaults  on various platforms, ie windows, linux, 64 bit 32 bit.
howefield removed your splash report probably due to info in that report that could of been a security risk(to you) or spammers.
here is the link encase you don't have it [https://obsproject.com/forum/list/bug-reports.6/](https://obsproject.com/forum/list/bug-reports.6/)
Best Regards

---

### Post by devdlp on 2015-05-08
thnx

---

