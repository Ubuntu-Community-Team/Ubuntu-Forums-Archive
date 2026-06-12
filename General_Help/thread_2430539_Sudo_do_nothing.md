---
title: "Sudo do nothing"
date: 2019-11-03
forum: General Help
---

### Post by eensame on 2019-11-03
Hello, for start sorry if I make english mistake is because is not my first language and i'm still learn it. But let's go, my problem is sudo doesn't work. My space key doesn't work and I need sudo for open this command and remap my key:

           ```
" sudo -i gedit /usr/share/X11/xkb/symbols/pc "
```

But when I enter this in my terminal, he disapear and nothing appear. I even try to install something with sudo:

     ```
"sudo apt-get install xautomation"
```

But is the same problem. My terminal disapear and nothing appear. I install Ubuntu a few minutes so I don't know why this doesn't work.. I just install Visual Studio and Spotify, so it can't be something I do.. I think.. Can you help me?
[RIGHT]Thanks for your reply.
[/RIGHT]

---

### Post by eensame on 2019-11-03
So I do nothing but now it's working.. Sorry for the thread

---

### Post by Frogs Hair on 2019-11-03
Both commands work without quotes. Try the following. 

```
sudo -i gedit /usr/share/X11/xkb/symbols/pc
``` ```
sudo apt install xautomation
```

---

