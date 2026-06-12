---
title: "Linux is bad at controlling bad behavoring programs"
date: 2013-10-04
forum: General Help
---

### Post by Lem0nHead on 2013-10-04
Hello there
I'm wondering if someone can give me an idea on what's the real cause of this problem, and if it's possible to solve it on Linux current architecture.
I guess most of you already used Windows, and specially since Windows 7, it got extremly good at handling bad behavoring programs.

So let's say I run a program that start eating my memory, forcing the OS to swap, or that it starts consuming a lot of CPU.
In Windows, whenever you do ctrl-alt-ESC, you get the task manager and can end process.

Of course you can also do something similar on Linux, by creating a shortkey to a task manager, but it's not the same.
If your system is locked by a bad behavoring process, you won't get to launch a new process (the task manager).

I guess the main difference comes from what windows consider kernel vs userspace (I guess the graphical mode of Windows is part of its kernel, and maybe it has a process scheduler that can priorize the task manager and other system process). In Linux, your window manager and X are just other programs concurring for resources with your bad program.
Even ctrl-alt-F1 locks in this case (at least for a couple MINUTES), which could be understandable in a single-core computer, but not on a multi-core one.

So, is this considered an issue? Are there some reasonable solutions for that?

thanks!

---

### Post by 3rdalbum on 2013-10-05
There are two things you can do. First thing: Have a Launcher item that runs the "xkill" program. When you click on the Xkill icon, the next mouseclick will kill whatever program has its window underneath the mouse cursor (i.e. click Xkill, then click Firefox, and Firefox will be killed).

Alternatively, you can hit Control-Alt-F1, log into the text terminal, and run 'kill' or 'top' from there.

It's not that "Linux is bad at controlling bad-behaving programs", it's just that "Linux handles it differently". You're obviously quite new not to realise that Linux does almost EVERYTHING differently to Windows - and that doesn't make it better OR worse.

---

### Post by oldfred on 2013-10-05
I normally use the terminal and run top (q to exit) to see what task, and then sudo kill XXX where XXX is task number.
But sometimes you have to totally kill system and you should try to do a shutdown not a power off.

 Never force shutdown your laptop. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)

      
 Force quit icon
[http://superuser.com/questions/456363/how-to-add-force-quit-icon-in-ubuntu-12-04](http://superuser.com/questions/456363/how-to-add-force-quit-icon-in-ubuntu-12-04)

---

### Post by Lem0nHead on 2013-10-05
> **3rdalbum said:**
> There are two things you can do. First thing: Have a Launcher item that runs the "xkill" program. When you click on the Xkill icon, the next mouseclick will kill whatever program has its window underneath the mouse cursor (i.e. click Xkill, then click Firefox, and Firefox will be killed).

Alternatively, you can hit Control-Alt-F1, log into the text terminal, and run 'kill' or 'top' from there.

It's not that "Linux is bad at controlling bad-behaving programs", it's just that "Linux handles it differently". You're obviously quite new not to realise that Linux does almost EVERYTHING differently to Windows - and that doesn't make it better OR worse.

does this always work for you? as I said on my post, I tried ctrl-alt-F1, but even that takes a couple minutes to open
I think it's the job of a good multitask OS to not let one bad behavoring process to basically hijack it and block all other process, that's why I said it's worse (in this job) than windows

---

### Post by Lem0nHead on 2013-10-05
> **oldfred said:**
>  Never force shutdown your laptop. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

this doesn't solve the problem itself, but is a good tip :)
thanks!

---

### Post by grahammechanical on 2013-10-05
Can you give an actual example or is this all hypothetical? Let us say ... No give an actual example of a badly behaving program that you are having problems with. Better still uninstall that program and do not use it. Problem solved.
 
As regards this imaginary problem there is no difference between an OS running on a single core CPU and an OS running on a multi-core CPU. The issues are the same - the amount of system resources available. 

Oh, and that reminds me, is it not Windows that demands ever faster/more powerful CPUs and ever larger and faster amounts of RAM and ever more powerful GPUs? And still it needs a task manager to shutdown a process that is hogging all the system resources. It seems to me, from what you say, that Windows is not very good at multi-tasking even with excessive amounts of resources.

And here I am running the very latest version of Ubuntu on the same hardware that I started using Ubuntu on 6 years ago, with the exception of a more powerful graphic adapter but not top of the range even then. I bet you could not do that with Windows. Want the latest Windows - buy an new Windows machine!

Are you actually using Ubuntu? Try running this command

```
top
```

and see actually what is happening to system resources.

Regards.

---

### Post by Lem0nHead on 2013-10-05
> **grahammechanical said:**
> Can you give an actual example or is this all hypothetical?

No, this is all very real.
I have about 30,000 frames (from a video) that were extracted from a video I was working with.
I tried to visualize them on thumbnail format using gwenview and XnView. Both of those programs started consuming memory as crazy (which is expected and is NOT what I'm complaining about) and the system just locked. It took about 2 to 3 minutes for me to be able to get to shell (Ctrl-Alt-F1). So no matter which command you tell me to run (top, kill, xkill, whatever), it doesn't help while I can't even get a shell to type it in.
Of course after I got the shell, I was able to list the process and kill it, but that's not what's bothering me.

So, again, I'm not complaining about the program taking too much memory (or starting to swap) when I ask it to display thousands of images as thumbnail. I'm not even saying I'm the smartest person in the world for trying to do that. I'm just saying that doing it rendered my system completly unstable and, IMO, it's the job of the OS to prevent this from happening, NO MATTER WHAT a program do.

Again, IMO, I think I should be able to run ANY program and it should be impossible for this program to do anything that could lock my system and my only way out would be to reboot it; as Windows 7 do. Is this really expecting too much of a multiuser/multiprocess OS running on a multicore CPU?

So, just reinforcing, I'm not also saying that Windows is better than Linux, or that it runs on any kind of hardware. All I'm saying is that in years using Windows 7, I was never able to run a program that just locked it and made it impossible to kill this program. In 1 week running Ubuntu I've done that and lost some work due to this problem.

It's easy to say "just don't ever run a program that will start swapping", or "disable swap", or something in those lines.
But it's really not what I'm asking.

I just wanna know if there's a way for Linux to give a higher priority on its process scheduler for tty, or something like that.
If there isn't, alright; that doesn't make it worse than Windows. That just make it worse than Windows at handling misbehaving programs.

---

