---
title: "n00b messed up sudo"
date: 2005-06-08
forum: General Help
---

### Post by jwm68 on 2005-06-08
Hopefully, someone has a minute to help out a n00b.  I recently installed Ubuntu as a dual-boot with Win XP.

I got sick of forgetting to type in sudo every time I wanted to install something, so I did this from within the /usr folder:

sudo chmod -R 777 *

Now, sudo does not work -- in fact, anything that wants to use sudo to do its actions (synaptic, etc) does not work.  If I try to run anything using sudo from Terminal, I get the "sudo: must be setuid root" error.

I rebooted in recovery mode and tried resetting the permissions on /usr with:

sudo chmod -R 755 *

but that did not help.

Someone please help me -- I have no idea what to do, and I could not find anything on the forums that fit my particular situation.

Thx in advance.

---

### Post by Zifnab on 2005-06-08
Hm, can't answer your question, but some advice:

If you plan on doing more than one thing as root, just use the command "su" to become root. Type "exit" to return to your old self again. Then you don't have to deal with all that silly "sudo" stuff.

---

### Post by Joeb on 2005-06-08
[QUOTE=Zifnab]Hm, can't answer your question, but some advice:

If you plan on doing more than one thing as root, just use the command "su" to become root. Type "exit" to return to your old self again. Then you don't have to deal with all that silly "sudo" stuff.[/QUOTE]


Sudo and root are not the same thing.  With sudo, you are still logged in as you, but you have the equivalent of root priviledges.  With su, you actually are logged in as root (ie a different user than yourself).  Both have their places, but they are different solutions to the same problem.  Also, using sudo creates a file with all of the commands you entered, so that you can trace your steps if you screwed something up or put the steps into a script so you can run it again as needed.

---

### Post by az on 2005-06-08
That wasn't very smart.

Try booting into recovery mode and chmoding /usr/bin/sudo to 4755 

(-rwsr-xr-x)

You completely borked the permissions of your system and there is no easy way to reverse the security issues you just created.  Not to mention things may just not work anymore.

It is ironic that sudo is meant to prevent you from having to become root and do this sort of thing by accident...

Chalk it up as a learning experience...

---

### Post by desdinova on 2005-06-08
Yep I'll concur - the mistake is to assume root is a normal account - its for system admin only. The whole point of having a password request is to remind you that what you want to do next MAY screw up your machine....

The simplest way to fix your b0rken machine is a reinstall, and learn to respect the "root" ;-)

---

### Post by Zifnab on 2005-06-08
[QUOTE=Joeb]Sudo and root are not the same thing.  With sudo, you are still logged in as you, but you have the equivalent of root priviledges.  With su, you actually are logged in as root (ie a different user than yourself).  Both have their places, but they are different solutions to the same problem.  Also, using sudo creates a file with all of the commands you entered, so that you can trace your steps if you screwed something up or put the steps into a script so you can run it again as needed.[/QUOTE]
Heh, I know this. Nothing wrong with rooting around now and then. :P
Normal users have such limited file access...

---

### Post by az on 2005-06-08
[QUOTE=Zifnab]Heh, I know this. Nothing wrong with rooting around now and then. :P
Normal users have such limited file access...[/QUOTE]


Unless you are installing packages, you do not need to play around with any other files than what is in your home directory.

There is a reason why permissions are built into unix systems from the ground-up.

---

### Post by giddy on 2005-06-20
I have the same setup (windows XP but ubuntu running in VMware) and made the same mistake as jwm68 today after getting sick of having to change file permissions each time new programs were loaded up. changed the permissions of the sudo file back to 4755 as suggested by azz and things like synaptic can be used again when I am logged in as a standard (non-root) user. does anyone know if there likely to be other serious problems (yet to be discovered) created by changing the file permission of the /usr file to 777? ( i have various bioinformatics software packages / databases loaded and configured and would hate to have to do it all again...)

---

### Post by afonic on 2005-06-20
To all sudo-bored guys:

The is an option in Applications -> System Tools called "Root Terminal". Any guess what it does?

---

