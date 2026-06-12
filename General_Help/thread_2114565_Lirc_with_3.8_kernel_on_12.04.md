---
title: "Lirc with 3.8 kernel on 12.04"
date: 2013-02-10
forum: General Help
---

### Post by Axio on 2013-02-10
Hi,

I want to test 3.8 kernel to confirm or not this bug with the latest kernel: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1094904](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1094904)

I installed the latest 3.8 kernel from raring. Unfortunately I am facing a problem: the remote isn't working anymore. Thus I can't extensively test and I can't confirm or not the bug (the machine is used daily, I need a working remote).

The problem with lirc: at boot the remote doesn't work (I don't change my lirc configuration), when I try to restart lirc (/etc/init.d/lirc restart) it hangs forever and I can't kill the process).

The system runs fine with kernel 3.5 (even 3.7 iirc), I don't have to change my lirc configuration. It just works.

Can anyone confirm that installing 3.8 on 12.04 doesn't break lirc? Any clues?

---

### Post by pqwoerituytrueiwoq on 2013-02-10
i suggest trying the raring daily iso 
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)
[http://cdimage.ubuntu.com/xubuntu/daily-live/current/](http://cdimage.ubuntu.com/xubuntu/daily-live/current/)
[http://cdimage.ubuntu.com/lubuntu/daily-live/current/](http://cdimage.ubuntu.com/lubuntu/daily-live/current/)
[http://cdimage.ubuntu.com/kubuntu/daily-live/current/](http://cdimage.ubuntu.com/kubuntu/daily-live/current/)

---

### Post by Axio on 2013-02-10
Unfortunately it is not an option either. I need the machine to work everyday.

---

### Post by pqwoerituytrueiwoq on 2013-02-10
as a live cd test, not a full install

---

### Post by Axio on 2013-02-10
Good thinking, I will try the live cd to check if my remote works with it. So I will know if 3.8 breaks support for my remote or not. But in any case, I won't be able to confirm the bug or not from the livecd (the bug can happen 48 hours later and I can't stay on the live cd that long).

---

### Post by Axio on 2013-02-10
I have quickly tested. After an apt-get install lirc and some tests I managed to reproduce the bug on a live cd by using my actual configuration on the live cd. Basically I have copied lircrc. It probably has to do with it. On my actual config I have two lricrc (one in /etc/lirc/lircrc, the other in my /home/.lircrc). I have copied them both. When I will have some more time, I will try to test with just one (yes I should have tried that from the start).

---

### Post by Axio on 2013-02-13
I have tested it again. It seems that irexec is broken with kernel 3.8. When I copy my lircrc file on the live cd and that I restart lirc I get the bug. The one thing I haven't tested is the lircrc configs, maybe mine is weird.

How to reproduce:
(1) Start 13.04 live cd
(2) sudo apt-get install lirc
(3) sudo nano /etc/lirc/lircrc
(4) copy your config, here is mine:
```
begin
#blabla
remote = devinput
button = KEY_POWER
prog = irexec
repeat = 0
config = python /home/script.py
end
```

Could someone try to reproduce it?

---

### Post by Axio on 2013-02-13
I have opened a bug for that: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1124581](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1124581)

---

