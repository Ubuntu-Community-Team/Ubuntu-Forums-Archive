---
title: "[SOLVED] yet another sudo &amp;amp; scripts thread"
date: 2008-06-07
forum: General Help
---

### Post by priegog on 2008-06-07
I have pretty much read all the threads there are out there, but this still doesn't work. 
Here is the deal: I made a script to connect a bluetooth keyboard that needs sudo to run. (I know this is not necesary for bluetooth, but in my case it is, and besides I want to get this to work because there are other things that need sudo that I would like to get up and running as sripts).
So I went to edit the sudoers file. To be honest I do it with gedit (I can't use vi to save my life), so I have to change the permissions before and after editing. I don't think it matters since after doing that I run sudo visudo -c and it says everything is fine, just putting it out there for troubleshooting. I should also say the script in question lives in a folder in my /home folder. Before continuing I should post my sudoers file ```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Uncomment to allow members of group sudo to not need a password
#%sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

#this points to a script which connects teh keyboard via BT
jerry ALL=NOPASSWD: /home/jerry/Reinstallation/keyboard.sh

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL 
``` Does it look ok?
Anyways, No matter what I  change in teh sudoers file, everytime i go ```
sudo /home/jerry/Reinstallation/keyboard.sh
```(yes, the script is executable) it prompts me for the password, which is exactly what I'm looking to eliminate so I can just make a shortcut on my desktop out of it. I should note that at first I misunderstood what the sudoers file made and tried to execute the script without sudo (but the line that required sudo was within the script). Since I read what it really did, I eliminated the sudo from the inside of the script and insted try to run the whole thing with sudo.
So, what am I doing wrong?

---

### Post by drs305 on 2008-06-07
> **priegog said:**
> 

#this points to a script which connects teh keyboard via BT
jerry ALL=NOPASSWD: /home/jerry/Reinstallation/keyboard.sh
So, what am I doing wrong?

First, I am fairly sure your "jerry ALL=NOPASSWD" line has to go AFTER the %admin ALL=(ALL) ALL line, since the %admin line takes precedence over anything prior to it.


The following line gives permission for the ```
sudo /home/jerry/Reinstallation/keyboard.sh
``` to run without a sudo password. However, it does not cover commands *within* the script. Any command needing sudo power needs to be listed individually, or you can allow all commands from a specific folder to be run by a listed individual. 

I an not an expert on these scripts. I've toiled and got several to work with much effort, but I believe what I mentioned is the problem with this entry. I can't give you the exact format but a search of the forums might provide it.

Here is part of my sudoers to allow me to run certain commands without sudo:
```

# Cmnd alias specification
Cmnd_Alias TEST = /usr/bin/find, /usr/bin/gedit, /usr/bin/gparted    

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
 %admin ALL=(ALL) ALL

Defaults:drs64 timestamp_timeout=120

drs64 ALL=(ALL) NOPASSWD: TEST 


```

---

### Post by ibuclaw on 2008-06-07
Switch the last two commands around.

the "**%admin ALL=(ALL) ALL**" command overrides your "**ALL=NOPASSWD**" command. Hence why you are still asked for a password.

It should look like this:
```

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

#this points to a script which connects teh keyboard via BT
jerry ALL=NOPASSWD: /home/jerry/Reinstallation/keyboard.sh

```

[EDIT]
Although, if you are explicitly only going to execute the command as root, I suggest putting "**ALL=(%root)**" in the line.
```
jerry ALL=(%root) NOPASSWD: /home/jerry/Reinstallation/keyboard.sh
```

Regards
Iain

---

### Post by rampageoberon on 2008-06-07
[http://www.ducea.com/2006/05/19/linux-tips-the-proper-way-to-allow-regular-users-to-run-commands-as-root/](http://www.ducea.com/2006/05/19/linux-tips-the-proper-way-to-allow-regular-users-to-run-commands-as-root/)

That might be useful for you

---

### Post by VMC on 2008-06-07
Isn't the password coming from using 'sudo' in the string?

---

### Post by ibuclaw on 2008-06-07
> **VMC said:**
> Isn't the password coming from using 'sudo' in the string?

Can you iterate on what you mean by this VMC?

Iain

---

### Post by VMC on 2008-06-07
> **tinivole said:**
> Can you iterate on what you mean by this VMC?

Iain

The only thing I'm saying is he's using:
 'sudo /home/jerry/Reinstallation/keyboard.sh'
why not:
 './home/jerry/Reinstallation/keyboard.sh'

since he's the owner. Isn't the password coming from sudo itself?

---

### Post by priegog on 2008-06-08
wow, thanks to all! I figured the questin would take some time so I wrote it and went to bed. Now I come and see you've all answered within minutes. you were right about the order; that worked beautifully. Thank you all

---

