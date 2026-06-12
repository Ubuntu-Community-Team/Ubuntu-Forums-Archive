---
title: "xfce-power-manager don't start automatically"
date: 2022-01-03
forum: General Help
---

### Post by darwall on 2022-01-03
Hi Ubuntu friends! I use a laptop as a desktop computer with Lubuntu 20.04 and an external monitor connected and the lid closed on the laptop.
But every time I turn on the computer, the internal LCD screen on the laptop is on, and I have to go into display settings and turn it off.
You can select save, but it still does not save the setting.
If I go into power-manager settings, there is a setting that the monitor should turn off when the lid is closed. But the problem is that xfce4-power-manager do not start automatically.
Does anyone have any tips?
Thanks in advance 
Sven Darwall

---

### Post by KBar on 2022-01-03
Hi and welcome back.

Check if *xfce4-power-manager* is set to autostart. You should have an app called *Session and Startup*.

---

### Post by darwall on 2022-01-03
Hi KBar
Thanks to your tip, I have been able to set so that the fxce power manager starts automatically.
But unfortunately it did not solve the main problem I had hoped for.
It's so annoying that every time I turn on the computer I have to go into display settings and turn off the laptop's built-in 13 "LCD monitor. I press apply and then save,
But the next time I start the computer, the computer has completely ignored my "save" command,
and I have to repeat the same procedure again.
Do you possibly have any more tips
Regards Sven Darwall

---

### Post by guiverc on 2022-01-03
Why are you using Xfce4-power manager?

Lubuntu is LXQt based and uses `[lxqt-powermanagment]("https://packages.ubuntu.com/focal/lxqt-powermanagement")`

Refer
- [https://manual.lubuntu.me/lts/3/3.2/3.2.12/power_management.html?highlight=power](https://manual.lubuntu.me/lts/3/3.2/3.2.12/power_management.html?highlight=power)
- [https://cdimage.ubuntu.com/lubuntu/releases/20.04.3/release/lubuntu-20.04.3-desktop-amd64.manifest](https://cdimage.ubuntu.com/lubuntu/releases/20.04.3/release/lubuntu-20.04.3-desktop-amd64.manifest)

If you were using a 18.04 or older system with LXDE and upgraded; problems were to be expected, which is why [release notes]("https://lubuntu.me/focal-2-released/") said

> ***Note***, due to the extensive changes required  for the shift in desktop environments, the Lubuntu team does not support  upgrading from 18.04 or below to any greater release. Doing so will  result in a broken system. If you are on 18.04 or below and would like  to upgrade, please do a fresh install.

Xfce4-power-manager hasn't been used since [18.04 or LXDE]("https://packages.ubuntu.com/bionic/lubuntu-desktop") so shouldn't exist on a *modern *Lubuntu system as it's not used.  Lubuntu is LXQt & Qt5 now.

---

### Post by darwall on 2022-01-04
Thanks for your reply guiverc!
I wanted to use xfce-power-manager because I found a setting where you can set that built-in monitor to turn off when the lid is lowered on the laptop.
This problem started when I updated from Lubuntu 18.04 to 20.04
Before that, it worked perfectly.
But maybe there is a better way to make sure the monitor does not work when the lid is down?

---

### Post by guiverc on 2022-01-04
The warning on upgrading a 18.04/LXDE system to a later LXQt system was there for a reason; you've just found one issue, and there could be many.

Lubuntu doesn't support the upgrade because the problem vary on

- what packages were installed (esp. *manually installed*) on your system, what if any were removed etc
- what changes you made to configs (esp. on packages that would be removed; such as `[xfce4-power-manager]("https://packages.ubuntu.com/bionic/xfce4-power-manager")`) and other changes users had made
- unforeseen potential problems due to 3rd party packages added (*we couldn't predict*)
- and more.

The system I'm using now is a *release-upgraded* LXDE system, but it took me ~three weeks to get the system to what I considered *stable* and *problem free*. Those three weeks weren't *fun* (*and note I'm not saying it was three weeks worth of work to get it right; I would just use other boxes to do what I needed to & work on this when I had time..*).

The release notes said do a *fresh* install; myself I didn't do that and on most boxes I just re-installed without format, meaning any global changes (*in system directories*) got erased prior to install (ie. a *'[install using existing partition]("https://discourse.lubuntu.me/t/testing-checklist-understanding-the-testcases/2743")*' in Lubuntu terms, though I prefer '*upgrade via re-install*', but my user configs, files were untouched, and my *manually installed* packages were re-installed automatically. Sure I reviewed the system & manually removed any packages I felt would give me problems with this install method to ensure a clean re-install, but the re-install using this method is far faster than any `do-release-upgrade`.  I consider this an **unclean**install, and whilst it's possible some problems may survive the install (due to install method's re-install of *manually installed* packages if users fixed issues using for example `install --re-install` thus changed an *auto-installed* package flag to *manually installed*) I found it very reliable in my own QA-testing.

You were warned of breakage, and you've discovered one so far. There may be more.

Either way, your system is unsupported by Lubuntu due to the 18.04/LXDE to 20.04/LXQt upgrade, and not via re-install (where you'd have no `[xfce4-power-manager]("https://packages.ubuntu.com/focal/xfce4-power-manager")`)

---

