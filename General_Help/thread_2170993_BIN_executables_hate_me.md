---
title: "BIN executables hate me"
date: 2013-08-28
forum: General Help
---

### Post by slango20 on 2013-08-28
MultiMC: [http://www.minecraftforum.net/topic/1000645-multimc-43-windows-linux-mac](http://www.minecraftforum.net/topic/1000645-multimc-43-windows-linux-mac)

well, how do I put this: 'There is no application installed for executable files'

firefox said it was a BIN format program, and what do I use to run it?

---

### Post by lah7 on 2013-08-28
**Welcome to the Ubuntu forums! **Assuming you followed their instructions to mark it as executable in the properties permissions tab, it should just run by double clicking it.

If you have it saved on the desktop, try running it from the terminal:
1. Press **CTRL+ALT+T **to open the terminal.
2. Type:
```
cd Desktop
./MultiMC
```
It's important that you type it exactly as it's case sensitive.

And hopefully that should execute the application. If that still fails, try making it executable again by typing:
```
chmod +x MultiMC
```

---

### Post by slango20 on 2013-08-28
./MultiMC: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.15' not found (required by ./MultiMC)
./MultiMC: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.14' not found (required by ./MultiMC)


and I derped on the executable property, now it gives me this

---

### Post by lah7 on 2013-08-28
Ah, this terminal output explains why it wasn't launching the first time. Your system is missing some essential packages in order to function properly. The software is relying on some libraries which are not installed or linked.

I'm not sure which package this belongs to. However, I have found you this page which may be able to help you: [http://askubuntu.com/questions/315907/libc-so-6-version-glibc-2-16-not-found](http://askubuntu.com/questions/315907/libc-so-6-version-glibc-2-16-not-found)

**Try this:**
> [FONT=verdana][COLOR=#333333]If you want to update libc6 to version 2.16, run next command in [/COLOR][terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal")[/FONT][COLOR=#333333][FONT=UbuntuRegular][FONT=verdana]:[/FONT]
[/FONT][/COLOR][FONT=Ubuntu Mono]```
sudo apt-get install libc6=2.16-0ubuntu5
```[/FONT]

Packages vary depending on the Ubuntu distribution, I can assure you MultiMC runs fine on my system (Ubuntu 13.04 64-bit). Please could you share which Ubuntu edition you're using?

---

### Post by slango20 on 2013-08-28
updated to 12.04 (was running 10.XX (no idea what sub number it was, outdated version anyways)) and that fixed it

---

