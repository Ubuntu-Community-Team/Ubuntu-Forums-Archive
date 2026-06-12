---
title: "How to set a script to Always Execute as the Owner?"
date: 2015-11-07
forum: General Help
---

### Post by suaro on 2015-11-07
Hi Everyone,

Is there a way to set a bash script to always execute as the owner, regardless of who launches it ?
In a book I have specifically on Unix (/w touches on Linux) , it indicates the following should work.

chmod 4755 <scriptname>

However when I do this , the security context always seems to be the one who executed the script.

For example, I have a script called test.sh and the owner is root.  The script does a simple whoami .

-rwsr-xr-x 1 root root 8 Nov  7 18:20 test.sh


If I execute the script as User1, I'm hoping when the script executes the output of whoami will show root but it doesn't. It shows User1

Just checking with the experts to see if this can be done.

Thank you so much

---

### Post by suaro on 2015-11-07
I think I found my answer: [SIZE=2]http://unix.stackexchange.com/questions/364/allow-setuid-on-shell-scripts
[/SIZE]

---

### Post by Lars Noodén on 2015-11-08
One way around that is to put the script in /usr/local/bin/ or /usr/local/sbin/ read only but executable.  Then add a line to /etc/sudoers to grant privileges for just that script and nothing else, either with a password or without.  Then the script can be launched by any user with sudo.  

```

%users ALL=(ALL:ALL) NOPASSWD: /usr/local/bin/somescript ""

```

The empty quotes mean no options are allowed.

If you want to not have to type sudo, then make a second script to call the first script and have the users run that.

---

