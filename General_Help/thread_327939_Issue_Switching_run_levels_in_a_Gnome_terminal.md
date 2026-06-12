---
title: "Issue: Switching run levels in a Gnome terminal"
date: 2006-12-30
forum: General Help
---

### Post by jka on 2006-12-30
I am running a quite recent installation of ubuntu 6.10, everything upgraded and up to date.

Currently I am trying to figure out the mysteries of the new upstart concept.
Primarily, what I would like to do and what fails is switching run levels in a Gnome terminal. The commands “init”, respectively “telinit”, do not work as I would expect. 

E.g. after starting up, in a Gnome terminal, the command "runlevel" delivers the output:

N 2

In my understanding it should be “N 5”, because there is graphics mode.

Invoking the command:

init 3

or:

telinit 3

does not switch to the command line mode. But the command “runlevel” now delivers:

2 3

This would indicate that a change from run level 2 to 3 occurred. But the system is still in graphics mode and all the windows remaining open.

Invoking the command:

init 1

has some effect, the screen disappears and  the system hangs.

For comparison, I was doing all this with another Linux distribution. Everything worked fine there and I was able to switch run levels flawlessly.
This confirms to me that something in Edgy is wrong!

In demand is an expert's opinion. Is there anybody who can comment on this?

Thanks!

---

### Post by dcstar on 2006-12-30
> **jka said:**
> I am running a quite recent installation of ubuntu 6.10, everything upgraded and up to date.

Currently I am trying to figure out the mysteries of the new upstart concept.
Primarily, what I would like to do and what fails is switching run levels in a Gnome terminal. The commands “init”, respectively “telinit”, do not work as I would expect. 
......

Runlevel 2 is the "standard" Ubuntu run level which will start X (if you have it enabled).

Runlevel 1 is single-user mode (the CTRL-ALT-F1 screen should be the only one up), 6 is reboot and 0 is shutdown.

It seems that the various start files are in their traditional places in /etc.

---

### Post by jka on 2006-12-30
I must say that I am not experienced with Linux, particularly not with run levels, etc. But in the documentation I can read what the run levels are. This is not the question.

I have a normal Ubuntu (workstation) installation. I.e. the system starts automatically up to graphics mode, i.e. X running. In my understanding, this must be run level 5.

After login and opening a terminal window, I would expect to see run level 5 as the answer to the "runlevel" command. But this is not the case, it is 2.

Then, when entering an "init 3" command I would expect X to shut down and get a login prompt in a command line mode. After login there, I could enter "init 5", the command line mode would end and X would start up again.

All this is not the case here!

Then I wonder, after the system has started up and X is running, how can I switch to command line mode, let's say to runlevel 3 or 1?

When I enter "init 3" X does not shut down, when I enter "init 1" X might be closing, but I am unable to continue because the system hangs.

Is this behavior normal?

---

### Post by mjrclark on 2006-12-30
Yes, this is normal.
What the reply to your first post said was;
Ubuntu is different from many other distributions.
One difference is what each runlevel is.
5 is not used in Ubuntu.
What is 5 in many other distributions is 2 in Ubuntu.
Your results agree with this.
There is no problem, just a difference between what you read that said 5 is the normal GUI runlevel and what the Ubuntu developers decided to use.
Your trouble stems from differences between traditional runlevel use and Ubuntu- difference is not necessarily wrong.

---

### Post by jka on 2006-12-30
:-D Thanks everybody for the clarification!

---

### Post by dcstar on 2006-12-30
> **jka said:**
> 
.......
Then I wonder, after the system has started up and X is running, how can I switch to command line mode, let's say to runlevel 3 or 1?
.......

Command prompt logins are available after X starts, just use CTRL-ALT-F1 through to F6 to access them (F7 returns to X).

---

