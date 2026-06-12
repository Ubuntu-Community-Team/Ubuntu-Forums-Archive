---
title: "newuser shell script"
date: 2014-05-10
forum: General Help
---

### Post by billy14 on 2014-05-10
Hello there! :) 
I am searching for adding newuser shell script. I mean ... everyone to can add themselves in the syste. Something like, they ssh to server, and in username just type newuser, and after this, they fillout username, password, email, name, etc. ... ? Can somebody have a suggestion? Or give me some link url with examples? Please.

---

### Post by SeijiSensei on 2014-05-10
That's really a bad idea.  You do realize that, on the Internet, letting "everyone" do something like that will open your server up to exploitation, no?

Also there is the problem that only root can create new accounts, so they would have to have root privileges during the initial request.  

If someone wants an account on your machine, have them email the request to you.  If it's your machine then you need to administer it in a responsible manner.

---

### Post by TheFu on 2014-05-10
welcome to the forums.
The power to create a user is the power to destroy a system. It should NOT be allowed to the uninitiated.  It is a terrible, terrible idea. It is hard to explain the 500 reasons why this is a terrible idea.

However, you could use sudoers to strictly manage the inputs to the existing adduser/useradd programs (I get confused as to which is nearly complete and which is lower-level control) - be certain to prevent the uid/directory/shell options!  Allowing those means someone could take over any other userid on the machine.

If you want to run something like an ISP does it - check out the "Perfect Server" how-to guide on howtoforge.com.


If you don't believe me, let me create a user on your box ... please.  I'll own the entire machine after 1 command.

---

### Post by Lars Noodén on 2014-05-10
There are a lot of ways that allowing random visitors to create shell accounts could go wrong.  However, it is doable, with enough constant oversight.  One living example is [Grex](http://www.grex.org/newuser/).  You might take contact with them and see if there are any tips they are willing to share.  You will have to set up the defaults to limit or prevent various activities in order to constrain the potential of misuse.

---

### Post by TheFu on 2014-05-10
> **Lars Noodén said:**
> There are a lot of ways that allowing random visitors to create shell accounts could go wrong.  However, it is doable, with enough constant oversight.  One living example is [Grex](http://www.grex.org/newuser/).  You might take contact with them and see if there are any tips they are willing to share.  You will have to set up the defaults to limit or prevent various activities in order to constrain the potential of misuse.

Scanned the grex website.  They capture login request data, but manually create the accounts later. It also reads as if initial accounts get a restricted shell only, until payment is made.  Seems they are running a restrictive firewall to prevent all sorts of abuse from their systems.  This is vastly different from allowing automatic account creation.

If you want someone to ssh in as "newuser", then run only 1 program that appends to a text file, csv file or DB, then kicks them out ... that is relatively easy.  Just create a script that asks the questions you want, and writes the answers to a text file, csv, DB ... then ends. Make that script the login shell for "newuser" ....   I'd use perl with the "taint" checking enabled to avoid commonly used exploits in shell scripts. Then daily, hourly, weekly, someone manually reviews the requests to ensure nothing "bad" has been requested (for all values of "bad"), and create the accounts.  Then email the temporary password to the email address supplied.  Of course, those email addresses could be mistyped and the possibility of massive abuse is huge.  Definitely do this on someone elses network - at a vps.

---

### Post by billy14 on 2014-05-10
okay, then some suggestions for make web interface with html, php and sh for adding new user easy?


But I am just run a virtual machine, and want to do some experiment, with users behavior. And is not risky ... cuz this virtual machine is for this test. Just for that:)

---

### Post by TheFu on 2014-05-10
> **billy14 said:**
> okay, then some suggestions for make web interface with html, php and sh for adding new user easy?


But I am just run a virtual machine, and want to do some experiment, with users behavior. And is not risky ... cuz this virtual machine is for this test. Just for that:)

A VM on your network is extremely powerful for abuse. Using it to launch attacks internally towards other machines. Be very careful if you allow unknown users.  I wouldn't.

If the VM is at a hosting provider, go for it!

---

### Post by SeijiSensei on 2014-05-10
Because PHP scripts run with the permissions of the "user" running the webserver, a user called "www-data" in Ubuntu, they cannot execute programs which require root either.  I've worked around this problem by having the script drop a file with the required information into a directory and running a shell script as root from cron that checks for any file(s) and executes the required command.

If this machine is on a local network with **no** exposure to the Internet, then go ahead and experiment I guess.  I would definitely block any outbound traffic from this machine to IP addresses outside the local network.

Suppose the machine has address 192.168.1.100 on 192.168.1.0/24.  Then make sure you use iptables rules on the machine in question like these:
```

# default OUTPUT policy is deny
/sbin/iptables -P OUTPUT deny
# allow traffic from this machine to others on local network
/sbin/iptables -A OUTPUT -s 192.168.1.100 -d 192.168.1.0/24 -j ACCEPT

```

---

### Post by billy14 on 2014-05-10
Seems good, but I still miss the newuser shell script.

---

