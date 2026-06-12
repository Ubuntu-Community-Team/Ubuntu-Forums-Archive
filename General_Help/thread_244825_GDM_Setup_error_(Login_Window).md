---
title: "GDM Setup error (Login Window)"
date: 2006-08-27
forum: General Help
---

### Post by Dropknee on 2006-08-27
When I try to access the GDM via GUI (System-Administration-Login Window I got this error 

```
Could not access GDM configuration file.
```

any way to fix that???

---

### Post by Schalken on 2006-08-27
And yet when you restart you can login using GDM fine?

---

### Post by Dropknee on 2006-08-27
> **Schalken said:**
> And yet when you restart you can login using GDM fine?

Yes, I can log-in without any problem, but cant customize the GDM with the Login Window Option

---

### Post by Dinerty on 2006-08-27
> **Dropknee said:**
> Yes, I can log-in without any problem, but cant customize the GDM with the Login Window Option

how about if you

```
sudo gdmsetup
```

There you can play with the login window

---

### Post by kingborel on 2006-10-28
I have the same problem.

sudo gdmsetup still gives the same message

---

### Post by pgmario on 2006-10-29
Same thing here. Tried to change the permissions of the gdm configuration file to 755, but it still doesn't work.

---

### Post by gschoper on 2006-11-10
Any solutions to this issue? I've got it on edgy after installing the the 9625 nvidia drivers.

gschoper

---

### Post by gschoper on 2006-11-11
I was able to fix this issue on my system by restoring /etc/gdm/gdm.conf-custum which I had removed when I switched from xgl to aiglx and the new nvidia drivers.

gschoper

---

### Post by Rotarychainsaw on 2006-11-21
Restore it to what? Wasn't it basically empty before putting in the xgl stuff? I'm also having this problem.

---

### Post by gschoper on 2006-11-22
> **Rotarychainsaw said:**
> Restore it to what? Wasn't it basically empty before putting in the xgl stuff? I'm also having this problem.

Basically empty is not empty. It has default entries that apparently are needed (or at least the file needs to exist, don't know which). 

I restored it from a backup and removed the xgl entries bringing it back to it's pre-XGL state.

HTH,

gschoper

Here's a copy of my restored gdm.conf-custom:
```

# GDM Configuration Customization file.
#
# This file is the appropriate place for specifying your customizations to the
# GDM configuration.   If you run gdmsetup, it will automatically edit this
# file for you and will cause the daemon and any running GDM GUI programs to
# automatically update with the new configuration.  Not all configuration
# options are supported by gdmsetup, so to modify some values it may be
# necessary to modify this file directly by hand.
#
# Older versions of GDM used the "gdm.conf" file for configuration.  If your
# system has an old gdm.conf file on the system, it will be used instead of
# this file - so changes made to this file will not take effect.  Consider
# migrating your configuration to this file and removing the gdm.conf file.
#
# To hand-edit this file, simply add or modify the key=value combination in
# the appropriate section in the template below.  Refer to the comments in the
# /usr/share/gdm/defaults.conf file for information about each option.  Also
# refer to the reference documentation.
#
# If you hand edit a GDM configuration file, you should run the following
# command to get the GDM daemon to notice the change.  Any running GDM GUI
# programs will also be notified to update with the new configuration.
#
# gdmflexiserver --command="UPDATE_CONFIG <configuration key>"
#
# e.g, the "Enable" key in the "[debug]" section would be "debug/Enable".
#
# You can also run gdm-restart or gdm-safe-restart to cause GDM to restart and
# re-read the new configuration settings.  You can also restart GDM by sending
# a HUP or USR1 signal to the daemon.  HUP behaves like gdm-restart and causes
# any user session started by GDM to exit immediately while USR1 behaves like
# gdm-safe-restart and will wait until all users log out before restarting GDM.
#
# For full reference documentation see the gnome help browser under
# GNOME|System category.  You can also find the docs in HTML form on
# http://www.gnome.org/projects/gdm/
#
# NOTE: Lines that begin with "#" are considered comments.
#
# Have fun!

[daemon]

[security]

[xdmcp]

[gui]

[greeter]
GraphicalTheme=EarthLights
GraphicalThemedColor=#000000
DefaultWelcome=false
Welcome=Go Away!!!

[chooser]

[debug]

[servers]

```

---

### Post by Rotarychainsaw on 2006-11-23
Thanks!

---

### Post by benjaminmorris on 2007-04-16
Hi. I am having this same problem. My gdm.conf-custom doesn't look anything like yours, though. It has only a few lines and nothing to do with XGL. I am running Edgy with Beryl on XGL on Dell 6400 laptop with Radeon X1300 graphics card. I tried to change the screen directly in the gdm.conf file, but to no avail. Any help would be greatly appreciated.

---

### Post by gschoper on 2007-04-16
> **benjaminmorris said:**
> Hi. I am having this same problem. My gdm.conf-custom doesn't look anything like yours, though. It has only a few lines and nothing to do with XGL. I am running Edgy with Beryl on XGL on Dell 6400 laptop with Radeon X1300 graphics card. I tried to change the screen directly in the gdm.conf file, but to no avail. Any help would be greatly appreciated.

Do you have a backup of your gdm.conf? also, can you post the contents of your gdm.conf-custom?

gschoper

---

### Post by benjaminmorris on 2007-04-17
I was dumb enough to not make a backup before i manually edited it, but it still works the same, so I don't think there's a problem. Here's the contents of my gdm.conf-custom file:

[INDENT][daemon]
RemoteGreeter=/usr/lib/gdm/gdmgreeter

[security]
AllowRoot=true

[xdmcp]
Enable=false

[gui]

[greeter]
GraphicalThemedColor=#dbb183
GraphicalTheme=Ubuntu-CE-GDM *note: this was edited manually, originally I think it was *human* or something
SoundOnLogin=false
[/INDENT]

The first time i noticed this was when I installed kde via ```
sudo apt-get install kubuntu-desktop
```
That changed my login to i guess the default Kubuntu login which I don't like. When I tried to change it, it gives me the "Cannot connect to socket" and "Cannot access gdm configuration file" errors.

I then did```
sudo apt-get install xubuntu-desktop
``` to see if that would either fix the problem or at least put a different one on, but to no avail. Finally, I tried ```
sudo apt-get install ubuntu-desktop
``` to see if that would fix anything, but it didn't.

One final note is that when I logged into kde, i was able to open the login manager. It gives me the list of login screens to choose from, and i chose the ubuntu CE login. What's interesting is that the kubuntu screen is NOT an option. It's not even on the list, but IT'S STILL BEING USED.

I'm totally confused by all this. Any ideas?

---

### Post by gschoper on 2007-04-17
> **benjaminmorris said:**
> I was dumb enough to not make a backup before i manually edited it, but it still works the same, so I don't think there's a problem. Here's the contents of my gdm.conf-custom file:

[INDENT][daemon]
RemoteGreeter=/usr/lib/gdm/gdmgreeter

[security]
AllowRoot=true

[xdmcp]
Enable=false

[gui]

[greeter]
GraphicalThemedColor=#dbb183
GraphicalTheme=Ubuntu-CE-GDM *note: this was edited manually, originally I think it was *human* or something
SoundOnLogin=false
[/INDENT]

The first time i noticed this was when I installed kde via ```
sudo apt-get install kubuntu-desktop
```
That changed my login to i guess the default Kubuntu login which I don't like. When I tried to change it, it gives me the "Cannot connect to socket" and "Cannot access gdm configuration file" errors.

I then did```
sudo apt-get install xubuntu-desktop
``` to see if that would either fix the problem or at least put a different one on, but to no avail. Finally, I tried ```
sudo apt-get install ubuntu-desktop
``` to see if that would fix anything, but it didn't.

One final note is that when I logged into kde, i was able to open the login manager. It gives me the list of login screens to choose from, and i chose the ubuntu CE login. What's interesting is that the kubuntu screen is NOT an option. It's not even on the list, but IT'S STILL BEING USED.

I'm totally confused by all this. Any ideas?

As soon as you mentioned KDE and Kubuntu, you lost me. I have no idea how their desktop login process works as I am strictly a Gnome user. I don't even know if KDE uses GDM for handling logins.

Sorry I couldn't be of more help,

gschoper

---

### Post by linuxhelp on 2007-08-10
Go to 

/etc/rc2/ and rename @13gdm to @21gdm

that gdm is started later, it seems that it is a bug ,

in use with "startup" technics instead of older sysinit (if think the older system is better)

i have had same problems after i setup on ubuntu the complete xubuntu-desktop

at first i was thinking about internal network (127.XXX) problems

I hope it helps please post feedback

>> NEVER change a running system, Ubuntu makes the same Errors as M$ everything NEW but not Stable enough!! <<

Tom
Germany
[www.linuxonlinehelp.de](www.linuxonlinehelp.de)

---

