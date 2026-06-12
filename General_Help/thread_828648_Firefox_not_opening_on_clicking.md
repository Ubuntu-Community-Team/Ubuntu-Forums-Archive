---
title: "Firefox not opening on clicking"
date: 2008-06-13
forum: General Help
---

### Post by f4k1r on 2008-06-13
My firefox is'nt opening on clicking it.I try to start it from terminal still it doesnt open.Its working when i do sudo firefox in terminal.I dont understand what the problem is please help me out.:confused:
Ubuntu 8.04 hard:)y firefox 3 Beta 5.

---

### Post by AndThenWhat on 2008-06-13
what does it say in the terminal when you run it without sudo?

---

### Post by tamoneya on 2008-06-13
what does it say when you attempt to run firefox from terminal without sude.  Is there any output.  Also what are the permissions in /etc/firefox-3.0.  Check them by running the following command:```
ls -la /etc/firefox-3.0
```

---

### Post by f4k1r on 2008-06-14
> **tamoneya said:**
> what does it say when you attempt to run firefox from terminal without sude.  Is there any output.  Also what are the permissions in /etc/firefox-3.0.  Check them by running the following command:```
ls -la /etc/firefox-3.0
```
seems to be like the root is the owner
hummer@rishav:~/Videos$ ls -la /etc/firefox-3.0
total 24
drwxr-xr-x   4 root root  4096 2008-04-22 23:23 .
drwxr-xr-x 126 root root 12288 2008-06-14 09:34 ..
drwxr-xr-x   2 root root  4096 2008-04-22 23:32 pref
drwxr-xr-x   3 root root  4096 2008-04-22 23:32 profile
It doesnt give show anything when i do without sudo.

---

### Post by aysiu on 2008-06-14
Never run Firefox with the command *sudo firefox*

Never.

If you use the Firefox from the Mozilla website (instead of from the Ubuntu repositories), it's sometimes (for the purposes of installing updates) okay to run ```
gksudo firefox
```

Sounds as if you might have some permission problems. Type this command in the terminal: ```
sudo chown -R *username*:*username* /home/*username*/.mozilla
``` were *username* is your actual username. Then try to run the command ```
firefox &
```

---

### Post by f4k1r on 2008-06-14
Thanks a lot tamoneya,aysiu its working fine now:)
I dont understand how the permissions were changed,I installed it just a few days backs and i had the problem right from the first boot.anyway working fine now.

---

### Post by aysiu on 2008-06-14
The permissions changed because you ran *sudo firefox*. Read this for more details: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by zdarova on 2011-04-16
> **aysiu said:**
> Never run Firefox with the command *sudo firefox*

Never.

If you use the Firefox from the Mozilla website (instead of from the Ubuntu repositories), it's sometimes (for the purposes of installing updates) okay to run ```
gksudo firefox
```

Sounds as if you might have some permission problems. Type this command in the terminal: ```
sudo chown -R *username*:*username* /home/*username*/.mozilla
``` were *username* is your actual username. Then try to run the command ```
firefox &
```


it worked for me! 

thanks

---

