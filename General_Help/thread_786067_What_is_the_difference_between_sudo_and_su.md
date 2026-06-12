---
title: "What is the difference between sudo and su"
date: 2008-05-07
forum: General Help
---

### Post by hurinth on 2008-05-07
Hello. Just want to know the difference between 'sudo su root' and 'su'. For example:

> hurin@BREGO:~$ su
Password: 
su: Authentication failure

But if I use 'sudo su root' or just 'sudo su', the system takes my password.

---

### Post by kshtjsnghl on 2008-05-07
i think( i am not very sure) you need to prefix the su command with sudo because you are logged in as a user and you have to have privileges of the root user to switch the user to root or any other user..

---

### Post by damis648 on 2008-05-07
the command "su" instructs the terminal session to log in as root, so all commands are run as root. Sudo is an installed program that accepts the user password and runs the preceding command as root, but does not actually log in as root. The reason sudo su works is that you are running "su" or looging in as root with a root command. The sudo is the actual one accepting your password. (That is badly explained and probably does not make that much sense but re-read it and you will see what i mean :))

---

### Post by hurinth on 2008-05-07
> **damis648 said:**
> the command "su" instructs the terminal session to log in as root, so all commands are run as root. Sudo is an installed program that accepts the user password and runs the preceding command as root, but does not actually log in as root. The reason sudo su works is that you are running "su" or looging in as root with a root command. The sudo is the actual one accepting your password. (That is badly explained and probably does not make that much sense but re-read it and you will see what i mean :))


Hehe I do uderstand you. But now, I don't remember setting a password for root. The one I enter when issuing sudo su root, is my user password. How or where do I set up the root password?

---

### Post by mandrill on 2008-05-07
> **damis648 said:**
> the command "su" instructs the terminal session to log in as root, so all commands are run as root. Sudo is an installed program that accepts the user password and runs the preceding command as root, but does not actually log in as root. The reason sudo su works is that you are running "su" or looging in as root with a root command. The sudo is the actual one accepting your password. (That is badly explained and probably does not make that much sense but re-read it and you will see what i mean :))

Actually pretty well explained. I was gonna take a shot at it, but I realize when I'm in the presence of superior knowledge. My hat is off to you, sir! In effect, sudo is an ersatz and temporary way of running things as if you are root, but you are not? That is why you would be a "su-doer"?

---

### Post by ghost_ryder35 on 2008-05-07
> **hurinth said:**
> Hehe I do uderstand you. But now, I don't remember setting a password for root. The one I enter when issuing sudo su root, is my user password. How or where do I set up the root password?
under system, administration, users and groups
or
```

sudo passwd root

```

---

### Post by hurinth on 2008-05-07
OK now,  how do I switch to root?

I went to System>Users and Groups>, unlocked 'root' once, gave it password and everything, but how do I actually swap to root? and if I go now again to that place, root is again grayed out

---

### Post by hurinth on 2008-05-07
Right, so I can't completely be root as the link says... thats ok... but in that case, I can't even issue 'su' ever in Ubuntu?

[http://ubuntuforums.org/showthread.php?t=492010](http://ubuntuforums.org/showthread.php?t=492010)

---

### Post by heatpumpcontrol on 2008-05-07
> **hurinth said:**
> OK now,  how do I switch to root?

I went to System>Users and Groups>, unlocked 'root' once, gave it password and everything, but how do I actually swap to root? and if I go now again to that place, root is again grayed out

I'm still learning linux but from what I've gathered in the last year is that you don't need to log in as root as you would in Windows in either safe mode or in the regular environment when you have the log-in window set up to accept the Administrator. 

I understand your question. I had the same puzzling thoughts last year. Just like Vista now, in order to perform a serious function or installation, it will ask you for your password and if you're an administrator then the process will continue. 

Under linux, (ubuntu, not sure of others) you have administrative rights but, you need to tell them system that you are going to allow an action commanded and this is done by entering you password. Under the terminal, you are asked for your password but in order to perform an administrative function you must tell the system that you want to perform it as an "administrator" thus the need to preface it with "sudo". 

Hope this makes sense.

---

### Post by Ripfox on 2008-05-07
> **heatpumpcontrol said:**
> I'm still learning linux but from what I've gathered in the last year is that you don't need to log in as root as you would in Windows in either safe mode or in the regular environment when you have the log-in window set up to accept the Administrator. 

I understand your question. I had the same puzzling thoughts last year. Just like Vista now, in order to perform a serious function or installation, it will ask you for your password and if you're an administrator then the process will continue. 

Under linux, (ubuntu, not sure of others) you have administrative rights but, you need to tell them system that you are going to allow an action commanded and this is done by entering you password. Under the terminal, you are asked for your password but in order to perform an administrative function you must tell the system that you want to perform it as an "administrator" thus the need to preface it with "sudo". 

Hope this makes sense.


I like to > sudo nautilus

---

### Post by heatpumpcontrol on 2008-05-07
that would be 

```
gksudo nautilus
```

I see this as graphical sudo... which means to me that the root account is being graphically displayed and you can now change and delete anything without having to retype a password and it also bypasses the use of the terminal window.... meaning less commands.. you just do your editing. 

**[COLOR="Red"]BE CAREFUL![/COLOR]**

---

### Post by Ripfox on 2008-05-07
> **heatpumpcontrol said:**
> that would be 

```
gksudo nautilus
```

I just type sudo nautilus and it works fine.

Update: just tried both...no difference. Yea, you do have to be careful if you don't know what your doing. But if you do it's mad handy andy.

---

### Post by heatpumpcontrol on 2008-05-07
> **ripfox said:**
> I just type sudo nautilus and it works fine.

Update: just tried both...no difference.

OK, I've never tried it like that. Like I said, I'm still learning too.

---

### Post by Ripfox on 2008-05-07
> **heatpumpcontrol said:**
> OK, I've never tried it like that. Like I said, I'm still learning too.

I find it to be good when I have to move files around like dropping a new theme in for Pidgin ect...:)

I really need to learn how to use the cp command someday here soon ;)

---

### Post by heatpumpcontrol on 2008-05-07
one neat sript is nautilus open in terminal

```
sudo apt-get install nautilus-open-terminal
```

This inserts a command on right click that allows you to open the terminal with the directory already typed in... based on your current mouse location.

I use it all the time and it saves time. You don't have to deal with the cd command.

Update: you must reboot for it to take effect

---

### Post by hurinth on 2008-05-08
> **heatpumpcontrol said:**
> that would be 

```
gksudo nautilus
```

I see this as graphical sudo... which means to me that the root account is being graphically displayed and you can now change and delete anything without having to retype a password and it also bypasses the use of the terminal window.... meaning less commands.. you just do your editing. 

**[COLOR="Red"]BE CAREFUL![/COLOR]**
Thanks Heat.. one last thing: how should I return to normal user: gksudo user?

---

### Post by Ripfox on 2008-05-08
when you use > sudo nautilus it's just a temporary way to open your file system as root. when you close the terminal the session is over, returning you to normal user mode. As stated before, this command gives you complete control, so make sure not to delete anything important, just use it to perform specific tasks like moving files ect...

---

### Post by por100pre1 on 2008-05-08
> **ripfox said:**
> when you use  it's just a temporary way to open your file system as root. when you close the terminal the session is over, returning you to normal user mode. As stated before, this command gives you complete control, so make sure not to delete anything important, just use it to perform specific tasks like moving files ect...

Use this instead:

```
gksu nautilus
```

to use sudo in a graphical environment can change the permissions or ownership of some files used  by gnome, that's why gksu and gksudo are used in gnome programs. KDE users use this:

```
kdesu *kdeprogram*
```

---

### Post by Ripfox on 2008-05-08
> **por100pre1 said:**
> Use this instead:

```
gksu nautilus
```

to use sudo in a graphical environment can change the permissions or ownership of some files used  by gnome, that's why gksu and gksudo are used in gnome programs. KDE users use this:

```
kdesu *kdeprogram*
```

Maybe I'm missing something here, but when I use 

> sudo nautilus

I have the exact same abilities as when I use 

> gksu nautilus

Whats the difference again?

It changes the permissions permanently to what files? Random ones? That is a vague statement.

---

### Post by por100pre1 on 2008-05-08
> **ripfox said:**
> Maybe I'm missing something here, but when I use 



I have the exact same abilities as when I use 



Whats the difference again?

It changes the permissions permanently to what files? Random ones? That is a vague statement.

Ok, it seems like a vague statement, but it is NOT. Most of the time using sudo doesn't cause problems but that doesn't mean issues can't arise.

Here is another comment about it:

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Ripfox on 2008-05-08
> **por100pre1 said:**
> Ok, it seems like a vague statement, but it is NOT. Most of the time using sudo doesn't cause problems but that doesn't mean issues can't arise.

Here is another comment about it:

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Ahhh...thanks for the enlightenment. That is really interesting. I never knew about that issue.

---

