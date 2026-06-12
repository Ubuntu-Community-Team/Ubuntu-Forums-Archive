---
title: "Youtube-dl reinstall completely disfunctional"
date: 2022-04-30
forum: General Help
---

### Post by sofasurfer on 2022-04-30
I have been using yt-dl for some time now and what a blessing it has been. However, I recently glitched my system and did a  OS reinstall. I have had a few issues since but have been working through them. I have now reinstalled yt-dl and it is giving errors. Most recently I got ```
 /usr/bin/env: ‘python’: No such file or directory
```

I have done complete removal in synaptic abd then reinstalled with synaptic, pip, command line and I keep getting errors. I originally installed it on one try. What am I doing wrong?

---

### Post by CharlesA on 2022-04-30
This might be helpful:
[https://askubuntu.com/questions/1037666/youtube-dl-python-not-found-18-04](https://askubuntu.com/questions/1037666/youtube-dl-python-not-found-18-04)

---

### Post by sofasurfer on 2022-04-30
Thank you. I read that link and this is the part that helped...so far
```
 

On Ubuntu 18.04.2 LTS with youtube-dl version 2019.06.08, after creating symbolic link with following command:

$ sudo ln -s /usr/bin/python3 /usr/local/bin/python

youtube-dl worked as usual, the error "/usr/bin/env: &#8216;python&#8217;: No such file or directory" vanished.

```

---

### Post by csae2608 on 2022-05-01
normally i install youtube-dl via curl as it is newer than the version from repository most the times

[http://ytdl-org.github.io/youtube-dl/download.html](http://ytdl-org.github.io/youtube-dl/download.html)

---

### Post by vanadium on 2022-05-03
Ubuntu comes with a small package "python-is-python3" that sets up such symlink. So prefer to set up that link with the command
"sudo apt install python-is-python3". Not sure why it is not set up like that by default. The former "python-is-python2" package is obsolete now.

---

