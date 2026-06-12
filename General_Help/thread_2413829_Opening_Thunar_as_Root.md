---
title: "Opening Thunar as Root"
date: 2019-03-02
forum: General Help
---

### Post by RobGoss on 2019-03-02
Hello everyone I have been using **Xubuntu 18.04** for a few days now and I'm trying to customize it a bit, can anyone tell me how to open the Thunar file-manager as root? I'm trying to install a few themes but after downloading them and extracting them I cannot paste them in the theme folder.

I tried using
```
 gksudo thunar
```

But this does not seem to work


Thanks for any help with this

---

### Post by raleigh3 on 2019-03-02
```
sudo thunar
```

If you are the only one who can access your computer and you do feel like having to use your password

echo yourpassword | sudo -S thunar &>/dev/null

---

### Post by RobGoss on 2019-03-02
> **raleigh3 said:**
> ```
sudo thunar
```

If you are the only one who can access your computer and you do feel like having to use your password

echo yourpassword | sudo -S thunar &>/dev/null


Thanks so much got it

---

### Post by ajgreeny on 2019-03-02
> **raleigh3 said:**
> ```
sudo thunar
```

If you are the only one who can access your computer and you do feel like having to use your password

echo yourpassword | sudo -S thunar &>/dev/null

**[SIZE=3][COLOR="#FF0000"]No, no, no!![/COLOR][/SIZE]**

**Never ever use sudo for any GUI application**, but particularly for thunar or any other file manager as you risk changing the ownership of files and folders in your home to root and thus being unable to login as user.

The package **gksudo** is deprecated and no longer available for any of the *ubuntu family so another way round this is required if you must open thunar as root.

You can now use ```
pkexec thunar
``` to open thunar with root privileges, but use it with great care and make sure to close it as soon as you have finished doing whatever you need it for.  There will be an orange coloured warning bar at the top to remind you of the dangers which helps avoid the dangers, but it is still possible to damage the whole system if you are not a careful user.

---

### Post by RobGoss on 2019-03-02
> **ajgreeny said:**
> **[SIZE=3][COLOR="#FF0000"]No, no, no!![/COLOR][/SIZE]**

**Never ever use sudo for any GUI application**, but particularly for thunar or any other file manager as you risk changing the ownership of files and folders in your home to root and thus being unable to login as user.

The package **gksudo** is deprecated and no longer available for any of the *ubuntu family so another way round this is required if you must open thunar as root.

You can now use ```
pkexec thunar
``` to open thunar with root privileges, but use it with great care and make sure to close it as soon as you have finished doing whatever you need it for.  There will be an orange coloured warning bar at the top to remind you of the dangers which helps avoid the dangers, but it is still possible to damage the whole system if you are not a careful user.


Umm ok, so you're saying I can't access the Thunar file-manger using this command

```
sudo thunar
```

But instead use the command you suggested?

What does this code stand for **pkexec**?

Thanks so much

---

### Post by ajgreeny on 2019-03-02
It is simply (as far as I'm aware) the newer way to get root privileges temporarily for certain, but not all, GUI applications now that gksudo has disappeared.

I do not fully understand the details of this but am aware that various policykit configurations are required for the GUI apps that will allow this, mostly, if not all in /usr/share/polkit-1/actions.

---

### Post by again? on 2019-03-02
Make yourself a thunar right click menu.
Thunar > Edit > configure custom actions.
Use the add custom action button.

Create a name and description and for "Command" use
```
pkexec thunar %f
```
Select an icon.
[ATTACH=CONFIG]282666[/ATTACH]

In the second tab add an asterisk for file pattern and select "Directories".
[ATTACH=CONFIG]282667[/ATTACH]

Gives a right click "Open Root Directory" option when you
click on open space or a folder.
[ATTACH=CONFIG]282668[/ATTACH]

---

### Post by sisco311 on 2019-03-03
> **RobGoss said:**
> Umm ok, so you're saying I can't access the Thunar file-manger using this command

```
sudo thunar
```

But instead use the command you suggested?

What does this code stand for **pkexec**?

Thanks so much

Both sudo and pkexec are setuid root applications which allow you to run commands as another user or root. 

sudo (like su) was originally designed for CLI applications. In the past, the default configuration of sudo caused some problems when users tried to run GUI applications as root. The most notable one was when users ended up with files owned by root in their home directory. 

pkexec is part of polkit an application-level toolkit for defining and handling the policy that allows unprivileged processes to speak to privileged processes. The concept is simple.  You run the application as an unprivileged user and when you need higher privileges (root) then polkit jumps in an decides if you are allowed to do so or not and if you need to provide a password or not.

Most users don't even notice when polkit allows them to run something as root. For example, you are allowed to mount an USB stick (only root can do it) without being prompted for a password.  

Of course I'm talking about the current default settings.  Both sudo and polkit are very well configurable tools. They have a tons of options... 


EDIT:
Oh, and there is a new kid on the block (it uses polkit) gvfs admin backend. The following command will allow you to use thunar as root:
```
thunar admin://
``` ;)


EDIT2 warning (from the arch wiki)
> 

Warning: As put by Emmanuele Bassi, a GNOME developer: "there are no *real*, substantiated, technological reasons why anybody should run a GUI application as root. By running GUI applications as an admin user you're literally running millions of lines of code that have not been audited properly to run under elevated privileges; you're also running code that will touch files inside your $HOME and may change their ownership on the file system; connect, via IPC, to even more running code, etc. You're opening up a massive, gaping security hole [...]."[1]



---

### Post by ajgreeny on 2019-03-03
Interesting! I remember seeing that used before but admit that I had totally forgotten about it.

However, if you open thunar with that **thunar admin://** command it does not show the warning orange bar, reminding you it is open with root permissions, so I would therefore suggest that it is not quite such a safe way for users to open and use it.

---

### Post by sisco311 on 2019-03-03
> **ajgreeny said:**
> Interesting! I remember seeing that used before but admit that I had totally forgotten about it.

However, if you open thunar with that **thunar admin://** command it does not show the warning orange bar, reminding you it is open with root permissions, so I would therefore suggest that it is not quite such a safe way for users to open and use it.

You are absolutely right. I have edited my post to include a warning.

---

### Post by scaine on 2019-03-04
The sheer confusion this causes. It's pretty infuriating, the way they're going about this. They're saying on one hand "don't run GUI apps as root, there's never a need to do so", but on the other hand, something as simple as editing an SMB config, installing a theme, a printer driver perhaps, or updating your X.org config (say to disable mouse acceleration... something there's still no GUI for, in 2019) ALL need admin rights. So now we're supposed to be terminal gods and the whole act of selling Linux to the rest of the world takes a massive step back.

Why are gnome-devs (and recently even KDE devs) all so scared of promoting the GUI? Their own GUI. In the latest Kubuntu, you literally can't run Kate as root. It detects when you try to do, and refuses to run. So I have to install Geany on a KDE system to get a working text editor. Right. Good job.

So yeah, it's frustrating. I might love the terminal *now*, but any time I have to open it to show a Windows person how to do something, I know that I've immediately lost them.

---

### Post by raleigh3 on 2019-03-04
> **scaine said:**
> The sheer confusion this causes. It's pretty infuriating, the way they're going about this. They're saying on one hand "don't run GUI apps as root, there's never a need to do so", but on the other hand, something as simple as editing an SMB config, installing a theme, a printer driver perhaps, or updating your X.org config (say to disable mouse acceleration... something there's still no GUI for, in 2019) ALL need admin rights. So now we're supposed to be terminal gods and the whole act of selling Linux to the rest of the world takes a massive step back.

Why are gnome-devs (and recently even KDE devs) all so scared of promoting the GUI? Their own GUI. In the latest Kubuntu, you literally can't run Kate as root. It detects when you try to do, and refuses to run. So I have to install Geany on a KDE system to get a working text editor. Right. Good job.

So yeah, it's frustrating. I might love the terminal *now*, but any time I have to open it to show a Windows person how to do something, I know that I've immediately lost them.

In my opinion, it's ok to run GUI apps as root as long as you know what you are doing.

The key thing is "knowing what you are doing."

I should have put that on previous post.

Ubuntu is a large learning process.

It gives you great power and great responsibility. :-)

---

### Post by sisco311 on 2019-03-05
> **RobGoss said:**
> Hello everyone I have been using **Xubuntu 18.04** for a few days now and I'm trying to customize it a bit, can anyone tell me how to open the Thunar file-manager as root? I'm trying to install a few themes but after downloading them and extracting them I cannot paste them in the theme folder.

I tried using
```
 gksudo thunar
```

But this does not seem to work


Thanks for any help with this

On a single user system I would extract the files in my user's themes directory: ~/.themes

---

### Post by ajgreeny on 2019-03-05
> **raleigh3 said:**
> In my opinion, it's ok to run GUI apps as root as long as you know what you are doing.

The key thing is "knowing what you are doing."

I should have put that on previous post.

Ubuntu is a large learning process.

It gives you great power and great responsibility. :-)

^^^^++++^^^^
I totally agree.

I have been using Ubuntu now exclusively for over 14 years and (luckily perhaps) never had any major problems occur as a result of using a GUI application as root whereas in my previous Windows days, where you could do just about anything to the OS with no warnings or password request, I occasionally killed the system by playing with things that I ought to have left alone.

Also do not forget there are certain GUI applications that must be run as root in order to use them; synaptic package manager, the various software stores, gparted, etc etc; the list goes on.

---

### Post by sisco311 on 2019-03-05
> **ajgreeny said:**
> ^^^^++++^^^^
I totally agree.

I have been using Ubuntu now exclusively for over 14 years and (luckily perhaps) never had any major problems occur as a result of using a GUI application as root whereas in my previous Windows days, where you could do just about anything to the OS with no warnings or password request, I occasionally killed the system by playing with things that I ought to have left alone.

Also do not forget there are certain GUI applications that must be run as root in order to use them; synaptic package manager, the various software stores, gparted, etc etc; the list goes on.

I really like gparted but it's insane that you have to run the whole app as root.  You don't  need root to display a GUI OK/Cancel dialog window. Take a look at gnome-disks (aka palimpsest). You can run it as regular user. When you want to perform something as root you are asked for an admin or the root password. If the authentication is successful a little subset of operations are executed as root and you are back to a beautiful GUI which runs as an unprivileged process.

---

### Post by again? on 2019-03-05
> **sisco311 said:**
> I really like gparted but it's insane that you have to run the whole app as root.  
You don't  need root to display a GUI OK/Cancel dialog window. Take a look at gnome-disks (aka palimpsest). 
You can run it as regular user. When you want to perform something as root you are asked for an admin or the root password. 
If the authentication is successful a little subset of operations are executed as root and you are back to a beautiful GUI which runs as an unprivileged process.
That's the bit that many fail to understand.
It's ok for a GUI to perform privileged operations, just don't write it so the whole thing needs to run as root.

Some quotes from a "[wayland] can't run application as root using sudo" bug.
 [https://bugzilla.gnome.org//show_bug.cgi?id=772875#c5](https://bugzilla.gnome.org//show_bug.cgi?id=772875#c5)
> 
[COLOR="#696969"]> I am sorry, but I do take issue with the stance that: "There is no reason
> whatsoever to run a GUI application as root". What you mean to say is that
> YOU PERSONALLY can not think of an instance where the benefit of doing so
> will outweigh the downsides, as you perceive them, of doing so.[/COLOR]
Speaking as the developer of a GUI toolkit, and as an application developer, no: there are no *real*, 
substantiated, technological reasons why anybody should run a GUI application as root. 
By running GUI applications as an admin user you're literally running millions of lines of code 
that have not been audited properly to run under elevated privileges; 
you're also running code that will touch files inside your $HOME and may change their ownership on the file system; 
connect, via IPC, to even more running code, etc.

You're opening up a massive, gaping security hole &#8212; likely because application developers were too lazy to 
properly do separation between the code that creates and manages the GUI bits, and the code that executes the privileged operations.
> [COLOR="#696969"]> Suppose, just for the moment, that I would like to run GParted. That is a
> GUI application that kinda benefits from being run as root.[/COLOR]

No, it really doesn't.

The GUI part should be running as your user, and it should defer the privileged operations to an auditable, 
self-contained, *minimal* piece of code that gets executed after doing a privilege escalation, and gets dropped when not needed.

This is how applications that interact with any privileged operation, such as interacting with hardware or with system services, should be written.

---

### Post by Holger_Gehrke on 2019-03-05
Regarding the bit about the editor kate not running as root: you do not need to run kate with root-privileges to edit files that are only writeable for root. Just use 'sudoedit' or 'sudo -e', this make a copy of the file that can be edited, runs the editor and copies the edited file back. I've got a shortcut on my desktop with an exec-line of```
env EDITOR=/usr/bin/mousepad SUDO_ASKPASS=/usr/bin/X11/ssh-askpass sudo --askpass -e %F
```I can just drag and drop a file from the file manager to this shortcut and edit the file. Just change the definition of EDITOR and it should work with kate, too. You might need to install 'ssh-askpass' or one it's variants; it's a small program used by sudo to ask for the password in a GUI. Or you could use this line as a user-defined action in Thunar.

Holger

---

