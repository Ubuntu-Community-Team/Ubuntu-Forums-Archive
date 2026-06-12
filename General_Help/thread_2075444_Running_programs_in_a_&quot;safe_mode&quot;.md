---
title: "Running programs in a &quot;safe mode&quot;"
date: 2012-10-23
forum: General Help
---

### Post by njitram on 2012-10-23
I was wondering, is it possible to run programs that can't affect your files other then where the program is running, can't affect your linux system?

Im working on a project with an automatic compiling system, after this it sends a shell command to run the compiled object. The compiled program should not harm the system in anyway.. is this possible?

---

### Post by dcstar on 2012-10-23
> **njitram said:**
> I was wondering, is it possible to run programs that can't affect your files other then where the program is running, can't affect your linux system?

Im working on a project with an automatic compiling system, after this it sends a shell command to run the compiled object. The compiled program should not harm the system in anyway.. is this possible?

Linux user accounts have no rights to affect the system unless **you** give them admin privileges.

Running any program under normal user privileges can do nothing outside of that user.

---

### Post by Scott Goodgame on 2012-10-24
Install another instance of ubuntu in a virtualbox and run it in there.

---

### Post by njitram on 2012-10-25
> **dcstar said:**
> Linux user accounts have no rights to affect the system unless **you** give them admin privileges.

Running any program under normal user privileges can do nothing outside of that user.

Thank you =)

Is it also possible too read bad intensions from programs? or when its stuck in a infinite loop?

---

### Post by Mark Phelps on 2012-10-25
Not sure what you're really asking ...

The "safe mode" in Window is a misnomer. It actually just launches Windows with the default set of drivers and is useful primarily when some form of driver corruption (like forcing the installation of the WRONG video drivers) otherwise prevents you from getting to the Windows desktop.

This doesn't make an app running in "safe" mode any more or less "safe" than when it runs at other times.

As to "causing damage", Ubuntu enforces access limits to certain files and directories, so you can't accidentally, running under your own account (for example) delete the "/etc" folder and the files under it.

Does this mean you can't cause other damage -- no it does not.

So basically, there's no "safe mode" in which you can run programs that will severly limit what they can do.

---

