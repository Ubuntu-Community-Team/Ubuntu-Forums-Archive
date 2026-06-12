---
title: "&quot;shutdown&quot; doesn't shut down, restarts"
date: 2013-04-12
forum: General Help
---

### Post by scy on 2013-04-12
Hello ubuntu forums! First I just want to say thanks for all of the awesome help you have provided for other people because it has really helped me!

I am a newb to Lubuntu and these forums so sorry if I am difficult to help out :)

I have been having a problem with my installation of Lubuntu 12.10. I am using an IBM NetVista 8307.

So far I have tried reinstalling Lubuntu twice, but I have had the same issue:
When I click the Shutdown button at the Logout Screen, The computer shows the Lubuntu logo and the blue and white dots, then it restarts, instead of shutting down. My BIOS is set to "stay off on power failure", if that helps.

However, I am comfortable and familiar with general UNIX and the command line, so if you want me to run stuff on the command line that's fine.

So really I am just trying for it to actually shut down. It's kind of a pain to hold down the power button instead.

Thanks everyone!

---

### Post by Rex Bouwense on 2013-04-12
What happens when you try to shut down from the lxterminal?
```
halt
```
Does it shut down or does it kick out errors?

---

### Post by scy on 2013-04-12
Well,
```
halt
```
returned
```
halt: must be root
```
so i did
```
sudo halt
```
which just brings it up to a screen with "lubuntu" and the 5 dots (they are all white).

No errors or anything from halt besides "The system is going down NOW!"

---

### Post by Rex Bouwense on 2013-04-12
Well, does it shut down or reboot?

---

### Post by scy on 2013-04-12
It didn't do either. It just hung and hung at the lubuntu and 5 white dots screen.

---

### Post by scy on 2013-04-13
So how do i fix it???

---

### Post by Rex Bouwense on 2013-04-13
OK.
1.  When you downloaded the Lubuntu ISO, did you check the MD5Sum?  This will determine if you got a good download. 
2.  When you burned the ISO to the CD did you burn it at the lowest possible speed?  Higher speeds occasionally screw up the burn.
3.  Since you have already installed twice, I suspect that one of those (1 or 2) is responsible.  Using the power button to try to shutdown the computer never is a good idea and should be avoided whenever possible.

I found this discussion concerning shutdown of Ubuntu 10.04.
[http://ubuntuforums.org/showthread.php?t=1466589](http://ubuntuforums.org/showthread.php?t=1466589)  
There are perhaps half a dozen solutions offered that some people said solved their problem.  Perhaps one of them will work for you.

---

### Post by angry_johnnie on 2013-04-13
try 
```
sudo halt -p
```
instead of just "sudo halt"
or maybe 
```
sudo poweroff
```
or maybe plain old
```
sudo shutdown -h now
```
good luck!

---

### Post by scy on 2013-04-13
When I burned the cd it was at 2x (lowest possible) and i did run "Check disc for errors" at the install, and it was fine.

On a side note when I just press the power button as it is logging in it restarts instead of turning off. Is that a problem??

Also, I've tried all of the commands:

sudo init 0
sudo shutdown (and with flags)
sudo halt

And it just won't shut down.

---

### Post by scy on 2013-04-13
And Rex, none of those solutions worked. Thanks though.

---

### Post by scy on 2013-04-13
angry_johnnie,

None of those worked. But thanks for the help.

---

### Post by scy on 2013-04-15
bump

---

### Post by gifford on 2013-04-15
Check the file /etc/default/halt. It should be set to Halt=poweroff. You could add INIT_HALT = POWEROFF to see if it helps.

---

