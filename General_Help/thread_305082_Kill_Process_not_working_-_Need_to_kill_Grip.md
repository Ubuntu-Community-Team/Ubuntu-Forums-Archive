---
title: "Kill Process not working - Need to kill Grip"
date: 2006-11-22
forum: General Help
---

### Post by drezha on 2006-11-22
Earlier, an instance of grip froze on me so I clicked close and the force quit app closed it.

I went to re open it again and it didn't open. So I looked in system monitor and there was now two instances of grip in it. Tried to open again and now 3. Right clicking and issuing kill didn't work nor did end.

All 3 appear as uninterruptable.

I've tried ```
killall grip
``` and kill with the PID's but they still remain. I've tried restarting X with Ctrl Alt Backspace because I know that closes some programs tat are open but no joy.

I want to get into grip again but cant until these 3 processes are closed.:-k  Any help? I don't really want to restart the PC if I don't have to.:(

---

### Post by finferflu on 2006-11-22
Try with this:

```
killall -9 grip
```

---

### Post by drezha on 2006-11-22
No joy :(

---

### Post by finferflu on 2006-11-22
mmmh, try this then:

```
sudo killall -9 grip
```

Ah, and by the way, are you sure the app is called grip?

If it still doesn't work, the only solution I know is rebooting...

---

### Post by ~LoKe on 2006-11-22
Type "top" in the terminal to see if grip is the actual process name.  Also, I've noticed I sometimes have to terminate python to get a python based application to end.

---

### Post by drezha on 2006-11-22
Shows up as grip in system monitor.

I didn't want to restart. This is linux after all and thought there'd be a way to sort it without rebooting.

Sudo didn't work either. Looks like a restart. I'll head to bed and see what's happened when I wake up if anything.

---

### Post by drezha on 2006-11-22
Sorry for the double post, but it appears it's either causing or linked to the fact my CD tray wont open.

I assume that the CD won't unmount and eject because grip is still using it. If this is the case then it looks worse than before and I may well have to reboot :(

---

### Post by creaturex on 2006-11-23
...rebooting isn't a death sentence or anything. Even the best of computers need a little reboot every once in a while. I've seen that happen before with  reading video files from a cd, and the easiest thing to do is reboot. (Also the only thing I've bothered to try after sending kill signals)

---

### Post by reclusivemonkey on 2006-11-23
> **drezha said:**
> 
I've tried ```
killall grip
``` and kill with the PID's but they still remain. I've tried restarting X with Ctrl Alt Backspace because I know that closes some programs tat are open but no joy.


Use top to find out whether grip is a zombie process. You can't kill a zombie process; as we all know you can't kill something that is already dead!!!

---

### Post by Qew on 2006-11-23
I'm sure, but I might be wrong, that the kill command, unlike killall, only takes the PID of a process and not its name. So, you'll have to find the PID of the process before you can give the kill command to kill it. Do what's below.

ps aux | grep -i grip

(The PID is the first number you get on the left (after the process's owner.)

kill -9 PID

(If the PID is 5222, then you'll do "kill -9 5222" {no quotes}.)

---

### Post by checho4 on 2007-09-20
Then how DO you get rid of a zombie process?  And how do you use top?  I try to run it in Kubuntu 7.04, but nothing happens.

---

### Post by reclusivemonkey on 2007-09-20
> **checho4 said:**
> Then how DO you get rid of a zombie process?

Reboot

> **checho4 said:**
>  And how do you use top?  I try to run it in Kubuntu 7.04, but nothing happens.

Its a CLI application; are you running it from a terminal? If so, and you don't get anything,

```

sudo aptitude install top

```

---

### Post by checho4 on 2007-09-20
I have a zombie called amarokapp, and I've tried rebooting, but it still shows up.

---

### Post by reclusivemonkey on 2007-09-20
> **checho4 said:**
> I have a zombie called amarokapp, and I've tried rebooting, but it still shows up.

It must be getting started everytime you boot up. Its mostly something to do with Amarok judging by the name. Do you have Amarok set to start on every boot?

---

### Post by strabes on 2007-09-20
Just so you know, CD ejecting issues are non-existant in gutsy. It's pretty stable now (less than a month before its actual release.) You should try upgrading using ```
sudo upgrade-manager -c
``` I can't remember if the flag is -c or -d. Try both.

---

### Post by checho4 on 2007-09-20
ReclusiveMonkey, no I don't have it to startup, but amarokapp is still there.  In fact, everytime I try to open Amarok, two processes come up: amarok and amarokapp.  I can kill amarok, but not amarokapp.  What's more, the actual program doesn't OPEN, it only appears in the process table.


Ok, if it's any help, I just found what MAY BE The problem. I have another ext3 partition with all of my music, that is accessed through both Windows XP and Kubuntu. However, when I try to navigate to that partition, Konqueror freezes on me.

---

### Post by checho4 on 2007-09-22
Well, I got Amarok to open now. I had to go in through Windows and delete the trash folders. However, I still can't access my music partition through Linux.

---

### Post by hendoc on 2007-09-22
I put an xkill shortcut on my toolbar. It hasn't failed me yet.

---

