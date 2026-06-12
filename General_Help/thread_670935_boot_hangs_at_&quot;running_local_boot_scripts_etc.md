---
title: "boot hangs at &quot;running local boot scripts /etc/rc.local....[OK]&quot;"
date: 2008-01-18
forum: General Help
---

### Post by npjw on 2008-01-18
running gutsy rc1  on a dell 9300 laptop. No problems for several months. I rebooted tonight and it hangs after the line "running local boot scripts (/etc/rc.local)...........[OK]"

Before that is a bit about vmware and apacheserver not finding an address

I rebooted several times and got the same result. I then checked the contents of /etc/rc.local and it consists of the commented out section and then "exit 0"

---

### Post by bodhi.zazen on 2008-01-18
Yea, it is strange

Just hit the enter key or change consoles (Ctrl-Alt-F2)

---

### Post by npjw on 2008-01-20
thanks for the help. that gets me into a terminal, but is there a way to get Xserver up and running so i can get a gui?

---

### Post by KrisWood on 2008-01-20
I'm having this exact same problem with a fresh install of ubuntu on a vmware server. On first boot after install (and all subsequent boots) I'm stuck at:

> * Running local boot scripts (/etc/rc.local)                                  [ OK ]

Enter key, or crtrl+alt+f2, make no change to what's shown on the screen at all. I can reboot and get into recovery mode just fine though.

Any ideas?

Edit: The network admin was able to reboot the machine and it went through just fine, I'll post back if it comes up again >.<

---

### Post by npjw on 2008-01-20
i didnt post this before, but right after i made this thread i tried booting into ubuntu out of curiousity..and it actually worked o.O

update: today i had to reboot and now its hanging on boot again

my windows partition is starting to run out of space so right now i'm working on freeing up space and then doing a defrag. [this comp always gets screwy when theres not enough space]. dont know if it'll help this problem, but i need to tidy up anyway :P

---

