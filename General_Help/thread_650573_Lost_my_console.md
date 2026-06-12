---
title: "Lost my console"
date: 2007-12-26
forum: General Help
---

### Post by jschneider on 2007-12-26
Hi,

I have lost my console. That means, X starts up as expected, but Ctrl-Alt-F1/F... shows only a black screen with a blinking cursor but *no* Login prompt.

I did not find any entries within /var/log/messages or dmesg that helped me to solve the problem.

So could anybody give me a hint what could be wrong/where I can search for more detailed informations about the problem?


Thanks.

---

### Post by markharding557 on 2007-12-26
try booting up in recovery mode.
do this by pressing esc as ubuntu starts to boot,you should see the grub screen with two options on it.
it should boot into command line mode

---

### Post by kellemes on 2007-12-26
> **jschneider said:**
> Hi,

I have lost my console. That means, X starts up as expected, but Ctrl-Alt-F1/F... shows only a black screen with a blinking cursor but *no* Login prompt.

I did not find any entries within /var/log/messages or dmesg that helped me to solve the problem.

So could anybody give me a hint what could be wrong/where I can search for more detailed informations about the problem?


Thanks.

You actually mean no login prompt? Or no prompt at all? You only see the cursor?

---

### Post by jschneider on 2007-12-26
The X-Server starts fine. No problem with that. Just the console windows show *nothing*. Just a blinking cursor (no text or anything else).
This is the same on each console. Just Ctrl-Alt-F7 shows the X-Server.

Maybe the run level is not completed (one of the services is stalled). Do you know a way to find this out?

---

### Post by markharding557 on 2007-12-26
if you want to get back to the log in screen the command is ctrl-alt-backspace
when you say console do you mean terminal or gdm log in screen

---

### Post by jschneider on 2007-12-26
Okay, I try to explain it more detailed:

The X-Server/GDM works as expected (as it always has been). 

When I press Ctrl-Alt-F1/F2/F3 it used to show a login prompt where I could get a console. 
Today I recognized that this is no longer the case. The screen is completely black - only the cursor is blinking.

So I think I have screwed up my system (don't know how) and ask for advice how I can find out what went wrong.

---

### Post by p_quarles on 2007-12-26
Yeah, that's a pretty strange problem. I'd suggest trying to change the tty using a different method:
```
chvt 1
```should do the same thing as ctrl-alt-F1. The only difference is that it might give you debugging output in the terminal emulator from which you run it.

EDIT: Also, given that you may need to restart the X server after doing this, you could also make sure that the session is recorded to a file:
```
nohup chvt 1
```
Then, you can get the error output by looking at nohup.out (in your home dir)

---

### Post by winter_mute on 2007-12-26
What video card do you use?  If I remember correctly, the ATI drivers in the repo's cause the terminals to be broken.  Not sure if this is exactly your problem, but it's one I have run into before.  The open-source drivers generally fix this, but at the cost of OpenGL speed.

---

### Post by jschneider on 2007-12-26
I have a Nvidia card here...

"chvt 1"
results in:
Couldnt get a file descriptor referring to the console

"sudo chvt 1"
does the same as Ctrl-Alt-F1 (black screen with blinking cursor).


I think the console runs fine. But it could not start the login prompt. Maybe there it is blocked from some other program that must be finished before the login prompt is shown?

---

### Post by santiagozky on 2008-02-12
I have exactly the same problem, I am not sure when it started. Did you find a solution?

Edit. Ok, apparently the problem is being caused by usplash.

---

### Post by mfaust731 on 2008-02-12
i too have a very similar issue.

i started a service at boot ( galleon ) through System, Admin< services.

now i get no prompt, just a message that says Galleon has started.   ctl-alt f1,2,3,4,5,6 dont do anything

i can ssh into it, and have prompt there

---

### Post by mbsullivan on 2008-02-13
Hey all,

These consoles are called the virtual terminals or virtual consoles, and issues with them are often linked to problems with the framebuffer setup. I don't know if I can help at all, but I could give a few suggestions:

First, make sure that the virtual terminals are actually running in the background.  Whilst logged into X windows, check for tty1-7 by running:

```
ps aux | grep tty
```

If the search doesn't return something like the following, there's a problem.

```
root      4785  0.0  0.0   1624   500 tty4     Ss+  Feb12   0:00 /sbin/getty 38400 tty4
root      4786  0.0  0.0   1628   504 tty5     Ss+  Feb12   0:00 /sbin/getty 38400 tty5
root      4788  0.0  0.0   1624   504 tty2     Ss+  Feb12   0:00 /sbin/getty 38400 tty2
root      4789  0.0  0.0   1624   504 tty3     Ss+  Feb12   0:00 /sbin/getty 38400 tty3
root      4790  0.0  0.0   1628   508 tty1     Ss+  Feb12   0:00 /sbin/getty 38400 tty1
root      4792  0.0  0.0   1628   508 tty6     Ss+  Feb12   0:00 /sbin/getty 38400 tty6
root      5124  4.6  0.9  23388 18312 tty7     Ss+  Feb12   1:06 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7

```

Next, let's try and fix a framebuffer problem under Gutsy with later kernels described [here]("https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910"). Honestly, this bug should really only arise if you've changed the resolution of your virtual terminals, but using video=vesafb has fixed VT problems for me before, so I think it's worth a shot.

Procedure (mostly from [here]("http://ubuntuforums.org/showthread.php?t=454392&page=3")):

(1) add fbcon and vesafb to /etc/initramfs-tools/modules
```
sudo vi /etc/initramfs-tools/modules 

...add fbcon and vesafb to the bottom, separated by endlines
```

(2) update this kernel's initramfs (do this for any kernel you want to affect)
```
sudo update-initramfs -u -k `uname -r`
```

(3) remove vesafb from blacklist
```
sudo vi /etc/modprobe.d/blacklist-framebuffer

... change "blacklist vesafb" to "#blacklist vesafb"
``` 

Then reboot and see if the problem has magically disappeared. If not, you may want to keep these changes since they'd let you change the resolution of your virtual terminals later on... (you can find out how by Googling, or PM me).

Hope this helps some... if not, at least you have some new names to call the consoles when searching for answers!

Mike

---

### Post by torco on 2008-02-20
Hi.

I've got a somewhat similar problem.
I've previously used CTRL+ALT+1 to get a console login, recently I can't log on.
I only recieve a "Login incorrect" message. I have checked the /etc/group file but can't find anything amiss.

Any pointers appreciated.

T.

---

