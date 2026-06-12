---
title: "error message with package installer"
date: 2007-07-22
forum: General Help
---

### Post by wolfgang959 on 2007-07-22
hi i was trying to install virtual box on a Ubuntu 7.04 Feisty Fawn computer.

it download fine and then i tried to install it using *package installer* so i click install enter the admin password and then it says to close all other applications like 'synaptic','update manager','aptitude'. 

i have attached a screen shot of the message as well.

thanks :)

---

### Post by happy-and-lost on 2007-07-22
Try *sudo killall update-manager* before running the package installer

---

### Post by wolfgang959 on 2007-07-22
thanks happy and lost but it still doesn't work:confused:

its says no processes were killed i tried it for all of them
synaptic
aptitude
and update-manager

---

### Post by happy-and-lost on 2007-07-22
Strange. There must be a problem with the lockfile. Rebooting usually clears that up.

---

### Post by wolfgang959 on 2007-07-22
it has now come up with this message.

Same version is available in a software channel

You are recommended to install the software from the channel instead.

what does it mean.

well i clicked ok then the same error came up again.

---

