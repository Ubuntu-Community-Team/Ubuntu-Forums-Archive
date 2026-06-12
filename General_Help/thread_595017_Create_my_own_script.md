---
title: "Create my own script?"
date: 2007-10-28
forum: General Help
---

### Post by justtech on 2007-10-28
I have searched around and tried to find a solution to my bluetooth keyboard woes.  I normally don't have any issues with it but I still have to keep a PS/2 keyboard laying nearby just incase.  Now, it's not a hard fix once I get my wired keyboard hooked up... all I have to do is type in 
```
sudo hidd --search
```
Then it prompts for my password.  Hit the connect button on the bottom of my keyboard and within 10 seconds I'm back up and running.  So what I would like to accomplish is to make a Bluetooth Icon on the desktop that I can double click on that will execute a script that will run all of this for me without having to type any of it in. So far I have....
```
#!/bin/sh
sudo hidd --search
"My Password"
```
When I run that, I get a permission error and then an unknown code on line 3.  What should I do to make it run it as sudo and use my password?

---

### Post by edoviak on 2007-10-28
Disclaimer: I use Debian, not Ubuntu. Nonetheless, I think this will work:

First, get rid of line 3 and [COLOR="Red"]remove[/COLOR] the **sudo** command from line 2. Second, make sure your script is executable. Third, (as root) place it in **/usr/bin** Then, go open up a terminal, become root and type
[B]
# visudo
[/B]
That will open your **/etc/sudoers** file. Then add a line like:
[B]
%group_name ALL=NOPASSWD: /usr/bin/script_name
[/B]
Press **Ctrl-X** to exit, **Y** to save and **Enter** to write. Then check the **/etc/sudoers** file:
[B]
# visudo -c
[/B]
If all is OK, then exit and add a menu item with the command: **sudo script_name**

That will enable you to run the script from the menu without having to type a password.

Hope this helps,
- Eric

---

### Post by nick_h on 2007-10-28
Have you tried putting the command in your /etc/rc.local file?  Commands in this file run as root at startup.

---

### Post by justtech on 2007-10-28
> **edoviak said:**
> Disclaimer: I use Debian, not Ubuntu. Nonetheless, I think this will work:

First, get rid of line 3 and [COLOR="Red"]remove[/COLOR] the **sudo** command from line 2. Second, make sure your script is executable. Third, (as root) place it in **/usr/bin** Then, go open up a terminal, become root and type
[B]
# visudo
[/B]
That will open your **/etc/sudoers** file. Then add a line like:
[B]
%group_name ALL=NOPASSWD: script_name
[/B]
Press **Ctrl-X** to exit, **Y** to save and **Enter** to write. Then check the **/etc/sudoers** file:
[B]
# visudo -c
[/B]
If all is OK, then exit and add a menu item with the command: **sudo script_name**

That will enable you to run the script from the menu without having to type a password.

Hope this helps,
- Eric

I have tried this with one slight problem.... when I added the line to the file and saved... I went to check it and now I get....
```
>>> sudoers file: syntax error, line 24 <<<
sudo: parse error in /etc/sudoers near line 24

```
Now I can't even get back into that file to edit it to try and move forward.

---

### Post by edoviak on 2007-10-28
> **justtech said:**
> I have tried this with one slight problem.... when I added the line to the file and saved... I went to check it and now I get....
```
>>> sudoers file: syntax error, line 24 <<<
sudo: parse error in /etc/sudoers near line 24

```
Now I can't even get back into that file to edit it to try and move forward.

Oh ****! What happened? 

Please clarify: are you having trouble editing the **/etc/sudoers** file? or are you having trouble recovering your keyboard script?

I've never screwed up my sudoers file, but you should be able to fix it with **visudo** 

If you're having trouble recovering your keyboard script (and assuming that you  already placed your script in **/usr/bin**), you should be able to recover it from **/usr/bin** At the very least, you should be able to get the text of the script back with **cat**
[B]
$ cat /usr/bin/script_name
[/B]

Also, what did you type in your **/etc/sudoers** file?

Please write back with a little more detail, 
- Eric

EDITED: but he responded quicker than I could type!

---

### Post by edoviak on 2007-10-28
For reference, here's a copy of my **/etc/sudoers** file:
```

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL
%eric ALL=NOPASSWD: /usr/bin/wlassistant
%eric ALL=NOPASSWD: /usr/bin/mnt-extdisk
%eric ALL=NOPASSWD: /usr/bin/umnt-extdisk

```

and here's a copy of **mnt-extdisk** the script I use to mount an external hard disk formatted with NTFS:
```

#! /bin/sh
mount -t ntfs-3g /dev/sda1 /media/external_disk

```
 
The command in my K menu is:
```

sudo mnt-extdisk

```

Hope this helps,
- Eric

---

### Post by justtech on 2007-10-28
> **edoviak said:**
> Oh ****! What happened? 

I assume that you already placed your script in **/usr/bin** Can you get it back from there? Second, was your script executable? Third, what did you type in your **/etc/sudoers** file?

If you need the script back, you can get the text with **cat**
[B]
$ cat /usr/bin/script_name
[/B]
Please write back with a little more detail,
- Eric

Yes I have already placed my script in "/usr/bin/"  I can overwrite it with a new file.  Yes my script was executable.  In "/etc/sudoers/" I typed in...
```
%group_name ALL=NOPASSWD: BluetoothBash
```
If I try and do anything with sudo it gives me the parse error that I gave earlier.

---

### Post by edoviak on 2007-10-28
I see the problem. You have to type the name of your group (not "group_name"). For example, use your login name.

I think that you may have to type in the path to the script. For example, **/usr/bin/BluetoothBash**

You should be able to fix it with **visudo**

- Eric

---

### Post by justtech on 2007-10-28
I see.  Sorry about that.  How can I get back in there to change that?  I can't sudo anything.

---

### Post by edoviak on 2007-10-28
> **justtech said:**
> I see.  Sorry about that.  How can I get back in there to change that?  I can't sudo anything.

Don't apologize to me! I owe you an apology for leading you into this mess! 

What do you mean when you say that you "can't **sudo** anything?" I assume that you mean that you cannot use **sudo** to execute a root command.

If so, use **su** to log in as root and then run **visudo**:
[B]
$ su
Password:
# visudo
[/B]
- Eric

---

### Post by justtech on 2007-10-28
> **edoviak said:**
> Don't apologize to me! I owe you an apology for leading you into this mess! 

What do you mean when you say that you "can't **sudo** anything?" I assume that you mean that you cannot use **sudo** to execute a root command.

If so, use **su** to log in as root and then run **visudo**:
[B]
$ su
Password:
# visudo
[/B]
- Eric

Oh boy.  I can't log into "su" either because I don't know the "su" password.  I've tried everything under the sun and get get it to Authenticate it.  I don't know.

---

### Post by edoviak on 2007-10-28
When you used to type a command with **sudo** didn't it ask you for a password? 

That's the root password.

- Eric

---

### Post by nick_h on 2007-10-28
In Ubuntu the root account is not active by default.  The password for sudo will be the user password.

---

### Post by justtech on 2007-10-28
Correct.  I would use my user password for the "sudo" password.  I remember reading on here one time about someone that made a "su" password but when I just did a search for it, it requires sudo.

---

### Post by edoviak on 2007-10-28
I'm stunned that **sudo** allows you to install whole software packages as a normal user, but that's an argument for a another day.

In the meantime, you must know the root password. After all, you set the root password when you installed the operating system.

I used Kubuntu for a two-month period and I always logged in as root ("super-user") if I wanted to install a package, mount my external hard disk, etc. The root account is there, so you must know the root password.

- Eric

ps: Actually, "su" stands for "switch user," so if you have two normal users on your computer you could login as the other user by typing:
[B]
$ su wifes_username
[/B]
If you don't specify another user name, then the default is to login in as root ("super-user").

---

### Post by justtech on 2007-10-28
When I installed Ubuntu, it just asked for me to set up my user.  Then the sudo password defaults to my user password.

---

### Post by justtech on 2007-10-28
NE other way to get in there and edit it?  How about before it boots into X server?

---

### Post by justtech on 2007-10-28
I went into failsafe mode and fixed that file and then rechecked the visudo and everything parsed "OK"

---

### Post by edoviak on 2007-10-28
> **justtech said:**
> NE other way to get in there and edit it?  How about before it boots into X server?

Here's an idea: 

Ask someone to post their **/etc/sudoers** file on this thread (I posted mine, but I use Debian). Copy the text of that post to a USB device, floppy, whatever. Then shut down the computer and insert the Live CD. After the live CD loads, mount the partition of your hard disk where the root file system is located. Then replace the **/etc/sudoers** file with the one that was posted on this thread.

Depending on how much the **/etc/sudoers** file changed, you might not even need a copy of someone else's file. It should be sufficient just to remove the bad line. Another alternative might be to copy the **/etc/sudoers** file that's on the Live CD.

Shutdown, eject the Live CD, reboot into your system and you should be back to normal.

- Eric

---

### Post by edoviak on 2007-10-28
> **justtech said:**
> I went into failsafe mode and fixed that file and then rechecked the visudo and everything parsed "OK"

Whew! Glad to hear it! 

Apologies for leading you into trouble,
- Eric

---

### Post by justtech on 2007-10-28
No No... you have no reason to apologize.  I thank you very much for your help in all of this.  I have gotten everything pretty close to being complete.  Thank you very much for all of your help.  I should have made a backup anyways.  Your instruction has helped me get it to exactly what I need.  Thank you very much again.

---

