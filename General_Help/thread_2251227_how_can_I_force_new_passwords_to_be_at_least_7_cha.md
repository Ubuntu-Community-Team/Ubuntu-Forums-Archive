---
title: "how can I force new passwords to be at least 7 characters long?"
date: 2014-11-02
forum: General Help
---

### Post by eltiti55555 on 2014-11-02
Hi,

I would like to know how I can force new passwords to be 7 characters long?

Also, how can I change the password of current users and make them 7 characters long?

Thanks!

---

### Post by 1clue on 2014-11-02
[http://manpages.ubuntu.com/manpages/hardy/man8/pam_passwdqc.8.html](http://manpages.ubuntu.com/manpages/hardy/man8/pam_passwdqc.8.html)

---

### Post by eltiti55555 on 2014-11-02
> **1clue said:**
> [http://manpages.ubuntu.com/manpages/hardy/man8/pam_passwdqc.8.html](http://manpages.ubuntu.com/manpages/hardy/man8/pam_passwdqc.8.html)

I don't really understand that, and that doesn't seem to be a command...

---

### Post by Irihapeti on 2014-11-02
> **1clue said:**
> [http://manpages.ubuntu.com/manpages/hardy/man8/pam_passwdqc.8.html](http://manpages.ubuntu.com/manpages/hardy/man8/pam_passwdqc.8.html)

This isn't helpful to the OP. More detail is needed - please elaborate.

---

### Post by mastablasta on 2014-11-03
> **Irihapeti said:**
> This isn't helpful to the OP. More detail is needed - please elaborate.

sure it is - it says which application does it as well as how to do it:

> 
[h=4]**DESCRIPTION**[/h]     The **pam_passwdqc** module is a simple password strength checking module for
     PAM.  In addition to checking regular passwords, it offers support for
     passphrases and can provide randomly generated passwords.

> 
The following options may be passed to the module:

     **min**=_N0_,_N1_,_N2_,_N3_,_N4_
             (**min**=**disabled**,24,12,8,7) [U][I][B]The minimum allowed password lengths for
             different kinds of passwords/passphrases.[/B][/I][/U]  The keyword **disabled**
             can be used to disallow passwords of a given kind regardless of
             their length.  Each subsequent number is required to be no larger
             than the preceding one.


---

### Post by Elfy on 2014-11-03
> **mastablasta said:**
> sure it is - it says which application does it as well as how to do it:

Then use the information to help the OP who obviously has a problem understanding the man pages.

---

### Post by matt_symes on 2014-11-03
Hi

I understand that the manual pages are not always the easiest to read and they don't always tell the full story, so...

Open a terminal and type

```
sudo apt-get install libpam-passwdqc
```

This will install the package: libpam-passwdqc and its dependencies libpasswdqc0 and passwdqc.

Here's a brief description

```
matthew-laptop:/home/matthew % apt-cache search passwdqc                      
libpam-passwdqc - PAM module for password strength policy enforcement
libpasswdqc-dev - password checking and policy enforcement library (devel)
libpasswdqc0 - password strength checking and policy enforcement library
passwdqc - password strength checking and policy enforcement toolset
matthew-laptop:/home/matthew % 
```

This will add an entry for pam_passwdqc.so to the file

```
/etc/pam.d/common-password
```

```
matthew-laptop:/home/matthew % grep passwdqc /etc/pam.d/common-password
password    requisite            pam_passwdqc.so 
matthew-laptop:/home/matthew %
```

You can add options by changing the file /etc/passwdqc.conf like so....

As always, make a backup file of any configuration files you change before you edit them.

```
sudo cp /etc/passwdqc.conf{,.bk}
```

First you need to open up the file using elevated privileges using you favourite editor. Below i using vim but you can use nano, gedit, mousepad or whatever editor you are comfortable with.

```
sudo vim /etc/passwdqc.conf
```

It is here that you can change any options for the password checking functionality.

Here is a reference from shotwell as they originally wrote it.

[http://www.openwall.com/passwdqc](http://www.openwall.com/passwdqc)

I should state that i have not tested this so if you have any problems then please post back and i'll double check my advice is correct. Also it goes without saying that you should check my advice yourself if this is a production system. You may have to add the options to /etc/pam.d/common-password instead you see.

Anyway, to immediately expire passwords, use the passwd command with the -e flag.

```
sudo passwd -e <username>
```

You should be able to create a simple script to loop over all the users expiring their passwords.

Kind regards

---

### Post by btindie on 2014-11-03
A simple google for 'ubuntu set min password length' brings up this page [https://help.ubuntu.com/lts/serverguide/user-management.html#password-policy](https://help.ubuntu.com/lts/serverguide/user-management.html#password-policy)

You don't need to install any additional modules to set a minimum password length policy, it uses the existing pam_unix module.

This one liner will update it to 7 characters, by default it's 6 (man pam_unix).
```
sudo sed -i -e '/^password.*pam_unix.so/s/$/ minlen=7/' /etc/pam.d/common-password
```
it simply appends ' minlen=7' onto the end of the correct line.

---

### Post by matt_symes on 2014-11-03
Hi

> **btindie said:**
> A simple google for 'ubuntu set min password length' brings up this page [https://help.ubuntu.com/lts/serverguide/user-management.html#password-policy](https://help.ubuntu.com/lts/serverguide/user-management.html#password-policy)

You don't need to install any additional modules to set a minimum password length policy, it uses the existing pam_unix module.

This one liner will update it to 7 characters, by default it's 6 (man pam_unix).
```
sudo sed -i -e '/^password.*pam_unix.so/s/$/ minlen=7/' /etc/pam.d/common-password
```
it simply appends ' minlen=7' onto the end of the correct line.

Nice !

I should have checked myself.

Kind regards

---

### Post by 1clue on 2014-11-03
Sorry to leave this hanging.  I put it in and went to bed, and since then everything else happened.

I  just googled "ubuntu password quality" and the link I sent seemed pretty self explanatory.

IMO just setting a minimum length is of little use.  Overall password quality would be my end goal.

It all seems to be taken care of here, so I'll step out.

---

