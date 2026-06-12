---
title: "Firestarter and Gutsy"
date: 2007-10-20
forum: General Help
---

### Post by sefs on 2007-10-20
Has ubuntu now linked firestarter to itself more intricately.  I noticed some strange behaviour that i have never seen before.

1) restarting the network also restarts firestarter

2) firestart tool try icon sometimes disappears etc.

3) it seems to me that now somehow there is a deeper integration with firestarter and gutsy?

---

### Post by ruibernardo on 2007-10-20
You are right.

Before, if you restarted the network and Firestarter, it would say that the network device was not ready and didn't start. By taking a look at the [changelog of Firestarter in Gutsy]("http://changelogs.ubuntu.com/changelogs/pool/universe/f/firestarter/firestarter_1.0.3-6ubuntu1/changelog"), you can see that now Firestarter is restarted with the network devices (network manager and if-up) to avoid problems.

---

### Post by pwk on 2007-10-20
Re the disappearing tray icon.

Are you sure Firestarter isn't crashing entirely in Gutsy? I had the Firestarter GUI open several times and when it disappeared (as it usually does) I checked for it with ps and there was no Firestarter running.

---

### Post by ruibernardo on 2007-10-21
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/148418](https://bugs.launchpad.net/ubuntu/+bug/148418) [br].[/br] ---------------------------- [br].[/br] [br].[/br]                 I've seen that happening. 

Firestarer starts normally, but after a while (or some changing in the settings/rules) it vanishes. I think it's just the GUI - the firestarter window and icon in the pane)l.

Iptables rules are set on boot and when you change or create a rule in Firestarter, the changes in rules are only applied, iptables isn't cleared and start over again, it's just a new rule that is applied when you change/create the rule.

So it's my believe that this "disappearing" is just a graphical matter, running Firestarter from the menu starts the GUI again, no harm done (but a boring one, for those who use it). 

Check [https://launchpad.net](https://launchpad.net) for more info about bugs (and maybe this one about this subject: [https://bugs.launchpad.net/ubuntu/+bug/148418](https://bugs.launchpad.net/ubuntu/+bug/148418)).

---

### Post by ckwright@allmail.net on 2007-12-22
Firestarter isn't just disappearing on me - its crashing with a segmentation fault! I have firestarter 1.0.3 and the kernel is Linux toshiba 2.6.22-14-generic. I am thinking that rebuilding firestarter from source to eliminate the possibility of a mismatch between the kernel I have and the code for firestarter supplied through Ubuntu. Has any one else noticed similar problems?

---

### Post by ckwright@allmail.net on 2007-12-22
Firestarter isn't just disappearing on me - its crashing with a segmentation fault! I have firestarter 1.0.3 and the kernel is Linux toshiba 2.6.22-14-generic. I am thinking that rebuilding firestarter from source to eliminate the possibility of a mismatch between the kernel I have and the code for firestarter supplied through Ubuntu. Has any one else noticed similar problems?

---

