---
title: "avconv + x11grab capturing question"
date: 2013-02-06
forum: General Help
---

### Post by sr_guy on 2013-02-06
Hi folks, 

-Running Ubuntu 12.10 x64

My wife and daughter are oversees visiting my wife's family, so we have been skyping alsmost every night. I want to capture the video chat session, so I have been using the following code to capture video of my desktop screen:

avconv -f alsa -i pulse -f x11grab -r 30 -s 1400x1050 -i :0.0 -vcodec libx264 -preset ultrafast -threads 4 -y skype_`date +%d%b%Y-%T`.mp4

The only problem I have is sound. In realtime I can hear them fine, but anything on her mic side in the captured video is hardly audible. Is there a way to fix this?

---

### Post by sr_guy on 2013-02-07
Anyone have any ideas?

---

