---
title: "What does this &quot;Kernel Panic&quot; mean?"
date: 2016-06-11
forum: General Help
---

### Post by Cesar_Blanco on 2016-06-11
I'm new to Ubuntu Forums. Can someone tell me during a kernel panic what the number with a decimal on the left is? (Ex: [33.847317584])
-Thanks in advance, Cesar

---

### Post by djchandler on 2016-06-12
I believe it means that the kernel is not compatible with your hardware. Are you getting this when trying to install, or on a system that's already installed (not as likely)? The only time I've seen any kernel panic error was while trying to install Darwin (foss version of OS X) on an AMD cpu. AFAIK, Darwin and OS X will only run on  Intel cpus. Either you have an ARM cpu trying to install an x86 version or vice-versa, possibly insufficient RAM would be my guesses.

---

### Post by buzzingrobot on 2016-06-12
It means something seriously wrong has happened and the kernel can't continue executing.  So, it displays a message and stops. Typically, you'll see a dozen or more lines displayed.  

Unfortunately, the text of the error message is needed to diagnose the problem.  Try Googling with the "kernel panic: ..." line.

If this is a new install, be sure you're following the guidance here: [http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop)

---

### Post by grahammechanical on 2016-06-12
If you are enquiring about the actual number 33.847317584, then my guess is that it is log number. Linux creates log of various actions and each task is numbered as are the results of the task.

Regards.

---

### Post by steeldriver on 2016-06-12
... isn't it a timestamp (seconds.nanoseconds since boot)?

---

### Post by Cesar_Blanco on 2016-06-16
It also appears on boot.

---

### Post by djchandler on 2016-06-20
> **Cesar_Blanco said:**
> It also appears on boot.

Before you do anything else, try searching "kernel panic" on our forum, and see if someone has already answered your question.

I assume you mean you are booting from an installed kernel on an ssd or hard disk, rather than the installation dvd.

The first thing that comes to mind is you are not giving us nearly enough information to help you. Anything we write will probably still mean you have an installation that won't boot.

The second thing I can think of is that you replaced a video card and the kernel's video driver is incompatible now. The only time I encountered a kernel panic was during a virtual machine boot of an installation 7-8 years ago. I agree that the number is seconds elapsed. Is it the same number, or nearly so, every time? If it's a laptop, the number may be higher when on battery rather than plugged-in and fully charged.

Tell us about your hardware setup, if anything has significantly changed regarding the aforementioned.

Do you want a workaround solution, or do you only want to recover your data? You may be best served to find someone locally to actually help you. Ask a teacher or librarian to help you find someone. There are user groups all over the world. You may be able to find someone here. Search the various forum groups.

We can help you here, but the learning curve may be steep, and it involves much more than I want to write without good reason to do so.

---

### Post by Cesar_Blanco on 2016-06-28
Ok. I see. The number is the system uptime when the text displayed.

---

### Post by Cesar_Blanco on 2016-06-28
Also, I see what a kernel panic is. It's caused by a variety of factors:
Pid 1 (init) is killed
Mount failed
General protection fault
Kernel NULL dereference
Fail to handle kernel paging request
Fatal machine check, or
Interrupt handler is killed

Thank you everybody.

---

### Post by djchandler on 2016-07-04
Please mark the thread "solved." Only the thread-starter can do this.

---

