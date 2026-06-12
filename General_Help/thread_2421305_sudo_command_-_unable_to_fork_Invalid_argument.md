---
title: "sudo command - unable to fork: Invalid argument"
date: 2019-06-19
forum: General Help
---

### Post by ogola89 on 2019-06-19
Hi guys,

So I am a bit new to the whole Linux environment, although I can work my way around, I am no way an expert. I am a biologist and know the commands in a general manner, but not necessarily what is going on underneath the hood for everything.

I have the Ubuntu WSL installed on my Windows 10 pro laptop.

I have been installing various things for some analyses I would want to perform in python, R, etc and have installed various environments with no issue.

However, today, something happened when I wanted to install nautilus. I typed in: 
```
sudo at update
``` 
instead of 
```
sudo apt update
```

I am using COMODO firewall, which prompted me as to how to treat the command/file. However, I noticed at that point that I had a typo and selected it to be 'contained' so as to not allow writing of anything that I wasn't sure.

I am not sure if the firewall setting worked, but now it seems my sudo command is broken.

Any time I use sudo now to install anything, it gives me the following error:
```
$ sudo apt-get update
sudo: unable to fork: Invalid argument

```

```
$ sudo apt install nautilus
sudo: unable to fork: Invalid argument
```

```
$ sudo apt-get install python3-matplotlib
sudo: unable to fork: Invalid argument

```

It seems it is a ubiquitous issue which comes up nomatter what I am trying to install. I installed some packages shortly prior to the ```
sudo at update
``` blunder, and I am convinced it may be something to do with this.

Could you please help me diagnose/fix the issue?

Thanks!

---

### Post by mc4man on 2019-06-19
Know nothing about using Ubuntu via windows but maybe read here

[https://help.comodo.com/topic-72-1-766-9200-.html](https://help.comodo.com/topic-72-1-766-9200-.html)

---

### Post by Rubi1200 on 2019-06-19
To check what sudo permissions you have run this in the terminal:

```
sudo -l
```

Requires password input.

You can also try this:

```
sudo -v
```

---

### Post by ogola89 on 2019-06-19
Thanks for the reply, I typed in sudo-l and this is what it says:

```
$ sudo -l
[sudo] password for ogola:
Matching Defaults entries for ogola on Tom-HP:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin


User ogola may run the following commands on Tom-HP:
    (ALL : ALL) ALL

```

When I run any sudo commands, I type in my password with no problem, but it still gives me this.

```
$ sudo apt get update
sudo: unable to fork: Invalid argument 
```

sudo -v doesn't return anything

---

### Post by Rubi1200 on 2019-06-19
Your permissions seem to be fine and the output is normal.

Have you by chance made any changes to the /etc/sudoers file or changed permissions for it?

I would also look into the link posted by mc4man in case Comodo somehow blocked an essential system file.

And perhaps also check here in case we missed something:
[https://docs.microsoft.com/en-us/windows/wsl/about](https://docs.microsoft.com/en-us/windows/wsl/about)

---

### Post by kpatz on 2019-06-19
"Invalid argument" is errno EINVAL.  The fork() system call can only return EAGAIN, ENOMEM, or ENOSYS.  So if it's returning EINVAL, something is causing it, probably your Comodo firewall.  Can you temporary disable it and see if sudo works?

Can other processes fork?  For example, can you log in or ssh into another terminal, or launch another application from the GUI, or run a program from the shell without sudo? Those things fork as well.

I was about to mention selinux/apparmor, but then I re-read your post and see you're using WSL in Windows, so it's not even a "real" Linux kernel.  I'd try disabling Comodo and see what happens, and if that works, check the settings and see if you can figure out what you blocked.

---

### Post by ogola89 on 2019-06-19
Hi Rubi1200, mc4man,

Thanks for your responses.

Would interference by the comodo firewall give such a problem with sudo, which returns the invalid argument so quickly, occur without any prompt from the firewall? I had previously unblocked all the files/applications soon after what I did earlier, even turning off the firewall temporarily but without avail.

I did make some changes to some files today, the ~/.bashrc file - to include setting ```
[COLOR=#231F20]export DISPLAY=:0[/COLOR]
``` to allow for displaying of GUIs using xming, a well as editing the sshd_config with the following changes/additions:

```
*Change - PermitRootLogin no*
*Add - AllowUsers yourusername*
*Change - PasswordAuthentication yes*
*Add - UsePrivilegeSeparation no*
*Change - ListenAddress 0.0.0.0*
*Change - Port 2200*
```

Could the above PermitRootLogin = no be the cause?

---

### Post by ogola89 on 2019-06-19
Hi kpatz,

I can launch already-installed apps through Xming, I can run python and R and execute plotting functions with them that show up. I can more or less run everything fine except sudo.

---

### Post by kpatz on 2019-06-19
Check application rules in Comodo: [https://help.comodo.com/topic-72-1-766-9200-.html](https://help.comodo.com/topic-72-1-766-9200-.html)  There's mention of "containment rules" on this page... maybe that's where you need to go to fix this.

---

### Post by mc4man on 2019-06-19
> I am using COMODO firewall, which prompted me as to how to treat the command/file. However, I noticed at that point that I had a typo and **selected it to be 'contained'** so as to not allow writing of anything that I wasn't sure.

Check comodo as per link

---

### Post by ogola89 on 2019-06-19
Hi there,

As mentioned, I unblocked everything, have checked that it is not contained, I have even restarted the laptop, went through the list, even added it as an allowed application, exited comodo etc and still getting the same thing

---

### Post by ogola89 on 2019-06-19
Hi All,

I decided to uninstall comodo firewall from your advice, and it worked! Changing the settings didn't seem to work, but this has.

---

### Post by Rubi1200 on 2019-06-19
Glad to hear you got this resolved :-)

---

