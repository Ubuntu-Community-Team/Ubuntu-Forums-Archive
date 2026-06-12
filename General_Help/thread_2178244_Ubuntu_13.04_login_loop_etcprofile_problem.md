---
title: "Ubuntu 13.04 login loop /etc/profile problem"
date: 2013-10-02
forum: General Help
---

### Post by michiel-reenaers on 2013-10-02
Hey

This morning when I tried to loggin I suddenly couldn't login into any of my accounts on my ubuntu.

When I went into console (ctrl-alt-f1) I stumbled accross an error message after login stating:

-bash: /etc/profile: line 1: syntax error near unexpected token '('
-bash: /etc/profile: line 1: '\nn# /etc/profile: system-wide .profile file for the Bourne shell (sh(1))n# and Bourne compatible shells (bash(1), ksh(1), ash(1), ...).nnif [ "$PS1" ]; thennif [ "$BASH" ] && [ "$BASH" != "/bin/sh"]; thenn# the file bash.bashrc already sets the default PS1.n# PS1=h:w$ nif [-f /etc/bash.bashrc ]; thenn. /etc/bash.bashrcnfinelsenif [ "'id -u'" -eq 0 ]; thennPS1=# nelsenPS1=# nfinfinfinn# The default umask is now handled by pam_umask.n# See pam_u mask(8) and /etc/login.defs.nnif [-d /etc/profile.d ]; thennfor i in /etc/profile.d/*.sh; donif [ -r $i ]; thenn. $infindonenunset infinPT5HOME=/usr/local/PacketTracer5nexport PT5HOME\nPT5HOME=/usr/local/PacketTracer5\nexport PT5HOME' 

(remember that this was not copied but written, I couldn't copy from my console to my second pc, therefor small mistakes could have been made)

What I can make out of it, given my limited knowledge, is that PacketTracer is the problem. Yesterday I installed it for my school. It could be that it caused an irregularity. 

I do not know why PacketTracer would change my /etc/profile. 

For the rest I do not know what happened

Following you can find the 2 commands used to install packettracer. 

1) download packettracer file from internet
2) cd /Downloads
3) sudo sh PacketTracer533_i386_installer-deb.bin
4) sudo -i 
5) ./PacketTracer533_i386_installer-deb.bin

My specs are: 
AsusN75 series
GEFORCE GT 630 2GB
I7 2670QM

What I already tried: 
restarting lightdm
reconfiguring lightdm and dpg
reinstalling gnome 
shutting down/reconfiguring/restarting compizconfig-settings-manager

---

### Post by steeldriver on 2013-10-02
It looks like you edited /etc/profile in an external editor (possibly a Windows editor?) and messed up all the newlines - up to the new stuff you added, it should look like

```
# /etc/profile: system-wide .profile file for the Bourne shell (sh(1))
# and Bourne compatible shells (bash(1), ksh(1), ash(1), ...).

if [ "$PS1" ]; then
  if [ "$BASH" ] && [ "$BASH" != "/bin/sh" ]; then
    # The file bash.bashrc already sets the default PS1.
    # PS1='\h:\w\$ '
    if [ -f /etc/bash.bashrc ]; then
      . /etc/bash.bashrc
    fi
  else
    if [ "`id -u`" -eq 0 ]; then
      PS1='# '
    else
      PS1='$ '
    fi
  fi
fi

# The default umask is now handled by pam_umask.
# See pam_umask(8) and /etc/login.defs.

if [ -d /etc/profile.d ]; then
  for i in /etc/profile.d/*.sh; do
    if [ -r $i ]; then
      . $i
    fi
  done
  unset i
fi
```

---

### Post by papibe on 2013-10-02
Hi michiel-reenaers.

I can't help you with PacketTracer, but if you want to recover your profile file as it was, you can get it by running:
```
sudo cp /usr/share/base-files/profile /etc/profile
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by michiel-reenaers on 2013-10-02
> **papibe said:**
> Hi michiel-reenaers.

I can't help you with PacketTracer, but if you want to recover your profile file as it was, you can get it by running:
```
sudo cp /usr/share/base-files/profile /etc/profile
```
Hope it helps. Let us know how it goes.
Regards.

Ok I did what you suggested but now once it boots it just shows a black screen with an blue stripe with date and hour.
I don't know if it's because I copied the usr/share/base-files/profile or because of my previous commands. 
Underneeth you can find a list of all the commands I ran in order to try and resque my system. 

compiz --replace ccp &
setsid unity
compiz --replace ccp & (tried it again)
chown michiel:michiel .Xauthority
ls -lah
ls -ld /tmp
dpkg-reconfigure lightdm (first pressed lightdm in the menu then tried dpg an reverted back to lightdm when that didn't work)
and of course: 
sudo cp /usr/share/base-files/profile /etc/profile

I also tried recovery mode and chose repair broken packages.

---

### Post by steeldriver on 2013-10-03
Your /etc/profile shouldn't really have any effect on the lightdm login, afaik

> dpkg-reconfigure lightdm (first pressed lightdm in the menu then tried dpg an reverted back to lightdm when that didn't work)

Do you mean you switched to **gdm** and then back to lightdm? Can you post a screenshot of what you're seeing now? I can't really visualize what it might be

---

