---
title: "First several characters of terminal get &quot;stuck&quot;"
date: 2022-06-19
forum: General Help
---

### Post by afollette on 2022-06-19
Hi,

I've started getting a quite annoying bug on my terminal. The first few characters of the terminal seem to get stuck and I cannot `ctrl-l` or `clear` the from my screen. When I hit enter they get printed to the screen. Often this happens when I `ctrl-a` to the front of the line. Other times it gets worse and the terminal will print a newline for every character I type causing general corruption.

Video attached showing the general behavior of the bug. [https://imgur.com/a/iSBUEq6](https://imgur.com/a/iSBUEq6)

How can I go about debugging this? Please advise!

System stats:
OS: Ubuntu 22.04 LTS 
Host: XPS 15 9520
Kernel: 5.15.0-39-generic
Shell: bash 5.1.16

---

### Post by dragonfly41 on 2022-06-20
Try a different terminal to gather clues ..

yakuake is one I use .. a dropdown terminal (F12 to toggle)

---

### Post by Holger_Gehrke on 2022-06-20
I see that you've got a really involved multi-line prompt that includes some colour emoji. Those are encoded as several bytes but put only one character on the screen. This might break the simple logic of the shell's display logic. Try a simpler prompt.

Holger

---

### Post by TheFu on 2022-06-20
Try
```
$ stty sane
```

If that doesn't help, close the terminal program and open it again.  Sometimes a program we run (accidentally or on purpose) will send control characters to the screen that changes things.
"stty sane" will reset to reasonable defaults.  However, when entering that command and option, it is likely that the displayed text won't look anything like what we are typing. That usually doesn't matter.

If the prompt is really complex, that's likely the issue.  The default prompt of 
{user}@{hostname}:{pwd}$ is brilliant.  It is exactly what we need for rsync or scp to transfer files between systems.  A little select/paste and by just using the current prompt, we've made something that could take 20 seconds into a 2second task.

I use xterm -  and have for about 25 yrs.

---

### Post by afollette on 2022-06-20
Alright, I switched to gnome-shell.

Removed the emoji and simplified my prompt as recommend by @TheFu

Using ``` stty  sane``` I still get the behavior.

Should I start removing recently install packages/programs that I think maybe interfering with the command line?

---

### Post by TheFu on 2022-06-21
> **afollette said:**
> Alright, I switched to gnome-shell.
Ouch. I'd never ask anyone to take that hardship on.

> **afollette said:**
> Should I start removing recently install packages/programs that I think maybe interfering with the command line?
I wouldn't expect any program would be screwing around with your command line, but if you use a non-standard shell, perhaps that is the issue?

Might I suggest you return to the default prompt and see if that solves it?  The easy way to test this is to create a new userid, login with it and see if the issue still happens. If not, then you know it isn't any installed program, but YOUR settings/environment.

People often forget that creating and removing userids is pretty trivial.  Linux is multi-user, all the way down to the core.  I have different users on my systems for different needs, mostly testing, but also for other needs.  If I completely clear the $HOME directory, including all the ~/.directory/ files there, I know it is a fresh user.

---

