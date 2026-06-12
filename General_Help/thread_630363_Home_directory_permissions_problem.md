---
title: "Home directory permissions problem"
date: 2007-12-03
forum: General Help
---

### Post by dcroxton on 2007-12-03
I was unable to boot into the GUI yesterday because the permissions on my home directory had been changed to 777 instead of 755.  I got some error about the .dmrc file being ignored.

Fortunately, once I figured out the problem, I was able to fix it easily.  But I'm a little concerned about why the permissions were changed in the first place, as I am sure that I didn't do it (at least not directly).  I haven't noticed any other problems with my home directory -- i.e., no files erased -- but I don't like the idea of having the permissions changed without my knowledge.

Is there any known cause of this?  Some Ubuntu update, or some program?  If not, is there any way I could find out who did it?  I get lots of unauthorized login attempts in auth.log, which I guess is expected; is there any other way to look for intruders?

Sincerely,
Derek

---

### Post by bingoUV on 2007-12-03
Do you often play around with command-line, or do you mostly work in GUI?

---

### Post by p_quarles on 2007-12-03
A couple of fairly easy-to-setup security tools are Snort (intrusion detection) and Bastille (system hardening). 

If you really believe that this permissions change was a result of unauthorized access, I would suggest scouring your entire home directory for anything that seems off. Changing the permissions on user-owned files doesn't require root access, so there's not much reason to believe you've been rootkitted, but a compromised system needs to be treated with caution. 

The one way I know of that can cause permissions to get messed up is using "sudo" to run graphical applications. While that usually doesn't cause problems, it can. Always use "gksudo" (Gnome, Xfce) or "kdesu" (KDE) to run graphical apps as root.

---

### Post by dcroxton on 2007-12-03
BingoUV:  I use the command line a lot, not because I particularly like it, but because it often seems the easiest way to do something.  But I'm sure I didn't just change the permissions on my home directory by accident.

p_quarles:  I really don't know if the problem was the result of unauthorized access; I just don't know how I could have done it, or why an innocuous program would have done it.  I vaguely remember having this same problem once a long time ago (6+ months), but I don't know what to make of that.

I do run sudo a fair amount, though mostly just for synaptic.  I'll try to use gksudo instead -- I didn't know about that feature of it.

I will definitely install snort.  I'm hesitant to install any hardening measures, because I have spent a lot of time trying to work around firewalls and permission problems, but I've never had any known issues with hackers.

Sincerely,
Derek

---

### Post by metalheart on 2007-12-03
You can look in to /var/log/auth.log for privileged access attempts and do  cat .bash_history | grep chmod to see if you really have not changed mode.

---

### Post by bingoUV on 2007-12-03
This is what I was looking for. If you do not particularly like command line and sometimes use it, you might make the following kind of mistake :
1. /home/dcroxton is your home directory
2. You want to chmod all files in /home/dcroxton/folder
3. You type "chmod -R 777 /home/dcroxton/folder/*", but this does not fix the permissions of hidden files e.g /home/dcroxton/folder/.file
4. You type "chmod -R 777 /home/dcroxton/folder/.*". This seemingly harmless command actually changes the permissions of all files in your home directory, including subdirectories.

I have made such a mistake even though I used to live and die in the command line.  Just a possibility. It comes to my mind before malware suspicions because of apparent lack of malware for linux. I might be wrong.

---

