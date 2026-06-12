---
title: "Linux through Windows??"
date: 2007-11-02
forum: General Help
---

### Post by Anthrax9 on 2007-11-02
I have a Dual boot XP and Ubuntu system
Is it possible to use this Linux from Windows using programs like [KevTerm]("http://www.geocities.com/SiliconValley/Network/1027/")??
Did not know where to put this topic:confused:

---

### Post by dcstar on 2007-11-02
> **Anthrax9 said:**
> I have a Dual boot XP and Ubuntu system
Is it possible to use this Linux from Windows using programs like [KevTerm]("http://www.geocities.com/SiliconValley/Network/1027/")??
Did not know where to put this topic:confused:

No, that is a basic terminal program to access a working Linux (or other) server via a network connection.

You do not "use" Linux from Windows unless you install it in Windows with something like Virtual PC.

---

### Post by Anthrax9 on 2007-11-02
so is there any way to start the linux kernel in windows and then access it through kevterm????:-k:-k
Thanx

---

### Post by MarinaraOfDeath on 2007-11-02
Depending on what you want to do in windows, you could just run cygwin or a live CD. If you don't need to run anything to flashy visually (meaning with a X server without a lot of fiddling and configuration done by hand), you probably want cygwin. I've used it to compile and run scientific software written in Fortran, which worked fine for generating data I needed. The problem is that it isn't all that up to date (I don't even think it's maintained actively anymore, from some stuff I've read).

If, instead, you want you want to run linux on windows, you're gonna need to start reading about [virtualization]("http://en.wikipedia.org/wiki/Virtualization") and [virtual machines]("http://en.wikipedia.org/wiki/Virtual_machine"). My roommate is running Parallels and has convinced me of its virtues, so I'm looking into virtualizing an existing windows install in linux (via either [virtualbox]("http://en.wikipedia.org/wiki/VirtualBox") or [VMware]("http://en.wikipedia.org/wiki/VMware")). That debacle wasn't all that hard to recover from, but I gotta say, establishing a brand spanking new restore point in windows is absolutely essential before doing this (i.e., if you have system restore turned off, TURN IT BACK ON AND CREATE A RESTORE POINT FIRST). I say this as someone who just finished putting his laptop back in order late late last night.

Now, getting back to the very original question, look at virtualbox for windows. That might let you run linux in a virtual machine hosted by windows. I don't promise it will, I'm still looking into it myself, but the possibility is intriguing.

---

### Post by Anthrax9 on 2007-11-03
i too thought of virtualising will try it but is there anyway to go around this without virtualization????

---

