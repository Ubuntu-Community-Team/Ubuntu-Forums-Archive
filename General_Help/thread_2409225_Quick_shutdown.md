---
title: "Quick shutdown"
date: 2018-12-29
forum: General Help
---

### Post by BusaDave9 on 2018-12-29
My computer is running Ubuntu 18. I'd like to shut it down by simply pressing the power button but I don't want a confirmation dialog box.
I've researched a few options but can't get this to work.  Some say I should be able to do this with dconf-editor. I am told I should be able to go under apps > indicator-session and select suppress_logout_restart_shutdown
I don't have that option. I have very few options. Under apps I only have seahorse and update-manager. I have also tried starting it with the command "sudo dconf-editor".
What am I doing wrong?

FYI the reason I want to do this is because this is my "entertainment computer". I use it to play videos and music. After starting it up I set the mouse and keyboard aside. When I want to shut it down I want to just press the power button without getting out the keyboard and mouse again.

---

### Post by TheFu on 2018-12-29
I don't have any 2017 or 2018 systems.  16.04 only here still to avoid issues.  On 16.04, /etc/systemd/logind.conf has settings to control what the power button does.  The manpage for this file will have many more details. It can be seen by running **man -s 5 logind.conf**.  Your system manpage is probably different from others, so it is best to always check manpages on your specific machine.

Why not tie the remote control power button to the "**/sbin/shutdown -h now**" command?   BTW, Kodi does this.  You can use the sudoers file to allow any userid to run that command with those exact options.

I've never tried to use sudo with dconf-editor. Seems like an un-needed effort at best and may cause problems at worse. Using sudo on files that are stored per-userid is a bad idea almost always. The dconf DB is per-userid. Also, it doesn't apply with all variants of Ubuntu, though it probably is used by the most popular versions running popular DEs.

---

### Post by vidtek on 2018-12-30
> **BusaDave9 said:**
> My computer is running Ubuntu 18. I'd like to shut it down by simply pressing the power button but I don't want a confirmation dialog box.
I've researched a few options but can't get this to work.  Some say I should be able to do this with dconf-editor. I am told I should be able to go under apps > indicator-session and select suppress_logout_restart_shutdown
I don't have that option. I have very few options. Under apps I only have seahorse and update-manager. I have also tried starting it with the command "sudo dconf-editor".
What am I doing wrong?

FYI the reason I want to do this is because this is my "entertainment computer". I use it to play videos and music. After starting it up I set the mouse and keyboard aside. When I want to shut it down I want to just press the power button without getting out the keyboard and mouse again.

Dave-
I am running Kubuntu as my HTPC using Mythtv and have mapped an infra-red key to my harmony remote to automatically log-off the machine when I go to bed ( Mythtv takes care of poweroff after all recordings finish overnight which is why I have to just log off).  The command you would need to use is this one for poweroff```
/sbin/systemctl poweroff
``` 
/sbin might not be the location for the systemctl file in your distro, check /bin and /usr/bin and /usr/sbin to find it.
Cheers, Tony.

---

### Post by BusaDave9 on 2018-12-30
Thanks. I looked at the man pages for logind.conf.  I tried:
HandlePowerKey=poweroff
I am still asked to confirm the shutdown. 
The options can be "ignore", "poweroff", "reboot", "halt", "kexec", "suspend", "hibernate", "hybrid-sleep", "suspend-then-hibernate", and "lock".
Unfortunately I can't use a command like "/sbin/shutdown -h now"

---

### Post by vidtek on 2018-12-30
> **BusaDave9 said:**
> Thanks. I looked at the man pages for logind.conf.  I tried:
HandlePowerKey=poweroff
I am still asked to confirm the shutdown. 
The options can be "ignore", "poweroff", "reboot", "halt", "kexec", "suspend", "hibernate", "hybrid-sleep", "suspend-then-hibernate", and "lock".
Unfortunately I can't use a command like "/sbin/shutdown -h now"

Dave-

You don't say what flavour of Ubuntu you are using.  What desktop environment if any?
It's helpful for all if you put what your machine is and what flavour it is using in your signature.  That way you
won't get replies which have no relevance to you and you don't waste other respondent's time.

Tony.

---

### Post by TheFu on 2018-12-30
> **BusaDave9 said:**
> Thanks. I looked at the man pages for logind.conf.  I tried:
HandlePowerKey=poweroff
I am still asked to confirm the shutdown. 
The options can be "ignore", "poweroff", "reboot", "halt", "kexec", "suspend", "hibernate", "hybrid-sleep", "suspend-then-hibernate", and "lock".
Unfortunately I can't use a command like "/sbin/shutdown -h now"

Did you remember to **sudo systemctl restart systemd-logind**?

If you have a remote control, pretty much any key can be mapped to do any command.
On my media center, that's what I do.

Different DEs will have different methods to request a shutdown.  For gnome-based DEs, I'd guess that editing settings for the userid via dconf is necessary or making a request like **gnome-session-quit --no-prompt --power-off**. I don't use DEs, so can't test it.

[https://manpages.ubuntu.com/manpages/cosmic/man1/gnome-session-quit.1.html](https://manpages.ubuntu.com/manpages/cosmic/man1/gnome-session-quit.1.html)

---

### Post by ajgreeny on 2018-12-30
I have been using a keyboard shortcut to carry out an immediate shutdown (or suspend) for several years now.

I use Xubuntu and in 14.04, 16.04 and 18.04 the following commands both work with no confirmation request seen.
***xfce4-session-logout --halt*** or ***shutdown -h now*** for complete power-off.
***xfce4-session-logout --suspend*** to suspend.

Both are linked to the Pause/Break key, plus the Winkey for shutdown and without Winkey for suspend.

I imagine other DEs have a similar command available for suspend/shutdown but I do not know what they are at present; no doubt others will tell us if they know.

---

### Post by BusaDave9 on 2018-12-31
> **vidtek said:**
> Dave-

You don't say what flavour of Ubuntu you are using.  What desktop environment if any?
Tony.

I am running GNOME


> **TheFu said:**
> Did you remember to **sudo systemctl restart systemd-logind**?

I tried that but I am still asked to confirm the shutdown. 


> **ajgreeny said:**
> I have been using a keyboard shortcut to carry  out an immediate shutdown (or suspend) for several years now.

Thanks but I'm hoping to do this without my keyboard or mouse.  I start up my computer and get the music playing. Then I put my keyboard and mouse under my end table.  It would be nice to use the power button. It's right on the top of my PC. If I have to get out my keyboard I might as well confirm the shutdown. A keyboard shortcut won't help much. If I can't get the power button to shutdown without a confirmation I will try a keyboard shortcut

---

### Post by vidtek on 2019-01-01
> **BusaDave9 said:**
> I am running GNOME




I tried that but I am still asked to confirm the shutdown. 




Thanks but I'm hoping to do this without my keyboard or mouse.  I start up my computer and get the music playing. Then I put my keyboard and mouse under my end table.  It would be nice to use the power button. It's right on the top of my PC. If I have to get out my keyboard I might as well confirm the shutdown. A keyboard shortcut won't help much. If I can't get the power button to shutdown without a confirmation I will try a keyboard shortcut

Dave-
With Kubuntu I can shut the machine down with no prompts just by pressing the power button on the machine.  It is configurable within the KDE DE System-Settings.
If you can't find an equivalent setting in Gnome then maybe you should switch to KDE.
Tony

---

### Post by TheFu on 2019-01-01
Which version of gnome?

---

### Post by BusaDave9 on 2019-01-01
> **TheFu said:**
> Which version of gnome?

how can I tell?

---

