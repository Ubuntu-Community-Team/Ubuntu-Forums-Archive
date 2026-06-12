---
title: "Startup application with sudo"
date: 2014-08-20
forum: General Help
---

### Post by markodd on 2014-08-20
Hey,

I'm trying to auto-start an application (run it as soon as the OS boots) that requires sudo.

I've gone to the "Startup Applications" and added ```
sudo application
```

I obviously changed "application" for the application's name.

However, it's not working. It doesn't run at system startup..


EDIT: 

I'm using Ubuntu 14.04, 64bits.

EDIT 2:

** What I've done:**

Edited the sudoers file with: ```
sudo visudo
``` and added the following:  ```
markodd ALL = NOPASSWD /usr/bin/airvpn
```

At this point, if I run *"sudo /usr/bin/airvpn"* in a console, it doesn't ask me for the password..

After that, I've added: ```
sudo /usr/bin/airvpn
``` to the AutoStartup applications. I've also tried that command with a "sleep 20", but it doesn't work either way.

Some additional info:

If I run ```
ps aus | grep airvpn
``` I get the following output:

```

markodd@mypc:~$ ps ax | grep airvpn
 2466 ?        Sl     0:00 /usr/bin/gksu -u root -m AirVPN Client needs  administrative privileges. Please enter your password. mono  /usr/lib/AirVPN/AirVPN.exe path=/home/markodd/.airvpn
 2469 ?        Ss     0:00 /usr/bin/sudo -H -S -p GNOME_SUDO_PASS -u  root -- mono /usr/lib/AirVPN/AirVPN.exe path=/home/markodd/.airvpn
 2474 ?        Sl     1:52 mono /usr/lib/AirVPN/AirVPN.exe path=/home/markod/.airvpn
 2496 ?        S      0:12 /usr/sbin/openvpn --config  /home/markod/.airvpn/1dasdsa4396c20edadas5fb43de08b0cd2fds3242d0f213df8.tmp.ovpn
 3829 pts/7    R+     0:00 grep --color=auto airvpn

```

---

### Post by Dennis N on 2014-08-20
What is your system using: Ubuntu, Xubuntu, Lubuntu ...?

---

### Post by markodd on 2014-08-20
> **Dennis N said:**
> What is your system using: Ubuntu, Xubuntu, Lubuntu ...?

Oh sorry, I forgot that info. 

I'm using Ubuntu 14.04, 64bit

---

### Post by JKyleOKC on 2014-08-20
To run at system boot time, open the file /etc/rc.local with a text editor, using sudo or gksudo since root access is required to change this file, and add the command line for the desired program just in front of the line at reads "exit 0" then save the file.

That is,```
#at a command line prompt, type
gksudo gedit /etc/rc.local
```

This file is intended for the specific purpose of invoking programs at the final step of powering up, and it runs with root privilege so does NOT require sudo ever. In fact using sudo in it guarantees an error since rc.local runs with no connection to a terminal to provide input.

The autostart list, on the other hand, runs during your login sequence, not at system boot time. Again, though, it runs with no input capability so using sudo there also creates problems (as you have discovered).

Using rc.local is extremely powerful; it's well worth studying...

Hope this helps!

---

### Post by ajgreeny on 2014-08-20
I don't actually know if this will work, never having tried it, but I wonder if you can do it by copying the application.desktop file  for whatever this application might be (you didn't tell us that, and it may be useful to know) from /usr/share/applications to /etc/xdg/autostart.  This may be totally wrong, but as the desktop file is in a root owned folder it may be able to start application that need root permissions. 

OK, I've just tried that for gparted (a GUI program, see below) and it starts the application but it also asks for the password at session start, so may not be what you are looking for

Is this application one that runs in the GUI (I assume not, as you should not use sudo for those) but if by chance it is, using the /etc/rc/local file entry will not work as that is run before the GUI starts.

---

### Post by steeldriver on 2014-08-20
... if it's something that needs to run as root AFTER the X server starts, then perhaps a lightdm session-setup-script ?

---

### Post by markodd on 2014-08-20
> **JKyleOKC said:**
> To run at system boot time, open the file /etc/rc.local with a text editor, using sudo or gksudo since root access is required to change this file, and add the command line for the desired program just in front of the line at reads "exit 0" then save the file.

That is,```
#at a command line prompt, type
gksudo gedit /etc/rc.local
```

This file is intended for the specific purpose of invoking programs at the final step of powering up, and it runs with root privilege so does NOT require sudo ever. In fact using sudo in it guarantees an error since rc.local runs with no connection to a terminal to provide input.

The autostart list, on the other hand, runs during your login sequence, not at system boot time. Again, though, it runs with no input capability so using sudo there also creates problems (as you have discovered).

Using rc.local is extremely powerful; it's well worth studying...

Hope this helps!

Hey, thank you, but unfortunately, it's not working.

For the peopel asking, the application is a VPN client (airvpn).

I added the ```
airvpn
``` just before exit 0, so it looks something like:

```
airvpn
exit 0
```

However, it's not working.. Does it make any difference that I'm testing this on a PC running xubuntu 14.04 instead of ubuntu?

---

### Post by ian-weisser on 2014-08-20
No.

Have you tried the full path to airvpn in the script?

---

### Post by markodd on 2014-08-20
> **ian-weisser said:**
> No.

Have you tried the full path to airvpn in the script?

To do that I run the following command:

 ```
whereis airvpn
```

And find where airvpn is, correct? If so, I get three paths: 

```
airvpn: /usr/bin/airvpn /usr/bin/X11/airvpn /usr/share/man/man1/airvpn.1.gz
```

Which one should I pick? what are the differences between the first two?

---

### Post by ian-weisser on 2014-08-20
> **markodd said:**
> ```
airvpn: /usr/bin/airvpn /usr/bin/X11/airvpn /usr/share/man/man1/airvpn.1.gz
```
Which one should I pick? what are the differences between the first two?

Well, 
/usr/share/man/man1/airvpn.1.gz is a manpage, not an application
/usr/bin/X11/airvpn may be a graphical application. If so, it won't run well in /etc/rc.local, which has no display attached when it runs.
So I would try /usr/bin/airvpn

---

### Post by markodd on 2014-08-21
> **ian-weisser said:**
> Well, 
/usr/share/man/man1/airvpn.1.gz is a manpage, not an application
/usr/bin/X11/airvpn may be a graphical application. If so, it won't run well in /etc/rc.local, which has no display attached when it runs.
So I would try /usr/bin/airvpn

I do need the graphical interface though, to change configurations and etc.. Isn't it possible to autostart a GUI application?

EDIT:

I've tried adding both of them (tried one, restarted, then tried the other, restarted) and none of them works..

---

### Post by bra|10n on 2014-08-21
I'm fairly certain this can be done using systemd and is one of the benefits systemd offers, only don't ask me how!

I think it involves writing a small script in which you can then declare 'depends on' (in your case x) before starting.
The script is then initiated by systemd during startup and is along the lines of "*sudo systemctl enable <name of service>.service*".

I'm sure someone who knows more about systemd will chime in and correct me if I've mislead you any and offer their advice.

HTH

---

### Post by ian-weisser on 2014-08-21
> **markodd said:**
> I do need the graphical interface though, to change configurations and etc.

Ah, that's critical information.
rc.local cannot help you with that, since (if I recall correctly) it cannot start graphical applications. Root has no display to show the application on, and root is not you anyway. 

Of course it's possible -even trivial- to autostart a GUI application. The problem is the sudo password.
You must change the rules of sudo to allow that application to run without a password.
You do that by using the visudo application to edit the sudoers file.
Be careful - improper changes to the sudoers file can break your system.

---

### Post by markodd on 2014-08-21
Well, I've edited the sudoers file with visudo.. I bet I just broke my system.. If I don't edit this in 5 minutes, it means I'm pissed and re-installing my OS.

EDIT:

Well, didn't break my system, but it's still not working..

---

### Post by steeldriver on 2014-08-21
Can you tell us some more about the app? I can't help feeling that if you need to permanently run a GUI app using sudo there is something not configured right - it's really not a secure way of operating. Really sudo is ONLY meant for TEMPORARY escalation of privileges.

Can you link to the instructions you're following?

---

### Post by markodd on 2014-08-21
I cannot find exactly the link now, but it's practically the same as this one: [http://askubuntu.com/questions/17322/autostart-firestarter-gui-on-boot](http://askubuntu.com/questions/17322/autostart-firestarter-gui-on-boot)

See answer #2. So I did:

```
sudo visudo
```

and then added the following:

```
user ALL = NOPASSWD: /usr/lib/AirVPN/AirVPN.exe
```

I also tried with:

```
user ALL = NOPASSWD /usr/bin/X11/airvpn
```

None of those worked.

EDIT:

Maybe I should be adding the symbol % before the user? That thing I linked is from 2010...

---

### Post by JKyleOKC on 2014-08-21
The "user" in the example should be your own user name; putting the "%" in front would mean that it's a group name. And try it with the /usr/bin/airvpn path. I'm guessing that the file in the X11 directory is a configuration file of some sort, or maybe a helper, rather than the basic executable. "/usr/bin" is the standard location for executables in *buntu, similar to "Program Files" in Windows. 

If you want this to happen for more than just one user, you can either list each user name at the start of the added line, or create a new group with a name of your choosing, add each of the users to that group, and replace "user" in the visudo line with the group name preceded by "%"...

You were wise to use visudo rather than editing the file directly; visudo **always** makes certain that any changes will not crash the system, before committing them to disk!

EDIT: When you add the command to your autostart list, you may find it necessary to put "sleep 10 &&" in front of it to provide a 10-second delay before trying to launch it. Look at this guide for a similar problem that I found in another thread (the program is different but the problem is the same): [http://ubuntuhandbook.org/index.php/2014/06/turn-on-numlock-ubuntu-14-04/](http://ubuntuhandbook.org/index.php/2014/06/turn-on-numlock-ubuntu-14-04/) Look at the "tip" near the end just above the poster's bio, and ignore the part about installing "numlockx."

---

### Post by Lars Noodén on 2014-08-21
Remember the colon:

```

%user ALL = NOPASSWD: /usr/bin/X11/airvpn ""

```

The empty quotes mean that it can be launched but only without extra parameters.  I'm not sure that matters here but maybe it does.

---

### Post by markodd on 2014-08-21
> **JKyleOKC said:**
> The "user" in the example should be your own user name; putting the "%" in front would mean that it's a group name. And try it with the /usr/bin/airvpn path. I'm guessing that the file in the X11 directory is a configuration file of some sort, or maybe a helper, rather than the basic executable. "/usr/bin" is the standard location for executables in *buntu, similar to "Program Files" in Windows. 

If you want this to happen for more than just one user, you can either list each user name at the start of the added line, or create a new group with a name of your choosing, add each of the users to that group, and replace "user" in the visudo line with the group name preceded by "%"...

You were wise to use visudo rather than editing the file directly; visudo **always** makes certain that any changes will not crash the system, before committing them to disk!

EDIT: When you add the command to your autostart list, you may find it necessary to put "sleep 10 &&" in front of it to provide a 10-second delay before trying to launch it. Look at this guide for a similar problem that I found in another thread (the program is different but the problem is the same): [http://ubuntuhandbook.org/index.php/2014/06/turn-on-numlock-ubuntu-14-04/](http://ubuntuhandbook.org/index.php/2014/06/turn-on-numlock-ubuntu-14-04/) Look at the "tip" near the end just above the poster's bio, and ignore the part about installing "numlockx."

Hello,

I did switch "user" for my username. I also tried with the path "/usr/bin/airvpn" and it's still not working...

One question though: After editing the sudoers file, we still need to add the command "sudo airvpn" to the autostart list? I mean, I need to edit the sudoers AND add the command to the auto-start list?

---

### Post by markodd on 2014-08-21
I think I'm close, because by doing:

```
 sudo usr/bin/airvpn 
```

it no longer asks for the password.. I think now it's a problem of adding it to the auto-startup (which I did already, but it's not working..)

Some additional info:

By ```
doing  ps aux | grep airvpn
``` I get the following output:
```

markodd@mypc:~$ ps ax | grep airvpn
 2466 ?        Sl     0:00 /usr/bin/gksu -u root -m AirVPN Client needs administrative privileges. Please enter your password. mono /usr/lib/AirVPN/AirVPN.exe path=/home/markodd/.airvpn
 2469 ?        Ss     0:00 /usr/bin/sudo -H -S -p GNOME_SUDO_PASS -u root -- mono /usr/lib/AirVPN/AirVPN.exe path=/home/markodd/.airvpn
 2474 ?        Sl     1:52 mono /usr/lib/AirVPN/AirVPN.exe path=/home/markod/.airvpn
 2496 ?        S      0:12 /usr/sbin/openvpn --config /home/markod/.airvpn/1dasdsa4396c20edadas5fb43de08b0cd2fds3242d0f213df8.tmp.ovpn
 3829 pts/7    R+     0:00 grep --color=auto airvpn

```

---

### Post by markodd on 2014-08-21
I've edited the main post and added what I've tried so far... Would really like to solve this once and for all..

---

### Post by markodd on 2014-08-21
Someone on the AirVPN forums is having the same problem. Unfortunately, he hasn't posted a solution just yet. I pmed him asking if he got it.

Anyway, here is the link: [https://airvpn.org/topic/12055-airvpn-client-in-linux-ubuntu-some-questions/#entry19655](https://airvpn.org/topic/12055-airvpn-client-in-linux-ubuntu-some-questions/#entry19655)

The admin does give some answers but I've no idea what he's saying. Can anyone help me out?

---

### Post by steeldriver on 2014-08-21
How did you run it in order to get the 'ps aux' output that you just added to the original post? did you use gksu in a terminal or did you launch it from the dash or a desktop icon?

---

### Post by markodd on 2014-08-21
> **steeldriver said:**
> How did you run it in order to get the 'ps aux' output that you just added to the original post? did you use gksu in a terminal or did you launch it from the dash or a desktop icon?

I launched it from the icon.

---

### Post by steeldriver on 2014-08-21
So it looks like the command you need to run from your 'Startup Applications' (with sudo **-H**) is actually **mono**, with the AirVPN.exe as its **argument**

```

sudo -H -u root -- /usr/bin/mono /usr/lib/AirVPN/AirVPN.exe path=/home/markod/.airvpn

```

(although the '-u root' is superfluous here I think - may as well leave it in for consistency)

and then in your sudoers file (using 'sudo visudo') something like

```

markod    ALL=(ALL) **NOPASSWD:** /usr/bin/mono

```

or perhaps (not sure how exactly you can specify the command - the more specific the better from a security POV)

```

markod    ALL=(ALL) **NOPASSWD:** /usr/bin/mono /usr/lib/AirVPN/AirVPN.exe path=/home/markod/.airvpn

```

---

### Post by markodd on 2014-08-21
@Steeldriver

Hey, thanks for replying!!

Unfortunately, I've tried both ways and none of them works. ://

---

### Post by steeldriver on 2014-08-21
Can you now run

```

sudo -H -u root -- /usr/bin/mono /usr/lib/AirVPN/AirVPN.exe path=/home/markod/.airvpn

```

from a terminal without entering your password? if not, what happens exactly?

---

### Post by markodd on 2014-08-21
@steeldriver 

No, I cannot run that without entering the password ://. It asks for it. If I type the password, it runs.

---

### Post by steeldriver on 2014-08-21
oops I forgot the **NOPASSWD:** (see my edited post above) - did you remember to add that?

---

### Post by ian-weisser on 2014-08-21
Er, why all the effort to get AirVPN working instead of one of existing and supported VPN clients?

For example, Ubuntu's built-in VPN client already has a checkbox-setting for autoconnect. And it's integrated with Network Manager. Is there something special about AirVPN that makes all this extra setup work desirable?

---

### Post by markodd on 2014-08-21
> **steeldriver said:**
> oops I forgot the **NOPASSWD:** (see my edited post above) - did you remember to add that?

**YOU'RE THE MAN!!** This &"#(//&#/"%#&"/ is finally working!! Thank you so much steeldriver!

> **ian-weisser said:**
> Er, why all the effort to get AirVPN working instead of one of existing and supported VPN clients?

For example, Ubuntu's built-in VPN client already has a checkbox-setting for autoconnect. And it's integrated with Network Manager. Is there something special about AirVPN that makes all this extra setup work desirable?

There are some advantages to using the provider's client. For example, it'll feature leak protection and we're also able to see the server status (statuses?) in the GUI (the ping, load, etc)

---

### Post by markodd on 2014-08-22
Just adding this post so I know what to know later on (I added this thread to my "Solved" folder)

In order to delay the auto-startup of the application, I had to use the following command:

```
sh -c "sleep 10; command for the VPN"
```

EDIT: Markodd, you'll come to this thread quite a few times.. How are you doing in the future mate?

The command for the VPN is the following:

sudo -H -u root -- /usr/bin/mono /usr/lib/AirVPN/AirVPN.exe path=/home/markod/.airvpn

Don't forget to "sudo visudo"

---

### Post by JKyleOKC on 2014-08-22
You can experiment with the number of seconds to sleep; I usually use 10 but it may do just fine in this case with as few as 1. The idea is to allow enough time for the GUI to get set up and settled down, plus any other items that are auto-started.

Glad to hear that the problem is solved!

---

