---
title: "Shutdown only using keyboard (w/o terinal)"
date: 2008-06-21
forum: General Help
---

### Post by patrickaupperle on 2008-06-21
Is it possible?

---

### Post by cmnorton on 2008-06-21
Does "w/o terinal " = w/o terminal = without being at an x-term (command line)?

You could probably map the shutdown command to either the shutdown command or a shell script that issued the shutdown command to a combination of keystrokes. However, root has to issue a shutdown command.

---

### Post by issih on 2008-06-21
Default would be to hit ctrl+alt+delete, which will bring up the logout dialog as if you clicked the quit applet button.

You can then choose what you want to do with either the arrow keys and enter, or hit the alt key and the keyboard accelerator as indicated by the underlined letter.

If you want something more immediate, you could bind:

"sudo shutdown -h now"

to a keyboard shortcut in your window manager, but as said above that needs your password to run so you'll need to modify your sudoers file to allow that command to run without a password.

Hope that helps

---

### Post by geo909 on 2008-06-21
Maybe ```
sudo shutdown -hP now
```
The sudoers true is true if you want to use that on a script or something

---

### Post by babylon2233 on 2008-06-21
You don't even need a keyboard. Unplug your PC.Done

---

### Post by christhemonkey on 2008-06-21
Type:
```
<Alt>+<SysRq>+o
```

---

### Post by patrickaupperle on 2008-06-21
> **issih said:**
> <snip>

If you want something more immediate, you could bind:

"sudo shutdown -h now"

to a keyboard shortcut in your window manager, but as said above that needs your password to run so you'll need to modify your sudoers file to allow that command to run without a password.

Hope that helps

Could you explain exactly how to do this?

For now, ctrl+alt+delete then alt+s works.

---

### Post by issih on 2008-06-22
This page covers a lot about sudo:

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch09_:_Linux_Users_and_Sudo](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch09_:_Linux_Users_and_Sudo)

Be warned that messing with it and getting it wrong could leave your system in a very big mess....

as for binding to a command it depends on the window manager you are using...compiz, metacity, kwin?

they will all do it slightly differently

---

### Post by patrickaupperle on 2008-06-22
> **issih said:**
> This page covers a lot about sudo:

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch09_:_Linux_Users_and_Sudo](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch09_:_Linux_Users_and_Sudo)

Be warned that messing with it and getting it wrong could leave your system in a very big mess....

as for binding to a command it depends on the window manager you are using...compiz, metacity, kwin?

they will all do it slightly differently

Thank you for the link. I am using compiz.
Edit: Sorry, but I don't see how to modify the sudo thing correctly. I  would like some help also because I don't mess this up.

---

### Post by issih on 2008-06-23
Perhaps unsurprisingly I don't really want to feel responsible for totally borking your box either :) I've never actually done any editing of the sudo file myself as I haven't felt the need. I just know it's possible. starting a new thread asking specifically for someone to show you what to do may find someone more confident that their advice is correct.

Anyway, I'll cover the binding a command to a shortcut in compiz...

open ccsm , then go to the general plugin, and open the commands tab.

Now expand the commands section (click the little arrow) and enter the command you want into an empty box, and remember the command line number.

You then expand the key bindings section and set a key binding for the corresponding run command X.

Hope you follow that

---

### Post by DJ_Barney on 2008-06-23
See 

HOWTO : Create a custom keyboard shortcut

[http://ubuntuforums.org/showthread.php?t=79560](http://ubuntuforums.org/showthread.php?t=79560)

Another way.

---

### Post by dracayr on 2008-06-23
Alt+SysRq+R+E+I+S+U+O

those don't have to be pressed at the same time, but only seconds apart...


dracayr

---

### Post by tgrimley on 2008-06-23
Here's a "gnu"monic:

[http://en.wikipedia.org/wiki/Magic_SysRq_key#Raising_Elephants](http://en.wikipedia.org/wiki/Magic_SysRq_key#Raising_Elephants)

---

### Post by beckols on 2008-06-23
I think it's alt+SysRq+R+E+I+S+U+O

Where you hold alt and sysrq and then type the letters about a second apart

---

### Post by dracayr on 2008-06-23
> **beckols said:**
> I think it's alt+SysRq+R+E+I+S+U+B

Where you hold alt and sysrq and then type the letters about a second apart

that's to reboot, use O instead of B for shutting down the system..


dracayr

---

### Post by beckols on 2008-06-23
just changed it before you said that ;-)

---

### Post by dracayr on 2008-06-23
> **beckols said:**
> just changed it before you said that ;-)

unfair:mad:

---

### Post by issih on 2008-06-23
Whilst I know that kernel commands can be used for shutdown (and many other things) I'm not convinced its really a good idea to recommend them without warnings, mistyping could cause a lot of nasty side effects after all. Where there is a safer alternative, surely we should recommend that, if someone really is going to use kernel shortcuts, I feel they should have been using linux for a long time and come across them by learning, that way they'll have some idea of the power of what they are doing.

Not really trying to criticise you guys, just feel that recommending these things should come hand in hand with a big "DANGER WILL ROBINSON" style warning.

---

### Post by patrickaupperle on 2008-06-23
> **dracayr said:**
> Alt+SysRq+R+E+I+S+U+O

those don't have to be pressed at the same time, but only seconds apart...


dracayr

It did nothing for me. What was the last post saying about kernel commands?

---

### Post by beckols on 2008-06-23
did you hold alt and SysRq the whole time, then type each letter separately AND in order

---

### Post by molotov00 on 2008-06-23
> **babylon2233 said:**
> You don't even need a keyboard. Unplug your PC.Done
My first thought.

---

### Post by patrickaupperle on 2008-06-25
> **beckols said:**
> did you hold alt and SysRq the whole time, then type each letter separately AND in order

Yes. Still did nothing. Oh well.

---

### Post by christhemonkey on 2008-06-26
Could you post the result of this command?
```
cat /proc/sys/kernel/sysrq 
```

If the result is 1, then the key combos with SysRq in them should work.

(if the result is "permission denied" or similar, then try adding the word sudo on the front of the command)

---

### Post by patrickaupperle on 2008-06-26
```
patrick@patrick-laptop:~$ cat proc/sys/kernel/sysrq
cat: proc/sys/kernel/sysrq: No such file or directory
patrick@patrick-laptop:~$ sudo cat proc/sys/kernel/sysrq
[sudo] password for patrick: 
cat: proc/sys/kernel/sysrq: No such file or directory
patrick@patrick-laptop:~$ 


```

Is what I get

---

### Post by raul_ on 2008-06-26
you fotgot the first /

---

