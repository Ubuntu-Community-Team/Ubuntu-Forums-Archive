---
title: "stuck at login - after changing login screen"
date: 2008-05-05
forum: General Help
---

### Post by 4now on 2008-05-05
Now i've done it

using ubuntu I added a new login screen from the gnome-look site

upon next boot the wheel is stuck spinning before the login screen appears

help please

:cry:

---

### Post by 4now on 2008-05-05
sudo /etc/init.d/gdm stop
startx

gets me in

then sudo /etc/init.d/gdm start - to try and access login manager

but I'm stuck with this error: 
Failed to run gdm setup as root, unable to copy user's xauthorization file.

---

### Post by 4now on 2008-05-06
now i've done it

i'm all alone

---

### Post by VanguardOutlander on 2008-05-07
I had the same issue, running Synaptic Package Manager from the menu was giving this error:

```
"unable to copy user's xauthorization file"
```
"unable to copy user's xauthorisation file" <-- added that for people who search for the international spelling of authorisation ;)

I thought logging out of X and back in again would fix it, but that only got me stuck at the login screen as well. It then wouldn't log in again.

Ok so what was the problem and how did I fix it?

The problem appeared to be the permissions on the /tmp filesystem where many programs write their temporary files. My permissions for /tmp were 744 on my machine I think and I'm not sure how this happened.

To fix your permissions, if you're at the X login screen unable to log into X, then you will need to use a text terminal to set the permissions.

Hit Shift-F2 and log into the console.

Now fix the permissions of /tmp:

```
sudo chmod 777 /tmp
```

and enter your password when sudo asks for it.

Now programs can write to /tmp and hopefully this will resolve your issue. To exit from the terminal, type "exit" or just hit CTRL-D, does the same thing.

Now to get back to the X login screen, type Shift-F7 and you should be back at the gui, try logging in, see how you go. 

Hope I could help people out there :)

Rock On!

:guitar:

---

### Post by 4now on 2008-05-07
My situation must be too different

I can restart gdm & login to x 

with the interface - when I hit login manager - it produces the error

in terminal- sudo chmod 777 /tmp does nothing
if I log out I only have the option to log back in - not enter a command.  If I then enter sudo chmod 777 /tmp - nothing seems to happen - and the situation has not changed when i restart gdm and try

---

### Post by VanguardOutlander on 2008-05-07
Just in case you could set permissions recursively in /tmp if you're really stuck I guess. So could be worth a try to do:

sudo chmod -R 777 /tmp

in case it's not just the tmp dir itself with incorrect permissions but something inside /tmp that needs perms fixing.

After that if you still see this error:

unable to copy user's xauthorization file

then there could be something amiss with the .Xauthorization file located in your home dir, it might be missing possibly.

So what I believe is trying to occur is a program is copying your ~/.Xauthorization file to /tmp/somewhere

I believe the "cannot copy" error happens when the file isn't able to be copied for any reason, like the source file doesn't exist, or the destination isn't writable...

Let me know how you go :)

---

### Post by 4now on 2008-05-07
xauth: error in locking authority file /home/username/.Xauthority...
X:  /tmp/X11-unix has suspicious mode (not 1777) or is not a directory, aborting...

---

### Post by 4now on 2008-05-07
while in x interface tried this from another thread
opened terminal

cd ~
then change permissions on that file:

sudo chown YOURUSERNAME .Xauthority


tried login manager - heart stopped!
new message

gdm (gnome Display Manager) is not running.

You might be using a different display manager such as KDM (KDE Display Manager)...or XDM.  If you wish to use this feature, then your system will need to be configured to use GDM instead ????

---

### Post by VanguardOutlander on 2008-05-07
Ok first lets try to fix the permissions for:

/tmp/X11-unix

by doing:

chmod 1777 /tmp/X11-unix

---

### Post by 4now on 2008-05-07
no such file or directory

---

### Post by VanguardOutlander on 2008-05-07
ok maybe we can just create it:

sudo mkdir /tmp/X11-unix

then

sudo chmod 1777 /tmp/X11-unix

---

### Post by 4now on 2008-05-07
forgot to mention why my heart stopped on the last attempt to lauch login manager

I was presented with the password box this time

and then it told me gdm wasn't running

---

### Post by 4now on 2008-05-07
ok so after creating it

I tried chmod 1777 /tmp/X11-unix

got:

chmod: changing permissions of ' /tmp/X11-unix': Operation not permitted

---

### Post by VanguardOutlander on 2008-05-07
and you did that chmod 1777 with the sudo?

ok maybe just do "sudo chmod 777 /tmp/X11-unix" now that it actually exists...

---

### Post by 4now on 2008-05-07
now trying

sudo chmod 777 /tmp/X11-unix

at least there was return to the next line

what do I do now?

---

### Post by VanguardOutlander on 2008-05-07
try logging into X and see what happens...

---

### Post by 4now on 2008-05-07
thanks

but still gdm not running error when I select - login mangager

---

### Post by VanguardOutlander on 2008-05-07
alrighty

lets try restarting the gdm service then

sudo /etc/init.d/gdm restart

then try logging in

---

### Post by 4now on 2008-05-07
you're the best!

thank you thank you thank you


I will clarify some things for others when I have more time
there is one thing that I borrowed from another thread

thanks again

---

### Post by VanguardOutlander on 2008-05-07
No probs! :D

---

### Post by 4now on 2008-05-07
:popcorn: final notes (to self)

I was in x - graphic mode

entered 
sudo /etc/init.d/gdm restart
into terminal

screen goes black with white bordered box.
Contains scary message with choices YES or NO

select neither - get out of there fast!
with:
ctrl-alt-f7

brings you back to the interface

admin - login manager is now accessible

change back to Ubuntu Human

don't ever try to customize the login screen again

shut down - and restart

---

### Post by 4now on 2008-05-08
one more question please

my username is no longer on the top bar

am I now set to login as root ??

should I be setting something back

-- 
well I guess that was just the user-switching button that became lost in the process

---

### Post by ringwill on 2008-05-23
Thank you, Vanguard Outlander. :) That fixed my problem.

---

