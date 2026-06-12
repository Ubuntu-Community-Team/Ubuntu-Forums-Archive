---
title: "export EDITOR=gedit &amp;&amp; sudo visudo opens the sudoers file in the terminal window"
date: 2008-05-03
forum: General Help
---

### Post by linuxed on 2008-05-03
I need to edit my sudoers file but for some reason the sudoers file keeps opening in the terminal window instead of gedit.  What am I doing wrong?  I'm currently running Ubuntu 8.04.

export EDITOR=gedit && sudo visudo

At the moment the only way I can edit the file is to chmod it and then double click on the file icon.  I can't even open gedit from the terminal as root.  The following error is displayed when I type /usr/bin/gedit or gedit as root.

cannot open display: 
Run '/usr/bin/gedit --help' to see a full list of available command line options

---

### Post by linuxed on 2008-05-03
Any suggestions would be appreciated.

---

### Post by prshah on 2008-05-03
> **linuxed said:**
> 
export EDITOR=gedit && sudo visudo


When you set an environment variable, it is set only for the particular user, not for sudo (root).

Try code:
```

export EDITOR=gedit && sudo -E visudo

```

Where "-E" means "preserve environment". 

Alternatively, you can change the value of "editor" in the sudoers file.

---

### Post by bollix47 on 2008-05-03
From man sudoers:

```
The sudoers file should **always** be edited by the visudo command
which locks the file and does grammatical checking. It is imperative that 
sudoers be free of syntax errors since sudo will not run with a syntactically 
incorrect sudoers file.

```

---

### Post by linuxed on 2008-05-03
Thanks prshah. The -E fixed it. My only other question is how I can get gedit to open from the terminal as root.  If I type su - , enter the root password, and then type gedit I'm still presented with an error stating that gedit can't open.  However if I type gedit in the terminal from my standard user account it opens without any problems.  Is there a line I can add to the sudoers file to fix this?

---

### Post by ibuclaw on 2008-05-03
[EDIT]
Sorry, you mean to open visudo with gedit automatically?

you can add some lines to the bottom of your .bashrc file to do that.

```
gedit ~/.bashrc
```
And add to the bottom.
[PHP]
export EDITOR=gedit
alias visudo='-E visudo'
[/PHP]

That will fix it.

All you now have to type in is:
```
sudo visudo
```
Without worrying about anything else!

Regards
Iain

---

### Post by linuxed on 2008-05-03
Perfect! I can now open gedit from the terminal as root using sudo -s.  However I'm not prompted to enter a password when I use sudo -s.  I'm only prompted to enter the root password with su -.

---

### Post by ibuclaw on 2008-05-03
> **linuxed said:**
> Perfect! I can now open gedit from the terminal as root using sudo -s.  However I'm not prompted to enter a password when I use sudo -s.  I'm only prompted to enter the root password with su -.

If you have used the sudo command. Sudo will remember that you've used it, so you can do other sudo commands without being prompted for a password.

To change this (ie: to be prompted for a password everytime):
open up visudo.
Then type in:
```
Defaults:ALL    timestamp_timeout=0
```
Put it at the bottom of the file.

Or if every time you use sudo is a bit excessive (ie: "sudo apt-get update && sudo apt-get upgrade && sudo apt-get clean" asks you three times in one sitting.)

You can change the **timeout=0** to **timeout=1** or **2**. The value stands for the number of minutes before it asks you again.
I think the default is 15 minutes, or until the shell is closed.

Regards
Iain

---

### Post by linuxed on 2008-05-03
Many thanks.  That fixed it and I'm now prompted for the password each time.

---

### Post by p_quarles on 2008-05-03
> **prshah said:**
> Try code:
```

export EDITOR=gedit && sudo -E visudo

```

Where "-E" means "preserve environment". 
Thanks for this, prshah. The need to use environment preservation with sudo is apparently need to Ubuntu 8.04. I'll try to incorporate this into a more permanently visible location, since there are *dozens* of tutorials on the web that explain how to export editors, but none that I have seen mention this.

---

### Post by ibuclaw on 2008-05-03
> **p_quarles said:**
> Thanks for this, prshah. The need to use environment preservation with sudo is apparently need to Ubuntu 8.04. I'll try to incorporate this into a more permanently visible location, since there are *dozens* of tutorials on the web that explain how to export editors, but none that I have seen mention this.

If you want a more permanent link. I made a [bug]("https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/207369") about this when Hardy was in Alpha (I'd never used vi before and got quite a shock).

But I think that my workaround is sound too.

Regards
Iain

---

### Post by p_quarles on 2008-05-03
> **tinivole said:**
> If you want a more permanent link. I made a [bug]("https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/207369") about this when Hardy was in Alpha (I'd never used vi before and got quite a shock).

But I think that my workaround is sound too.

Regards
Iain
I added it to the forum policy statement in Security Discussions, which is a sticky thread. 

And, yes, your workaround is good, but it's just a more permanent version of the same thing. ;) The -E option is the key to both.

---

