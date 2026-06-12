---
title: "Few (networking) problems"
date: 2005-10-15
forum: General Help
---

### Post by jounihat on 2005-10-15
The new Kubuntu has been almost perfect for my G4 iBook. I only have few complaints:

1) The installer should ask whether the user wants to use ntp for synchronizing the system clock. As a laptop user I almost always make an offline install, and after the installation is complete, Kubuntu throws me to the command line just because it couldn't sync the clock and thus messed up all the timestamps. Then I'll have to set the date and remove ntpdate from the init services manually. A bit irritating.

2) The new system settings program is great, but with 1024x768 resolution I can't see all the buttons at the bottom of certain windows (e.g. Network settings). I think there should be buttons for "Administrator mode", "Apply", "Cancel" or something like that, but I just can't see them, and I can't scale the windows big enough either.

3) I can't change the network settings. Every time I apply the new settings, I get a dialog "Restarting network. Please wait." And I may wait ten minutes without the dialog going away. There's a process called "perl" that takes 100% of my cpu cycles. If I kill it and close the dialog, I'm ok, but the network settings don't change. Any ideas to fix this problem?

Anyway, this far this new release looks great!

---

### Post by jounihat on 2005-10-15
Ok, I fixed the problem by editing /etc/network/interfaces. It's a workaround, though, not a real solution.

---

### Post by scsever on 2005-10-15
I have a problem with the Administrator Mode you mentioned in #2 and hope someone can help.  When I am presented with a configuration that needs Administrator Mode and I enter my sudo password I end up back at the same window that allows for Administrator Mode login. I can never get to the Admin window in any of the configuration settings.  This is the one and only sudo password on the system and works if I am doing sudo from a command line so I know the password is right.

---

### Post by knappen on 2005-10-16
[QUOTE=scsever]I have a problem with the Administrator Mode you mentioned in #2 and hope someone can help.  When I am presented with a configuration that needs Administrator Mode and I enter my sudo password I end up back at the same window that allows for Administrator Mode login. I can never get to the Admin window in any of the configuration settings.  This is the one and only sudo password on the system and works if I am doing sudo from a command line so I know the password is right.[/QUOTE]

Try:  kdesu kcontrol

---

### Post by githeko on 2005-12-03
[QUOTE=jounihat]Ok, I fixed the problem by editing /etc/network/interfaces. It's a workaround, though, not a real solution.[/QUOTE]

Great answer if only the system would allow me to save the file!!

I have read a lot of posts about the absence of a root password for Kubuntu.  My Kubuntu system demands a password and attempts to use "sudo" without  a password don't seem to impress the system.

What is the root passord for kubuntu?

I can open files like the 'interfaces'  quoted above but can't save.... I need help to understand the philosophy of a system that doesn't allow the owner to change anything on it..... or a way around the big steel gate.


How frustrating....

If my network could work, I would be pretty happy.  In my case, it can't resolve host names.  All I need is a way to configure my DNS server ip...

---

