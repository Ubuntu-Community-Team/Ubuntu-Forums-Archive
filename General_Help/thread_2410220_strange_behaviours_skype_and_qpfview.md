---
title: "strange behaviours skype and qpfview"
date: 2019-01-12
forum: General Help
---

### Post by monkeybrain20122 on 2019-01-12
There was a skypeforlinux update a few months ago, since then I often have to reboot for skype to find audio and video devices  (no no such problem with cheese and guvciewer so camera works) especially but not always just after waking up from suspension (restarting camera doesn't work for skype but works for cheese and guvcviewer so it is a skype problem, on this laptop camera has to be restarted manually after suspension, but it is not my issue on this thread )

I don't use skype often so I didn't bother looking into it. I just reboot as needed. 

But it is bothering me lately so I am trying to find a solution, but instead I observed something quite strange. 

I have installed qpdfview the tabbed pdf reader with many (>100) tabs open. It turns out that skype is only having problem finding camera and audio device when qpdfview is running with all the tabs. If I then close qpdfview and restart skype it finds the camera again, if quit skype, start qpdfview and then start skype it again complains can't find devices, but if start skype first and then start qpdfview camera continues to work. Also skype can find the audio and video devices if qpdfview is running with only 5-6 tabs.  I tried this a dozen of times and and can reproduce it 100%.

So it seems that loading too many tabs in qpdfview somehow prevents skype from finding the camera and audio devices. I am not trying to troubleshoot skype since it is close source and a workaround in my case is simple enough, just close qpdfview first. But I am curious, any theory? Maybe has something to do with inode number limit? 

Thanks.

---

### Post by monkeybrain20122 on 2019-01-13
Ok figured it out. Edit /etc/sysctl.conf, increase fs.inotify.max_user_instances from 256 to 2048 and reboot fixes it. Now Skype always finds audio and video devices. (As well it fixes the problem of spotify client not opening after a while. The error message of this first alerted me about inotify or inode..)

---

