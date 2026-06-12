---
title: "lost password, reset doesn't work"
date: 2013-02-06
forum: General Help
---

### Post by TheChristianHippie on 2013-02-06
My daughter's kubuntu has stopped accepting her password for login. I followed the advice here @ [psychocats]("http://www.psychocats.net/ubuntu/resetpassword") website and also tried to follow the advice on this [page]("http://www.noobslab.com/2011/07/recover-ubuntu-password-linux.html") but there is no line that begins with "kernel".

In recovery I "dropped to root" and entered "passwd -d" then "passwd kiersten" and went through the password change, and it said successful, but then on reboot the password doesn't work, it just flashes then returns to the login screen :( Advice? She's running Kubuntu 12.04 dual with windows xp. Windows boots fine. Thanks in advance?

---

### Post by rnerwein on 2013-02-06
> **TheChristianHippie said:**
> My daughter's kubuntu has stopped accepting her password for login. I followed the advice here @ [psychocats]("http://www.psychocats.net/ubuntu/resetpassword") website and also tried to follow the advice on this [page]("http://www.noobslab.com/2011/07/recover-ubuntu-password-linux.html") but there is no line that begins with "kernel".

In recovery I "dropped to root" and entered "passwd -d" then "passwd kiersten" and went through the password change, and it said successful, but then on reboot the password doesn't work, it just flashes then returns to the login screen :( Advice? She's running Kubuntu 12.04 dual with windows xp. Windows boots fine. Thanks in advance?
hi
i ain't be sure - but is the root-filesysten not mounted read-only ?
type: mount -o rw,remount /
and then: passwd kiersten
change it and reboot.
cheers

---

### Post by steeldriver on 2013-02-06
If the login manager "just flashes then returns to the login screen" (no message such as 'login or password incorrect') then it suggests the problem is not the password itself, but the user's X session failing to start

One way to test that is to try logging in at one of the non-GUI virtual terminals using the Ctrl-Alt-F1 or Ctrl-Alt-F2 key combos - if that works, then the password is not the problem and we can start trying to figure out why the session is failing - some possible reasons are:

- home partition full or home dir unwriteable
- user's ~/.Xauthority or ~/.ICEauthority ownership / permissions messed up
- something in the user's profile or bashrc that is killing the session

---

### Post by TheChristianHippie on 2013-02-06
> **rnerwein said:**
> hi
i ain't be sure - but is the root-filesysten not mounted read-only ?
type: mount -o rw,remount /
and then: passwd kiersten
change it and reboot.
cheers

Oh yes of course, I mounted first :D I should have mentioned that.

@ steeldriver, when should I enter the key combos? At grub? Or on the login screen? Thank you!

---

### Post by kanikilu on 2013-02-06
> **TheChristianHippie said:**
> when should I enter the key combos? At grub? Or on the login screen? Thank you! Switch to the virtual console once you get to the normal login screen. If you need to switch back, it's Ctrl+Alt+F7.

---

### Post by TheChristianHippie on 2013-02-06
Thank you kanikilu, I pushed ctrl+alt+f1 at the login screen and it took me to a terminal. I entered her login info and it was successful. :) It gave me "last login" information and is waiting for commands.

So does this mean the problem is the "user's X session failing to start"? So it could be one of these probs steeldriver suggested?;
- home partition full or home dir unwriteable
- user's ~/.Xauthority or ~/.ICEauthority ownership / permissions messed up
- something in the user's profile or bashrc that is killing the session

- She should have plenty of space, her kubuntu is installed on a 20G partition and her /home partition is about 50g and she doesn't have much on it. I don't know how it would become unwritable or how to check?
- I don't know anything about the rest of that list, or how to check it. Thank you for your helps!

---

### Post by lykwydchykyn on 2013-02-06
Once you log in, the command:
```

tail .xsession-errors

```

Should point you in the direction of the problem.  Also, the "mount" command will show you the status of each mounted partition.  If you can post the output of both command, that might give some clues.

---

### Post by TheChristianHippie on 2013-02-06
Thank you lykwydchykyn;

It gave me an error report, I will try and copy it here (by sight):

xsession: xsession started for kiersten
QDBusconnection: session d-bus connection created before QCoreApplication. Application may misbehave. QDBusconnection: session d-bus connection creasted before QCoreApplication. Application may misbehave. X-Terminal-emulator: fatal IO error: client killed
konsole(1947) konsole:: sessionmanager:: ~sessionmanager: konsole session manager destroyed with sessions still alive kiersten a kiersten@-w3644: ~$

I hope that's good enough. The computer is across the room from this one :redface:

---

### Post by TheChristianHippie on 2013-02-06
after "mount" command:

/dev/sda6 on / type ext4 (rw,errors=remount-ro)
porc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on / sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusect1 (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,nosuid,nodev)
/dev/sda5 on /home type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

ps, is there a way to copy/paste this stuff between computers? I don't know if I am getting all the details of these long reports right. My daughter is reading them out to me and I am typing them :) If not, that's ok. I appreciate ya'll's patience :)

---

### Post by lykwydchykyn on 2013-02-06
Well, the disk is not mounted read-only, so you can rule that out.

.xsession-errors is not as helpful as one could wish, in this case.

Try deleting the .ICEauthority and .Xauthority files:
```

rm .ICEauthority .Xauthority

```

they get created automatically on login.  Also double-check the free disk space with:
```

df -h

```

---

### Post by TheChristianHippie on 2013-02-06
> **lykwydchykyn said:**
> Well, the disk is not mounted read-only, so you can rule that out.

.xsession-errors is not as helpful as one could wish, in this case.

Try deleting the .ICEauthority and .Xauthority files:
```

rm .ICEauthority .Xauthority

```

they get created automatically on login.  Also double-check the free disk space with:
```

df -h

```


I typed in the "rm .ICEauthority .Xauthority" and it came back saying "cannot remove, no such file or directory" for both of them.

She has 20g for / with 5g used and 14g available, and for /home she has 50g with 365m used and 47g available.

---

### Post by lykwydchykyn on 2013-02-06
Were you in her home directory when you typed those?  They should be right in her home directory.  

If you're logged in as her and in her home directory, can you create a new file?  try:
```

touch testfile
rm testfile

```

to see if you can create and remove a file.

---

### Post by TheChristianHippie on 2013-02-06
I typed in "touch testfile" and then "rm testfile" and nothing happened.

At the beginning of all this, I pressed "ctrl+alt+f1" while on the login screen and got to this terminal. I typed in her login name, then her password as prompted. So I don't really know where I'm "in" but I'm "in"! :) This is where I've been entering the commands you've given me.

Here's what the prompt looks like in case that tells you where I am:
kiersten@kiersten-w3644:~$

---

### Post by steeldriver on 2013-02-06
OK how about when you type

```
ls -l .{ICE,X}authority
```at the [FONT=Courier New]kiersten@kiersten-w3644:~$ [/FONT]prompt?

---

### Post by TheChristianHippie on 2013-02-06
Thanks steeldriver. Still says, "cannot access" "no such file or directory" for both files.

---

### Post by steeldriver on 2013-02-06
OK well that's not necessarily a problem since they get regenerated as required

Let's just do a quick check on the home dir itself before we move on to try other things

```
ls -ld $HOME
```We're interested in the ownership (user and group) and permissions

---

### Post by TheChristianHippie on 2013-02-06
It came back:
drwxr-xr-x 27 kiersten kiersten 4096 Feb  6 20:06 /home/kiersten

/home/kiersten at the end there is in blue text.

---

### Post by steeldriver on 2013-02-06
OK that all looks good so far

My *guess* is it is something screwed up in the user's saved session profile (or possibly in one of the saved startup applications) - you could try renaming the session file, I don't have a KDE-based machine at the moment but I think that's going to be at ~/.kde4/share/config/ksmserverrc so you could try temporarily renaming that e.g.

```
mv ~/.kde4/share/config/ksmserverrc ~/.kde4/share/config/ksmserverrc.ignore
```

then Ctrl-Alt-F7 back to the GUI and try logging in there again

Alternatively you may just want to wait for someone who really knows about these things to chime in

---

### Post by TheChristianHippie on 2013-02-06
> **steeldriver said:**
> OK that all looks good so far

My *guess* is it is something screwed up in the user's saved session profile (or possibly in one of the saved startup applications) - you could try renaming the session file, I don't have a KDE-based machine at the moment but I think that's going to be at ~/.kde4/share/config/ksmserverrc so you could try temporarily renaming that e.g.

```
mv ~/.kde4/share/config/ksmserverrc ~/.kde4/share/config/ksmserverrc.ignore
```

then Ctrl-Alt-F7 back to the GUI and try logging in there again

Alternatively you may just want to wait for someone who really knows about these things to chime in

Ok, I typed in "mv ~/.kde4/share/config/ksmserverrc ~/.kde4/share/config/ksmserverrc.ignore" and it came back with:

mv: missing destination file operand after '/home/kiersten/ .kde4/share/config/ksmserverrc.ignore'
Try 'mv --help' for more information

I guess I'll see ya'll tomorrow :)

---

### Post by TheChristianHippie on 2013-02-07
Ok, ready for more today ):P I'll check back often for replies. I haven't done anything on it since yesterday.


Ok, well, life happening, be back later tonight :)

---

### Post by steeldriver on 2013-02-07
OK I just stuck Kubuntu 12.0.1 in a VM

The saved session file appears to be in ~/**.kde**/share/config (NOT ~/.kde**4** as I suggested yesterday) i.e. if you want to suppress it you can do

```
mv ~/**.kde**/share/config/ksmserverrc ~/**.kde**/share/config/ksmserverrc.ignore
```The name of the file you 'mv' it to shouldn't matter.

I just tried it, and mv'ing the file caused the next login to revert to a default session

---

### Post by TheChristianHippie on 2013-02-07
Ok, I typed in "mv ~/.kde/share/config/ksmserverrc ~/.kde/share/config/ksmserverrc.ignore" and nothing came back. So I figured it ahd accepted it and I "ctrl+alt+f7"ed back to the login screen, and tried to login, and it flashed and returned to login again :(

---

### Post by steeldriver on 2013-02-07
Hmm OK well it was only a hunch - sorry

A couple of other quick things you could check - does the user kiersten have a ~/.xinitrc or ~/.xsession file in their home directory?

EDIT: or could possibly be a corrupted ~/.dmrc file - see link below (symptoms appear to be the same as yours - including the .xsession-errors message)

[http://www.kubuntuforums.net/showthread.php?59153-HELP!-Can-t-pass-the-login-screen](http://www.kubuntuforums.net/showthread.php?59153-HELP!-Can-t-pass-the-login-screen)

---

### Post by TheChristianHippie on 2013-02-07
Looks promising :)

A few questions though:
1 How do I " make sure you don't have any files owned by root or anyone else in your home directory (mostly just the config files)."? Did we already do that?
2. How do I "pass the login screen by creating a new user."
3. Did we already "[try] renaming .kde and .config to something else to force recreation"? How do I do that if we didn't?
4. How do I "try checking each of the .xxx files by renaming->try login" and what do I rename them to? Do I change it back if that one doesn't work before going on to the next file? How many files are there?
5. How do I remove ".dmrc"? Is there only one of them?

It's like greek to me :( I've probably found the fix many times googling, but just couldn't understand that's what it was when I saw it :( I appreciate ya'll's patience in walking such a n00b through all this! :) <3

---

### Post by steeldriver on 2013-02-07
I think I'd just jump to removing (or just renaming - for now) the ~/.dmrc file, if you have one

```
ls -l ~/.dmrc
``````
mv ~/.dmrc ~/.dmrc.old
```Most of the other suggestions either we did already or don't seem to have helped the posters in that thread

---

### Post by TheChristianHippie on 2013-02-08
> **steeldriver said:**
> I think I'd just jump to removing (or just renaming - for now) the ~/.dmrc file, if you have one

```
ls -l ~/.dmrc
``````
mv ~/.dmrc ~/.dmrc.old
```Most of the other suggestions either we did already or don't seem to have helped the posters in that thread

Ok, I typed in "ls -l ~/.dmrc" and on the next line "mv ~/.dmrc ~/.dmrc.old" it seemed to have accepted it. I then "ctrl+alt+f7"ed to the login window. I typed in her password and it flashed and returned to the login page. I decided to restart and see if it will work, and a warning window popped up asking "would you like to abort active session?" I hit cancel. I decided to try her password again, and IT LOGGED IN! :guitar:

I decided to test our success by restarting the computer to see if login will be successful "next time". The window popped up again, "abort active session?" :( I hit cancel again (Maybe I should hit "ok"???) It returned to the login window instead of restarting. It allowed me to log back in and the system notification helper said something had crashed. I clicked on it and it was the;

"knetattach has closed unexpectedly" 
I couldn't find a "report" button, so I took screen shots of the text in the window. If they would be helpful let me know and I will attach them here. It then requested a restart to "complete the update process", it also had the update icon there, so I clicked it and downloaded/installed the updates listed there.

When the updates were done, I clocked the restart icon in the system try. Again, I am confronted with the "abort active sessions" window with "kiersten: TTY login" in the text window listed under "session" and "vt1" listed under "location".

Should I click "ok"? Or keep hitting "cancel"? What's going on with it? :-s

---

### Post by steeldriver on 2013-02-08
Well I don't know how any sessions can be 'active' if you've restarted the machine. It seems to be referring to your Ctrl-Alt-F1 virtual terminal - but that should be long dead. Are you sure you are really restarting (not just hibernating / suspending?)

Anyhow I don't think it would do any harm to choose 'OK'

---

### Post by TheChristianHippie on 2013-02-08
You were right it was the terminal session. I hit "cancel" again and it took me back to the login screen. I hit "ctrl+alt+f1" and the last command was still visible in the terminal. I typed in "exit" and it logged me out, leaving "login" in the terminal. So I "ctrl+alt+f7"ed back to the login screen, logged in, hit restart, and it restarted without a hitch! It again allowed me to login!

THANK YOU for your help Steeldriver (and others)!! :biggrin: This is an awesome community ):P

---

