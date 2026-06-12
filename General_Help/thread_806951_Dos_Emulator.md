---
title: "Dos Emulator"
date: 2008-05-25
forum: General Help
---

### Post by I Faw Down on 2008-05-25
I have linux mint (based on ubuntu) and when I wanted to play a dos game (The Rise And Decline Of The Third Reich) So I got wine and I don't know what to do.  I went to ubuntu tutorials, but the first command line ("sudo aptitude install dosbox") isn't recognized.

Any help on what to do?

---

### Post by bwhite82 on 2008-05-25
Yes. Leave all of that junk alone and simply install dosemu from the repos.

---

### Post by imbjr on 2008-05-25
> **I Faw Down said:**
> I have linux mint (based on ubuntu) and when I wanted to play a dos game (The Rise And Decline Of The Third Reich) So I got wine and I don't know what to do.  I went to ubuntu tutorials, but the first command line ("sudo aptitude install dosbox") isn't recognized.

Any help on what to do?

Try DOSBox Emulator, it's under Applications | Add/Remove - search for DOSBox. I run run Quake under it successfully.

---

### Post by I Faw Down on 2008-05-25
what version of dosbox should I get?

---

### Post by imbjr on 2008-05-25
> **I Faw Down said:**
> what version of dosbox should I get?

The version I'm running is 0.72, which I believe is the one in the repositories.

---

### Post by I Faw Down on 2008-05-25
thanks, I got the windows download using wine.  But when I start the DosBox terminal, I can't type any commands...

What am I doing wrong?

---

### Post by ibuclaw on 2008-05-25
The commands would be near identical to that of the real Windows DOS shell.

For the list of commands, type into the shell:
```
help
```

For a slight indepth overview of DosBox:
```
intro
```

[EDIT]
You are using the native Linux version? Aren't you?

Regards
Iain

---

### Post by I Faw Down on 2008-05-26
I hit a snag,

I have mounted C:\ and D:\ and I tried to run the install.exe but it says it can't be done in dosmode...

Any help?

P.S. Heres the guide I was using...
[http://vogons.zetafleet.com/viewtopic.php?t=8933](http://vogons.zetafleet.com/viewtopic.php?t=8933)

---

### Post by jocko on 2008-05-26
> **I Faw Down said:**
> I hit a snag,

I have mounted C:\ and D:\ and I tried to run the install.exe but it says it can't be done in dosmode...

Any help?

P.S. Heres the guide I was using...
[http://vogons.zetafleet.com/viewtopic.php?t=8933](http://vogons.zetafleet.com/viewtopic.php?t=8933)

That guide seems to be for installing a DOS game in windows or mac os, but what you want is to install a windows game on linux.
Have you tried just running the installer with wine?

---

### Post by I Faw Down on 2008-05-26
I'm using the windows version with wine.

---

### Post by Steveway on 2008-05-26
> **I Faw Down said:**
> I'm using the windows version with wine.

Why? The Linux-version is in the repositories.
So open up Synaptic and search for it.

---

### Post by jocko on 2008-05-26
> **I Faw Down said:**
> I'm using the windows version with wine.

Ok, but still, you need to run the installer **directly** in wine, not in a dos emulator, as it clearly tells you that it can't be run in a dos environment. Try running this in a terminal:
```
cd [path to where you have the installer]
wine installer.exe
```

If it really was a DOS game, you should run it in a dos emulator installed in directly in linux and not in a dos emulator installed in a windows emulator.
To many levels of emulation will probably cause some weird behaviour...

---

### Post by I Faw Down on 2008-05-26
linux Mint doesn't seem to have Synaptic...

I'll try to find a Download...

By the way, I don't know if this would clear anything up or not but I have 2 games I DL'd on wine's C:\ Drive (A-Train also)

---

### Post by I Faw Down on 2008-05-26
I cant find a download...

Anyone have a link?

---

### Post by jocko on 2008-05-26
> **I Faw Down said:**
> linux Mint doesn't seem to have Synaptic...
I'm convinced mint uses synaptic. Do you see "Package Manager" anywhere in the menu (should be under "System")?
Otherwise, just type:```
gksudo synaptic
```in a terminal...

---

### Post by I Faw Down on 2008-05-26
It says (after I type my password in) that sudo is not allowing me to run the program, the top says "Failed to run synaptic as user root"

---

### Post by I Faw Down on 2008-05-28
any help?

---

### Post by jocko on 2008-05-29
That sounds weird...
Does your user have admin right?
Type "groups" in a terminal to see which groups your user is a member of.
This is what I see:
```
[COLOR=Gray]*yourusername*[/COLOR] adm dialout cdrom floppy audio dip video plugdev scanner fuse lpadmin [COLOR=Red]admin[/COLOR] pulse pulse-access pulse-rt vboxusers
```
If you see "admin" there, you should have the permission to run synaptic.

Can you run anything else with sudo (try "sudo gedit")?

---

### Post by I Faw Down on 2008-06-01
well, it doesn't have that that on their...

though my father put in his password and it says doesn't like his password either...

---

### Post by jocko on 2008-06-02
> **I Faw Down said:**
> well, it doesn't have that that on their...

though my father put in his password and it says doesn't like his password either...

Who installed ubuntu on the computer? Which username was created during the installation?
Usually only the first user have admin rights. And that user have to be logged in and run the command from his/her own session.
It would not work for you to use your fathers password from your session, if that's what you tried.

---

