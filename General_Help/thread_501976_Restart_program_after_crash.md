---
title: "Restart program after crash"
date: 2007-07-16
forum: General Help
---

### Post by brent113 on 2007-07-16
I'm using avant window navigator, and it tends to close a lot, I'd assume it's crashing on something.

Is there a script or something I can do to automatically restart it when it closes?  I don't know anything about linux scripting, but I was thinking maybe something polling for it's process every 10 seconds or something, and if it's not found starting it.

Is there a better way to do this and/or could that be translated into a script?

---

### Post by mouseboyx on 2007-07-16
```

kill $(pgrep programtorestart)
killall -v programtorestart
pkill programtorestart
kill `ps -ef | grep programtorestart | grep -v grep | awk '{print $2}'`
programtorestart
```

---

### Post by brent113 on 2007-07-16
That gives syntax errors along with otherwise not working.  Thanks for the try, but i'm not sure how I should use that.

I forgot to mention I was hoping for it to be continulously restarted as long as the computer is on, not just once.

---

### Post by mouseboyx on 2007-07-26
make a shell script and copy/pate it to the bin directory

then you can launch it like a comand if you name it restart<nameofprogram>

and you can make a launcher for it a pannel

```
sudo killall <name of program>
<name of program>
```

---

### Post by tszanon on 2007-07-26
> **mouseboyx said:**
> make a shell script and copy/pate it to the bin directory

then you can launch it like a comand if you name it restart<nameofprogram>

and you can make a launcher for it a pannel

```
sudo killall <name of program>
<name of program>
```
The problems about it are:
1. It would require the user to re-enter the password when sudo times out;
2. It does not rerun the application automatically.

To solve (1), I think it should be:
```
killall <program name>
su <username> <program name>
```
This script should be run as root (gksu <script name>). It would ask for the password only once, and would run the program as if the user were doing it (no root access).

To solve (2), the script should be modified to have an infinite loop. Unfortunately, I don't remember how to do that. But, then, it would be necessary to kill the script before closing the program.

---

