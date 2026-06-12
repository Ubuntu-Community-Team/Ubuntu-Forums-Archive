---
title: "[SOLVED] Super User"
date: 2008-06-02
forum: General Help
---

### Post by kshane on 2008-06-02
Hi all!

I'm running KDE4 and would like to know if there is a way to temporarily activate super user while under the gui?  I need to do some changes I cannot do in terminal and need to be super user.

Thanks!

Kevin

---

### Post by Zorael on 2008-06-02
The GUI equavilence of sudo is kdesudo, if that's what you're asking about. Making it '**kdesudo systemsettings**', '**kdesudo adept_manager**', '**kdesudo kcontrol**', etc.

---

### Post by mkrahmeh on 2008-06-02
> **Zorael said:**
> The GUI equavilence of sudo is kdesudo, if that's what you're asking about. Making it '**kdesudo systemsettings**', '**kdesudo adept_manager**', '**kdesudo kcontrol**', etc.


u may wanna try gksudo as well..but u need to specify the command name rather than the application name as it is, so i guess kdesudo is a good choice..

---

### Post by kshane on 2008-06-02
> **Zorael said:**
> The GUI equavilence of sudo is kdesudo, if that's what you're asking about. Making it '**kdesudo systemsettings**', '**kdesudo adept_manager**', '**kdesudo kcontrol**', etc.

One step closer!

Thank you...

Kevin

---

### Post by aysiu on 2008-06-02
Alt-F2 ```
kdesu konqueror
``` will probably be the most useful.

---

### Post by kshane on 2008-06-02
Well, my point in all this was to try and get a launcher on my panel in KDE4 for nautilus.  I am still unable to do so. I am able to get an icon on it and when I set it up to activate "nautilus --no-desktop", it tells me I don't have permission to change nautilus.  I CAN do it by hitting <F-2> and just running the command line, but this is a gui and I would like a gui-type access top the program...

Can any one help?

Kevin

---

### Post by aysiu on 2008-06-02
Nautilus in KDE? Weird.

Okay. Make a launcher with this command, then: ```
gksudo nautilus --no-desktop
```

---

### Post by kshane on 2008-06-02
> **aysiu said:**
> Nautilus in KDE? Weird.

Okay. Make a launcher with this command, then: ```
gksudo nautilus --no-desktop
```

I've done that and it tells me "gksudo nautilus --no-desktop" does not exist...

Kevin

---

### Post by aysiu on 2008-06-02
> **kshane said:**
> I've done that and it tells me "gksudo nautilus --no-desktop" does not exist...

Kevin
Then paste these commands into the terminal: ```
sudo apt-get update
sudo apt-get install gksu nautilus
gksudo nautilus --no-desktop
``` If that works, create the launcher. If it doesn't, post the error message back here.

---

### Post by kshane on 2008-06-02
> **aysiu said:**
> Then paste these commands into the terminal: ```
sudo apt-get update
sudo apt-get install gksu nautilus
gksudo nautilus --no-desktop
``` If that works, create the launcher. If it doesn't, post the error message back here.

Okay.  I did as you said.  First 2 commands had no negative results.

```
sudo apt-get update
sudo apt-get install gksu nautilus
gksudo nautilus --no-desktop
```

After the 3rd command (gksudo nautilus --no-desktop) I get:

```
kevin@Enigm-desktop:~$ gksudo nautilus --no-desktop
gksudo: unrecognized option `--no-desktop'
GKsu version 2.0.0

Usage: gksudo [-u <user>] [options] <command>

  --debug, -d
    Print information on the screen that might be
    useful for diagnosing and/or solving problems.

  --user <user>, -u <user>
    Call <command> as the specified user.

  --disable-grab, -g
    Disable the "locking" of the keyboard, mouse,
    and focus done by the program when asking for
    password.
  --prompt, -P
    Ask the user if they want to have their keyboard
    and mouse grabbed before doing so.
  --preserve-env, -k
    Preserve the current environments, does not set $HOME
    nor $PATH, for example.
  --login, -l
    Make this a login shell. Beware this may cause
    problems with the Xauthority magic. Run xhost
    to allow the target user to open windows on your
    display!

  --description <description|file>, -D <description|file>
    Provide a descriptive name for the command to
    be used in the default message, making it nicer.
    You can also provide the absolute path for a
    .desktop file. The Name key for will be used in
    this case.
  --message <message>, -m <message>
    Replace the standard message shown to ask for
    password for the argument passed to the option.
    Only use this if --description does not suffice.

  --print-pass, -p
    Ask gksu to print the password to stdout, just
    like ssh-askpass. Useful to use in scripts with
    programs that accept receiving the password on
    stdin.

  --sudo-mode, -S
    Make GKSu use sudo instead of su, as if it had been
    run as "gksudo".
  --su-mode, -w
    Make GKSu use su, instead of using libgksu's
    default.
```

BTW:  I appreciate your efforts...   :)

Kevin

---

### Post by aysiu on 2008-06-02
Try ```
gksudo "nautilus --no-desktop"
```

---

### Post by kshane on 2008-06-02
> **aysiu said:**
> Try ```
gksudo "nautilus --no-desktop"
```

That gave me a root access nautilus window.

---

### Post by kshane on 2008-06-02
Well, I got it "working", but it doesn't "feel" like it does in gnome...  I know...  What an idiot, right?

Well, I set out to get it going and I did.  In the meantime, I was able to get Thunar working the way I use nautilus, so I am happy...

Kevin

---

### Post by aysiu on 2008-06-03
Of course it doesn't feel right. You're using GTK applications (Nautilus/Thunar) in a QT environment. If you want it to feel right, use ```
kdesu konqueror
```

---

### Post by kshane on 2008-06-03
> **aysiu said:**
> Of course it doesn't feel right. You're using GTK applications (Nautilus/Thunar) in a QT environment. If you want it to feel right, use ```
kdesu konqueror
```

Results:  

kevin@Enigm-desktop:~$ kdesu konqueror
kbuildsycoca running...
Reusing existing ksycoca
sudo: konqueror: command not found

Launched ok, pid = 5801
kevin@Enigm-desktop:~$ ICE default IO error handler doing an exit(), pid = 5798, errno = 11

---

### Post by Zorael on 2008-06-03
It may be named konqueror-kde4, so '**kdesudo konqueror-kde4**'.

---

### Post by kshane on 2008-06-03
> **Zorael said:**
> It may be named konqueror-kde4, so '**kdesudo konqueror-kde4**'.

Much appreciated, but same result...

As I said, Thunar is working well for me now, sort of.  Well, enough.  :)

Kevin

---

### Post by aysiu on 2008-06-03
Maybe KDE 4 uses Dolphin?

Can you paste in these commands? ```
which konqueror
which dolphin
kdesu dolphin &
```

---

