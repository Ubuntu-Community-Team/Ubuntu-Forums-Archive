---
title: "file edit permissions"
date: 2012-11-17
forum: General Help
---

### Post by majorburt on 2012-11-17
while trying to edit a ".conf" file using "Text Editor", i get this error when i try to save (You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.). 

i believe that i have the file location correct because when i try to save, i overwrite the file that i was editing.

i am the admin and only user of my comp so i see no reason as to why i don't have the necessary permissions to edit the file.

am i doing something wrong?

any help would be greatly appreciated.

---

### Post by papibe on 2012-11-17
Hi majorburt.

In order to actually gain admin privileges, you have to use either sudo, or gksudo.

For example, let's say you want to edit the file /etc/resolv.conf

There 2 options:

[LIST=1]
[*]You can either open a terminal and run:
```
sudo gedit /etc/resolv.conf
```
your password will be asked on the terminal as security measure.


[*]Or, Press Alt+F2 and run:
```
gksudo gedit /etc/resolv.conf
```
same procedure except your password will be ask using a GUI tool.
[/LIST]
For more information on sudo, and on how the security works, I'd recommend taking a look at this [tutorial]("https://help.ubuntu.com/community/RootSudo").

Hope that helps. Let us know how it goes.
Regards.

---

### Post by majorburt on 2012-11-17
> **papibe said:**
> Hi majorburt.

In order to actually gain admin privileges, you have to use either sudo, or gksudo.

For example, let's say you want to edit the file /etc/resolv.conf

There 2 options:

[LIST=1]
[*]You can either open a terminal and run:
```
sudo gedit /etc/resolv.conf
```
your password will be asked on the terminal as security measure.


[*]Or, Press Alt+F2 and run:
```
gksudo gedit /etc/resolv.conf
```
same procedure except your password will be ask using a GUI tool.
[/LIST]
For more information on sudo, and on how the security works, I'd recommend taking a look at this [tutorial]("https://help.ubuntu.com/community/RootSudo").

Hope that helps. Let us know how it goes.
Regards.

you rock!!! i really need to remember some of these codes.

---

### Post by ajgreeny on 2012-11-17
> **majorburt said:**
> you rock!!! i really need to remember some of these codes.
Strictly speaking, you should always use **gksu** or **gksudo** when using an application which has a GUI from gnome or other gtk DE (xfce, lxde) and never just sudo.  You will be OK with gedit using sudo but in some cases you could lock yourself out of the OS by corrupting the whole Root/sudo system.

See **RootSudo** in my signature for more info.

---

### Post by majorburt on 2012-11-19
> **ajgreeny said:**
> Strictly speaking, you should always use **gksu** or **gksudo** when using an application which has a GUI from gnome or other gtk DE (xfce, lxde) and never just sudo.  You will be OK with gedit using sudo but in some cases you could lock yourself out of the OS by corrupting the whole Root/sudo system.

See **RootSudo** in my signature for more info.

that's good to know. 
does that apply to the terminal or the GUI command prompt (alt-F2)?

---

