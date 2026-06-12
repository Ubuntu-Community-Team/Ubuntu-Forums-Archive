---
title: "[SOLVED] Is there any way I can run admin programs without having to type in a"
date: 2008-02-23
forum: General Help
---

### Post by WarMonkey on 2008-02-23
Is there any way I can stop administrative programs from asking for my password?

On startup, I have it so I login automatically, but nm-applet also starts up (it asks for my password) so the automatic login is really useless.

Is there a way I can bypass this?

---

### Post by Sam Lars on 2008-02-23
You can use /etc/sudoers to add applications that will not need a root password to open.

---

### Post by Yellow Pasque on 2008-02-23
As annoying as it may be, you should probably leave the security meaasure in place, unless you want your Ubuntu system to be as wide-open as your Windows system :)

---

### Post by irishgoth8822 on 2008-02-23
> **Sam Lars said:**
> You can use /etc/sudoers to add applications that will not need a root password to open.


how do you do that?

can you add a file to the sudoers file so that regular uses can access certain files without a password? ive been having issues with my sudo command and being able to access and write '/etc/hosts' without a password would be fantastic.

---

### Post by WarMonkey on 2008-02-24
It still asks for my password when I tried to sudo. What gives?

Here is my /etc/sudoers:

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Defaults

Defaults	!lecture,tty_tickets,!fqdn

# Uncomment to allow members of group sudo to not need a password
%sudo ALL=NOPASSWD: ALL
%warmonkey ALL=NOPASSWD: ALL
%admin ALL=NOPASSWD: ALL
warmonkey ALL=NOPASSWD: ALL
# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL
natural ALL=(ALL) ALL
%admin ALL=(ALL) ALL

---

### Post by Sam Lars on 2008-02-24
It's not really a good idea to let yourself run things without a password.  It may seem convenient, but there's a reason it's set up the way it is.  It's much less secure if you unlock it like that...

---

### Post by imoatama on 2008-02-24
What password is nm-applet asking for? Surely it's just your wireless network password right? You should be able to store that with keyring manager, and then give nm-applet the permanent right to access such keys on the keyring.

---

### Post by Yellow Pasque on 2008-02-25
> **irishgoth8822 said:**
> how do you do that?

can you add a file to the sudoers file so that regular uses can access certain files without a password? ive been having issues with my sudo command and being able to access and write '/etc/hosts' without a password would be fantastic.
```
cd /etc
su
visudo sudoers
```

---

### Post by bodhi.zazen on 2008-02-25
If you want to do this be warned, it is really not such a good idea.

Read these links :

[http://www.debian-administration.org/articles/33](http://www.debian-administration.org/articles/33)

	[http://www.gratisoft.us/sudo/man/sudoers.html](http://www.gratisoft.us/sudo/man/sudoers.html)

---

### Post by WarMonkey on 2008-02-25
> **imoatama said:**
> What password is nm-applet asking for? Surely it's just your wireless network password right? You should be able to store that with keyring manager, and then give nm-applet the permanent right to access such keys on the keyring.

No, it asks for my own password; not the wep key. It does this with all administrative programs (such as network-admin).

Also, bodhi.zazen, I tried the links, but no luck.

Here is an updated /etc/sudoers:

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Defaults

Defaults	!lecture,tty_tickets,!fqdn

# Uncomment to allow members of group sudo to not need a password
%sudo ALL=NOPASSWD: ALL
%warmonkey ALL=NOPASSWD: ALL
%admin ALL=NOPASSWD: ALL
warmonkey ALL=NOPASSWD: ALL
# Host alias specification

# User alias specification
User_Alias      ADMINS = warmonkey,jewman
# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL
natural ALL=(ALL) ALL
%admin ALL=(ALL) ALL
ADMINS      ALL = ALL
```

Is there anything wrong with this file?

---

### Post by WarMonkey on 2008-02-25
I also forgot to mention that immediately after I type in:

```
sudo visudo -f /etc/sudoers
```

I get this message:

```
E325: ATTENTION
Found a swap file by the name "/etc/.sudoers.tmp.swp"
          owned by: root   dated: Mon Nov 26 10:54:08 2007
         file name: /etc/sudoers.tmp
          modified: YES
         user name: root   host name: ubuntu
        process ID: 4315
While opening file "/etc/sudoers.tmp"
             dated: Mon Feb 25 16:21:08 2008
      NEWER than swap file!

(1) Another program may be editing the same file.
    If this is the case, be careful not to end up with two
    different instances of the same file when making changes.
    Quit, or continue with caution.

(2) An edit session for this file crashed.
    If this is the case, use ":recover" or "vim -r /etc/sudoers.tmp"
    to recover the changes (see ":help recovery").
    If you did this already, delete the swap file "/etc/.sudoers.tmp.swp"
    to avoid this message.
"/etc/sudoers.tmp" 25L, 593C
Press ENTER or type command to continue

```

I noticed it comes up every time I edit sudoers, but sudoers itself is OK.

---

### Post by bodhi.zazen on 2008-02-25
first, you should ALWAYS use visudo to make your edits.

second, follow the instructions in the error message.

Third , you are putting users in the groups section and groups in the users section. I do not think sudoers likes that.

See the post I make in this blog : [http://php.8ez.com/drsmall/blog/?p=187](http://php.8ez.com/drsmall/blog/?p=187)

---

### Post by aysiu on 2008-02-25
How often do you use administrative applications?

If it's just the network manager issue, this may help:
[Howto: Get Network Manager to stop asking you for your keyring password (pam_keyring)](http://ubuntuforums.org/showthread.php?t=192281)

---

### Post by Yellow Pasque on 2008-02-26
> **WarMonkey said:**
> I also forgot to mention that immediately after I type in:
```
sudo visudo -f /etc/sudoers
```
I get this message:

Even when you use visudo, the default save name is sudoers.tmp. Apparently, you saved to this name somewhere along the way. To remedy, use Applications -> System Tools -> Root Terminal (you can add this by right-clicking on the word 'Applications' and selecting 'Edit Menus'). Then:
```
cd /etc
chmod 600 sudoers.tmp
rm sudoers.tmp
```

---

### Post by imoatama on 2008-02-26
You can stop nm-applet from perstering for a password by going into System->Administration->Keyring Manager, selecting the passwords used by nm-applet, clicking the Applications tab and adding nm-applet as an app that has access to those passwords.

---

### Post by WarMonkey on 2008-02-29
For some reason, after a fresh install of Hardy Heroin, I am able to use sudo without it asking for my password.

There is one problem though, Hardy Heron sucks. But, I guess it's okay since it's still in alpha. :)

Problem solved, how do I close topics? Or do admins do that?

---

### Post by Sam Lars on 2008-02-29
> **WarMonkey said:**
> For some reason, after a fresh install of Hardy Heroin, I am able to use sudo without it asking for my password.

That sounds more like a bug... but if that fits your needs, then that's cool.

> **WarMonkey said:**
> There is one problem though, Hardy Heron sucks. But, I guess it's okay since it's still in alpha.

Yes, but it gets to beta by people submitting bugs...
Please look to see if any of the problems you have are already bugs (including the sudo thing), and if they're not, report them.

> **WarMonkey said:**
> Problem solved, how do I close topics? Or do admins do that?

At the top op the thread there is a dropdown called Thread Tools.  Select Mark as Solved.

---

