---
title: "broken command line shutdown"
date: 2007-07-09
forum: General Help
---

### Post by fm1234 on 2007-07-09
Hi,

I'm using VNC and since the GUI doesn't give me the options to shutdown the computer, I use a terminal to enter "shutdown now". The vncviewer closes, but the shutdown process stops somewhere in the middle and gives me a shell prompt. I can enter "halt" to finally shutdown, but this should not be happening.

BTW, "halt" instead of "shutdown now" works fine. What's the difference between these two?

Also, it seems a design bug that the power button brings the Quit dialog box instead of simpy doing "halt". If I want the quit dialog, I use the mouse to get it from the desktop menu. If I want to shutdown the computer I would just like to press the power button to do it. Seems the prety obvious thing for an elctrical machine to do...:(

Regards,
Fernando

---

### Post by Mr. C. on 2007-07-09
Read:
```

man halt
man shutdown

```
MrC

---

### Post by fm1234 on 2007-07-09
MrC, do you realise your reply is totally useless and even unfriendly? 

Did I ask how to get help info about shutdown or halt?

Don't you think most people know about man or at least about google?

Don't you realise that if I'm posting is because I want to reach someone, not reach a document? 

Why bother reply to an obvious minor part of the post, a passing-by-question, without even giving a direct answer? Even indirectly it doesn't reply the main question, does it?

Sending people to man in such a cheap manner is unproper. It really is. Think about it.

If you don't feel compeled to give a proper reply to the post just don't post. Don't send noise back.

Fernando

---

### Post by Mr. C. on 2007-07-09
Your premises are incorrect.  A large set of GUI-centric users are completely unaware of the help and information available in the man pages or other.  Nobody here can possibly know what you know, and don't know.

Some are perfectly happy with simple pointers, and say "Thank You" afterwards.  Other's like yourself expect the world's crystal ball to be tuned your channel.

If you're looking for human contact, go to a social.  If you're looking for information and guidance, read and ask for further clarification on what you don't understand.

You asked one question, made some observations and expressed some opinions.  What specifically did you expect to receive given that?

MrC

---

### Post by fm1234 on 2007-07-10
I see, my main question is not so clear. The shutdown command is not working it stops in the middle and I get a shell. Why do I get a shell? what can I do to fix this? Why can I shut down from the GUI but not from a terminal?

Fernando

---

### Post by mcduck on 2007-07-10
> **fm1234 said:**
> I see, my main question is not so clear. The shutdown command is not working it stops in the middle and I get a shell. Why do I get a shell? what can I do to fix this? Why can I shut down from the GUI but not from a terminal?

Fernando

If you want the shutdown to actually shut the computer down, you need to use "shutdown -h now" (which is eaxctly same as running 'halt')

---

### Post by Mr. C. on 2007-07-10
> **fm1234 said:**
> ...The shutdown command is not working it stops in the middle and I get a shell. Why do I get a shell? what can I do to fix this? Why can I shut down from the GUI but not from a terminal?
Fernando

It is working.  The problem is you have decided in your mind what "working" means, regardless that the man page tells you differently:

> Once TIME has elapsed, shutdown sends a request to the init( 8 ) daemon to bring the system down into the **appropriate runlevel**.

This does not say the system will be powered off, or halted.

The command changes the system's run level generally to single user mode, where you can perform administrative operations.

MrC

---

### Post by marsbt on 2007-07-10
> **mcduck said:**
> If you want the shutdown to actually shut the computer down, you need to use "shutdown -h now" (which is eaxctly same as running 'halt')

the manpage tells the same thing..... if one is willing to read though! Quoting from the manpage.......
> shutdown does its job by signalling the init process, asking it to change the runlevel.  **Runlevel 0** is used to halt the system, **runlevel 6** is used to reboot the system,  and  **run&#8208;level  1**  is  used to put to system into a state where administrative tasks can be performed; *[COLOR="Red"]this is the default if neither the -h or -r flag is given to shutdown[/COLOR]*.

---

### Post by Mr. C. on 2007-07-10
marsbt, your man page is from a different distro or version.  It has been changed, and no longer has that text.

MrC

---

### Post by fm1234 on 2007-07-10
Thanks to all for your replies.

I used to routinely shutdown remotely, then for several months I had the computer broken, finally I fixed it and installed the new version of Ubuntu. I restarted with the same routine but obvioulsy I forgot the -h. Since I was doing it mechanically, I didn't question the command, I just thought there was a problem with the new install.

Regards,
Fernando

---

