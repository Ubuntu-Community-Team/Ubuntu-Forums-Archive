---
title: "lost power, now only login screen and no recovery mode 12.04"
date: 2013-03-26
forum: General Help
---

### Post by alvinmoneypit on 2013-03-26
Hi,
was working in recovery mode (CNTRL+ALT+F2), logged in.  lost power and when rebooted came to login screen as normal, logged in, but just returned to login screen - not an invalid password yet still only goes to login screen.  A message comes up briefly, but cannot figure out how to stop process to read it.  Tried to login in recovery mode, but it doesn't seem to be available.  I held shift button during boot, but it simply boots up normally to the password screen and of course always returns there on login.  I was going to try changing the password, but no recovery mode to work with.

---

### Post by alvinmoneypit on 2013-03-26
I got back in by downloading/installing gdm and making it default.  After a successful login, I tried switching back to light gdm, but still just returns to login screen, so I broke light gdm - go me.  I'm a little concerned that I can't access recovery mode, although I've never really had to use it, I can see the importance of having it around like a fire extinguisher.  And how to fix light gdm?  Can I delete and reload it from somewhere?

---

### Post by Bashing-om on 2013-03-26
alvinmoneypit;
Maybe you have lost the authority to access your own desktop. See what these terminal commands return:
```

ls -al .ICEauthority
ls -la .Xauthority
```My output for comparison:
> sysop1@1204-a:~$ ls -al .ICEauthority
-rw------- 1 sysop1 sysop1 57876 Mar 26 11:52 .ICEauthority where sysop1 is my user name, if all is well with your access your user name should be present.[INDENT=3]
hope this helps

[/INDENT]

---

### Post by alvinmoneypit on 2013-03-26
Thanks, yes it returned as my username on both requests.  However, I was concerned about that but was able to log in with gdm.  I think light gdm is broken or being prevented by something that happened when I lost power with the root terminal working,  I was trying to start xorg when it happened - it had problems and wasn't finished working yet, although it may have been hung as it was working for a long time.

---

### Post by mrc01 on 2013-03-26
This - login bouncing back to login screen - has happened to me at least twice. In both cases it was my "tmp" storage device not being mounted, so temp wasn't writable to everyone. Was able to log in via text mode (Ctrl-Alt-F1, F2), edit /etc/fstab to mount tmp storage and make the directory writable.

---

### Post by Bashing-om on 2013-03-26
alvinmoneypit;
Also; As you had lost power and the system shutdown could have produced a bad state; Check the filesystem:
```

sudo touch /forcefsck 
sudo shutdown -r now
```does a fs  check on the  re-boot you are performing now.
Watch your screen for any reported errors.

If still a problem try resetting unity/compiz to defaults:.
```
unity --reset
```[INDENT=4]hope this helps

[/INDENT]

---

### Post by alvinmoneypit on 2013-03-26
I looked at my fstab.d folder, it is empty.  Here are the contents to my fstab file, both the folder and file are found in the ect folder.  What do I edit, it's not obvious to me.

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=b7b20a4c-7c48-4f56-a318-a262cfb9dc5a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
#UUID=a0a979f7-4da5-4bf4-80cc-f8a138b3300a none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
```

---

### Post by alvinmoneypit on 2013-03-26
Bashing-om,

I checked the disk on reboot per your instructions: no errors.  I reset unity and it's still working 10 minutes later.  It's has lots of warnings and some errors, I'll post when it's done if need be.

---

### Post by Bashing-om on 2013-03-26
alvinmoneypit;
Did not expect lots of error upon resetting unity, but. how are things looking now ?

And on the topic of fstab: "cryptswap1" --- did you encrypt your home directory on purpose ?
else: that needs fixing !
[INDENT=2]
look'n and strok'n
[/INDENT]

---

### Post by alvinmoneypit on 2013-03-26
Bashing-om,
drive encrypted on purpose, 

unity reset still working, I have to leave and I'll let it work.

---

### Post by alvinmoneypit on 2013-03-26
A sample of a good many of the warnings have to do with these 2 mentioned files/directories, plus there are some errors with compiz I'll post later if need be.

```
WARN  2013-03-26 18:21:34 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application263326262

ERROR 2013-03-26 18:21:36 unity.glib-gobject <unknown>:0 g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
WARN  2013-03-26 18:21:48 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application570171121

```

---

### Post by Bashing-om on 2013-03-26
alvinmoneypit;
With the home directory encrypted, I am stepping into waters I know nothing about. Never done it, never been there.
Resetting unity should not take long at all ... Might consider (re-)installing unity ?
I will await your convenience. 
[INDENT=2]
->sometimes I wonder, other times I just do not know

[/INDENT]

---

### Post by alvinmoneypit on 2013-03-26
Bashing-om,

I'm back for a little, unity reset failed as the reset stalled, never completing, last thing logged was at 18:21 local time and it's now 21:26 and I haven't killed the reset yet..  I have no idea what reinstalling unity would do to my whole system, but willing to give it a try. 
 I have the logs from the reset and all the warnings and errors. 

 I'm going to reboot it again and see where its at, and that'll be it for tonight.  Keep in mind I currently have access through GDM and everything looks good from a desktop standpoint.

---

### Post by alvinmoneypit on 2013-03-26
I shut down the "reset unity" project, rebooted, still had GDM as the default login screen.  I switched it back to light gdm and rebooted.  System still hangs on login, continually returning to the login screen when the correct password is entered.  I switched it back to GDM login through terminal and rebooted, held down shift key, still no recovery mode either, so the whole unity reset routine didn't appear to do anything for me.

Is there a way to stop the process so I can read the messages that come up during shutdown and startup?  I'm talking Ubuntu, not BIOS.

---

### Post by alvinmoneypit on 2013-03-26
I'll consider reloading the whole OS since I'm having so much trouble with various parts, and not encrypt the home folder this time.  I looked briefly for ways to change from encryption back to default, but couldn't find anything right away.  Who knows, maybe encryption is exacerbating the whole problem I've been having with driver installs.  I only had this installed for 10 days or so.

---

### Post by steeldriver on 2013-03-26
You could try resetting lightdm and the 'greeter' by logging in to a virtual terminal (Ctrl-Alt-F1...F6) and then doing

```
sudo service gdm stop
sudo dpkg-reconfigure lightdm 
sudo dpkg-reconfigure unity-greeter 
sudo service lightdm start
```

If that doesn't help, you could consider removing any saved user-sessions by deleting ~/.dmrc

The lightdm/greeter log files might also give some idea what's going wrong

```
sudo tail /var/log/lightdm/lightdm.log
sudo tail /var/log/lightdm/x-0-greeter.log
```

---

### Post by Bashing-om on 2013-03-26
alvinmoneypit;
I am somewhat perturbed that "recovery mode" also is not working. I do not know what correlation could exist with the desk top.
I am considering (re-)installing the entire desktop rather than only the unity portion. Wiser heads may come up with advisement on this issue.

To see the boot messages - maybe - I can and do (10.04 ; 12.04) Try this:
Boot to the grub menu, "e" key for edit, arrow down to the boot line "linux /boot/vmlinuz-3.2.0-24-generic root=UUID=dbd69ed2-530c-4409-8f5a-a3f1ea41fc67 ro quiet splash $vt_handof" or similar and delete the terms "quiet splash". ctl+x keys to continue the boot process.
Maybe ctl+s will stop the display , and ctl+o to resume (got to be real quick)
maybe - works for me- scroll lock key (got to be real quick)
maybe - pause/break key

I find a better way is boot via the above to a text login(remove "quiet splash" insert the term "text"), login, start the Xserver from the terminal, ctl+alt+f7 to get to the gui then when ctl+alt+f1 is executed; the last of the boot messages remain on the display.

I have seen documentation (old ??) that if one were to use the boot parameter "set_page=1" (?? as not certain of the syntax) will be able to page the boot messages. I do not know as I have not tried it to this time.

This is non persistent and does not survive a re-boot. To make it permanent requires an edit to the /etc/default/grub file. Consider making it permanent -- I personally want to see my boot messages.[INDENT=4]try'n to help

[/INDENT]

---

### Post by alvinmoneypit on 2013-03-26
Steeldriver,

Here is the output from the light gdm query:
```
yor@yor-System-Product-Name:~$ sudo tail /var/log/lightdm/lightdm.log
[sudo] password for yor: 
[+85.77s] DEBUG: Process 1180 exited with return value 0
[+85.77s] DEBUG: X server stopped
[+85.77s] DEBUG: Removing X server authority /var/run/lightdm/root/:0
[+85.77s] DEBUG: Releasing VT 7
[+85.77s] DEBUG: Display server stopped
[+85.77s] DEBUG: Display stopped
[+85.77s] DEBUG: Seat stopped
[+85.77s] DEBUG: Display manager stopped
[+85.77s] DEBUG: Stopping daemon
[+85.77s] DEBUG: Exiting with return value 0
yor@yor-System-Product-Name:~$ sudo tail /var/log/lightdm/x-0-greeter.log
[+2.51s] DEBUG: Setting keyboard layout to 'us'
[+2.56s] WARNING: Getting layout failed: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such interface `com.canonical.dbusmenu' on object at path /com/canonical/indicator/users/menu
[+2.56s] DEBUG: notify visible signal received
[+2.56s] CRITICAL: ido_calendar_menu_item_set_date: assertion `IDO_IS_CALENDAR_MENU_ITEM(menuitem)' failed
[+2.56s] DEBUG: New calendar item
[+2.56s] DEBUG: indicator-sound: new_volume_slider_widget
[+2.57s] DEBUG: indicator-sound: new_voip_slider_widget
[+2.57s] DEBUG: background.vala:116: Render of background /usr/share/backgrounds/warty-final-ubuntu.png complete
[+2.59s] DEBUG: background.vala:116: Render of background /home/yor/Pictures/2012/02/07/P2070003.JPG complete
[+2.59s] CRITICAL: background_loader_create_pattern: assertion `image != NULL' failed 
```

---

### Post by Bashing-om on 2013-03-26
alvinmoneypit; steeldriver ***

Wow , I do not know what to make of the output. This could turn into a real learning experience !
Here are the outputs from my working system for comparison to what it should look like.
> sysop1@1204-a:~$ sudo tail /var/log/lightdm/lightdm.log
[sudo] password for sysop1: 
[+147.97s] DEBUG: Greeter quit
[+148.02s] DEBUG: Dropping privileges to uid 1000
[+148.02s] DEBUG: Restoring privileges
[+148.06s] DEBUG: Dropping privileges to uid 1000
[+148.06s] DEBUG: Writing /home/sysop1/.dmrc
[+148.14s] DEBUG: Restoring privileges
[+148.18s] DEBUG: Starting session ubuntu as user sysop1
[+148.18s] DEBUG: Session 1406 running command /usr/sbin/lightdm-session gnome-session --session=ubuntu
[+148.24s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session0
[+148.24s] DEBUG: Greeter closed communication channel


sysop1@1204-a:~$ sudo tail /var/log/lightdm/x-0-greeter.log
[+1.19s] DEBUG: indicator-sound: new_voip_slider_widget
[+1.22s] DEBUG: background.vala:116: Render of background /usr/share/backgrounds/warty-final-ubuntu.png complete
[+1.26s] DEBUG: background.vala:116: Render of background /usr/share/backgrounds/Flocking_by_noombox.jpg complete
[+146.98s] DEBUG: Providing response to display manager
[+146.98s] DEBUG: Wrote 19 bytes to daemon
[+147.09s] DEBUG: Read 8 bytes from daemon
[+147.09s] DEBUG: Read 18 bytes from daemon
[+147.09s] DEBUG: Authentication complete for user sysop1 with return code 0
[+147.10s] DEBUG: Starting session ubuntu
[+147.10s] DEBUG: Wrote 18 bytes to daemon
sysop1@1204-a:~$ [INDENT=4]
inquiring minds want to know

[/INDENT]

---

### Post by steeldriver on 2013-03-26
well I would guess the OP's lightdm.log is just showing lightdm going down and being replaced by gdm - I doubt there will be anything very interesting in the 'tail' of that one unless lightdm is restarted

the greeter log might be indicating a problem with custom image(s) - see

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg3600484.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg3600484.html)

---

### Post by alvinmoneypit on 2013-03-26
Well, recovery mode is back somehow, but not able to mount the file system from dpkg, etc.  If I stop GDM I lose everything to a text screen unfamiliar to me that states a few processes I don't recall, struck me as insignificant.  I don't know how to exit, so I pressed CNTRL+ALT+DEL, some more text came up and I stopped it using SCRLK.  Somethings that may point to problems in that code before reboot:
```

apache2: could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for server name
```
```

nm_dispatcher action: could not get the system bus.  Did not receive a reply.  Possible causes: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
```

---

### Post by alvinmoneypit on 2013-03-27
reconfiguring  to lightdm also shuts the system back to text.  I switched back to lightdm tried to log in, still goes back to login screen, opened terminal.  accessed the logs for light dm and x-0-greeter.  there wasn't much, but I wrote down everything I thought was significant.  tail lightdm.log:

```
session 1846 running 
greeter comment display is ready
stopping greeter display being switched from 
session 1919 got 1 message(s) from PAM
prompt greeter with 1 message
```

tail x-0-geeter.log:

```
CRITICAL: ido_calendar_menu_item_set_date: assertion 'ido_calendar_menu_item_set_date' failed
background 144 Error loading background: Failed to open file [path to pic] Permission denied
background.vala 116 render of background [path to pic] complete
CRITICAL: background_loader_create_pattern: assertion 'image l=NULL' failed
```

---

### Post by Bashing-om on 2013-03-27
alvinmoneypit;

Getting real old saying I do not know. What in the world has "apache2" got to do with a desk top install ?

If and when all else fails, no other solution found; I have a code sequence that will totally rebuild the desk top environment. I have tested in on my system with only unity for the manager; do not know how it would react with GDM also installed on a encrypted home directory. Prior to giving up on fixing your system and going for a (re-)install, will be worth a shot.[INDENT=3]not a great solution, but


[/INDENT]

---

### Post by alvinmoneypit on 2013-03-27
I don't know either.  I wonder about the dispatcher not finding the system bus, but that may be because I was stopping the system with the scrlk.    others have had the issue with the background picture and the calendar, in fact that is where I found the gdm solution.

---

### Post by alvinmoneypit on 2013-03-27
I have a problem with my video driver, too.  Solutions that work for everyone else with the same video card and installed OS don't work for me.  I'll let it sit like this for a week or so, GDM doesn't bother me.  But I'd like to restore full functionality to recovery mode.  I've seen things resolve on their own in the past, maybe this as well.

---

### Post by Bashing-om on 2013-03-27
alvinmoneypit;
With all the errors, let's try and re-configure the desk top,watching, as always, for errors generated ->see what happens:
terminal code:
```
sudo dpkg-reconfigure -plow ubuntu-desktop
```

worth a shot

---

### Post by alvinmoneypit on 2013-03-27
Huh, this command:



```
sudo dpkg-reconfigure -plow ubuntu-desktop
```

returned nothing at all.

---

### Post by Bashing-om on 2013-03-28
alvinmoneypit;

I am at a complete loss. Before proceeding with the "complete" rebuild, I would like others input on this situation. I can think of no reason why the "dpkg" command did not have some kind of return.[INDENT=2]
I am in a learning condition

[/INDENT]

---

### Post by alvinmoneypit on 2013-07-04
I had to reinstall the entire system.

---

### Post by Bashing-om on 2013-07-04
alvinmoneypit; Hey ..

(re-)installing is one solution that always works !

[INDENT][INDENT]still, it is all a process of learning[/INDENT][/INDENT]

---

