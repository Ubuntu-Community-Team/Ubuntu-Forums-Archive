---
title: "Why is Virtual Box only showing 32 bit guest versions on my 64 bit host OS?"
date: 2017-09-30
forum: General Help
---

### Post by RobGoss on 2017-09-30
Hello everyone as you probably read in the title, I have a **64 bit** host machine but can only run a **32 bit** version of Ubuntu's ISO in  Virtual Box  on my Ubuntu desktop. There is not list for a 64 bit ISO in Virtual Box settings

Thanks for any help on this matter, Oh and I have VM setup of a few other machines but this one machine is the one that has this issue. All my machine are 64-bit

---

### Post by QIII on 2017-09-30
Hello!

Is VT-x or AMD-v (Intel or AMD, respectively) set in the BIOS?

---

### Post by RobGoss on 2017-09-30
> **QIII said:**
> Hello!

Is VT-x or AMD-v (Intel or AMD, respectively) set in the BIOS?


Hello QIII, not to sure this machine is a Dell Optiplex 755, I would have to check in the BIOS. On my other machines I did not have to change anything in the BIOS

I see something that says, **VT for direct I/O** in my BIOS would this be the setting you mean?

---

### Post by RobGoss on 2017-09-30
Thanks QIII I found **virtualization **in the BIOS and it was disabled so I just enabled it and I'm go to go. I  appreciate your time and efforts as always. I would mark this thread as solved

---

