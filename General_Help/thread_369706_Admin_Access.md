---
title: "Admin Access"
date: 2007-02-24
forum: General Help
---

### Post by ejrives on 2007-02-24
Is there anyway to stop this OS from prompting you for a password after every command that you enter. I entered all relevant info into /etc/group just to make sure and I still get permission denied errors. The only way to resolve is using sudo. I hate having to use sudo on  a workstation that is mine and no one else uses. In a nutshell I would like to have full on "root" access from my account .....no passwords to do anything except for logins (local and remotely) "sudo su -" is not an option. Any suggestions???????

---

### Post by disturbedite on 2007-02-24
i'd kinda like not being bugged for the password all the time but...

it isn't considered (or recommended) to run your system as root.  you can screw too many things up.  and its not as secure.  its kind of a staple of linux, not distro specific.  (thats why you're asked for the root password when you do certain things).

not to sound like a jerk, but what it'll prolly boil down to is getting used to it.

---

### Post by yabbadabbadont on 2007-02-24
Add "timestamp_timeout=-1" to your /etc/sudoers file.  You will need to use "sudo visudo" to edit the file.  The appropriate line should look something like this:

Defaults        !lecture,tty_tickets,!fqdn,timestamp_timeout=-1

---

### Post by ejrives on 2007-02-24
Cool...that is what I figured...In my other flavor of Linux that I use I have been able to nearly  bypass the whole sudo thing by effectively changing the timeout . Is that the same syntax here in /etc/sudoers?

"timestamp_timeout=7200"  something like that?????

---

### Post by ejrives on 2007-02-24
> **yabbadabbadont said:**
> Add "timestamp_timeout=-1" to your /etc/sudoers file.  You will need to use "sudo visudo" to edit the file.  The appropriate line should look something like this:

Defaults        !lecture,tty_tickets,!fqdn,timestamp_timeout=-1

Well I see that we are thinking alike

---

### Post by yabbadabbadont on 2007-02-24
> **ejrives said:**
> Well I see that we are thinking alike

Not really.  I have timestamp_timeout=0 in my file so that it prompts me every single time.  I just figured that you have been warned so if you want to do it anyway, so be it.  ;)

---

### Post by ejrives on 2007-02-24
Since this is a test installation I am not too worried about the length of timeout that I am using. It's not really being warned as I am aware of what can happen. I am not installing anything under root. I just want to be able to change system settings and rund useful commands such as without the damned password.

 find / -name "*.tgz*" -print -exec gzip -9 {} \; 
and 
du -kx / |sort -nr |head -50  without being prompted to use a password.

---

### Post by ejrives on 2007-02-24
thanks for the help all.

---

