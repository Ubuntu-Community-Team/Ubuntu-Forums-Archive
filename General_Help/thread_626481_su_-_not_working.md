---
title: "su - not working"
date: 2007-11-29
forum: General Help
---

### Post by N-t-F on 2007-11-29
Hello everyone!

I use Ubuntu Feisty Fawn and have a problem with the command su.

I've been startled to see that:

```
su -
```
followed by root's password did not work (su: Authentication failure). I tried several times to be sure it wasn't a typo. So I pressed Ctl-Alt-F6 to and tried to log as root in the console, which worked.

Furthermore, trying to do: ```
su - usertest
``` and typing usertest's password gives me the following message: ```
initgroups: Opération non permise
```(forbidden operation).

Oh, and I've checked that /bin/su belongs to root with rights 755...

Never stumbled on such an issue before (even with Feisty Fawn on the same hardware config). Any help would be really appreciated.

---

### Post by oscarsfriend on 2007-11-29
By default Ubuntu doesn't have a root account (or at least it doesn't have a password).  It gives superuser privileges (via the sudo command) to the account you created when you installed Ubuntu.  You should be able to manually create a root account with a password if you really need one.

EDIT: You say that you can login as root, so that can't be it.  Sorry.  Maybe this has something to do with PAM?  Check: /etc/pam.d/su

---

### Post by broggyr on 2007-11-29
I was able to go to System > Users & Groups (in Xubuntu) and manually change the root password (since I am prompted to enter my sudo password to do this).  While I still cannot login as root, I can log into a terminal as su and run commands as root such as editing various files or even running Thunar to move stuff.  Thunar even reminds you, because you are using the root account, to be careful! :)

---

### Post by posterboy on 2007-11-29
Try this one: sudo su -

---

### Post by N-t-F on 2007-11-29
> **posterboy said:**
> Try this one: sudo su -I get ```
sudo: must be setuid root
```

And I'll try to check PAM, thank you :)

---

### Post by viking777 on 2007-11-29
Try this:

```
sudo -s 
```

---

### Post by N-t-F on 2007-11-29
> **viking777 said:**
> Try this:

```
sudo -s 
```When I try this from my account, I get the "must be setuid root" message. When I log in as root, I get nothing, not even an error message.

Oh, but I guess I owe you some context about this strange behaviour. It started after I've played around with iptables and chmod...

Regarding iptables, I've made sure to flush them and ```
iptables -L -v
```confirms that they're back to the default permissive policies.

As to chmod, I used it to put rights 700 to /usr/bin/sudo, /bin/su, /bin/chown and /bin/chmod. But I've put them back to rights 755 afterwards (ls -al confirms this).

_Edit:_ Ooops, one more thing to know is that accounts are based on a NIS server, except for root and a single local account (which is the sudoer, but cannot use su - any better than normal accounts).

---

### Post by N-t-F on 2008-03-07
I have forgotten to let you know that the problem is solved. Rights on /bin/su should not be: ```
-rwxr-xr-x
```but```
-rwsr-xr-x
```and that was the problem. Now, I don't know how I happened to change them, but here you go.

Thanks for your help.

---

