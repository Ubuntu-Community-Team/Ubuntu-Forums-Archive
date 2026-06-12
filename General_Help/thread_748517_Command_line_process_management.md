---
title: "Command line process management"
date: 2008-04-07
forum: General Help
---

### Post by Ariod on 2008-04-07
Hello,

I have a server I'd like to run rtorrent from occasionally. Is it somehow possible to log in to that server via SSH, start a download in rtorrent, then log out, log in after a few hours and see the status of the download?

The way I did it was start rtorrent to run in the background, log out, log in, but then I can't bring it back to foreground in order to see the status of the download. Is there any way around this?

---

### Post by SOULRiDER on 2008-04-07
I do that, leave rtorrent at home and log in from work. What I do is run screen at home and rtorrent there. When im at work I just ssh into my computer and do
```
screen -d -r
``` that allows me to go on using the screen session i left at home.

So basically:
At home run:
```
screen
rtorrent
```
And then once youve SSHed into your computer do:
```
screen -d -r
```

---

### Post by Ariod on 2008-04-08
Wow! Exactly what I was looking for! Thanks a ton!

---

