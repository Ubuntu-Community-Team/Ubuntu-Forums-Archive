---
title: "Unsing cron to capture tv"
date: 2007-01-04
forum: General Help
---

### Post by tzulberti on 2007-01-04
Hi. I am using the following command to capture the tv:
mencoder -tv driver=v4l2:width=640:height=480:norm=pal-nc:input=2:chanlist=us-cable:channel=17 -ffourcc DIVX -fps 25 -ovc lavc -lavcopts vcodec=mpeg4:vhq -oac mp3lame -lameopts cbr:br=128 -endpos 180 -o /home/tzulberti/outfile.mpg tv://

It works perfectly... I am trying to use cron to capture the tv while i am not in home. For that, i have tried the following:,
contrab -e
0 22 4 1 * sh /home/tzulberti/script.sh
and
0 22 4 1 * All the Command Directly.

But it only saves less than a second, creating a video of 182kb

What i am doing wrong??

---

### Post by jjross on 2007-01-04
have you tried it like this
> 0 22 4 1 *  /home/tzulberti/script.sh

---

### Post by tzulberti on 2007-01-04
I have just tried it, and it happens the same thing... Nevertheless, thanks for your help.

---

