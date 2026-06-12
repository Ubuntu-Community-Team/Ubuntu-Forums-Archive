---
title: "Why am I able to execute shutdown as a normal user?"
date: 2016-11-28
forum: General Help
---

### Post by chopra on 2016-11-28
As far as I am aware, if the shutdown executable is not setuid or setgid, only root should be able to invoke the command, unless it's preceded with sudo.
As my ordinary self, I issued the command 
shutdown -h
I typed in -h instead of --help out of habit, but I got a message:
Shutdown scheduled for Mon 2016-11-28 16:16:15 CST, use 'shutdown -c' to cancel.

So I canceled.  This was using my primary user account, which is a member of sudo and adm groups.  (btw, shutdown is not aliased to sudo shutdown, nor anything else)

I tend to create separate user accounts when my work requires me to download software on my laptop, so each program I only use with a designated, unpriveledged account, especially software that involves connecting to the internet. None of these accounts have sudo priveledges, nor belong to any priveledged groups.

So I logged out from my main account, and logged in with an unpriveledged account, and typed into the command line:

shutdown now

I was expecting to get an error message, but instead, my machine turned off.
When I type in the command
 
ls -l `which shutdown`

I get:

lrwxrwxrwx 1 root root 14 Oct 26 08:04 /sbin/shutdown -> /bin/systemctl

stat /bin/systemctl gives, Access: (0755/-rwxr-xr-x)

ie, no setuid or setgid.

Is this normal behavior? If so, I'm very surprised.

Chopra

---

### Post by QIII on 2016-11-28
Hello!

Which release are you running?

---

### Post by oldrocker99 on 2016-11-28
Since you don't need to be root to use a graphical shutdown command, it stands to reason that you don't need it to use **shutdown** or **reboot** in a terminal.

---

### Post by mc4man on 2016-11-28
This seems to be a recent change in Ubuntu, previously sudo was always required to reboot or shutdown from cli.
Actually not sure if intended or a bug, if I knew what source handles this I'd look in changelog for evidence of the former.

Probably not a matter of groups as a guest can run the commands.

---

### Post by The Cog on 2016-11-28
I think the shutdown command just sends a shutdown request to some other process (I don't know what) that *is* running as root.

---

### Post by mc4man on 2016-11-28
This seems to be a systemd thing, check for example on 14.04 & you'll need sudo.

---

### Post by jeremy31 on 2016-11-28
It was discussed previously [https://ubuntuforums.org/showthread.php?t=2338547&p=13551032#post13551032](https://ubuntuforums.org/showthread.php?t=2338547&p=13551032#post13551032)
And another link
[http://askubuntu.com/questions/774740/why-does-reboot-and-poweroff-work-without-super-user-privileges-in-ubuntu-16](http://askubuntu.com/questions/774740/why-does-reboot-and-poweroff-work-without-super-user-privileges-in-ubuntu-16)

---

### Post by ajgreeny on 2016-11-28
It has been noted and asked about before quite recently, and I admit I was surprised as I was still using 14.04 at the time which did require sudo to shutdown from terminal using the shutdown or reboot commands.

There are still some situations where you will not be able to do so without root permissions, such as if you have ssh connection to the machine.  You can only do it when logged in as user to a desktop OS, not remotely, and as discussed in the thread at [https://ubuntuforums.org/showthread.php?t=2338547&p=13551032](https://ubuntuforums.org/showthread.php?t=2338547&p=13551032) it does make some sense.

---

### Post by mc4man on 2016-11-28
> **jeremy31 said:**
> It was discussed previously [https://ubuntuforums.org/showthread.php?t=2338547&p=13551032#post13551032](https://ubuntuforums.org/showthread.php?t=2338547&p=13551032#post13551032)

bad memory on me or something..

---

### Post by sisco311 on 2016-11-28
> **chopra said:**
> 
Is this normal behavior?


I would say, yes it is. 

> **chopra said:**
> 
If so, I'm very surprised.



systemd instead of setuid apps uses a server/client method.

---

### Post by chopra on 2016-11-28
> **jeremy31 said:**
> It was discussed previously [https://ubuntuforums.org/showthread.php?t=2338547&p=13551032#post13551032](https://ubuntuforums.org/showthread.php?t=2338547&p=13551032#post13551032)
And another link
[http://askubuntu.com/questions/774740/why-does-reboot-and-poweroff-work-without-super-user-privileges-in-ubuntu-16](http://askubuntu.com/questions/774740/why-does-reboot-and-poweroff-work-without-super-user-privileges-in-ubuntu-16)

It has been noted and asked about before quite recently, and I admit I  was surprised as I was still using 14.04 at the time which did require  sudo to shutdown from terminal using the shutdown or reboot commands.

[QUOTE=ajgreeny]There are still some situations where you will not be able to do so  without root permissions, such as if you have ssh connection to the  machine.  You can only do it when logged in as user to a desktop OS, not  remotely, and as discussed in the thread at [https://ubuntuforums.org/showthread....547&p=13551032]("https://ubuntuforums.org/showthread.php?t=2338547&p=13551032") it does make some sense.[/QUOTE]

Ahh, I wish I'd been more thourough on my searching.  In the modern world of single-user machines like laptops, this seems less of a concern than it would be back in the day. Changing the permissions of the systemctl, as suggested in one of the links, seems like it could work. I still like to "shield" myself from issueing potentially unwise commands, by forcing sudo and a password.  Just a force of habit, probably overkill, but left over from my early days as a less experienced and less patient user.

Chopra

---

### Post by kpatz on 2016-11-28
Shutdown without sudo is possible only from the desktop, including terminals launched from the desktop.  If you ssh in to a terminal, or use a tty console, you won't be able to shut down without sudo.  So, that pretty much eliminates the issue with servers able to be shut down by non privileged users.  If there's no desktop installed, or not accessible due to remote location and no remote desktop server, sudo is needed to shut down.

I bet there's a configuration option somewhere to change this, if you really wanted/needed to.

---

