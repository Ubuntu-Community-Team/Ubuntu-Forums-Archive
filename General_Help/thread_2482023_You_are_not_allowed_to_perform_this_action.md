---
title: "You are not allowed to perform this action"
date: 2022-12-16
forum: General Help
---

### Post by mickee384 on 2022-12-16
I get this when I try to use the GUI software updater. 
[IMG]https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjTZ9NfDPhKLIkO78E2KO1gajum1yFq0lABfxjvn8skpC_EEYCZzSoNszpn2GjYac0gWNsV29Wgdf4Ki6Hglq1vSqPQKee--pIJ6_kd_IGnwncU9qD6lHcnrokdo9JZ37CoD0esp2cG21Cw2qhIuCSUcr0YqVzEKrjJpq9oiqDgY4LoAOcgGos/s707/1.png[/IMG]

[IMG]https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEi80vYRoz11-tgthz18V6Gkp8RZfXJCMP7fp4kzLYlsbIJmSPHHmmem5554OJvaXp7s6h9dtrSuB1oAYjQi_TG8W_vc_bmChjxEFfFyW4zLYZAl5KP6oJ3sscn7H-piRDHglv-CmAWFhtelDkk17oIKsMYzQ9F2NUIUEWTaROe1_fl5YFhAUQ8/s1035/2.png[/IMG]

I rebooted. That changed nothing. I noticed after launching the Software Updater the window shows up and briefly says "awaiting authentication' then displays the "not allowed to perform this action. Is this something to do with pam?

I also cannot view my USB external drives, get this message:
[IMG]https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjRJDEkeD5TGxBVLi8J5-liuN1W4tKpbu9NhAOEbz1elUlHoBWOWYCghu4VlzEjhfLvwXDHUxM0L2uGZW67kU_OyhWR895D_-wyY96mk8Cf4cMPzi2amhFakJ97lnjapA1c8V39qlwKdvd1E6Fl9mXsqQ_cjAumrQtsjo5cMzJYvqkyzhdTCjU/s436/3.png[/IMG]

Seriously all was fine yesterday and I have installed no new software or made any changes in over 2 or more weeks, but have run sudo apt update/upgrade in terminal daily. Also my backups are also now failing due to access denied when trying to run. I cannot use grsync either. Same reason. I am in the sudo group and the only one in that group.

[IMG]https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgYqKZYKulYbJmmOTS8gyveoS6clHEH0KRJhqZDrPXbS8RqVzXCY_dS1tPhUAmQrSm60Nkqni81TnwKUysLs4x-OnzYDeigMPV4Xjxn27zRXZiLQgF1vWafWu_McPMlTX1lvajFpFOb2LxL43GPQ5TLjWtr4lA_5CjcyCJuUvtnFnztNpE1cxQ/s320/4.jpeg[/IMG]

I have been doing som Google searches and more than one mention to check if gksudo is installed. If I run gksudo from CLI, it says basically not found. I think this is depricated.

so since everything works from the terminal and not when using GUI applications I can assume the app is not actually invoking the pop-up to authenticate in GUI. As I mentioned previously I did not perform the partial upgrade.

Is there something from the syslog or other info you require to help you help me solve this that I need to post? It basically seems that the GUI is not challenging authentication - it doesn't produce the popup authentication window. It works fine in Terminal. I am open to learning and doing this by myself, and I will keep looking, but I do need a hand with this issue. 

Any help is definitely appreciated

---

### Post by mickee384 on 2022-12-16
mickee@mickeymouse:~$ sudo -l
[sudo] password for mickee: 
Matching Defaults entries for mickee on mickeymouse:
    env_reset, mail_badpass,
    secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin,
    use_pty

User mickee may run the following commands on mickeymouse:
    (ALL : ALL) ALL

---

### Post by mickee384 on 2022-12-16
I don't think The PolicyKit Authentication Agent is running but is in the Start up applications:

/usr/lib/x86_64-linux-gnu/polkit-mate/polkit-mate-authentication-agent-1

To be sure I ran that command in Terminal and got this output:

```
sudo /usr/lib/x86_64-linux-gnu/polkit-mate/polkit-mate-authentication-agent-1
```
```
```

(polkit-mate-authentication-agent-1:830904): GLib-CRITICAL **: 08:27:44.712: g_variant_new_string: assertion 'string != NULL' failed

(polkit-mate-authentication-agent-1:830904): polkit-mate-1-WARNING **: 08:27:44.713: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
```
```

---

### Post by mickee384 on 2022-12-16
```
mickee@mickeymouse:~$ sudo systemctl status polkit.service
[sudo] password for mickee: 
&#9679; polkit.service - Authorization Manager
     Loaded: loaded (/lib/systemd/system/polkit.service; static)
     Active: active (running) since Wed 2022-12-14 20:24:29 CST; 1 day 12h ago
       Docs: man:polkit(8)
   Main PID: 1739 (polkitd)
      Tasks: 3 (limit: 18908)
     Memory: 6.4M
        CPU: 1.770s
     CGroup: /system.slice/polkit.service
             &#9492;&#9472;1739 /usr/libexec/polkitd --no-debug

Dec 16 08:27:32 mickeymouse polkitd(authority=local)[1739]: Registered Authenti>
Dec 16 08:27:38 mickeymouse polkitd(authority=local)[1739]: Unregistered Authen>
Dec 16 08:27:38 mickeymouse polkitd(authority=local)[1739]: Unregistered Authen>
Dec 16 08:27:38 mickeymouse polkitd(authority=local)[1739]: Registered Authenti>
Dec 16 08:27:44 mickeymouse polkitd(authority=local)[1739]: Registered Authenti>
Dec 16 08:34:55 mickeymouse polkitd(authority=local)[1739]: Unregistered Authen>
Dec 16 08:35:26 mickeymouse polkitd(authority=local)[1739]: Registered Authenti>
Dec 16 08:35:33 mickeymouse polkitd(authority=local)[1739]: Unregistered Authen>
Dec 16 08:38:14 mickeymouse polkitd(authority=local)[1739]: Registered Authenti>
Dec 16 08:38:27 mickeymouse polkitd(authority=local)[1739]: Unregistered Authen
```

---

### Post by TheFu on 2022-12-16
Looks like you may have gotten a bad update due to patching too often.
I'd check using 'id' if you are still in the sudo group.  Besides that, I'd use the CLI for not to do patching/installs and system work.

May want to consider patching less often, say weekly, and never when you need the system to work perfect.  I patch weekly, only on weekends, when I have an extra hour to fix or restore from a backup if things like this happen.  If you are using a volume manager, then you could create a snapshot before patching and discard any changes afterwards. That would be possible with ZFS, BTRFS, or LVM-based systems.  
[https://www.tecmint.com/take-snapshot-of-logical-volume-and-restore-in-lvm/](https://www.tecmint.com/take-snapshot-of-logical-volume-and-restore-in-lvm/) has a guide for this using LVM.  Just don't keep the snapshot forever, only as long as you need to know that nothing catastrophically bad happened.  Snapshots are handy for getting perfect backups, without corruption, too.

A key part of being a good admin is AVOIDING issues before they happen and having a plan to put things back easily if they do happen.

---

### Post by mickee384 on 2022-12-16
```
mickee@mickeymouse:~$ /usr/lib/mate-polkit/polkit-mate-authentication-agent-1
bash: /usr/lib/mate-polkit/polkit-mate-authentication-agent-1: No such file or directory
```

---

### Post by mickee384 on 2022-12-16
Thank you for your response. I will change the frequency of updates. Here is the output of "id"

```
mickee@mickeymouse:~$ id
uid=1000(mickee) gid=1000(mickee) groups=1000(mickee),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),121(lpadmin),135(lxd),136(sambashare),138(vboxusers)
```

Is there a solution to this issue or do I have to reinstall?

---

### Post by TheFu on 2022-12-16
> **mickee384 said:**
> Thank you for your response. I will change the frequency of updates. Here is the output of "id"

```
mickee@mickeymouse:~$ id
uid=1000(mickee) gid=1000(mickee) groups=1000(mickee),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),121(lpadmin),135(lxd),136(sambashare),138(vboxusers)
```

Is there a solution to this issue or do I have to reinstall?

I don't know. I don't have this issue.  I'd wait a few days, then update again, now that you have a workaround.  It would be good to pull the logs to see what was updated via snap and apt the last few days.  That could help you to recognize when/if a fix is applied.  APT has logs under /var/log/ just like every other subsystem.

If I need to elevate privileges for a GUI program, I'll use 'sudo -H {gui-program-name}' to force the HOME environment variable to be set to the user's HOME for the user I'm switching into. 

sudo isn't just for becoming root. It can be used to become any user on the system unless your sudo access is limited by another admin to prevent it.  99.999% of users barely use sudo's massive capabilities.

---

### Post by MAFoElffen on 2022-12-16
The first think I suspected was permissions and group membership... sudo for possible elevated permissions, and plugdev for mounts (includes USB's). If it were something with gksudo or equivalent, you would not have the errors on USB's (plugdev). So then have you submit the output from "id". 

And you did. AND Your group memberships look good(???) They are all the standard group memberships for an admin user.

The only thing I would suggest now is to create another admin user, log in as that user and test it. If it doesn't let you create another admin user, then do so as root from the rescue mode... from a root prompt.

If that corrects it, then use 'deluser' or 'gpasswd' to remove your group original user's memebrship from sudo and plugdev, then re-add those two group memberships. (With a step in-between that to log-in as so it took affect.)
```

deluser YourUserName sudo pludev

```
Beyond that, at the moment, I'm at a lose. This does come up often like this. Especially on user uuid 1000: group guid 1000.

EDIT: After that, if not fixed, then try reinstalling the software center 
```

sudo apt install --reinstall gnome-software

```
(### Those above things would also report polkit auth errors)

Then checking into the GVfs frontends to see if an update failed or messed with "your" installation. I say that because other people haven't been reporting this problem on recent updates... But it is possible that there may have been some recent updates that affected you.

---

### Post by TheFu on 2022-12-16
I've never seen any issues with the core groups having sudo issues. Doubt it is related to that.  

All the tools that are supposed to make the GUI elevated privileges mostly seamless seem to be hacks.  There are some issue every few years.  Some of the tools have been deprecated, for reasons I've never bother to look into.  If you look at the .desktop file used by the menu item, you can see which tool is being used.

sudo has been around and working since the mid-early 1990s.

There are some odd permissions issues if a user is added to the sudo group that can require rebooting. Those have been tied to systemd - yet another "improvement" since running the 'newgrp' command was too hard to have new group membership picked up without a logout/login or reboot.  Sigh.  Many things ARE better, but not everything, unfortunately. Sadly, these improvements tend to break existing, working, long-used, methods for some reason that I don't understand. I'm stupid that way.

To properly troubleshoot this, the exact OS, release, and version of the tools are needed.  Best if people don't guess, since there are currently 3 supported versions (I think).  20.04, 22.04, and 22.10, each with different versions of everything.

---

### Post by MAFoElffen on 2022-12-16
+1 100%. Something *very weird* is going on... More info needed, please.

---

### Post by mickee384 on 2022-12-16
Ubuntu MATE 22.04.1 I will look into the versions of the tools that are not prompting for password and post that here

---

### Post by mickee384 on 2022-12-16
The MATE polkit is indeed installed. Is it fixable or  should I just reinstall?

---

### Post by TheFu on 2022-12-16
> **mickee384 said:**
> The MATE polkit is indeed installed. Is it fixable or  should I just reinstall?

IDK. I don't have Mate nor 22.04.  Wait for someone who does to provide input, unless you can't wait any longer.  You can still run sudo for patching and package management, so it really isn't very important.

You can always use 'sudo -H synaptic' for a GUI package manager too.

---

### Post by mickee384 on 2022-12-17
thank you... I created a new admin user. Everything seems to be fine there as far as this issue goes, however my new user does not have access rights to any of my old /home and external drives files. If i keep that new user (uuid 1001) I will need access to all files owned by uuid 1000, which I will need help doing. I can't just copy the backup (rsync) to my new /home directory as I do not have file access to the external disk containing it.

---

### Post by MAFoElffen on 2022-12-17
Are you up to try to fix your user's group permissions? (Since you now know that is the problem...)

While logged in as your second user
```

sudo deluser OriginalUserName sudo
sudo deluser OriginalUserName plugdev

```
Log in an your old user, then log out again...
```

sudo adduser OriginalUserName sudo
sudo adduser OriginalUserName plugdev

```
Then test your original user...

That way you are not deleting any files, just trying to refresh/jump start the group membership and permissions.

---

### Post by mickee384 on 2022-12-19
I ended up creating a new user and migrating my data to it, however I don't think I was able to restore all my data to it. I will have to practically do a byte by byte restore. (I will have to see what did not restore and do a manual copy from my backup files). Makes me think that the new user created still has some issues with it. So I am not deleting the original user just now, in case someone helps me configure the authentication popup to have it show when elevated rights are needed in GUI.

---

### Post by mickee384 on 2022-12-20
I will try that. Thanks

---

### Post by mickee384 on 2022-12-21
Ubuntu MATE 22.04, what tools are you referring to?

---

### Post by mickee384 on 2022-12-21
> **TheFu said:**
>  A key part of being a good admin is AVOIDING issues before they happen and having a plan to put things back easily if they do happen.

Thanks for the advice. I appreciate it

---

### Post by mickee384 on 2022-12-22
I tried creating a new user and copy the .config files as well as all other files in my other user /home dir. It doesn't appear to be working. It was from a backup on an external Hard drive. I restored that to new user and took ownership on the whole shebang. Very slow and is almost non usable. Should I blow away the home directory and then restore only data? Or is there something else I can do?

---

### Post by #&amp;thj^% on 2022-12-22
After studying this for days now, mickee384 will you try to install this please
```
sudo apt install policykit-1-gnome
```
and either restart or logout, I prefer the restart, it's cleaner.
I'm using the New XFCE 4.18 and I install it regularly:
```
apt policy policykit-1-gnome
policykit-1-gnome:
  Installed: 0.105-7+b1
  Candidate: 0.105-7+b1
  Version table:
 *** 0.105-7+b1 500
        500 https://deb.kaisenlinux.org kaisen-rolling/main amd64 Packages
        100 /var/lib/dpkg/status
     0.105-7 500
        500 http://deb.debian.org/debian bullseye/main amd64 Packages


```
This is apparently a little known bug with XFCE and Mate in Ubuntu where it tries to use policykit-1 instead of policykit-1-gnome. Even running 'pkexec synaptic' on the command line would fail (just as described in the bug). Installing policykit-1-gnome fix's this issue for me.
If this is still the same please see if anything is in "**/var/log/auth.log **"

---

### Post by reckstay on 2022-12-23
[COLOR=#000000]The first think I suspected was permissions and group membership... sudo for possible elevated permissions, and plugdev for mounts (includes USB's). If it were something with gksudo or equivalent, you would not have the errors on USB's (plugdev). So then have you submit the output from "id".

[/COLOR][hellodear.in](https://hellodear.in/)


[tea tv apk](https://teatv.ltd/)

---

### Post by ActionParsnip on 2022-12-23
if you run
```

sudo apt update

```
Is that OK please?

---

### Post by mickee384 on 2022-12-23
I tried creating a new user and copy the .config files as well as all other files in my other user /home dir. It doesn't appear to be working. It was from a backup on an external Hard drive. I restored that to new user and took ownership on the whole shebang. Very slow and is almost non usable. Should I blow away the home directory and then restore only data? Or is there something else I can do?

---

