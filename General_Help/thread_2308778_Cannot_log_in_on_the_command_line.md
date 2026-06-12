---
title: "Cannot log in on the command line"
date: 2016-01-05
forum: General Help
---

### Post by daryl9 on 2016-01-05
I am evaluating ubuntu, actually the edubuntu version, 14.04.3LTS.  I did a fresh install, created my user and set a password.  I want to be able to log into the command line via CTRL + ALT + F1.  I know my user name and password, but I continually get "Login Incorrect".

Is there something preventing a person from logging in via the command line?

Thanks

Daryl

---

### Post by Bashing-om on 2016-01-05
daryl9; Well ...

As one thought - been there I did this - verify case sensitivity of the password .
Did you accidentally input the password in the installer stage in uppercase - or upper case set when inputting the password in the interface ?

Else, from grub's recovery console - root access - verify that "you" own the
.Xauthority
.ICEauthority 
files in your /home directory .

[INDENT][INDENT]just a thought
[/INDENT][/INDENT]

---

### Post by steeldriver on 2016-01-05
@Bashing-om I don't think .Xauthority / .ICEauthority should affect CLI logins

Like you say, password case is a common gotcha

Second would be something funky about the keyboard or language settings (are there accented characters in the password?)

Third would be mistaking the user's full name (John Smith) for the actual login name (jsmith) - this is quite a common mistake, since the GUI login manager displays the full name

---

### Post by daryl9 on 2016-01-05
> **steeldriver said:**
> @Bashing-om I don't think .Xauthority / .ICEauthority should affect CLI logins

Like you say, password case is a common gotcha

Second would be something funky about the keyboard or language settings (are there accented characters in the password?)

Third would be mistaking the user's full name (John Smith) for the actual login name (jsmith) - this is quite a common mistake, since the GUI login manager displays the full name

Thanks for the replies.  

Case sensitivity is not an issue.  I know what password I typed in, and I know what case I typed it in.   However,  I suspect that the user name may be an issue.  I'm actually in the process of doing a reinstall.  I wasn't happy with the way things were initially setup, so I decided to reinstall the OS. During this install, I'm going to try a different user name and see if that makes a difference.

Thanks

Daryl

---

### Post by Bashing-om on 2016-01-05
daryl9; :)

Please to keep us advised .

[INDENT][INDENT]good things happen too
[/INDENT][/INDENT]

---

### Post by daryl9 on 2016-01-05
> **Bashing-om said:**
> daryl9; :)

Please to keep us advised .[INDENT][INDENT]good things happen too
[/INDENT]
[/INDENT]



Hello all.

I completed the reinstall.  This time I used a simpler user name and I am now able to log in on the command line.  I am also suspecting that the keyboard might have an issue, causing the password not to be typed correctly.  The equipment that I am using is used.  I'll have to do some maintenance cleaning up sticky keys etc...

Thank you for your help and suggestions.  I always appreciate it.

Daryl

---

### Post by Habitual on 2016-01-05
> **daryl9 said:**
> This time I used a simpler user name and I am now able to log in on the command line.Can you clarify this please?

---

### Post by yetimon_64 on 2016-01-05
> **daryl9 said:**
> Hello all.

I completed the reinstall.  This time **I used a simpler user name and I am now able to log in on the command line**.  I am also suspecting that the keyboard might have an issue, causing the password not to be typed correctly.  The equipment that I am using is used.  I'll have to do some maintenance cleaning up sticky keys etc...

Thank you for your help and suggestions.  I always appreciate it.

Daryl

I suspect you may have initially hit a known bug with the ubuntu installer. It will let by a user-name with upper case or non standard characters in use. This will cause authentication problems on trying to access a tty terminal, as you initially noted. But you can still log in graphically under these circumstances.

However if you've reset the user name now to one with no capitals or other non standard characters involved your new set up is likely to work perfectly. 

A simple command "whoami" posted here would have shown the character, most likely masked with an underscore "_" in the terminal. Cheers, yeti.

---

