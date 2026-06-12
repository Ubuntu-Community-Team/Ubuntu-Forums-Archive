---
title: "Ubuntu Mate 24.04 recent clean install but can't run appimages"
date: 2024-06-19
forum: General Help
---

### Post by andy.r2 on 2024-06-19
After a failed LTS upgrade to 24.04, I did a clean install a few days ago.  I have a number of Appimages in my ~/Applications folder.  Most are fairly up to date.  none that I tried will run and give an error such as:
```
andy@Andy-hp-laptop:~/Applications$ ./Bitwarden-2024.6.2-x86_64.AppImage 
[645040:0619/215644.296928:FATAL:setuid_sandbox_host.cc(158)] The SUID sandbox helper binary was found, but is not configured correctly. Rather than run without sandboxing I'm aborting now. You need to make sure that /tmp/.mount_BitwarygU5sC/chrome-sandbox is owned by root and has mode 4755.
Trace/breakpoint trap (core dumped)
```

Approx 10 appimages give the same structure of error.  

An old version of Siril (1.2-beta) does run, so its not a fundamental issue with appimages?

Any suggestions what may be the issue?

Many thanks!

---

### Post by currentshaft on 2024-06-19
Did you already try this? [https://docs.appimage.org/user-guide/troubleshooting/electron-sandboxing.html](https://docs.appimage.org/user-guide/troubleshooting/electron-sandboxing.html) 

Why anyone would use a password manager of all programs based on Electron ... that's a different topic.

---

### Post by andy.r2 on 2024-06-20
All good there, nothing to do.

---

### Post by andy.r2 on 2024-06-21
I'm not familiar with teh background to the password manager comment.  

I do also have an issue with thunderbird not remembering the account passwords I enter for it.   I check the use password manager box each time but the passwords never get selected.  Is this related to my issue, above?

---

### Post by andy.r2 on 2024-06-21
Running .App.appimage --no-sandbox gets a couple of appimages to run.  I still have several others that do not.  Somewhat frustrating  is that they all ran with no tweaks required in 22.04 on the same hardware.

---

### Post by lproven on 2024-09-24
**If** you do not mind relaxing your security settings, then this fix works for me, which `--no-sandbox` and `--disable-setuid-sandbox` do not.

````
sudo sysctl -w kernel.apparmor_restrict_unprivileged_userns=0
````

Snag: you need to redo this every time you boot.

---

### Post by lproven on 2024-09-24
**If** you do not mind relaxing your security settings, then this fix works for me, which `--no-sandbox` and `--disable-setuid-sandbox` do not.

````
sudo sysctl -w kernel.apparmor_restrict_unprivileged_userns=0
````

Snag: you need to redo this every time you boot.

---

