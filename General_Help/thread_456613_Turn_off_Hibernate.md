---
title: "Turn off Hibernate"
date: 2007-05-27
forum: General Help
---

### Post by udz2002 on 2007-05-27
When I am logged in to Ubuntu remotely from WinXP my Ubuntu PC will hibernate after so many minutes. I have sleep and hibernation shut off under power management. I have Ubuntu 7.04 Feisty Fawn, Any ideas?

---

### Post by energiya on 2007-05-28
A nasty work-around would be (only in the case you don't use hibernate) to rename the hibernate script :) and touch it.

---

### Post by udz2002 on 2007-05-28
I am an Ubuntu newbie. Please explain. I just want to be able to log in remotely without the computer hibernating on me. I have no intention of using the hibernation feature.

---

### Post by energiya on 2007-05-28
The thing is I don't have easy acces to a Ubuntu machine, but you could post the output of
```

whereis hibernate

```
so that I can see in relative paths what to do (or see if I can help you)

---

### Post by udz2002 on 2007-05-30
When I type that it prints...

Hibernate:

---

### Post by loathsome on 2007-05-30
I think it's located under /etc/acpi -  so the full path would be:

[COLOR="Red"]**/etc/acpi/hibernate.sh**[/COLOR]

---

### Post by energiya on 2007-05-30
> **loathsome said:**
> I think it's located under /etc/acpi -  so the full path would be:

[COLOR="Red"]**/etc/acpi/hibernate.sh**[/COLOR]

If thats true try
```

sudo mv /etc/acpi/hibernate.sh /etc/acpi/hibernate.sh.bak
sudo chmod -x /etc/acpi/hibernate.sh.bak
sudo touch /etc/acpi/hibernate.sh

```

To undo just
```

sudo mv /etc/acpi/hibernate.sh.bak /etc/acpi/hibernate.sh
sudo chmod +x /etc/acpi/hibernate.sh

```

Never tryed something like this, but should in theory work wiyhout any problems (thats why I will have to put a "use at your own risk"). If anything goes bad just folow the undo steps and you should be fine.

Hope this helps !

---

### Post by udz2002 on 2007-05-31
I tried that. I also changed...

/apps/gnome-power-manager/action_ac_sleep_type to **nothing**

/apps/gnome-power-manager/ac_sleep_computer to **0**

/apps/gnome-power-manager/ac_dpms_sleep_method **off**

...and nothing, the computer still suspends after being idle for 20 mins or so. My issue is that I use this computer as a juke box and log in remotely. For some reason the computer does not recognize the remote connection as being *active* and suspends it's self. When hooked to a keyboard and mouse, I do not have this problem.

I need to completely remove suspend/sleep/hibernate abilities
or
make the computer recognize the remote keyboard and mouse as being active.

---

