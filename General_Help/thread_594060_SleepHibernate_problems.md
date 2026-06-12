---
title: "Sleep/Hibernate problems"
date: 2007-10-27
forum: General Help
---

### Post by soccerboy on 2007-10-27
I have been having problems with power management putting my computer to sleep or hibernate.  My network manager crashes afterwards and I have to reboot my computer to get gutsy functional again.  anyone know a good fix.

---

### Post by chameleonkid on 2007-10-27
Nearly having the same problems. Sleep worked in Feisty and not hibernate. The problem seems to have reversed itself in Gutsy. Did you upgrade via the internet, cd, or just a clean install right off the bat?

I am sure there are a lot of power management problems for people, but the lack of updates troubles me.

---

### Post by soccerboy on 2007-10-27
i did a clean install to gutsy from feisty.

---

### Post by ddrichardson on 2007-10-27
> **soccerboy said:**
> I have been having problems with power management putting my computer to sleep or hibernate.  My network manager crashes afterwards and I have to reboot my computer to get gutsy functional again.  anyone know a good fix.For me, turning off networking before suspend works.```
sudo vi /etc/default/acpi-support
```Change the line that reads:```
STOP_SERVICES=""
```To```
STOP_SERVICES="networking"
```Worked for me and I've had a hell of a job getting suspend and hibernate to work properly.

---

### Post by chameleonkid on 2007-10-27
Another option provided by sunspots in a different thread: [http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/](http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/)

Although I haven't tried it, I would back up these files before hand.

---

### Post by soccerboy on 2007-10-27
> **ddrichardson said:**
> For me, turning off networking before suspend works.```
sudo vi /etc/default/acpi-support
```Change the line that reads:```
STOP_SERVICES=""
```To```
STOP_SERVICES="networking"
```Worked for me and I've had a hell of a job getting suspend and hibernate to work properly.

This method causes the network manager to break on my installation.

---

### Post by soccerboy on 2007-10-27
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/157916](https://bugs.launchpad.net/ubuntu/+bug/157916) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				bug reported at [https://bugs.launchpad.net/ubuntu/+bug/157916](https://bugs.launchpad.net/ubuntu/+bug/157916).

You guys should post your descriptions of the problem.  Maybe that'll attract more attention to the problem.

---

### Post by protenniser on 2007-11-01
> **ddrichardson said:**
> For me, turning off networking before suspend works.```
sudo vi /etc/default/acpi-support
```Change the line that reads:```
STOP_SERVICES=""
```To```
STOP_SERVICES="networking"
```Worked for me and I've had a hell of a job getting suspend and hibernate to work properly.

Hi ddrichardson,

Thanks for this elegant solution for the one of the most annoying problems that come with gutsy. However I have a question, by using a similar code you have used to rerun network, can we also rerun the power management in gutsy? Because when I hibernate my computer let's say on AC power, it remembers the last state I hibernated it (AC power) and although I do open it without it is plugged in, it doesn't switch to battery power and I can't switch without a restart. This is quite annoying especially my battery is not very good so I really do need the extra time that comes from screen brightness etc. 
If you can provide me how to rerun power management after each hibernation, I will be glad.

Thanks again, regards...

---

### Post by ddrichardson on 2007-11-01
I'm afraid networking is my thing, what I know about power management could be written in crayon on a postage stamp. Your best course of action is to report it as a bug [here]("https://bugs.launchpad.net/gnome-power/+filebug"). I believe this bug was fixed in 2.19.1 kernel but might have resurfaced as we are now on 2.6.22.

---

### Post by ddrichardson on 2007-11-01
Infact you probably could, but you'd need a new script in /etc/init.d.

---

### Post by protenniser on 2007-11-01
Hi,

Could you provide that script? (Of course if it is not  a lot of work) I haven't tried writing any scripts yet.

Thanks...

---

### Post by ddrichardson on 2007-11-01
I really don't have time to write one at the moment sorry, have you checked out launchpad for the bug reports? Someone may already have solved this issue - if not I can spend a bit of time on it this weekend.

---

### Post by protenniser on 2007-11-01
Hi again,

I have reported the bug. If you have spare time at the weekend to write the script I will be glad. Thanks for all the help.

Regards...

---

