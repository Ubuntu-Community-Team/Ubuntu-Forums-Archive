---
title: "Synaptic wont run and neiter will software updates program"
date: 2006-11-30
forum: General Help
---

### Post by JoeC21 on 2006-11-30
I am currently having two problems, they may or may not be related...

1.  I am unable to install any of the software updates available in the Software Updates program (I'm not sure if there is an actual name for this).  It says I can install 18 updates.  It wont let me install any of them.  I have tried all at once and individually and neither way works.  The install updates button seems to do the exact same thing as the check button.  When I click "Install updates"  I get a little window that says Checking for updates with a progress bar.  Under the progress bar it says "Building dependency tree" and then "Reading State information."  After that it takes me back to the main window saying I have 18 updates available.  Any ideas what is going on?

2.  I also can not get synaptic to run.  It wont open from the system menu so I tried running it from the terminal and I get this error...

joe@hercules:~$ sudo synaptic
Password:
synaptic: error while loading shared libraries: /usr/lib/libapt-inst-libc6.4-6.so.1.1: invalid ELF header

Should I just uninstall and reinstall synaptic?  Would that cause problems?  I can still install things from the command line with apt just fine so that will work I guess but would be convenient for some things if synaptic worked.

Thanks for any help,

Joe

---

### Post by apjone on 2006-12-01
try 
sudo apt-get update
sudo apt-get install -f
sudo apt-get upgrade
sudo apt-get dist-upgrade

---

### Post by picker77 on 2006-12-01
I have the same problem on three different machines. Can't do updates from the GUI, but updates/installs via the terminal using apt-get work just fine. Now I'm curious as to why the GUI won't work (BTW, updates via Synaptic/GUI have worked fine in the past on all three machines).

---

### Post by hanzomon4 on 2006-12-01
Post the output from this command ```
ldd /usr/lib/libapt-inst-libc6.4-6.so.1.1
```

---

### Post by picker77 on 2006-12-01
Ok, here 'tis:

ldd: /usr/lib/libapt-inst-libc6.4-6.so.1.1: No such file or directory

---

### Post by hanzomon4 on 2006-12-01
My bad remove the [COLOR="Red"]**:**[/COLOR]right after ldd. Here's my output ```
ldd /usr/lib/libapt-inst-libc6.4-6.so.1.1
        linux-gate.so.1 =>  (0xffffe000)
        libapt-pkg-libc6.4-6.so.3.51 => /usr/lib/libapt-pkg-libc6.4-6.so.3.51 (0xb7e39000)
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb7d5a000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7d1a000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb7d0f000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7bdb000)
        /lib/ld-linux.so.2 (0x80000000)

```

---

### Post by picker77 on 2006-12-01
Guess I'm confused today...  I entered the following in terminal:

ldd /usr/lib/libapt-inst-libc6.4-6.so.1.1



Ubuntu returned the following:

ldd: /usr/lib/libapt-inst-libc6.4-6.so.1.1: No such file or directory

---

### Post by hanzomon4 on 2006-12-01
Gottcha reinstall synaptic

---

### Post by picker77 on 2006-12-01
Thanks, hanzomon - reinstalled Synaptic, and it worked like a champ. Still don't know why my Synaptic self-destructed on all three machines at about the same time, but I suppose some previous program update ate it like a dog eats homework. Anyway, thanks for your time.

---

### Post by JoeC21 on 2006-12-01
> **hanzomon4 said:**
> Post the output from this command ```
ldd /usr/lib/libapt-inst-libc6.4-6.so.1.1
```


The command returns

"not a dynamic executable"

I see Picker77 got it corrected by reinstalling synaptic.  Should I do the same?

Thanks,
Joe

---

### Post by hanzomon4 on 2006-12-01
Try it

---

### Post by JoeC21 on 2006-12-01
hmm, it wants to remove ubuntu-desktop.  Is that a very good idea?

---

### Post by JoeC21 on 2006-12-01
> **apjone said:**
> try 
sudo apt-get update
sudo apt-get install -f
sudo apt-get upgrade
sudo apt-get dist-upgrade

I did this, seems to have fixed the trouble with the update program as now it says my system is up to date, however I am still having the same trouble with synaptic

---

### Post by hanzomon4 on 2006-12-01
Try > sudo aptitude reinstall synaptic 

---

### Post by JoeC21 on 2006-12-02
Nope that didnt fix it either.  If you have any more suggestions I would love to hear theme.  If not thanks for trying anyway, I appreciate it.

Joe

---

