---
title: "Firestarter - does not startup with root pswd"
date: 2007-09-19
forum: General Help
---

### Post by tech9 on 2007-09-19
I have edited the following file to be able to start firestarter without entering a password everytime...

sudo gedit /etc/sudoers

#Defaults !lecture,tty_tickets,!fqdn

my_user_name ALL= NOPASSWD: /usr/sbin/firestarter

Replaced 'my_user_name' with my actual username. 

Reboot. 


The problem that I have is that firestarter does not load at all under my user profile, even if I execute it.

Any Ideas?  :confused:

---

### Post by tech9 on 2007-09-19
Another Stumper? :(

---

### Post by por100pre1 on 2007-09-19
Try changing the Firestarter launcher command from:

```
gksudo firestarter
```

to:

```
sudo /usr/sbin/firestarter
```

Let me know if this works or not. :-k

EDIT: By the way, sudo gedit /etc/sudoers is NOT the correct way to edit that file.

This is correct way:

```
export EDITOR=gedit && sudo visudo
```

Let's hope your sudoers file is not hosed...

---

### Post by tech9 on 2007-09-19
> **por100pre1 said:**
> Try changing the Firestarter launcher command from:

```
gksudo firestarter
```

to:

```
sudo /usr/sbin/firestarter
```

Let me know if this works or not. :-k

EDIT: By the way, sudo gedit /etc/sudoers is NOT the correct way to edit that file.

This is correct way:

```
export EDITOR=gedit && sudo visudo
```

Let's hope your sudoers file is not hosed...

Hi por100pre1,

    Thank you for being the only one to respond to my post. I guess this one stumped everyone else too. I did try your suggestion and it still did not work. I believe I found a bug in 7.04

---

### Post by tech9 on 2007-09-19
> **por100pre1 said:**
> Try changing the Firestarter launcher command from:

```
gksudo firestarter
```

to:

```
sudo /usr/sbin/firestarter
```

Let me know if this works or not. :-k

EDIT: By the way, sudo gedit /etc/sudoers is NOT the correct way to edit that file.

This is correct way:

```
export EDITOR=gedit && sudo visudo
```

Let's hope your sudoers file is not hosed...

Can't I edit this file directly in the root profile? or could that possibly hose the file too?

---

### Post by tech9 on 2007-09-19
I found that you have to be very careful messing with the sudo file... I put everything back... but still cannot get firestarter to automatically launch without a password under my normal user profile.:(

---

### Post by por100pre1 on 2007-09-19
You don't need to have Firestarter running at startup. The iptables firewall will run at startup without the Firestarter GUI running. In fact, running Firestarter like that at startup it's a security breach.

---

### Post by por100pre1 on 2007-09-19
> **tech9 said:**
> I found that you have to be very careful messing with the sudo file... I put everything back... but still cannot get firestarter to automatically launch without a password under my normal user profile.:(

The command should be (under normal conditions):

```
gksudo firestarter
```

If you think firestarter is not working well try:

```
sudo dpkg-reconfigure firestarter
```

or:

```
sudo aptitude reinstall firestarter
```

---

### Post by WakkaDojo on 2007-09-19
I believe I had this problem as well. Find the following line in /etc/sudoers
```
Defaults       !lecture,tty_tickets,!fqdn
```
Then comment it out and put this line in:
```
Defaults !lecture,tty_tickets,!fqdn,env_reset,env_keep+="DISPLAY HOME XAUTHORIZATION"
```
This is a common fix for this problem. I'm not sure of the exact reason, but it fixed it for me.

---

### Post by tech9 on 2007-09-20
> **WakkaDojo said:**
> I believe I had this problem as well. Find the following line in /etc/sudoers
```
Defaults       !lecture,tty_tickets,!fqdn
```
Then comment it out and put this line in:
```
Defaults !lecture,tty_tickets,!fqdn,env_reset,env_keep+="DISPLAY HOME XAUTHORIZATION"
```
This is a common fix for this problem. I'm not sure of the exact reason, but it fixed it for me.

Hi WakkaDojo,

This line worked... Thanks for the help
Defaults !lecture,tty_tickets,!fqdn,env_reset,env_keep+="DISPLAY HOME XAUTHORIZATION"

I have seen this line before in another thread, but it stated that it was optional as far as inputting it into sudoers.

Take Care!

T9

---

### Post by tech9 on 2007-09-20
> **por100pre1 said:**
> You don't need to have Firestarter running at startup. The iptables firewall will run at startup without the Firestarter GUI running. In fact, running Firestarter like that at startup it's a security breach.

I realize that the firewall is in deed built in and working in the background. I wanted to install firestarter more or less so that I can monitor connections... How is this a security breach?

---

### Post by WakkaDojo on 2007-09-20
The process involves allowing access to firestarter without the root password. Since firestarter isn't only a method of viewing firewall activity but also modifying settings, you are allowing access to firewall settings without a root password. So, if someone *really* wanted to, they could allow their IP address through the firewall.
I'm doing the same thing with firestarter, but am beginning to wonder if it's really worth it.

---

### Post by tech9 on 2007-09-20
> **WakkaDojo said:**
> The process involves allowing access to firestarter without the root password. Since firestarter isn't only a method of viewing firewall activity but also modifying settings, you are allowing access to firewall settings without a root password. So, if someone *really* wanted to, they could allow their IP address through the firewall.
I'm doing the same thing with firestarter, but am beginning to wonder if it's really worth it.

I understand... yeah maybe I should just input the password everytime then... Thanks!

---

### Post by nvteighen on 2007-09-20
Maybe you can try the How-To at my signature.

It can be that iptables is not being configured by Firestarter. The guide will make Firestarter start at boot (not at GNOME start), configure iptables, but without having to start the graphical interface (and then, not having to put your password).

---

### Post by WakkaDojo on 2007-09-20
Excellent solution!

---

### Post by nvteighen on 2007-09-20
> **WakkaDojo said:**
> Excellent solution!

Thank you very much, but it's not mine! I'm just the compiler.

---

### Post by tech9 on 2007-09-20
> **nvteighen said:**
> Maybe you can try the How-To at my signature.

It can be that iptables is not being configured by Firestarter. The guide will make Firestarter start at boot (not at GNOME start), configure iptables, but without having to start the graphical interface (and then, not having to put your password).

Thanks for the suggestion, but it did not work!:(

---

### Post by tech9 on 2007-09-20
> **WakkaDojo said:**
> The process involves allowing access to firestarter without the root password. Since firestarter isn't only a method of viewing firewall activity but also modifying settings, you are allowing access to firewall settings without a root password. So, if someone *really* wanted to, they could allow their IP address through the firewall.
I'm doing the same thing with firestarter, but am beginning to wonder if it's really worth it.

Please explain in a thorough process how you say 
"So, if someone *really* wanted to, they could allow their IP address through the firewall."

Anyone trying to connect or crack through would be denied right off the bat... so explain how this is a security breach.

---

### Post by nvteighen on 2007-09-21
> **tech9 said:**
> Thanks for the suggestion, but it did not work!:(

I'm hearing some people have another solution related to init.d script, but actually I don't understand it very well. Look at the same Howto thread comments; maybe you can PM some of those users.

---

### Post by tech9 on 2007-09-24
> **nvteighen said:**
> I'm hearing some people have another solution related to init.d script, but actually I don't understand it very well. Look at the same Howto thread comments; maybe you can PM some of those users.


Thanks for the suggestions

---

