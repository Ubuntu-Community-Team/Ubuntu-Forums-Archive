---
title: "The character '&amp;' in shell command argument"
date: 2007-09-29
forum: General Help
---

### Post by yinglcs2 on 2007-09-29
I am using ubuntu 7.0.4 and i get different result when I try these 2 commands in the shell:

This works:

vlc  -vvv -I dummy [http://sjl-casing1.sjl.youtube.com/get_video?video_id=XaXz-dryqLg](http://sjl-casing1.sjl.youtube.com/get_video?video_id=XaXz-dryqLg) --sout '#transcode{vcodec=mp4v,vb=400,acodec=mpga,ab=128}'

But as soon as I have '&' in my url, like this:
 ./vlc  -vvv -I dummy  [http://74.125.11.27/get_video?video_id=H_FCifobqWU&origin=ash-v88.ash.youtube.com](http://74.125.11.27/get_video?video_id=H_FCifobqWU&origin=ash-v88.ash.youtube.com) --sout '#transcode{vcodec=mp4v,vb=400,acodec=mpga,ab=128}'

I get an error:

command-not-found: error: no such option: --sout
bash: --sout: command not found


Can you please tell me why?

---

### Post by Wolki on 2007-09-29
& is a special character in the shell, it means "take everything up to here and execute it in the background", then it sees -sout as the next command instead of an option to vlc.

Similar things apply to ! by the way, which does something with the history (don't know what exactly though)

In order to prevent the shell from interpreting such characters, you will need to escape them. Often, putting the argument into quotes will suffice ("" or '', your choice). Alternatively, you can also put a backslash in front of them (i.e. "\&" or "\!"), which should always work.

---

### Post by yinglcs2 on 2007-09-29
Thank you!

---

