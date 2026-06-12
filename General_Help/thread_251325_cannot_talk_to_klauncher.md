---
title: "cannot talk to klauncher"
date: 2006-09-05
forum: General Help
---

### Post by Carol1976 on 2006-09-05
I'm running kubuntu 6.06 LTS (?)

I tried to enter Konqueror via sudo in Konsole so that I could place two files in a root folder,

ie I typed: sudo konqueror

I got the following error:

```

carol@carol-desktop:~$ sudo konqueror
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
ScimInputContextPlugin()
konqueror: ERROR: : couldn't create slave : Cannot talk to klauncher
konqueror: ERROR: : couldn't create slave : Cannot talk to klauncher
konqueror: ERROR: : couldn't create slave : Cannot talk to klauncher
konqueror: ERROR: : couldn't create slave : Cannot talk to klauncher
konqueror: ERROR: : couldn't create slave : Cannot talk to klauncher
konqueror: ERROR: : couldn't create slave : Cannot talk to klauncher
konqueror: ERROR: : couldn't create slave : Cannot talk to klauncher
konqueror: ERROR: : couldn't create slave : Cannot talk to klauncher
konqueror: ERROR: : couldn't create slave : Cannot talk to klauncher
~ScimInputContextPlugin()
carol@carol-desktop:~$
```

Any ideas?

I then tried kdesu konqueror instead after someone on the kubuntu forum said I shouldn't be using sudo to open GUI/Graphical stuff... but I got EXACTLY the same error.

I'm so lost and really need some help on what I might have broken? (ask _simon_ he'll tell you about my "pc go slow" and "break pc" buttons)

PS. It worked absolutely fine when I was dual booting with UBUNTU installed, it has only stopped working since I re-installed to Kubuntu only :(

---

### Post by PriceChild on 2006-09-05
I'm using GNOME with amarok and quite a few kde libraries installed.

I got the error randomly today, decided to reboot and all was fine!

---

### Post by Carol1976 on 2006-09-05
nah I've rebooted more times than I've had a drink today, still to no avail.

:(

Someone on Kubuntu forums suggested that it might be the resources.list or somet (repositries) causing a problem as it happened since I auto installed automatix and allowed it to write over the existing repositries list.

BUT I don't know how to fix that :(

---

### Post by Carol1976 on 2006-09-07
this can now be closed, after NUMEROUS re-installs and fixes that people were telling me to do, it STILL kept breaking on me, so now I've re-installed ubuntu and left kubuntu behind.

---

### Post by giuseppe.dem on 2007-03-24
I still have this problem in Ubuntu 6.0, gnome.
I installed kate, and I&#12288;cannot use any dialog of kde, like File Browsing and Saving.

The problem with Linux is that, even if you can solve one problem,
after a while another problem, related with the previous one, comes out.
Regards
G:(

---

### Post by Steve H on 2007-04-22
I´ve now started getting the same error. I get it with K3b and Ktorrent, even though i have all the KDE files needed for running under Gnome. This all started with the Feisty update. I haven´t managed to find any good reason this has failed.

---

### Post by Steve H on 2007-04-22
I´ve finally managed to get this sorted.

After a lot of testing (and trial and error), I tracked this error down to the ¨kdeinit¨ module, not starting properly. It controls the ¨klauncher¨ process, so without one the other can function.

My remedy was to uninstall ALL my KDE apps through Synaptic,(including all dependencies) and then reinstall them again. As you reinstall the KDE apps, it will rebuild all the KDE dependencies that these apps require and so solve the ¨kdeinit¨ problem.

Hope this helps.

---

### Post by kodoku on 2007-04-29
an easier way is just to type kdeinit in the terminal, and then try running your kde apps again =)

---

### Post by Steve H on 2007-04-30
I did try that, because that was how i worked out it was kdeinit that was failing. However i didn't want to spend my time constantly (well, after every reboot) starting kdeinit by hand, when spending 10mins reinstalling everything has solved the problem for good.....I know it is not a big deal, but it would bug me none the less.

:)

---

### Post by k7k0 on 2007-04-30
What about adding kinit to the initial session's programs?

---

### Post by Steve H on 2007-05-01
I did try adding to session startup programs but it still was failing....don't ask me why?! It only seemed to work if i called it from a terminal. I presumed it might have something to do with needing other progs that hadn't started during the session startup. But that is only a guess.

It is all fixed now, BTW. But I appreciate your thoughts, and your help.

:)

---

### Post by arijarot on 2007-05-24
> **kodoku said:**
> an easier way is just to type kdeinit in the terminal, and then try running your kde apps again =)

I closed all my KDE apps and typed kdeinit into the terminal and it worked! No more error! Thanks, kodoku:)

---

### Post by Cresho on 2007-05-30
install kdevelop in synaptic.  It fixed my klauncher issues.

---

### Post by Technobabel on 2007-06-03
Hi,

open a terminal and user kdeinit_shutdown & then kdeinit to restart it. Afterwards my prob with Amarok was fixed.

CU
Chris

---

### Post by seagull theme on 2007-06-13
> **Technobabel said:**
> Hi,

open a terminal and user kdeinit_shutdown & then kdeinit to restart it. Afterwards my prob with Amarok was fixed.

CU
Chris

This solved my problems with Amarok. Thank you :)

---

### Post by ububaba on 2007-07-22
> **Cresho said:**
> install kdevelop in synaptic.  It fixed my klauncher issues.

This helped my problem with Ktorrent. Thanks

---

### Post by taavi on 2007-11-22
My problem was solved by running these commands:

$ kdeinit_shutdown
$ dcopserver_shutdown

---

