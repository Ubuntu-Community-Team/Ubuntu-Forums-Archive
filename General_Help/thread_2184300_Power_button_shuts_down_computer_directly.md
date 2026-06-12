---
title: "Power button shuts down computer directly"
date: 2013-10-28
forum: General Help
---

### Post by josephellengar2 on 2013-10-28
On 13.10, pressing the power button shuts down my laptop directly instead of doing nothing or prompting me. It doesn't even give me the "are you sure?" dialog. It seems that many other people are having this problem, but I have already tried:

```

gsettings set org.gnome.settings-daemon.plugins.power button-WORD 'interactive'
[LEFT][COLOR=#333333][FONT=UbuntuRegular]where WORD is hibernate, power, sleep and suspend.
[/FONT][/COLOR][/LEFT]

```[LEFT][COLOR=#333333][FONT=UbuntuRegular]

and 
[/FONT][/COLOR]
[/LEFT]
```
[Login]
#NAutoVTs=6
#ReserveVT=6
#KillUserProcesses=no
#KillOnlyUsers=
#KillExcludeUsers=root
#Controllers=
#ResetControllers=cpu
#InhibitDelayMaxSec=5
#HandlePowerKey=poweroff
#HandleSuspendKey=suspend
#HandleHibernateKey=hibernate
#HandleLidSwitch=suspend
#PowerKeyIgnoreInhibited=no
#SuspendKeyIgnoreInhibited=no
#HibernateKeyIgnoreInhibited=no
#LidSwitchIgnoreInhibited=yes
#IdleAction=ignore
#IdleActionSec=30min
[LEFT][COLOR=#333333][FONT=UbuntuRegular]Uncomment the line that says #HandlePowerKey=poweroff and change the value to ignore.
[/FONT][/COLOR][/LEFT]

```[LEFT][COLOR=#333333][FONT=UbuntuRegular]

I have not yet tried to make an acpi handler because I am having other trouble with acpi anyway, but if you know an easy way to do that I'd love to hear. Any other suggestions?
[/FONT][/COLOR][/LEFT]

---

### Post by josephellengar2 on 2013-10-28
bump

---

### Post by josephellengar2 on 2013-10-29
bump

---

### Post by jspike397 on 2013-10-29
Hey, I have this problem as well on my AMD E2 based Sony Vaio.  Power settings in KDE on Kubuntu 13.10 says that it is supposed to ask what to do when I hit the power button.  What kind of specs do you have?

---

### Post by josephellengar2 on 2013-10-29
> **jspike397 said:**
> Hey, I have this problem as well on my AMD E2 based Sony Vaio.  Power settings in KDE on Kubuntu 13.10 says that it is supposed to ask what to do when I hit the power button.  What kind of specs do you have?

I'm on an HP Envy Touchsmart. It's Intel based i7 4900/12 GB RAM, Nvidia graphics. I also use the Cinnamon DE, not KDE.

---

### Post by mc4man on 2013-10-29
Well there was an extended time during 13.10 dev that the interactive option did not work, that's been resolved & is fine on Ubuntu default installs, (ubuntu session) & in a gnome session

So seems to be on Cinnamon so you should alter your thread title to reflect that (same for kde

---

### Post by josephellengar2 on 2013-10-29
> **mc4man said:**
> Well there was an extended time during 13.10 dev that the interactive option did not work, that's been resolved & is fine on Ubuntu default installs, (ubuntu session) & in a gnome session

So seems to be on Cinnamon so you should alter your thread title to reflect that (same for kde

Cinnamon is a fork of Gnome 3, and a very recent fork at that so most of the code is identical. It really is only a skin on top of Gnome 3. Do you have any idea where I might find the Launchpad record of this bug? It might be able to help me solve my problem.

---

### Post by mc4man on 2013-10-30
Yes & no - i had this one which I'll let expire, as you can see in comment 3 it was no longer an issue by sept 9 with  g-s-d ( 3.8.5-0ubuntu2
There were other issues but those are either now in separate reports or awaiting a few months in to 14.04

---

### Post by jspike397 on 2013-10-30
Well, obviously it cannot be only gnome's fault, as I am a KDE user and I have the bug as well on ubuntu 13.10.

---

### Post by mc4man on 2013-10-30
> **jspike397 said:**
> Well, obviously it cannot be only gnome's fault, as I am a KDE user and I have the bug as well on ubuntu 13.10.
There is no current fault with gnome or ubuntu, as far as kde not sure what they use for this
(in ubuntu it's handled thru g-s-d & additionally there is a ubuntu specific override in /usr/share/glib-2.0/schemas/10_ubuntu-settings.gschema.override

[org.gnome.settings-daemon.plugins.power]
button-power = 'interactive'

---

### Post by josephellengar2 on 2013-10-30
> **mc4man said:**
> There is no current fault with gnome or ubuntu, as far as kde not sure what they use for this
(in ubuntu it's handled thru g-s-d & additionally there is a ubuntu specific override in /usr/share/glib-2.0/schemas/10_ubuntu-settings.gschema.override

[org.gnome.settings-daemon.plugins.power]
button-power = 'interactive'

The override doesn't work. I've had it set that way for a while and it still turns off. :(

---

### Post by mc4man on 2013-10-31
> **josephellengar2 said:**
> The override doesn't work. I've had it set that way for a while and it still turns off. :(

That's for an ubuntu session & likely is more for setting up defaults in  a new user account. 

Both ubuntu & gnome have their own version of the 'interactive' window, can you 'summon' it in any fashion?, 
(does it exist?

Ex. here in ubuntu session, this will open the interactive screen, may also in gnome session, don't have one handy atm.
```
dbus-send --session --dest=org.gnome.SessionManager --type=method_call --print-reply --reply-timeout=2000 /org/gnome/SessionManager org.gnome.SessionManager.Shutdown
```

---

### Post by josephellengar2 on 2013-11-01
> **mc4man said:**
> That's for an ubuntu session & likely is more for setting up defaults in  a new user account. 

Both ubuntu & gnome have their own version of the 'interactive' window, can you 'summon' it in any fashion?, 
(does it exist?

Ex. here in ubuntu session, this will open the interactive screen, may also in gnome session, don't have one handy atm.
```
dbus-send --session --dest=org.gnome.SessionManager --type=method_call --print-reply --reply-timeout=2000 /org/gnome/SessionManager org.gnome.SessionManager.Shutdown
```

That summoned the window for me as well (Cinnamon, essentially identical to Gnome 3). Is there any way to tie that command to the power button?

---

### Post by josephellengar2 on 2013-11-06
bump.

---

