---
title: "Can't create file in /usr/share/keyrings even with sudo"
date: 2022-03-31
forum: General Help
---

### Post by klundermann on 2022-03-31
I am trying to add the Tor package repository.  The [instructions]("https://support.torproject.org/apt/") say to sudo
```
# wget -qO- https://deb.torproject.org/torproject.org/A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89.asc | gpg --dearmor | tee /usr/share/keyrings/tor-archive-keyring.gpg >/dev/null
```

but I get the error message:```
tee: /usr/share/keyrings/tor-archive-keyring.gpg: Permission denied
```

Permissions on /usr/share/keyrings are:```
drwxr-xr-x 2 root root
```

Shouldn't the superuser be able to create files there?

---

### Post by TheFu on 2022-03-31
Any ACLs?

---

### Post by klundermann on 2022-03-31
What's an ACL?

---

### Post by TheFu on 2022-03-31
> **klundermann said:**
> What's an ACL?

[https://www.redhat.com/sysadmin/linux-access-control-lists](https://www.redhat.com/sysadmin/linux-access-control-lists)  **getfacl**, **setfacl**.

There is also the immutable attribute.  **chattr**

And sometimes if there is a network share (typically samba), it will lock permissions on the top directory.  There was a different thread here about a user who couldn't delete files in his HOME.  Turned out he'd setup a samba share using some GUI tool for the directory. No way would anyone else know about that. After about 40 posts in the thread, it finally clicked for that person to consider it.

There's also aparmor and SELinux, but apparmor doesn't usually get in the way on systems where it is used.  Ubuntu doesn't install SELinux, so that shouldn't be important unless you've done something odd with it.

---

### Post by DuckHook on 2022-03-31
TOR's instructions are incomplete and, frankly, a bit sad. It assumes that you've invoked a root shell, which you can do with:```
sudo -s
```The rest of the command should then be fine.

If you want to avoid a root shell and just use a variant of the line in question, then you just need to tweak that line a bit as follows:```
wget -qO- https://deb.torproject.org/torproject.org/A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89.asc | sudo gpg --dearmor | sudo tee /usr/share/keyrings/tor-archive-keyring.gpg >/dev/null
```

When following online instructions in future, it pays to look at the # which basically says: "Do *everything* on this line as root." I suspect that your problem arose because you just used sudo on the first portion of the line (which doesn't actually need it) but didn't carry it over into the portions after the pipes (which do actually need it).

---

### Post by TheFu on 2022-03-31
I assumed the leading '#' on the line meant the commands were all being run from a root shell.
# == root shell
$ == normal user shell

---

### Post by DuckHook on 2022-03-31
> **TheFu said:**
> I assumed the leading '#' on the line meant the commands were all being run from a root shell.
# == root shell
$ == normal user shell
Understandable.

Also understandable are new users or those who rarely use the command line not knowing about this convention.

I believe OP may have just copy-pasted this line from the TOR site.

---

### Post by TheFu on 2022-04-01
> **DuckHook said:**
> Understandable.

Also understandable are new users or those who rarely use the command line not knowing about this convention.

I believe OP may have just copy-pasted this line from the TOR site.

And the TOR instructions didn't clearly say that '#' in a command prompt is for a root shell?
Just to be clear, ***every*** Unix book follows that convention and has for decades - probably 40-50 yrs. It is just one of those assumed knowledge things in the Unix world.  Hope this helps lurkers.

---

### Post by DuckHook on 2022-04-01
> **TheFu said:**
> And the TOR instructions didn't clearly say that '#' in a command prompt is for a root shell?
Actually, the TOR site is not a model of clarity. It says:> **Note:** The symbol # refers to running the code as root. This means you should have access to a user account with system administration privileges, e.g your user should be in the sudo group.Putting myself in the shoes of a newbie or someone who rarely uses the CLI:

[list=1]
[*]I *do* "have access to a user account with system administrator privileges",
[*]my user *is* in the sudo group,
[*]I *am* running the code as root when I preface the entire string with *sudo*,
[*]The understanding that *sudo* needs to be invoked for each piped segment requires a knowledge of pipes that the CLI newbie cannot be expected to have.
[*]Alternatively (and confusingly in this case), invoking a root shell before starting the whole process is discouraged in a lot of good advice that tells newbies to stick to just using *sudo*.
[/list]
Linux is not easy on newbies. Online instructions that are offered to the general public really should be more newbie friendly.

Moreover, even I, who've been around the block a few times, will sometimes miss the # in online instructions because it's a small single character detail lost in a line of what looks like dozens of characters of gobbledygook.
> Just to be clear, ***every*** Unix book follows that convention and has for decades - probably 40-50 yrs. It is just one of those assumed knowledge things in the Unix world.  Hope this helps lurkers.
We can't expect newbies to start their Linux journey with a deep dive into a -nix book. A lot just gather up their nerve and jump into it (like I did) and then learn to swim along the way. Surprisingly, I still haven't drowned yet! :)

---

### Post by ActionParsnip on 2022-04-01
Or:
```

[FONT=var(--ff-mono)]cd $HOME
wget https://deb.torproject.org/torproject.org/A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89.asc
[/FONT][FONT=var(--ff-mono)]sudo apt-key add <A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89.asc[/FONT][FONT=var(--ff-mono)]
[/FONT]
```

---

### Post by klundermann on 2022-04-03
Thank you so much, DuckHook and TheFu!  I have now executed```
wget -qO- https://deb.torproject.org/torproject.org/A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89.asc | sudo gpg --dearmor | sudo tee /usr/share/keyrings/tor-archive-keyring.gpg >/dev/null
```

without difficulty.  I knew that the # prompt indicated execution as root, but it had not occurred to me that a separate  sudo  was needed for each step in the chain of commands.

So, you've both solved my problem and taught me something.

---

### Post by TheFu on 2022-04-03
I think this would work:
```
$ wget -qO- [https://deb.torproject.org/torproject.org/A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89.asc](https://deb.torproject.org/torproject.org/A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89.asc) | gpg --dearmor | [COLOR="#FF0000"]**sudo**[/COLOR] tee /usr/share/keyrings/tor-archive-keyring.gpg >/dev/null
```
but I didn't try it.

Also, 
sudo $(wget -qO- [https://deb.torproject.org/torproject.org/A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89.asc](https://deb.torproject.org/torproject.org/A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89.asc) | gpg --dearmor | tee /usr/share/keyrings/tor-archive-keyring.gpg >/dev/null)
would group everything under a single sudo invocation. I didn't try it either.

Breaking the pipes into different parts produced an error on 20.04 here:
```
gpg: keyserver option 'ca-cert-file' is obsolete; please use 'hkp-cacert' in dirmngr.conf
gpg: no valid OpenPGP data found.
```

---

