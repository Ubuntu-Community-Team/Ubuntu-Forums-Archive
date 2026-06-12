---
title: "How to quickly secure Xubuntu against casual mischief?"
date: 2014-10-05
forum: General Help
---

### Post by Maximus559 on 2014-10-05
Hi, everybody. I've run across a security problem that I'm hoping the forum community can help me with.

I have Xubuntu 14.04 installed on my laptop. It's configured to log me in automatically at startup, never lock my screen during suspend / resume cycles, etc., because 99% of the time, this is what I want. However, from time to time, I have to leave my machine unattended for a while, and would like to lock out any casual troublemaker who might wander by.

Here's the problem: if I lock my screen with Light Locker, I can restart the machine from the lock screen and Xubuntu will log me in automatically! Same problem if I log out entirely. Amazingly, there doesn't seem to be a way to control Xubuntu's startup behavior vis-a-vis automatic login.

I can't be the first user to come across this design flaw. Any advice? Remember, the solution has to be quick and easy, so anything involving several pages of terminal commands is not going to cut it.

Thanks in advance.

---

### Post by pqwoerituytrueiwoq on 2014-10-05
add 'actions buttons' to your panel, you can lock the screen from that

---

### Post by Maximus559 on 2014-10-05
> **pqwoerituytrueiwoq said:**
> add 'actions buttons' to your panel, you can lock the screen from that
I don't mean to be rude, but did you even read my post? Locking the screen is not enough. Anybody with half a brain can just reboot the machine from the lock screen, and bam, they're in.

---

### Post by SuperFreak on 2014-10-05
Stating the Obvious here:Simple solution without terminal commands would be to enable password logon at start up

---

### Post by Maximus559 on 2014-10-05
> **SuperFreak said:**
> Stating the Obvious here:Simple solution without terminal commands would be to enable password logon at start up
Please describe the process for doing this. I can't find a check box anywhere. My user account is already set to "Password: asked on login," but that doesn't stop the system from logging me in automatically at startup.

As I recall, it IS possible to configure automatic login behavior during the installation process. What happens to this option after installation is complete?

---

### Post by matt_symes on 2014-10-05
Hi

> **Maximus559 said:**
> Please describe the process for doing this. I can't find a check box anywhere. My user account is already set to "Password: asked on login," but that doesn't stop the system from logging me in automatically at startup.

As I recall, it IS possible to configure automatic login behavior during the installation process. What happens to this option after installation is complete?

You used to have to remove yourself from the group ```
nopasswdlogin
```

It's been a while since i had passwordless login enabled on any machine so this may have changed for all i know.

Anyway, to test this, can you open a terminal and type ```
groups
```

Post the results back here. If you are a member of the nopasswdlogin group, and that is still how booting directly to desktop is achieved then it should just be a matter of removing yourself from that group and rebooting.

Kind regards

---

### Post by vasa1 on 2014-10-05
> **Maximus559 said:**
> I don't mean to be rude, but did you even read my post? Locking the screen is not enough. Anybody with half a brain can just reboot the machine from the lock screen, and bam, they're in.

It is coming across as less than polite if not rude ;) Your "casual" isn't defined. but seems to exclude those with half a brain and more.

Maybe you could explain why you chose to configure your machine > ... to log me in automatically at startup, never lock my screen during suspend / resume cycles, etc., because 99% of the time, this is what I want. ...

And that's what is happening. Entering a password isn't really that much of a headache compared to the extent of security provided. I know password protection isn't the absolute solution. As you've pointed out, anyone can reboot. As others have pointed out repeatedly: **physical access = game over**.

---

### Post by Maximus559 on 2014-10-05
Okay, my apologies... let me start over.

I don't worry too much about my machine's security, as I don't store anything sensitive on it. Whenever I install Xubuntu, I'm able to chose whether or not I want to be logged in automatically at startup. For the sake of convenience, I always enable automatic login. However, I would like to be able to reverse this decision temporarily when the occasion calls for it.

To clarify: the way things are now, I turn on my machine, and thirty seconds later, I'm sitting at an idle desktop. This is the default behavior for a single user install of Windows 98 or XP, for example. What I would like to see is the default behavior for any multi-user system: I turn on my machine and hit a login screen.

I realize that physical access = game over, so this doesn't need to be bulletproof. It just needs to confound the average non-technical computer user.

Note: I am already not a member of the nopasswdlogin group. If I manually log out after the system has started, I do need to enter a password if I want to log in again.

---

### Post by matt_symes on 2014-10-05
Hi

Sounds like it may have changed since i last booted straight to desktop.

Can we try something ?

From here - last edited in July 2014:

[https://wiki.ubuntu.com/LightDM](https://wiki.ubuntu.com/LightDM)

```
grep autologin-user /usr/share/lightdm/lightdm.conf.d/*.conf /etc/lightdm/lightdm.conf.d/*.conf /etc/lightdm/lightdm.conf
```

Does that command provide any useful output ?

Kind regards

---

### Post by CantankRus on 2014-10-06
Easiest solution seems to be enable password login.
But maybe you could use xtrlock to lock and blank the screen.
Nothing stopping anyone hitting the power button though.

> _**DESCRIPTION**_

xtrlock locks the X server till the user enters their password at the keyboard.
While xtrlock is running, the mouse and keyboard are grabbed and the mouse cursor becomes a padlock. Output displayed by X programs, and windows put up by new X clients, continue to be visible, and any new output is displayed normally.

The mouse and keyboard are returned when the user types their password, followed by Enter or Newline. If an incorrect password is entered the bell is sounded. Pressing Backspace or Delete erases one character of a password partially typed; pressing Escape or Clear clears anything that has been entered.

If too many attempts are made in too short a time further keystrokes generate bells and are otherwise ignored until a timeout has expired.

The X server screen saver continues to operate normally; if it comes into operation the display may be restored by the usual means of touching a key (Shift, for example) or the mouse.  

_**OPTIONS**_

-b
blank the screen as well as displaying the padlock

```
sudo apt-get install xtrlock
```

```
xtrlock -b
```

---

### Post by Maximus559 on 2014-10-06
> **matt_symes said:**
> Hi

Sounds like it may have changed since i last booted straight to desktop.

Can we try something ?

From here - last edited in July 2014:

[https://wiki.ubuntu.com/LightDM](https://wiki.ubuntu.com/LightDM)

```
grep autologin-user /usr/share/lightdm/lightdm.conf.d/*.conf /etc/lightdm/lightdm.conf.d/*.conf /etc/lightdm/lightdm.conf
```

Does that command provide any useful output ?

Kind regards

Thank you for the pointer! Deleting lightdm.conf produces the desired result.

May I say that **there should be a GUI option for this!** This took way too long to figure out.

---

### Post by matt_symes on 2014-10-06
Hi

> **Maximus559 said:**
> Thank you for the pointer! Deleting lightdm.conf produces the desired result.

Excellent and thanks for posting back your solution. I will mentally update my information.

> May I say that **there should be a GUI option for this!** This took way too long to figure out.

I delegate you to write it :)

Kind regards

---

