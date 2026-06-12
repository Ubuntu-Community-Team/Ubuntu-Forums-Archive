---
title: "Sudo problem when I upgraded to 8.04"
date: 2008-04-27
forum: General Help
---

### Post by lorderico on 2008-04-27
I know this is a common bug, but for some reason I can't seem to solve it.  When i do sudo, I get sudo: unable to resolve host Eric-desktop

In /etc/hostname, there is only one entry: Eric-desktop

I just upgraded to 8.04 and am happy with it except for this and that goolge toolbar doesn't work anymore (that's not ubuntu's fault, though).

Thanks,
Eric

---

### Post by bmorency on 2008-04-27
> **lorderico said:**
> I know this is a common bug, but for some reason I can't seem to solve it.  When i do sudo, I get sudo: unable to resolve host Eric-desktop

In /etc/hostname, there is only one entry: Eric-desktop

I just upgraded to 8.04 and am happy with it except for this and that goolge toolbar doesn't work anymore (that's not ubuntu's fault, though).

Thanks,
Eric

I had the same problem when I upgraded. I had to edit the hosts file. it is /etc/hosts

Add this line to it.

127.0.0.1 Eric-desktop

---

### Post by lorderico on 2008-04-27
I need root permissions to save /etc/hosts and can't get them via sudo.  Any ideas?
Thanks,
Eric

---

### Post by ghost_ryder35 on 2008-04-27
> **lorderico said:**
> I need root permissions to save /etc/hosts and can't get them via sudo.  Any ideas?
Thanks,
Eric
create password for root via
system, administration, user and groups, click root and type a password
then go to terminal and type 
```

su -

```
this will make you root, then issue the command yo need

---

### Post by lorderico on 2008-04-28
When I try that, I get this message:

root@Eric-desktop:~# gedit /etc/hosts
cannot open display: 
Run 'gedit --help' to see a full list of available command line options.

Also, my internet is now running extremely slowly, and my network Icon disappeared.  Before, it said my system's internet was offline.  Could this problem possibly cause that to happen?

---

### Post by Patsoe on 2008-04-28
> **bmorency said:**
> I had the same problem when I upgraded. I had to edit the hosts file. it is /etc/hosts

Add this line to it.

127.0.0.1 Eric-desktop

I think usually 127.0.0.1 is already assigned to "localhost". So you might use 127.0.1.1 (or something else starting with 127, I think). That's what is in my /etc/hosts anyway.

To get root access, you will need to reboot into recovery mode. Be careful because you'll have a full root session. Then at the command line edit /etc/hosts.

---

### Post by Patsoe on 2008-04-28
> **lorderico said:**
> When I try that, I get this message:

root@Eric-desktop:~# gedit /etc/hosts
cannot open display: 
Run 'gedit --help' to see a full list of available command line options.

Also, my internet is now running extremely slowly, and my network Icon disappeared.  Before, it said my system's internet was offline.  Could this problem possibly cause that to happen?

(I'm puzzled as to how you just managed to set a root password without being able to sudo, but anyway...)

So the error message means that the DISPLAY variable has not been set. I think this is because you used "-" after su. Try plain su.

Alternatively, you can use another editor, the shell default is "nano".

---

### Post by ludovicc on 2008-04-28
lorderico, use nano to solve your problem.

In summay, you should do:
  su -
  nano /etc/hosts

/etc/hosts should contain at least
  127.0.0.1 Eric-desktop

(note: 127.0.1.1 is an invalid address and may slow down your system...)

Then Ctrl+X, Y to exit and save

It would help if you colud post the current contents of your hosts file
(cat /etc/hosts)

Ludovic

---

### Post by bodhi.zazen on 2008-04-28
> **ghost_ryder35 said:**
> create password for root via
system, administration, user and groups, click root and type a password
then go to terminal and type 
```

su -

```this will make you root, then issue the command yo need

You should not set a root password in Ubuntu. To access a root terminal use :

```
sudo -i
```

For graphical applications, like gedit, use gksu (kdesu in kubuntu).

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

gksudo : [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

To lock your root account, after setting a password, use :

```
sudo passwd root -l
```

If you can not access sudo and need to repair your system, reboot and select recovery mode from the grub menu.

---

### Post by Patsoe on 2008-04-28
> **ludovicc said:**
> 
(note: 127.0.1.1 is an invalid address and may slow down your system...)


It shouldn't be invalid - everything starting with 127 is supposed to point to the loopback interface. But I've seen a bug claiming that it caused slowdowns, yes. Not on my system though...

By the way, the bug report is here [https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/32906](https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/32906) (although the original bug was due to a manually edited /etc/hosts, see the latest comments).

Edit: plus, it seems you don't need to become root to fix this: [http://ubuntuforums.org/showpost.php?p=4813225&postcount=2](http://ubuntuforums.org/showpost.php?p=4813225&postcount=2)
(Now I also understand how you enabled the root password without sudoing... PolicyKit)

---

### Post by lorderico on 2008-04-28
Well, for whatever reason, I was able to enable root through system>administration>users/groups.  I then did a su (not su -) and changed /etc/hosts to include 127.0.0.1 Eric-desktop.  Sudo now works.  I am still looking into whether 127.0.1.1 Eric-desktop.Home should be there.  Here is my /etc/hosts file:

leo@Eric-desktop:~$ cat /etc/hosts
127.0.0.1 Eric-desktop localhost
127.0.1.1 Eric-desktop.Home

# The following lines are desirable for IPv6 capable hosts
#::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet ip6-localnet
ff00::0 ip6-mcastprefix ip6-mcastprefix
ff02::1 ip6-allnodes ip6-allnodes
ff02::2 ip6-allrouters ip6-allrouters
ff02::3 ip6-allhosts ip6-allhosts

Does this look ok?
I'm still trying to figure out why my internet is so slow...

Thanks for your help,
Eric

---

### Post by bodhi.zazen on 2008-04-28
What is your hostname ? from what you have posted it looks like Eric-desktop

In that case, I would change your /etc/hosts :

```
127.0.0.1 Eric-desktop localhost
127.0.1.1 Eric-desktop.home **Eric-desktop**

# The following lines are desirable for IPv6 capable hosts
#::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet ip6-localnet
ff00::0 ip6-mcastprefix ip6-mcastprefix
ff02::1 ip6-allnodes ip6-allnodes
ff02::2 ip6-allrouters ip6-allrouters
ff02::3 ip6-allhosts ip6-allhosts
```

---

