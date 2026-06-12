---
title: "Disabled typing in Ubuntu 14.10"
date: 2014-12-05
forum: General Help
---

### Post by eight.coffee.beans on 2014-12-05
Well I can type in Firefox, Python, Skype, LibreOffice Writer, but I can't rename any file or folder elsewhere in Ubuntu.
I tried to restart the notebook, but that didn't fix the problem. Anyone knows possible reason for this to happen and of course a way to fix this?

---

### Post by kccv42 on 2014-12-05
Have you tried reinstall your keyboard drivers?

---

### Post by eight.coffee.beans on 2014-12-05
> **kccv42 said:**
> Have you tried reinstall your keyboard drivers?

I'm not sure how much it's the fault in driver since everything else works completely fine.
However running *sudo nautilus *gives me the ability to rename the folders.
 I'm owner and have permission to modify the folders, yet can't rename them in normal way. *confused*

---

### Post by kccv42 on 2014-12-05
Well the drivers allow the computer to communicate with the hardware/devices. Sometimes if the driver gets corrupt the hardware/devices can't work. I have seen in windows 7 the printer drivers get corrupt and have to be reinstalled to work or the printer would malfunction.

---

### Post by eight.coffee.beans on 2014-12-05
> **kccv42 said:**
> Well the drivers allow the computer to communicate with the hardware/devices. Sometimes if the driver gets corrupt the hardware/devices can't work. I have seen in windows 7 the printer drivers get corrupt and have to be reinstalled to work or the printer would malfunction.

Well I restarted the notebook and now it's working. 
So the fix is: restart your computer two times [?] :-s

---

### Post by kccv42 on 2014-12-05
Great! I am glad you solved the issue. Now you can mark the forum as solved.

---

### Post by grahammechanical on 2014-12-05
If we are the only user then we have two personas in Ubuntu we are both a standard user and an Administrator user. If as standard user we create a file or folder the we should be able to use the File Manager (Nautilus) to rename the file or folder.

On the other hand if we are administrator when we create the file or folder then we will only be able to rename the file of folder as administrator. Of, course, system files and folders can only be renamed by an administrator.

We do not recommend running Nautilus (File Manager) using the sudo prefix because we can easily and without realizing it change the file permissions. And this maybe is what has happened to files on your OS.

Really, the title of this thread is inaccurate. The problem is not with typing being disabled but with not being able to rename certain files and folders. I think it is preferable to use

```
sudo -H
```

as the prefix if we need to launch Nautilus as administrator.

> [COLOR=#333333][FONT=Ubuntu]You should **never** use normal sudo to start graphical applications as Root. You should use gksudo (kdesudo on [FONT=inherit]Kubuntu[/FONT]) to run such programs.gksudo sets HOME=~root, and copies .Xauthority to a tmp directory. This prevents files in your home directory becoming owned by Root. (AFAICT, this is all that's special about the environment of the started process with gksudo vs. sudo).[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Recent versions of some flavours might not have gksu installed.[/FONT][/COLOR]


[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Ubuntu no longer comes with gksu installed by default but we should still be able to install it. Or use sudo -H as the prefix. It seems to do the same thing.

>      -H          The **-H** (_HOME_) option sets the HOME environment variable to
                   the homedir of the target user (root by default) as
                   specified in _[passwd]("http://manpages.ubuntu.com/manpages/lucid/en/man5/passwd.5.html")_(5).  By default, **sudo** does not modify
                   HOME (see _set_home_ and _always_set_home_ in _[sudoers]("http://manpages.ubuntu.com/manpages/lucid/en/man5/sudoers.5.html")_(5)).




[http://manpages.ubuntu.com/manpages/lucid/en/man8/sudo.8.html](http://manpages.ubuntu.com/manpages/lucid/en/man8/sudo.8.html)

Launch the File Manager as a standard user and then use it to examine the permissions of those files and folders. Select the folder and right click it and select Properties and then Permissions. See, if the owner is Me and the Access is to Create and Delete files.

Regards.

---

