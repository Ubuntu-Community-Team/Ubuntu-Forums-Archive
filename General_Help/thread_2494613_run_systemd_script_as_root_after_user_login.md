---
title: "run systemd script as root after user login"
date: 2024-01-21
forum: General Help
---

### Post by aeronutt on 2024-01-21
I want to run a systemd script as root, but wait until after a user logs in to execute the one-time script, and ideally after a particular user logs in.  But after any user logs in would also work.  (I'm aware of "systemctl --user enable", but I believe this runs the script as the user.)

---

### Post by TheFu on 2024-01-22
While there might be a more elegant solution, I see two choices, neither use systemd. 

One uses cron with the @REBOOT tag and the other has the script run based on the login of the specific userid in the auto-start settings, but uses sudo which would either prompt for a password to continue or the /etc/sudoers file would need to be setup to allow that single command to run without a password.

If it were me, I'd use the cron method, since that would involve touching fewer files.
[LIST=1]
[*]Make a crontab entry to run @REBOOT that spawns a script to loop every 30 or 60 seconds, 
[*]Check whether a specific userid is logged in after the delay each time.  If you need a local GUI login, look for a specific DE process to be running.  If any sort of login is allowed, including a remote ssh login or remote program or remote desktop, then just check the process table for any program running by the specific userid.  
[*]Using **sleep 30s** in the script.  
[*]Once the userid's process is seen, then continue out of the loop, run the desired program with desired options and exit.
[/LIST]

You could actually pull the program/script directly from the systemd-unit file ... look for 'ExecStart' line  .... or just run 
```
/usr/bin/systemctl start {unit name}
```

By using the crontab and sleep, the process will only run once and when the conditions are met, it will finish.  Sleep takes no processing time, so it is very efficient. If the user isn't logged in, that overhead would be tiny-tiny-tiny-tiny-tiny ... so small as to be insignificant.  Once the user does login, it might take 30 seconds before the task runs, which is probably fine.

BTW, the unit file shouldn't run any GUI tools.

If you say exactly what the final goal is, perhaps there is an easier solution. Maybe an assumption has been made that isn't true or you are expecting a user's actions to cause something to happen which could be handled in a better way?

---

### Post by SeijiSensei on 2024-01-22
I've asked this same question in the past and gotten no effective replies. I have not found any method to run a script with root privileges after the login is completed. It's rather annoying since the network isn't up until the login takes place. Using the now-deprecated /etc/local doesn't help since that is run before the login is prompted.

---

### Post by TheFu on 2024-01-22
> **SeijiSensei said:**
> I've asked this same question in the past and gotten no effective replies. I have not found any method to run a script with root privileges after the login is completed. It's rather annoying since the network isn't up until the login takes place. Using the now-deprecated /etc/local doesn't help since that is run before the login is prompted.

[https://askubuntu.com/questions/159007/how-do-i-run-specific-sudo-commands-without-a-password](https://askubuntu.com/questions/159007/how-do-i-run-specific-sudo-commands-without-a-password)

**Update:**
Or you could just put in a 1 minute delay, if you don't want to learn systemd-wants/-requires methods to ensure that networking is completely up before running some other specific systemd unit file.  I haven't looked, but if you use NFS and mounts via the fstab, I best there's a -requires unit reference in the NFS that mandates networking is up and running.  Further, systemd is supposed to build these dependency tries and ensure that leave dependencies are shutdown first, until nothing is left to be shutdown.  In theory.
[https://fedoramagazine.org/systemd-unit-dependencies-and-order/](https://fedoramagazine.org/systemd-unit-dependencies-and-order/) has some info about Unit file dependencies.
```
$ systemctl list-dependencies --all
``` is the short answer, but the output won't be short.

For example, on an NFS server here, 
```
$ systemctl list-dependencies --all nfs-server.service  |wc -l
1160
```
That's a bunch of dependencies before the NFS server can run.  Every local mount is listed in the dependencies first. I suppose that makes sense, but I'm at a loss for why  systemd-machine-id-commit.service or keyboard-setup.service are also a dependencies.  There are a bunch of those things that got me scratching my head for why.

---

### Post by aeronutt on 2024-01-22
Thanks for the ideas, good stuff.

Not understanding the underlying systemd stuff, it would be nice if I could wait for a particular process to be running to then run a script as root. But I don't think that's possible either.

I've got a workable solution now.  Lots of useless details but here goes. :)
I'm opening a luks partition using seahorse and piping the luks key to the cryptsetup command. But I'm doing that in .profile, and using sudoers.d for the cryptsetup commands.   That means the commands in .profile have to match the commands in sudoers.d.  Initally, .profile was hanging and I couldn't log in because I had changed the .profile commands (ooops!).  What I ended up doing to bullet proof .profile is to add  the "--non-interactive" switch to "sudo" so it would escape rather than just wait for a password entry.

Thanks again for the quick responses.

---

### Post by TheFu on 2024-01-22
> **aeronutt said:**
> Thanks for the ideas, good stuff.

Not understanding the underlying systemd stuff, it would be nice if I could wait for a particular process to be running to then run a script as root. But I don't think that's possible either.

I've got a workable solution now.  Lots of useless details but here goes. :)
I'm opening a luks partition using seahorse and piping the luks key to the cryptsetup command. But I'm doing that in .profile, and using sudoers.d for the cryptsetup commands.   That means the commands in .profile have to match the commands in sudoers.d.  Initally, .profile was hanging and I couldn't log in because I had changed the .profile commands (ooops!).  What I ended up doing to bullet proof .profile is to add  the "--non-interactive" switch to "sudo" so it would escape rather than just wait for a password entry.

Thanks again for the quick responses.

Automatically opening a LUKS partition seems anti-security, however, there are ways to do it for USB storage devices using udev rules and a key-file.  This might help, but I haven't looked at it recently to be certain.   

LUKS on an external USB storage device that automatically unlocks when connected to a specific system:
[LIST]
[*]Creating Part1: [Https://youtu.be/vk9Z2_rEUak](Https://youtu.be/vk9Z2_rEUak) (nerds should find this very funny)
[*]Accessing Part2: [Https://youtu.be/ELEVo6SbYl0](Https://youtu.be/ELEVo6SbYl0) seems to be it.
[*]Text version: [Https://baldnerd.com/add-a-drive-to-linux-and-encrypt-it](Https://baldnerd.com/add-a-drive-to-linux-and-encrypt-it)
[*]
[/LIST]

---

### Post by aeronutt on 2024-01-22
Security and convenience are always at odds. 

In my case, the one threat that I don't quite have a 100% clear answer on is: Assume someone gets physical access to my laptop, and then can of course create/change the root and user password.  Does THAT also change the password for the seahorse keyring?  If yes, I have a security issue.  If not, then I know my risks.

---

### Post by TheFu on 2024-01-22
> **aeronutt said:**
> Security and convenience are always at odds. 

In my case, the one threat that I don't quite have a 100% clear answer on is: Assume someone gets physical access to my laptop, and then can of course create/change the root and user password.  Does THAT also change the password for the seahorse keyring?  If yes, I have a security issue.  If not, then I know my risks.

Er .... I don't trust Gnome with security - at least I don't intend to trust them very much.  Over and over the Gnome team has shown me they have different goals than I do related to software.  They prefer bloat over functionality almost every time.  That's fine, being different is 100% acceptable.  I've never used the built-in keyrings, beyond what ssh provides. My gpg keys and other authentication is stored in a password manager and it can be a slight hassle to use.  I don't mind security being a hassle, provided it leaves me in control.  To unlock LUKS encrypted storage, I use a challenge/response built into LUKS with YubiKeys in the middle.  The storage sits and waits for me to unlock it before boot on laptops.

On desktops and servers, I've considered encrypting everything to make storage warranty service safer.  At this point, I only have 2 HDDs that would able to have warranty service, so I should probably encrypt everything on them.  They have 5 yr warranties.  The last drive of a similar model like those 2 is still being used and has 12+ yrs of spinning. It is definitely beyond the warranty and still showing ZERO issues in the SMART data.

Thanks for your statement above. You've gotten me thinking about LUKS encrypting the newer 8TB Black drives and setting up a key file on the system for automatic opening of the LUKS container.  I might seek a way to read that key file anywhere on my secured LAN.  I've heard that corporations do this, but I've never implemented it.

Hummmmm. I need to sleep on this a few days.

---

### Post by aeronutt on 2024-01-22
Let me know where you end up!  I like having options.  
FYI, my real "sensitive" stuff is in a veracrypt container that requires real-time key entry from me.

---

### Post by #&amp;thj^% on 2024-01-22
> **aeronutt said:**
>  Assume someone gets physical access to my laptop, and then can of course create/change the root and user password.  Does THAT also change the password for the seahorse keyring?  If yes, I have a security issue.  If not, then I know my risks.
It is possible yes....see this:
```
ls ~/.local/share/keyrings
default  Default_keyring.keyring  user.keystore

```
```
cd ~/.local/share/keyrings

```

To uncover:
```
.local/share/keyrings 
&#9492;&#9472;> tac Default_keyring.keyring
```

Seahorse is just a front end for gnome-keyring
Also see TheFu's post#8

---

### Post by aeronutt on 2024-01-22
I may not know exactly what I'm looking at, but none of your commands revealed any problems with my gnome-keyring files.

---

### Post by #&amp;thj^% on 2024-01-22
That wasn't the point, you asked if Seahorse could be changed if someone had gained access to your machine.

---

### Post by TheFu on 2024-01-22
> **1fallen said:**
> That wasn't the point, you asked if Seahorse could be changed if someone had gained access to your machine.

If the files containing the keyring aren't inside a strongly encrypted - say LUKS - container with a file system, then they can be molested by local access to root.  If you don't use whole-disk-encryption on your laptop, you can be pwned.  

Security is hard because there are so many subtle attack vectors.  Encrypting just part of the system is helpful, but not fully secure since anyone with access to the hardware and the ability to mount storage with the OS or HOME directories can make you do things without your knowledge.  Encrypt the OS, home and all data.

Best case, local root can delete your keyring files or edit them in a way to make them unusable - denial is an attack just as much as gaining access.

---

### Post by SeijiSensei on 2024-01-22
> **TheFu said:**
> [https://askubuntu.com/questions/159007/how-do-i-run-specific-sudo-commands-without-a-password](https://askubuntu.com/questions/159007/how-do-i-run-specific-sudo-commands-without-a-password)

Thanks! I'll take a look at that approach.

---

### Post by MAFoElffen on 2024-01-24
On running a script from a unit file after login as root.

Unit files run as default as root unless you specify as a User. That part is a given.

On the timing of... Hmmm. SystemD as a load init sort of ends at multiuser.target or graphical.target, depending on what is used... It seemed plausible, so I looked into it more and found this:
[https://unix.stackexchange.com/a/398411](https://unix.stackexchange.com/a/398411)

---

