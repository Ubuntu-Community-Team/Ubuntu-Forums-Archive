---
title: "Bash error"
date: 2007-07-27
forum: General Help
---

### Post by Scooter7 on 2007-07-27
Hi, I ran this code:

```
sudo su
rm /bin/sh
ln -s /bin/sh /bin/bash
```

In a terminal.   I thought it would help me with running a .sh script, but it didn't - I got the code from here:

[http://www.kde-apps.org/content/show.php?content=11577&forumpage=16&PHPSESSID=6339b83f769ebd7394aaa208555b650b](http://www.kde-apps.org/content/show.php?content=11577&forumpage=16&PHPSESSID=6339b83f769ebd7394aaa208555b650b)

> Well actually you just have to link /bin/sh to /bin/bash.

sudo su
rm /bin/sh
ln -s /bin/sh /bin/bash

Now I get this error when starting the terminal:

> bash: /usr/bin/lesspipe: /bin/sh: bad interpreter: no such file or directory

If I type 'su', or 'sudo su', I get the above error as well as:

> bash: /usr/bin/groups: /bin/sh: bad interpreter: No such file or directory

Not only that, but Thunderbird was installed to '/usr/bin/', and I wouldn't be surprised if most of my other programs were, too.   I can't launch Thunderbird anymore.

I obviously messed up bad by deleting /bin/sh... is there a way to undo this?

---

### Post by Scooter7 on 2007-07-27
*bump*

i was thinking, and perhaps I could use someone else's sh file (from /bin/)?

An attached zip would be good.

Thanks,

---

### Post by jyba on 2007-07-28
That 'ln' command looks wrong to me. I bet if you type...
```
ls -l /bin/sh
```
...it'll say something like...
```
lrwxrwxrwx 1 root root       4 2007-04-26 13:50 sh -> bin/bash
```
...when it should say...
```
lrwxrwxrwx 1 root root       4 2007-04-26 13:50 sh -> bash
```

Try this...
```
cd /bin
sudo su
rm sh
ln -s bash sh
```

---

### Post by nick_h on 2007-07-28
The arguments are reversed.  Type:

```
sudo rm /bin/sh
sudo ln -s /bin/bash /bin/sh
```

The original was just a link.  To revert to the original type:

```
sudo rm /bin/sh
sudo ln -s /bin/dash /bin/sh
```

---

### Post by Scooter7 on 2007-07-29
Thanks guys,

...but now I can't boot.  I shut my computer down, and when I went to boot up into Ubuntu, after the initial boot screen, I was given the same error as before, and from there, I can only shut my computer off.   So as it stands, I can't access the terminal.

Unless I can do it via my liveCD...

---

### Post by dagnabit dang doohickey on 2007-07-29
"sudo su" is redundant.

Either:
```
sudo ls -s bash /bin/sh
```
or
```
su -
ls -s bash /bin/sh
exit
```

---

### Post by Scooter7 on 2007-07-29
Well, I didn't have to try any of your suggestions, but thanks for them anyway. ;)

What I did do was simply boot up on my liveCD and copy the sh file from there.    I had thought of this originally, but I was at a friend's at the time and had left my liveCD at home.

Thanks again,

---

