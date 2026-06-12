---
title: "Bash shell - Can I bg a process and silence its output"
date: 2013-01-18
forum: General Help
---

### Post by CaptainMark on 2013-01-18
As the title says if I run a command that has a lot of output, say for example apt-get update, if I use 'ctrl+z' to stop the job and 'bg' to continue it in the background the output continues to flood the screen, is there a way to let the command continue to run but to silence the output or direct it somewhere else.

Here is the reason I ask (incase you use a different method):
Sometimes if I run a command that takes a long time and then I realise I have to leave or go out I will 'ctrl+z' the job and 'bg' to background it, then I'll use ```
pidof apt-get;
1234
wait 1234; 
apt-get upgrade;
shutdown -P now
``` to have the computer run any other commands I want and then shutdown. The problem lies in that if the initial command has lots of output it becomes really hard to type the next commands and the shutdown signal. I tried using the wait command from another shell but it seems the pid has to be a child of the current shell for that to work.  Also this example is obviously quite a trivial thing to fuss over, please bear in mind it is just the first example that popped into my head but in practice it could be used for more important tasks which I don't want to interrupt.

Many thanks if you have suggestions
Mark

---

### Post by LewisTM on 2013-01-18
You can redirect an output to the digital black hole known as /dev/null and fork the process in the background, all on the same line:
```
apt-get update > /dev/null &
```
Cheers!

---

### Post by CharlesA on 2013-01-18
> **LewisTM said:**
> You can redirect an output to the digital black hole known as /dev/null and fork the process in the background, all on the same line:
```
apt-get update > /dev/null &
```
Cheers!

This works.

Any errors will be shown on the screen. ;)

---

### Post by CaptainMark on 2013-01-19
Yes I already knew that, thanks but that's not my question. I'm asking if it can be done after the first command has already been started, so for arguments sake if I already started my apt-get update but then had to leave and didn't wan't to interrupt it. 

Regards

---

### Post by CharlesA on 2013-01-19
Yes.

Screen is your friend too.

---

### Post by CaptainMark on 2013-01-19
Sorry, yes it can be done?
Can you give details?

---

### Post by CharlesA on 2013-01-19
Just ctrl+z then bg jobnumber

Or use screen. It's easier than messing with sending stuff to the background.

---

### Post by jerome1232 on 2013-01-19
I'd like to put a little plug for byobu, it's basically a nice profile for screen with "easier" (at least for me) to remember keyboard shortcuts.

In case you aren't aware, screen is a nifty little program that allows you to "window" your terminals.

---

### Post by efflandt on 2013-01-19
Web search "linux screen" to see how to use **screen** (you likely need to install it).  But I have not used it enough to know if you can stuff an already running process into a screen session.

If you are in a virtual text console (like tty1), simply switch to a different one to do something else.  There are 6 of them by default, Alt+F1 through F6.  Note that from X they would be Ctrl+Alt+F1 through F6, and Alt+F7 would take you back to X.

Of course if using an xterm or ssh you can simply open another one.

PS: I see a lot of people using apt-get **upgrade** when **dist-upgrade** would do a more intelligent upgrade including resolving dependencies.  Read the about the difference in **man apt-get**

---

### Post by steeldriver on 2013-01-19
It seems like a lot of people are having a hard time understanding what you are asking

The answer appears to be [FONT=Courier New]stty tostop[/FONT] - from the bash mnapage:

```
Background processes are those whose process group ID
differs from the terminal's; such processes are immune to keyboard-gen&#8208;
erated signals.  Only foreground processes are allowed to read from or,
[COLOR=Red]if the user so specifies with  stty  tostop[/COLOR],  write  to  the  terminal.

```This seems to work for me

```
$ ping 192.168.1.102
PING 192.168.1.102 (192.168.1.102) 56(84) bytes of data.
64 bytes from 192.168.1.102: icmp_req=1 ttl=64 time=0.860 ms
64 bytes from 192.168.1.102: icmp_req=2 ttl=64 time=0.863 ms
^Z
[1]+  Stopped                 ping 192.168.1.102
$ 
$ stty tostop
$ bg 1
[1]+ ping 192.168.1.102 &
$ 

[1]+  Stopped                 ping 192.168.1.102
$ fg 1
ping 192.168.1.102
64 bytes from 192.168.1.102: icmp_req=3 ttl=64 time=0.962 ms
64 bytes from 192.168.1.102: icmp_req=4 ttl=64 time=0.843 ms
64 bytes from 192.168.1.102: icmp_req=5 ttl=64 time=0.847 ms
^C
--- 192.168.1.102 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 25474ms
rtt min/avg/max/mdev = 0.843/0.875/0.962/0.044 ms

```If you want this behavior to be the default, you can probably put the stty tostop command in your profile

---

### Post by CaptainMark on 2013-01-19
> **CharlesA said:**
> Just ctrl+z then bg jobnumber

Have you read my original post? This doesn't answer it, I think your not understanding what I'm asking

I know how to background a job, what I'm asking is: After stopping a job can I background it or resume it and silence the output so I don't get any feedback from the running job to the current terminal.

I'm looking for a method that uses no special preparation beforehand, as in this theoretical situation I did not know I would need to shut down when I ran the original command

---

### Post by CaptainMark on 2013-01-19
> **steeldriver said:**
> It seems like a lot of people are having a hard time understanding what you are asking

The answer appears to be [FONT=Courier New] stty tostop[/FONT]

Absolutely perfect dude, this is just what I needed

EDIT: Hold the celebrations, this also stops the job from running in the background but it will remain stopped and never finish

---

### Post by steeldriver on 2013-01-19
You're welcome, I have to admit I didn't know about that but it seemed like it *should* be possible - so I went digging

---

