---
title: "error with Firestarter"
date: 2005-09-13
forum: General Help
---

### Post by chess007 on 2005-09-13
I installed Firestarter . It worked fine. The next time I boot up I get 2 dialog boxes:

"Insufficent privileges
You must have root user privileges to use firestarter." 

and the following message.

"Error Missing command to run." 

How can I fix this?

---

### Post by Hairy_Palms on 2005-09-13
heres how to fix it
[http://www.fs-security.com/docs/faq.php](http://www.fs-security.com/docs/faq.php)

---

### Post by chess007 on 2005-09-14
Exactly how do I do that?

From the root terminal I ran 

visudo

That loads the sudoers file.

How do i get to "insert mode" ? 

I want to add the following line to the bottom of the file

stewie00right  ALL= NOPASSWD: /usr/sbin/firestarter


After I add that line, I want to save it. There is no Save option in the file menu.  

The bottom part of my sudoers file currently says...

# Defaults

Defaults            ! lecture, tty_tickets, ! fqdn

# User privilge specification
root       ALL=(ALL) ALL


Should I change it to read...


# Defaults

Defaults            ! lecture, tty_tickets, ! fqdn

# User privilge specification
root       ALL=(ALL) ALL
stewie00right  ALL= NOPASSWD: /usr/sbin/firestarter

Thanks in advance for your help. :)

---

### Post by chess007 on 2005-09-15
Some help please... thanks:)

---

### Post by myha on 2005-09-15
Hi!

I solved this problem by adding it to startup programs with sudo command:
system-preferences-session-startup programs
```
sudo firestarter
``` 
Then close firestarter if running, reboot and select save current setup.

It worked for me!

---

### Post by chess007 on 2005-09-15
myha,

That stops firestarter from running. What I want is for firestarter to always run, thats why i needed - and still need - help with how to edit the sudoers file. :)

---

### Post by myha on 2005-09-15
[QUOTE=chess007]myha,

That stops firestarter from running. What I want is for firestarter to always run, thats why i needed - and still need - help with how to edit the sudoers file. :)[/QUOTE]
Well I dot know why would it stop it from running... You add it to startup programs so it starts when u boot system...
In firestarter FAQ it says how to add it to startup and thats exactly what I said... I never added any username ALL= NOPASSWD: /usr/bin/firestarter to sudoers list, I only gave myself to sudoers list ```
miha    ALL=(ALL) NOPASSWD: ALL 
``` and added sudo firestarter to startup programs and it worked...
You edit your sudoers with running ```
visudo
``` command, than you add your username at the end of file ```
miha    ALL=(ALL) NOPASSWD: ALL 
```, then ctrl+X to exit and it asks you to save, hit Y and save it to sudoers.tmp

That should be it!

---

### Post by abmcr on 2005-09-16
I have installed Firestarter (in Breeze) and, at the launch, i get a message: Firestarter has not privilege for running. I don't want Firestarter to the launch; i have rename the S20firestarter in the rc2.d directory:

This is the inittab

root@ubuntu:/etc# cat inittab

# The default runlevel.
id:2:initdefault:

# Boot-time system configuration/initialization script.
# This is run first except when booting in emergency (-b) mode.
si::sysinit:/etc/init.d/rcS

# What to do in single-user mode.
~~:S:wait:/sbin/sulogin

# /etc/init.d executes the S and K scripts upon change
# of runlevel.
#
# Runlevel 0 is halt.
# Runlevel 1 is single-user.
# Runlevels 2-5 are multi-user.
# Runlevel 6 is reboot.

l0:0:wait:/etc/init.d/rc 0
l1:1:wait:/etc/init.d/rc 1
l2:2:wait:/etc/init.d/rc 2
l3:3:wait:/etc/init.d/rc 3
l4:4:wait:/etc/init.d/rc 4
l5:5:wait:/etc/init.d/rc 5
l6:6:wait:/etc/init.d/rc 6
# Normally not reached, but fallthrough in case of emergency.
z6:6:respawn:/sbin/sulogin

# What to do when CTRL-ALT-DEL is pressed.
ca:12345:ctrlaltdel:/sbin/shutdown -t1 -a -r now




and this my rc2.d directory

root@ubuntu:/etc/rc2.d# ls
S05vbesave S12dbus S19hplip S20makedev S20powernowd S89anacron S99acpi-support
S10acpid S13gdm S20apmd S20mysql S20rsync S89atd S99fetchmail
S10sysklogd S14ppp _S20firestarter S20pcmcia S25bluez-utils S89cron S99rmnologin
S11klogd S19cupsys S20hotkey-setup S20postfix S25mdadm S91apache2 S99stop-bootlogd

I have also changed the value of apps -->firestarter--> startup on boot in the editor of configuration, but the error ""Insufficent privileges
You must have root user privileges to use firestarter." remain.

The solution
[QUOTE=myha]
You edit your sudoers with running ```
visudo
``` command, than you add your username at the end of file ```
miha    ALL=(ALL) NOPASSWD: ALL 
```, then ctrl+X to exit and it asks you to save, hit Y and save it to sudoers.tmp
[/QUOTE]

require a sudo user without password and i don't want that....

---

### Post by myha on 2005-09-16
You can still try inserting 
```
username ALL= NOPASSWD: /usr/sbin/firestarter 
``` 
to sudoers list...
[http://www.fs-security.com/docs/faq.php#trayicon](http://http://www.fs-security.com/docs/faq.php#trayicon)

---

### Post by chess007 on 2005-09-16
I did the fix from the fs security site. When I boot it says,"Insufficent privileges
You must have root user privileges to use firestarter."  

 But, firestarter is running in the background. :) 

 I don't understand why it still says the Insufficent privileges message.

---

### Post by myha on 2005-09-16
[QUOTE=chess007]I did the fix from the fs security site. When I boot it says,"Insufficent privileges
You must have root user privileges to use firestarter."  

 But, firestarter is running in the background. :) 

 I don't understand why it still says the Insufficent privileges message.[/QUOTE]

Im glad u managed to fix your problem.....
About error problem.... I told u at the beginning to
> Then close firestarter if running, reboot and select save current setup.
The message displays because firestarter tries to run two times.... The succesful run is the one you added to startup list, and the unsuccessful is the one saved session when you exit gnome and select save current setup.
So when u reboot next time first exit firestarter, select save session and reboot and error should not be there anymore...

Regards,
Miha

---

### Post by chess007 on 2005-09-16
Thanks it works fine now. :)

---

