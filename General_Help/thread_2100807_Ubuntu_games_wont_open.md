---
title: "Ubuntu games wont open"
date: 2013-01-02
forum: General Help
---

### Post by PhotonPunk on 2013-01-02
I've just installed 64bit Ubuntu 12.04 on a Thinkpad W500 laptop. I've spent the last week tweaking it and so far I love it, but for some reason I can't get the games "Nexuiz" or "Alien-Arena" to open. 

I downloaded them from the Software Center. When I try to run them using the launcher, nothing happens. When I look at the file that the launcher is pointing to, it's a shell script. I don't know if this is common, but other games I downloaded were all executable applications. I've tried running them from terminal too, but no luck.

Anybody know how to fix this, or what I'm doing wrong?

---

### Post by mad2-814 on 2013-01-02
Post what comes up when you try to run the games in the terminal.  Or try to make the shell scripts executable by using..```
sudo chmod +x <filename>
```

---

### Post by PhotonPunk on 2013-01-02
> **mad2-814 said:**
> Post what comes up when you try to run the games in the terminal.  Or try to make the shell scripts executable by using..```
sudo chmod +x <filename>
```

I got "no such file or directory". 

So I tried again from ```
cd /usr
``` because the launcher is linking to usr/games. Same result. 

So I tried it from /games/alien-arena. Same result.

So I tried it without the Sudo and got ```
chmod: changing permissions of `games/alien-arena': Operation not permitted
```

---

### Post by mad2-814 on 2013-01-03
Try 
```
cd /usr
```
then
```
sudo chmod +x ./games/alienarena
```

and if that doesn't work, try to use
```
sudo -s
```
then try the steps again.

---

### Post by PhotonPunk on 2013-01-03
Nothing happened. No message or anything.

---

### Post by mad2-814 on 2013-01-03
After those steps try to execute them again.

---

### Post by mad2-814 on 2013-01-03
```
./<filename>.sh
```

---

### Post by PhotonPunk on 2013-01-03
None of the above seems to have fixed the problem, games still wont open.

---

### Post by mad2-814 on 2013-01-16
Find where the shell script is, cd to that location, and try to execute it from the terminal.  Something will have to come up as an error or it will run.  Do that then post the output back on here.

---

