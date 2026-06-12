---
title: "Just a black screen when I boot up..."
date: 2008-01-31
forum: General Help
---

### Post by Lehto on 2008-01-31
Hello.

I'm running LinuxMCE with kubuntu (Installation package with both kubuntu and LinuxMCE.)
For about two days ago I finally got the TV and all stuff to work.
And was going to start LinuxMCE I pressed the icon and nothing happend...
So I decided to reboot the computer (shouldn't have done that...) then it started to boot normally but after the kubuntu loading screen the LinuxMCE core is trying to start, but somehow it doesn't I let it be on over a night to see if something happend but it is at 0% all the time...
And I don't know how I can load only Kubuntu...? Before the linuxMCE core have started automaticly and then from there I can press "KDE Desktop" and then kubuntu is booting up.
I have tried to exit the LinuxMCE core start and then I just get a black scren and nothing happends...

I tried ctrl + alt + F1 and login and ran: 
```
sudo /etc/init.d/kdm stop
```
and then:
```
sudo /etc/init.d/kdm start
```
Then I get the error message: 
Lock Launch_manager (LM) Fail
LM already running

huh? what?:confused:

Plz help me to start my pc again finally when I got all to work then I can't start it... :(

//Lehto

---

### Post by Fixman on 2008-01-31
Just reboot on single mode (or use some tty), and modify KDE startup files. If you remove LinuxMCE and reboot, it should work correctly.

EDIT:

```

cd (home)/.kde/Autostart
ls
rm #LinuxMCE file
reboot

```

Remember to log in as root!

---

### Post by Lehto on 2008-01-31
> **Fixman said:**
> Just reboot on single mode (or use some tty), and modify KDE startup files. If you remove LinuxMCE and reboot, it should work correctly.

EDIT:

```

cd (home)/.kde/Autostart

```

Remember to log in as root!

when I run that commande it says: No such file or directory... :/
I'm sure I have a directory named /home atleast but rest I don't know :/

---

### Post by Fixman on 2008-01-31
> **Lehto said:**
> when I run that commande it says: No such file or directory... :/
I'm sure I have a directory named /home atleast but rest I don't know :/

You can change (home) with your home directory, but, if you don't want to log in as root just write:

On the third line, put the LinuxMCE file that gets written after ls.

```

cd ~/.kde/Autostart
ls
rm #LinuxMCE file
sudo reboot

```

---

### Post by Lehto on 2008-01-31
> **Fixman said:**
> You can change (home) with your home directory, but, if you don't want to log in as root just write:

On the third line, put the LinuxMCE file that gets written after ls.

```

cd ~/.kde/Autostart
ls
rm #LinuxMCE file
sudo reboot

```

Well I am logged in as root but still it says No such file or directory

Same happends when I write:
```

cd ~/.kde/Autostart

```

I don't have any directory named: .kde it seems like... :/

---

### Post by Fixman on 2008-01-31
> **Lehto said:**
> Well I am logged in as root but still it says No such file or directory

Same happends when I write:
```

cd ~/.kde/Autostart

```

I don't have any directory named: .kde it seems like... :/

Try the second commands (from my second post) **NOT** logged in as root.

---

### Post by Lehto on 2008-01-31
yes, now I am in the directory: ~/.kde but I can't find autostart...

when I run ls

it just show those things:
[COLOR="Cyan"]cache-dcerouter[/COLOR]
[COLOR="cyan"]cache-linuxmce-desktop[/COLOR]
[COLOR="Blue"]share[/COLOR]
[COLOR="Cyan"]socket-dcerouter[/COLOR]
[COLOR="cyan"]tmp-dcerouter[/COLOR]

---

### Post by Lehto on 2008-02-01
well somehow I don't have that autostart file...
Is it possible to fix this problem anyway? I have used the Linuxmce dvd installation and with that one LinuxMCE boots up automaticly without rinning Kubuntu. But when I get the LinuxMCE launch Manager it says:
Core status: Not running Localy
Media station status: Not installed   :confused:
Remote Assistance: enabled, service code is -949198
And I can't press any button in that window except close it and then nothing happends.
I have crossed the options:
Autostart core
Autostart Media Station

Can that be the problem that its trying to start media station And then it is not installed? :confused:
Cuz it says in the Launch manager that it isn't installed... 

It worked so well until about 3days ago, and I havn't done anyting to it...

I really need some help here...

---

