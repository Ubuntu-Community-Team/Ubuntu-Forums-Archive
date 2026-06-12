---
title: "System administration items not working"
date: 2006-10-10
forum: General Help
---

### Post by Alessandro Allegri on 2006-10-10
I don't know if this is the right place to post.
I have this weird problem: almost all the items on the System->Administration menu don't work. I can only launch the Device Manager, the Network Tools, Printing, System log, System monitor. All the others (including the kinda important ones, Networking, Synaptic, Discs, Services...) will show the "waiting" icon, a button will appear for a while in the bottom bar, and then everything will disappear.
I don't really know what happened. I did not install any new stuff really, maybe some updates over the last few days when the laptop was on.
Maybe I should mention it's a dual-booting XP-Ubuntu laptop, but the thing never gave any trouble...

I have no idea how to restore the lost functions... anybody knows?
Thank you in advance...

---

### Post by dannyboy79 on 2006-10-10
i can't tell you why but this happened to me and i belive that after i restarted the machine everything was fine. if you find out the root cause please post back i would appreciate that.

---

### Post by Kateikyoushi on 2006-10-10
What's the feedback if you type "sudo synaptic" in the terminal ?

---

### Post by Alessandro Allegri on 2006-10-10
it works... but the menu isn't...

---

### Post by dannyboy79 on 2006-10-10
> **Alessandro Allegri said:**
> it works... but the menu isn't...


did a restart not fix it?

---

### Post by Kateikyoushi on 2006-10-10
That's a killer avatar dannyboy79. :D

---

### Post by Tomosaur on 2006-10-10
I have this exact same problem, but I've been pretty busy and it's slipped my mind. Good (kind of :P ) to see someone else has the problem too. Anybody got any ideas?

---

### Post by Alessandro Allegri on 2006-10-10
well, restarting was the first thing I tried, and many times too. but no, it didn't work.

---

### Post by srt4play on 2006-10-10
Maybe somehow the program 'gksu' has gotten screwed up on your system?  

Does entering 'which gksu' in the terminal return anything?

---

### Post by Alessandro Allegri on 2006-10-10
I don't think it's a superuser problem.
Some items do work, and all of them, after a long inactivity, ask for su password, and start "doing" something only after it is provided correctly.
The problem is that most of the items seem unable to end what they start doing.
Anyway, the which gksu gives:
/usr/bin/gksu

---

### Post by srt4play on 2006-10-10
Well, the reason I asked is because all of the ones you are able to launch don't use gksu as part of their launch command.

All of the ones that don't work for you, do use gksu in their launch command. 

It only seemed logical to verify the existence/non-corruption of the single command that all of your problem launchers have in common.

Good luck.

---

### Post by Alessandro Allegri on 2006-10-10
Actually, it might be something of the sort... I tried with 
/usr/bin/gksu synaptic
and the result was


Xlib: Invalid MIT-MAGIC-COOKIE-1 key

(synaptic:13055): Gtk-WARNING **: cannot open display:

and of course no result.
Tried again with 
/usr/bin/gksu gedit file

and the outcome was: 

Xlib: connectioncannot open display: (null)
Run 'gedit --help' to see a full list of available command line options.
 to ":0.0" refused by server
Xlib: Invalid MIT-MAGIC-COOKIE-1 key

and no result again...
I guess it's gksu then? and how can I mend it?
Thanks a lot!

---

### Post by Alessandro Allegri on 2006-10-10
Well, I found this thread that looks like the same problem as I got...
[http://www.ubuntuforums.org/showthread.php?t=248331&highlight=Invalid+MIT-MAGIC-COOKIE-1]("http://www.ubuntuforums.org/showthread.php?t=248331&highlight=Invalid+MIT-MAGIC-COOKIE-1")
Unfortunately there is no solution posted yet...

---

### Post by srt4play on 2006-10-10
> **Alessandro Allegri said:**
> 
I guess it's gksu then? and how can I mend it?
Thanks a lot!


Did you try any of the suggestions in the thread you found? Mainly creating another user with admin rights to see if the problem persists with other user accounts? 

Post the contents of /etc/sudoers

---

### Post by Alessandro Allegri on 2006-10-10
Well, I can't add a new user because I can't access that item on the System Administration menu. Terminalwise, I don't know how to.

sudoers:

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

# Defaults      !lecture,tty_tickets,!fqdn
Defaults        !lecture,tty_tickets,!fqdn,env_reset,env_keep+="DISPLAY HOME XAUTHORIZATION"

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin  ALL=(ALL) ALL
alessandro ALL= NOPASSWD: /usr/sbin/firestarter

---

### Post by srt4play on 2006-10-10
To create a user:

sudo useradd -m 'username'

And to set the password for the user:

sudo passwd 'username'

---

### Post by Alessandro Allegri on 2006-10-11
Thank you.
Unfortunately it didn't work. The new user is in the same position as the old one: they both can successfully launch the administrative utilities from terminal, but the gnome launcher doesn't make it. So basically sudo works and gksu does not...

I think the other thread, the one I posted above, is the right track. Unfortunately it seems kinda stuck...

Thank you again for your help.
A.A.

---

### Post by freedom7221 on 2006-10-13
I had the same problem with the system admin menu after changing my hostname.  I changed the hostname back to its original name and bingo, the menu worked normal again.  Perhaps there is some setting you changed?  good luck.

---

### Post by Alessandro Allegri on 2006-10-15
nope, I did not change anything. maybe some update-upgrade, I don't know because the laptop was on for a long time since the previous rebooting. surely I did not touch the hostname...
thank you anyway!

---

### Post by fragos on 2006-10-16
Your /etc/hostname should have your host name.  If you haven't configured a hostname it may default ti "linux".  Mine is set to "Geo".

Your /etc/hosts should have a line like as follows:

127.0.0.1 localhost Geo

If those don't agree, you won't be able to use administration applications.  I ran into this when my hosts file got corrupted.  Adding the line above with my hostname put everything back to normal.

---

### Post by Alessandro Allegri on 2006-10-18
well, here they are:

alessandro@ubuntu:/etc$ cat hostname
ubuntu

alessandro@ubuntu:/etc$ cat hosts
127.0.0.1 localhost ubuntu
127.0.1.1 ubuntu

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by DynamicMouse on 2008-05-13
I had the exact same problem and the fix suggested earlier to make sure that the hostname is listed in the hosts as mapping to 127.0.0.1 worked.  I was just wondering if it would cause any problems the fact that your host is ubuntu and it has 2 entries in the hosts file one for 127.0.0.1 and one for 127.0.1.1

try removing/commenting out the 127.0.1.1 entry and see if that has any effect

---

### Post by fragos on 2008-05-13
No problem what so ever.

---

