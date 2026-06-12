---
title: "root isn't accepting password"
date: 2013-06-22
forum: General Help
---

### Post by AbhimanyuAryan on 2013-06-22
since i updated my ubuntu i am not able to login as
root but i know i am rooted if u have any solution plz let me know. I
go to login screen type root and then password but it doesn't
recognize my password however i can get root access in terminal by
typing sudo su

plz explain me well i am a newbie just installed ubuntu 12.10 thanks in advance:P:P

---

### Post by Bashing-om on 2013-06-22
[COLOR=#000000]AbhimanyuAryan; Hello,

See if this applies to your situation:
[/COLOR]

1. At the login screen, press Ctrl+Alt+F1 to get to the console.
2. Log in there.
3. Check if ".ICEauthority" is owned by you:
```

ls -al .ICEauthority

```
4. If it isn't (but possibly by root), change it to you:
```

sudo chown USERNAME:USERNAME .ICEauthority

``` Where "USERNAME" is your own login name !
5. Switch back to the login screen by pressing Ctrl+Alt+F7 or F8
6. Try again to log in.
7. Better take a look at the permissions on ~/.Xauthority, too. It often gets changed when ~/.ICEauthority gets changed. The same fix applies.


If it worked, see here about a possible cause:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)[INDENT=3]
just try'n to help

[/INDENT]

---

### Post by ajgreeny on 2013-06-22
> **AbhimanyuAryan said:**
> since i updated my ubuntu i am not able to login as
root but i know i am rooted if u have any solution plz let me know. I
go to login screen type root and then password but it doesn't
recognize my password however i can get root access in terminal by
typing sudo su

plz explain me well i am a newbie just installed ubuntu 12.10 thanks in advance:P:P

Have you actually set up your system to be able to login as root?
By default in Ubuntu the root account is disabled and you would have had to enable it to be able to do what you're trying to.  If you have not done so (and I'm not going to tell you how to do it) you will simply need to use sudo, just like everybody else who uses Ubuntu.

See **RootSudo** in my signature for all details

---

### Post by grahammechanical on 2013-06-22
Are you saying that during installation you choose "root" as the user name? Have you set up a user called "root?" To open a terminal you must first log in. It is not wise to run Ubuntu as root. You will be loosing a large benefit of installing Ubuntu.

What do you want to do that requires you to be root user? Ordinary use of Ubuntu does not require that. Ubuntu is especially designed for people who do not understand these things and do not want to or need to understand them. 

Regards.

---

### Post by AbhimanyuAryan on 2013-06-23
sir i looged out and tried to enter ctrl+alt+F1 nothing happened tried several times.....restarted and again tried still the same.......plz help

---

### Post by AbhimanyuAryan on 2013-06-23
i putted my username as cooldudeabhi then rooted it via sudo passwd root command but since i updated root doesn't accept my password it says invalid password and i am sure that i am rooted able to access sudo su via terminal

---

### Post by sudodus on 2013-06-23
> **ajgreeny said:**
> Have you actually set up your system to be able to login as root?
By default in Ubuntu the root account is disabled and you would have had to enable it to be able to do what you're trying to.  If you have not done so (and I'm not going to tell you how to do it) you will simply need to use sudo, just like everybody else who uses Ubuntu.

See **RootSudo** in my signature for all details
+1

---

### Post by steeldriver on 2013-06-23
There should be no circumstances in which you need to start a GUI session as root - your first post says you can get root access in the terminal of your regular user account (btw it is usually better to do 'sudo -i' instead of 'sudo su' - see [https://help.ubuntu.com/community/RootSudo#Special_notes_on_sudo_and_shells](https://help.ubuntu.com/community/RootSudo#Special_notes_on_sudo_and_shells) )

If you need to start individual GUI programs as root (for example, to use the nautilus file manager with root permission to move system files) you can do so using gksudo e.g.

```
gksudo nautilus
```

---

### Post by AbhimanyuAryan on 2013-06-23
i have just got 13.04 update notification if i update do i need to follow the root procedure again?

---

### Post by sudodus on 2013-06-23
Please read very carefully the instructions how to use sudo (and gksudo) instead of running your system from the user root. This is because of security. You need not activate root as a user.

Many graphic user interface programs manage the superuser privileges automatically: You get a window, where you enter your password (if your user id has privileges to do such things). And the program continues with its task.

If it is your computer and you are the first user, then you have privileges to run sudo (and gksudo) and run all the qualified tasks, that need superuser privileges.

-o-

Example 1: Update and upgrade the system in the terminal window.

```
 sudo apt-get update
```

[sudo] password for aryan: [Write your password here. There is no echo, but it is OK. Finish with the ENTER key.]

Then the lists are updated. Then run the second command.

```
 sudo apt-get dist-upgrade
```

Now the privileges are still valid (10-15 minutes after the first time you wrote the password). So you upgrade the packages that need it.

Example 2: Update and upgrade the system with the GUI program.

Start the program. Fill in the password in the window, that asks for it, and let the program continue to work.

(The same things are carried out under the hood.)

---

### Post by ajgreeny on 2013-06-23
> **AbhimanyuAryan said:**
> i have just got 13.04 update notification if i update do i need to follow the root procedure again?

Which root procedure?

We keep telling you there is no need to login as root, but you seem not to be able to take that advice.

---

### Post by deadflowr on 2013-06-23
If you ran sudo passwd root, all you did was give root a new password.
Your sudo password should still work for your username.
Root is one user, and your username is another.
Giving root a password doesn't affect your username, unless you also disabled your username.

---

