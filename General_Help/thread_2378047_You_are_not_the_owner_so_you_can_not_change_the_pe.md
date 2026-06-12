---
title: "You are not the owner so you can not change the permissions"
date: 2017-11-19
forum: General Help
---

### Post by frequencyg on 2017-11-19
Why is this happening to my file? I tried some commands but did not work. Any help?

---

### Post by raja.genupula on 2017-11-19
once you are in directory of that file, execute below command and provide the output.

> who am i 

and 

> ls -l yourfilename

---

### Post by Impavidus on 2017-11-19
I think you should make that```
whoami
```without the spaces.

Read up on file permissions. They are at the basis of security in UNIX-like operating systems like Linux.
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Also, on what kind of file system is that file you want to change permissions of? If it's a non-Linux file system (like Windows or most removable drives) things can be rather different, but I expect a different error message in that case.

---

### Post by deadflowr on 2017-11-19
If I where to bet I'd put money on running something involving the file with sudo, like sudo cp(copy) or sudo some-editor...
> I tried some commands but did not work.
Post the commands you tried.
If you need some help remembering them, look in the .bash_history file
You could use
```
cat .bash_history
```
or if that file is really long and you know the last commands you tried you can cut the output to only the last few entries with tail
```
tail .bash_history
```
The dot signifies the file is a hidden file.
And as long as you are in top level of your home folder you can simply run the command above. (the ~$ sign means you are, anything else means you would not be)
If by chance you cd'd into another directory, then you would need to run the above commands with the fule path name, like /home/you/.bash_history.

Hope it helps

---

### Post by frequencyg on 2017-11-20
EDIT 1
I tried ```

root@freq-VirtualBox:~# gksudo nautilus 
No protocol specified


(gksudo:2580): Gtk-WARNING **: cannot open display: :0

``` it didnt work.
also tried
```

root@freq-VirtualBox:~# sudo chown -R freq /home/Desktop/dumpster

```
```

whoami

```
gives ```

root 

```

---

### Post by Impavidus on 2017-11-20
To get more familiar with sudo:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

sudo is meant to gain root permissions. There's no need to use sudo (or gksudo) when you're already root.

It would be very strange if the directory /home/Desktop existed. That would be the home directory of user Desktop. It seems things are pretty well mixed up. What do you get from```
ls -l /home
```

---

### Post by frequencyg on 2017-11-22
Hello,
i get 
```

total 4
drwxr-xr-x 24 freq freq 4096 [FONT=arial black](&#925;&#959;&#941;  22 15:24)-<date in greek[/FONT] freq.

```

---

### Post by mc4man on 2017-11-22
Do you always use a root terminal??
Anyway, assuming you are using Ubuntu 17.10 & nautilus - 
You cannot (or shouldn't) open nautilus as root with older methods, to get a root nautilus with some restrictions - 
Open nautilus, change to location entry (ctrl+l
Type this in, press enter
admin://
or specify, ex. /etc
admin:///etc

For a root gedit open gedit from terminal & specify file - ex. /etc/fstab
gedit admin:///etc/fstab

(- you may need to enter password twice.

Otherwise find another file manager & for text files use nano or I guess sudo -H gedit will still be ok. (- sudo -H nautilus is Not ok..

---

### Post by Impavidus on 2017-11-22
Your /home and /home/freq seem normal and it's quite obvious why your command```
root@freq-VirtualBox:~# sudo chown -R freq /home/Desktop/dumpster
```failed, as that directory doesn't exist. So, everything seems normal and I don't really see what's your problem. It's best if you copy-paste everything from the terminal: prompt, command and response.

Some things with sudo and graphical applications changed with Ubuntu 17.10, at least when using a wayland session, and not all documentation is up to date.

---

