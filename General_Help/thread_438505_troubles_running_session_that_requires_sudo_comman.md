---
title: "troubles running session that requires sudo command"
date: 2007-05-09
forum: General Help
---

### Post by Memory.Dump on 2007-05-09
I found a thread earlier that states how to properly install the g15 drivers and it works great I'm really happy....only problem I am currently having is I can't have it automaitcly startup

I have the session set to sudo g15daemon (name of the daemon file)
and I typed:

sudo visudo

and I added the text in blue

# User privilege specification
root ALL=(ALL) ALL
[COLOR="Blue"]user ALL=NOPASSWD: /usr/sbin/g15daemon[/COLOR]

however I still have to manually run the Daemon and when I type g15daemon in the terminal without the sudo it gives me an error I assume thats not correct either...could anybody help me

---

### Post by Memory.Dump on 2007-05-10
anybody know?

---

### Post by Memory.Dump on 2007-05-10
/bump for frustration, from what I can see this should work and allow me to run the daemon w/o typing in the password but it won't run on start

---

### Post by ikonia on 2007-05-10
entering a file into the sudoers file does not mean it will automaticlly be run as root.

you still have to do sudo $command - but it should not ask you for a password.

---

### Post by Memory.Dump on 2007-05-10
I figured that but having where it is and then in the sessions area I have a session set up for

sudo g15daemon

but it still doesn't startup, beryl and amsn and all the other stuff I put in there do startup though so I'm not sure if I may have it in the wrong portion or something wrong in it there? could I be missing something?

---

### Post by ikonia on 2007-05-10
but don't have have to still name the file

eg: 

sudo g15daemon amsn

---

### Post by Memory.Dump on 2007-05-10
not sure I know what you mean, when I start the x enviroment everytghinng starts but the daemon (its the only one that needs teh sudo command)

and when I go to the termial and start it manually I still have to type in teh password even with the above information in the file

---

### Post by sefs on 2007-05-10
in sudo visudo did you also remember to change...

```

Defaults       !lecture,tty_tickets,!fqdn

```

to 

```

Defaults !lecture,tty_tickets,!fqdn,env_reset,env_keep+= " DISPLAY HOME XAUTHORIZATION "

```

That may help your situation.


> **Memory.Dump said:**
> 
sudo visudo

and I added the text in blue

# User privilege specification
root ALL=(ALL) ALL
[COLOR="Blue"]user ALL=NOPASSWD: /usr/sbin/g15daemon[/COLOR]



---

### Post by Memory.Dump on 2007-05-10
ahhh I did not, I will try that when I get home!

---

### Post by Memory.Dump on 2007-05-10
ok so I've added in the code as listed to the Defaults section and I still need to enter the pw when I sudo g15daemon and it still won't start in the session

---

### Post by Memory.Dump on 2007-05-10
any other ideas? I still need to put the pw when I sudo g15daemon

I get:

  GNU nano 2.0.2                                     File: /etc/sudoers.tmp                                                                                  

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn,env_reset,env_keep+= " DISPLAY HOME XAUTHORIZATION "

# User privilege specification
root    ALL=(ALL) ALL
user    ALL=NOPASSWD: /usr/sbin/g15daemon

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL




I assume all is in order there? the session is set to

sudo g15daemon

---

### Post by pacificdrums on 2007-05-11
I have needed to do the same thing on a couple occasions. I have tried the same things as Memory.Dump without success. You should be able to do this, right?

---

### Post by Memory.Dump on 2007-05-14
this is starting to really frustrate me, does anybody out there have any ideas?

---

### Post by fragos on 2007-05-14
You can add the startup command with System-> Preferences-> Sessions-> "Startup Programs tab".  also you showed the sudoers file with the line "user ALL=NOPASSWD: /usr/sbin/g15daemon".  Unless your user name is "user" this won't work.  For example my user name is "fragos" and the line would have to be "fragos ALL=NOPASSWD: /usr/sbin/g15daemon".

---

### Post by Memory.Dump on 2007-05-16
I changed the user name in the sudoers to my user name and it still won't work any other ideas?

---

### Post by Memory.Dump on 2007-05-16
currently my file reads

```

GNU nano 2.0.2 File: /etc/sudoers.tmp 

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults !lecture,tty_tickets,!fqdn,env_reset,env_keep+= " DISPLAY HOME XAUTHORIZATION "

# User privilege specification
root ALL=(ALL) ALL
memorydump ALL=NOPASSWD: /usr/sbin/g15daemon

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```
but I still need to enter a pw when I sudo g15daemon, any body else have an idea as to why?

---

### Post by fragos on 2007-05-16
I assume you used "sudo visudo -f /etc/sudoers" to edit the file.  I noticed you have a space separating the filename.  Perhaps that is your problem.  Check the following that worked for me.

# allow fragos to start firewall
fragos ALL=NOPASSWD:/usr/bin/firestarter

---

