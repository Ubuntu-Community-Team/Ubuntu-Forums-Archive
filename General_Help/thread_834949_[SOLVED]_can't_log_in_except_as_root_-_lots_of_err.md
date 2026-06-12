---
title: "[SOLVED] can't log in except as root - lots of error messages"
date: 2008-06-20
forum: General Help
---

### Post by DouglasAWh on 2008-06-20
I am pasting together a couple e-mails here and it's late, so my apologies if something doesn't make sense.

This is not a GNOME issue since I install KDE and that doesn't work either, but I was trying to fix a 915resolution issue I was having with the resolution being funky after hibernation (worked fine otherwise)

I also did 'apt-get dist-upgrade' and that didn't fix either issue, though it did appear to update the kernel. 

When I try to 'startx' from any account other than root, I get the following error:

'waiting for X server to shut down FreeFontPath:FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing it'

When I boot up (I do the super secure, auto login) I get the error

'GDM could not write to your authorization file.  Thus could mean that you are out of disk space or that your home directory could not be opened for writing. In any case, it is not possible to log in.  Please contact your system administrator.'

at some point I was actually able to log in and I got this error:

'Your session only lasted less than 10 seconds.  If you have not logged out yourself, thus could mean that there is some installation problem or that you may be out of disk space.  Try loggin in with one of the failsafe sessions to see if you can fix this problem.

*box* view details (~/.xsession-errors file)'

and that errors file says...

'/etc/gdm/Xsession:Beginning session setup...
setting IM through im-switch for locale=en_US.
start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default
mkdtemp:private socket dir: Permission denied'


Possibly it's a permission issue, but that's the case for ALL the users other than root.  Very strange.  I even created a new admin user.

On the Carolina Open Source Initiative list I got the suggestion to use fsck, but I'm not sure how that would help. 

I also saw this error message:
'xauth: error in locking authority file /home/whitdoug/.Xauthority'

I tried to do something with the login screens (I can't remember what, it's late), but I got this error message:
'an error occurred while trying to contact the login screens.  Not all updates may have taken effect'.

One of the things I installed trying to fix the hibernation issue was acpi_support_0.91build2_i386.deb, but I wasn't exactly sure what I was doing, I was just following some instructions.  I'd get the post on ubuntuforums I was looking at, but that's more difficult since I'm not logged on to my account any more....and I'm tired.  I'll look into it more tomorrow.

---

### Post by kalesh7 on 2008-06-20
possibly the user does not own files in his home directory
login as root and try this 
chown -R username:username /home/username/

---

### Post by ryanhaigh on 2008-06-20
I don't think normal users are generally able to start the x server via the startx command on a normal ubuntu install. You could try something like 
```

sudo /etc/init.d/gdm restart

```
You might also want to move/delete the file which tells gdm to log you in automatically.
```

sudo mv /etc/gdm/gdm.conf-custom /etc/gdm/back_gdm.conf-custom

```
You might also want to check the permissions of the users home folders.
```

ls -l /home

```
Finally I remember having an issue similar to this when my home partition stopped mounting at boot due to a UUID issue so if you have /home on a separate partition you might want to make sure it is being mounted using the command ```
mount
```

---

### Post by DouglasAWh on 2008-06-20
```

root@laptop:~# ls -l /home
total 12
drwxr-xr-x  26 cosi       cosi       4096 2008-06-19 22:25 cosi
drwxr-xr-x  10 douglasawh douglasawh 4096 2008-06-19 22:28 douglasawh
drwxr-xr-x 100 whitdoug   whitdoug   4096 2008-06-20 01:10 whitdoug

```

none of those user accounts works....

EDIT: should I be able to see the .Xauthority file from root or does xauth have to be used to read that file?  I'm getting an encoding error with I try to look at the ,Xauthority file.

---

### Post by DouglasAWh on 2008-06-20
ok, I also set /.Xauthority to chmod 777 and I ran fsck, but neither of those fixed the problem...

---

### Post by DouglasAWh on 2008-06-20
I have also not uninstalled and reinstalled gdm.  I installed KDE, but I'm not sure how to log in as that.  Can someone please help me?  I do not like doing everything as root.

---

### Post by DouglasAWh on 2008-06-21
bump.  Please help me!  I've posted at Yahoo! Answers and on two listservs and so far know one knows what is going on :(

---

### Post by DouglasAWh on 2008-06-23
bump.  I still haven't gotten any useful info.  I'd also like to know how to make my root GNOME more like my normal account GNOME.

---

### Post by ryanhaigh on 2008-06-23
Have you tried removing the custom configuration for gdm as I suggested. To log in to kde you will need to modify the session settings on the login screen, obviously if you are logging in automatically you won't be able to do this.

Have you tried making a new user and then seeing if that user has the same issue?

---

### Post by chrisccoulson on 2008-06-23
Do you have any disk space? What is the output of:
```
df -h
```

---

### Post by DouglasAWh on 2008-06-23
> **chrisccoulson said:**
> Do you have any disk space? What is the output of:
```
df -h
```

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              88G   65G   19G  78% /
varrun               1009M  228K 1009M   1% /var/run
varlock              1009M     0 1009M   0% /var/lock
udev                 1009M   44K 1009M   1% /dev
devshm               1009M   48K 1009M   1% /dev/shm
lrm                  1009M   38M  972M   4% /lib/modules/2.6.24-19-generic/volatile

```

---

### Post by DouglasAWh on 2008-06-23
> **ryanhaigh said:**
> Have you tried removing the custom configuration for gdm as I suggested. 


not sure, I'll have to go back and look at that.

> **ryanhaigh said:**
> 
To log in to kde you will need to modify the session settings on the login screen, obviously if you are logging in automatically you won't be able to do this.


I did finally get this working.  I've mentioned that on other threads I think.  I've got threads going at Yahoo! Answers, on three different listservs and on LaunchPad so it's hard to keep up!  But KDE does have the same issue.

> **ryanhaigh said:**
> 
Have you tried making a new user and then seeing if that user has the same issue?

Yes, I can create new users and they all have this issue.  

As an aside, I've also not had consistent Internet while I've been moving, so that's made remembering what I say where and what I've done even more problematic because I can work on it in a continuous period.

---

### Post by DouglasAWh on 2008-06-24
> **ryanhaigh said:**
> Have you tried removing the custom configuration for gdm as I suggested. 

All that does is make it such that I can't log in as root from the log in screen and changes what it looks like.  I mean, there may be other things it does, but that's all I see.  I still get the same error about the authorization file.

---

### Post by x1a4 on 2008-06-24
While you've had a reply to change ownership of your home directory, have you set correct ownership of .Xauthority?  Also, make sure that it is writable.
```
# chown username:groupname /home/user/.Xauthority
# chmod u+rw /home/user/.Xauthority
```

To run KDE by default, modify ~/.dmrc and set Session to kde
```
[Desktop]
Session=kde
Language=en

```

---

### Post by DouglasAWh on 2008-06-24
> **x1a4 said:**
> While you've had a reply to change ownership of your home directory, have you set correct ownership of .Xauthority?  Also, make sure that it is writable.
```
# chown username:groupname /home/user/.Xauthority
# chmod u+rw /home/user/.Xauthority
```


Just tried that.  Didn't help.  Is the .Xauthority file something I can look at and change setting on or something I can replace with a default somewhere?  Does gdm act as a user?  Do I need to get gdm access to .Xauthority?

---

### Post by x1a4 on 2008-06-24
It just occured to me that .Xauthority should not exist when you're not logged in to X.  Delete it, then make sure you have read/write/execute permissions on your home directory.
```
chmod u+rwx /home/user
```

.Xauthority is a binary file containing login info.  It's used (among others) by gksudo.

---

### Post by DouglasAWh on 2008-06-24
ok, deleting the .Xauthority file makes it such that I get an error I used to get

```

Your session only lasted less than 10 seconds. If you have not logged out yourself, thus could mean that there is some installation problem or that you may be out of disk space. Try loggin in with one of the failsafe sessions to see if you can fix this problem.

*box* view details (~/.xsession-errors file)

```


and that errors file says...

```

/etc/gdm/Xsession:Beginning session setup...
setting IM through im-switch for locale=en_US.
start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default
mkdtemp: private socket dir: Permission denied

```

---

### Post by x1a4 on 2008-06-24
See if you now log in into the failsafe session.  If so wait at least 20 second and logout.  See if you can log in now.

---

### Post by DouglasAWh on 2008-06-24
> **x1a4 said:**
> See if you now log in into the failsafe session. 

Nope, new error though!

lots of touchy feely stuff, then:

> 
The error was "Failed to create file '/tmp/gconf-test-locking-file-3MOFDU' Permission denied" (errno = 13)


So, now to test the permissions on the /tmp dir...

---

### Post by yochaigal on 2008-06-24
I had this same problem on two separate machines after updating to the newest kernel....

To fix it, I logged in as root, started X, went to my home directory and checked the permissions.  They were all off. Somehow, doing it from the gui fixed it but when I did chmod and chown nothing happened.  
it seems fine now.
it also gave me a disk usage error but my disk usage was fine...

---

### Post by x1a4 on 2008-06-24
Set /tmp permissions to 777 recursively.
```
chmod -R 777 /tmp
```

Also, kill all instances of GDM, Xorg, KDE, GNOME etc., then see if you have stale .pid and sockets for them in /var/run/.  If so delete them.  The GDM socket, for example, is called **gdm_socket** and its .pid file is **gdm.pid**.  Also delete .Xauthority again, if exists.

---

### Post by DouglasAWh on 2008-06-24
> **yochaigal said:**
> I had this same problem on two separate machines after updating to the newest kernel....

To fix it, I logged in as root, started X, went to my home directory and checked the permissions.  They were all off. Somehow, doing it from the gui fixed it but when I did chmod and chown nothing happened.  
it seems fine now.
it also gave me a disk usage error but my disk usage was fine...

WOW.  What a FAIL on the new kernel.  You are my new best friend, btw.  If you were in Wisconsin, I'd buy you a drink!

---

### Post by yochaigal on 2008-06-24
So it worked, then?
It's interesting, it seems like the permissions get screwed up during the update.  Then, it thinks you are out of disk space because the .dmrc folder won't allow anything to be written.
I don't know why chown and chmod didn't work.  It was really getting me nervous, then I finally used the gui to log in and the permissions were easliy modifiable.

Double check yours---and make sure you apply to all enclosed folders.

---

### Post by DouglasAWh on 2008-06-24
> **yochaigal said:**
> So it worked, then?

So far so good!

> **yochaigal said:**
> 
It's interesting, it seems like the permissions get screwed up during the update.  Then, it thinks you are out of disk space because the .dmrc folder won't allow anything to be written.
I don't know why chown and chmod didn't work.  It was really getting me nervous, then I finally used the gui to log in and the permissions were easliy modifiable.

Double check yours---and make sure you apply to all enclosed folders.

I'll double check the enclosed folders for sure!  I was convinced I had screwed something up trying to fix my hibernation issue, but it doesn't look like it had anything to do with that!  Well, except that I did the upgrade command because of what I was looking at on a forum post about fixing the hibernation issue.  I think I am going to take a break from fixing computer issues for a little while though because this was very frustrating...especially while I was moving halfway across the country!

---

### Post by yochaigal on 2008-06-24
What sorts of hibernation issues were you having? 
Did you successfully install the 915resolution package?
Explain to me as well, if you can what you were trying to do with that acpi .deb

thanks

---

### Post by DouglasAWh on 2008-06-24
> **yochaigal said:**
> What sorts of hibernation issues were you having?


[thread]834667[/thread] explains some of them.  Someone showed me how to tag threads earlier, but I don't remember the syntax and am getting really tired.  The preview looks like it is working though.
 

> **yochaigal said:**
> 
Did you successfully install the 915resolution package?

yes, it has worked for a long time.  At some point, it stopped working in hibernate


> **yochaigal said:**
> 
Explain to me as well, if you can what you were trying to do with that acpi .deb

thanks

Now that I don't exactly remember.  When I find that post again, I'll post it in that other thread.

---

### Post by yochaigal on 2008-06-24
What was happening with the built-in hibernation function? Did you choose to use tuxonice because you thought it might work better?

hit me back when you're rested.

---

### Post by DouglasAWh on 2008-06-24
> **yochaigal said:**
> What was happening with the built-in hibernation function? Did you choose to use tuxonice because you thought it might work better?

hit me back when you're rested.

Here's where I saw TuxOnIce.
[http://groups.google.com/group/915resolution/browse_thread/thread/2522e25303890da0/8dfaadc25844604f?#](http://groups.google.com/group/915resolution/browse_thread/thread/2522e25303890da0/8dfaadc25844604f?#)

it's not really what I wanted to do.

At some point I got to [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/23497](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/23497), which is where I downloaded the acpi file from.  I had the keyboard freeze once I think so I tried that.  I don't remember how I got there though.  I know I was looking at this though [thread]2690982[/thread] post 14 to be specific.  I think I got there from this archived threead: [http://ubuntuforums.org/archive/index.php/t-503587.html](http://ubuntuforums.org/archive/index.php/t-503587.html), but I'm not 100% sure.

As to what it was doing, the resolution was just getting messed up when coming back from hibernate.  Resolution worked fine otherwise though.

As an aside, is there a way to fork this convo?  This is a total derail now. :)  The help is very much appreciate!

---

### Post by yochaigal on 2008-06-24
Create a new post ---- then send the link.

---

### Post by DouglasAWh on 2008-06-24
Why not use the TuxOnIce post?  No one (zero) has posted a response there.  As far as I'm concerned, getting the scripts fixed can be the Ubuntu TuxOnIce...that's really what I was looking for on that post.

Thanks again!

---

### Post by xntrk on 2008-10-12
Thanks guys. I had a similar issue but it was because i changed the permission on the /tmp directory. After I chmoded it 777 and chowned to root:root everything works fine. 

Thanks for all the help.

---

