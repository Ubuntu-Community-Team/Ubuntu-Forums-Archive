---
title: "Allowing partial sudo for non-admin users"
date: 2020-06-20
forum: General Help
---

### Post by heebiejeebies2 on 2020-06-20
Hi all,

I need to allow access to run a particular shell script for a non-admin user.  I believe there is a way to allow this in the sudoers file, but naturally I'm scared of breaking things in there.  

Supposing the user is called myuser and script is located at /myuser/Data/Myscript.sh , is there a simple way I can allow myuser to run this script as root?

Thanks for your help :)

---

### Post by TheFu on 2020-06-20
Yes. The manpage for the **sudoers** file has an example of that.  You can allow a specific user to run 1 or 50 exact commands, each with only specific options, as any userid, including root, but sudoers 

**There are caveats in using sudoers**, so reading the manpage isn't optional. It is required.  This manpage is a work of art, but do take some time to understand.  Start with the EXAMPLES section and work back to the other parts.

Be certain you have a flash boot "Try Ubuntu" setup ready to go and can mount the storage and undo any changes should you screw it up.  I've locked myself out a few times.  Best to test using a different account, not yours.  Easiest to make a backup of any file(s) you modify to make putting it back easier.

---

### Post by Impavidus on 2020-06-20
The directory /myuser/Data/ doesn't exist on a default system with a user named myuser. It looks like a place where user myuser is allowed to store files. So I'll give one warning: keep in mind that in no way this user must be capable of modifying or replacing the file /myuser/Data/Myscript.sh. If this user can modify or replace this script, you could just as well grant him complete root access via sudo. I.e., no write permissions on /myuser, no write permissions on /myuser/Data and no write permissions on /myuser/Data/Myscript.sh and no ownership of any of those. (Write permission on a directory is acceptable if myuser is not the owner of the directory and the sticky bit has been set.)

---

### Post by kneutron on 2020-06-20
PROTIP: always use ' **visudo** ' to edit the sudoers file, and you cannot go wrong. It literally will not allow you to save an invalid config.  And you don't have to use vi, set the EDITOR var before calling it to use whatever non-GUI editor you prefer.

Of course, you should be logged in on another xterm already as root in case $thing goes wrong (and backup the sudoers file before doing ANYthing.)

---

### Post by TheFu on 2020-06-20
> **kneutron said:**
>  
Of course, you should have a root password set and be logged in on another xterm already as root in case $thing goes wrong (and backup the sudoers file before doing ANYthing.)
 
No unlocked root is ever needed with ubuntu. Suggesting it was against forum rules last time i checked.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by kneutron on 2020-06-20
--Ah well, I can't keep track of everything. I'm old-school No True Sysadmin Should Be Afraid of Root style, that's what Backups and MC are for ;-)

---

### Post by heebiejeebies2 on 2020-06-20
Thanks everyone. I have no idea what I'm doing; I tried this example from the sudoers manual:

myuser       mymachine = RUN

I edited using visudo and it did save the changes, but it gave me this error in the terminal straight afterwards:

Warning: /etc/sudoers:28 Cmnd_Alias "RUN" referenced but not defined

I wasn't game to try it out in case I broke something so I reverted the changes.  Any thoughts?

---

### Post by TheFu on 2020-06-21
This would go into the sudoers or a file in sudoers.d/
```
# Setup some aliases to make things easier later:
User_Alias      WEBMASTERS = will, wendy, wim
Host_Alias      SERVERS = master, mail, www, ns
Cmnd_Alias      REBOOT = /usr/sbin/reboot

# What can those users do?
WEBMASTERS      SERVERS =  REBOOT
```

sudo allows:
[LIST=1]
[*]different users and/or groups to be specified
[*]different servers to allow and disallow capabilities
[*]different commands to be run
[*]different user IDs to be used for running processes, not just root.
[/LIST]
So users (will, wendy, wim) when on servers (master, mail, www, ns) can run exactly (/usr/sbin/reboot). If will is on a server with hostname "blog", he cannot reboot.

As said above by Impavidus, always lock down the command to be run so only root/sudo can modify it in any way. A good understanding of file and directory permissions is necessary or just make root:root the owner+group with 755 permissions for the program, script and directory holding the program/script. If that isn't handled correctly, the user can take over the system. Normally, root-only scripts should be placed into /usr/local/sbin/.

The EXAMPLES section in the manpage has more and all the caveats.

---

### Post by kneutron on 2020-06-21
> [COLOR=#000000]I wasn't game to try it out in case I broke something so I reverted the changes

--The warning it gave you wasn't a showstopper.  You tried to give it a definition but didn't say what that definition meant first. It needs to know what RUN is limited to before attaching it to a user. But using the textbook definition literally will not apply to your system.  You need to give it an actual userid to apply to.


--If you're extremely n00b-wary of trying things out with sudoers on your live system, I highly recommend you install virtualbox, install the same distro you're using in a VM, and try modifying things in that protected/safe/disposable environment.  You can easily make a snapshot before trying a change - and revert quickly if it fails.  Once you finalize things the way you want and verify they're working right, you can duplicate your VM setup on the host.  (This is actually recommended, having Test and Prod environments even for home use so you don't shoot yourself in the foot.)[/COLOR]

---

### Post by heebiejeebies2 on 2020-06-25
Thanks everyone. It worked!!

For posterity, all I did was create a command alias which showed the path to the shell script:
**Cmnd_Alias      MYCOMMAND = /home/myuser/script.sh**

Only needed one user and one server, so then I just put:

[B]myuser      mymachine =  MYCOMMAND
[/B]
Then I run the script from the terminal using "sudo /path/to/script.sh" :KS

---

### Post by TheFu on 2020-06-25
/home/myuser/script.sh is a poor choice for any program/script that can be run as root.  Best to put it in /usr/local/bin with root:root ownership and 755 permissions.  When someone takes over your account, they can modify that script to get root without the same difficulties that a script in /usr/local/ provides.

Security via sudo isn't all the security necessary.

---

### Post by ActionParsnip on 2020-06-26
If you use system groups then you can add users to groups to give access rather than faffing with visudo for each user

---

