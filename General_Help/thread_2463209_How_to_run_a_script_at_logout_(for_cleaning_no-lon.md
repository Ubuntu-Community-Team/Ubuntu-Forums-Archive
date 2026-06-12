---
title: "How to run a script at logout? (for cleaning no-longer-used mountpoint dirs)"
date: 2021-06-06
forum: General Help
---

### Post by &amp;KyT$0P# on 2021-06-06
I have a case where I would like to run a cleanup script whenever my user has logged out of all active sessions*, including when I'm logged out due to system shutdown/reboot.  I'm currently have it set up as a systemd user service in [FONT=Courier New]~/.config/systemd/user/[/FONT].  It works when I manually do
```
systemctl --user start myservice
systemctl --user stop myservice
```
But [FONT=Courier New]systemctl --user enable myservice[/FONT] and a couple logout/login cycles doesn't result in my script running on logout.

I saw [this thread]("https://ubuntuforums.org/showthread.php?t=2451318") which seems to initially be asking about the same thing.  But the solution there isn't suitable for me, because:

1) I need this within a single user account, not something run as root.

2) I'm on Xubuntu 20.04, which (as I found out the hard way for other reasons) is incompatible with gdm. (And I prefer lightdm anyway.)

My current service, with details irrelevant to this problem edited -
```
[Unit]
Description=blah blah blah
ConditionPathExistsGlob=/home/me/some-dir/*

[Service]
Type=oneshot
RemainAfterExit=yes
ExecStop=/full/absolute/path/to/my/cleanup/script arg1 arg2 argN...

[Install]
WantedBy=default.target
```

How to fix this service to run on logout?  Or is systemd just plain the wrong approach for doing this on Xubuntu 20.04?

* To clarify "all active sessions": I generally only log in one graphical session, but sometimes also log in from a tty in parallel.  In that case the script should not run if only tty session or only graphical session logs out; it should only run when both tty session and graphical session log out.

---

### Post by scorp123 on 2021-06-06
> **halogen2 said:**
>  I have a case where I would like to run a cleanup script whenever my user has logged out of all active sessions*, including when I'm logged out due to system shutdown/reboot. 

How about a **"cron"** job?

I had a similar problem once, ages ago. And I solved it that way. At that time I was using a sub-folder encryption software that was somewhat popular at the time. It has since fallen out of use and hasn't been updated in ages, so no one should be using it these days. But that's not the point ... The point is that back then in one of the last releases the stupid thing had a bug: It would not auto-close the encrypted folder after logging out. Not good ...

I solved this by running a **"cron"** job that would only trigger if I wasn't logged in. "Logged in" meaning both remote via SSH or locally via the desktop.

The "cron" job looked like this and was running as "root" in my case, 1 x every second. You could adjust the timing of course to whatever suits your needs better, e.g. once every hour maybe?

```

*/1 * * * *  /path/to/my/script.sh > /dev/null 2>&1

```

And the script would thus look like this:

```

#! /bin/bash
if [[ -z $(who | grep ^myusernamehere) ]]; then
  #
  # ... do whatever needs to be done when I am not logged in
  #
fi
```

What the *"if [[ -z ..."* line above does:
It triggers the command **"who | grep ^myusernamehere"** and checks if the result is an empty string (-z).

Because if I am logged in that string won't be empty and thus the actions should not be run. But if I am logged out then **"who | grep ^myusername"** should definitely be an empty string and thus the action should be run.

Not super duper elegant, I know. But it does the job and it worked for me back then.

---

### Post by Skaperen on 2021-06-06
> **scorp123 said:**
> 
```

*/1 * * * *  /path/to/my/script.sh > /dev/null 2>&1

```


```

*/1 * * * *  /path/to/my/script.sh &>/dev/null

```
i have not tested if cron will pass the & correctly as i always do this in the script itself.  but &> does make bash code a tiny bit smaller.  and the space after redirection is not needed.  unless you think that makes it easier to read or something, i suggest to leave out that space.

---

### Post by Skaperen on 2021-06-06
> **scorp123 said:**
> 
```

#! /bin/bash
if [[ -z $(who | grep ^myusernamehere) ]]; then
  #
  # ... do whatever needs to be done when I am not logged in
  #
fi
```


continuing my theme of keeping the code short:

```

#!/bin/bash
[[ -z $(who | grep ^myusernamehere) ]]||exit
#
# ... do whatever needs to be done when I am not logged in
#

```
the " | " can probably also be squeezed.

---

### Post by scorp123 on 2021-06-06
> **Skaperen said:**
> continuing my theme of keeping the code short:

I prefer readable + understandable (also for new people) over short.

---

### Post by &amp;KyT$0P# on 2021-06-06
Thanks for the answers.

Regarding use of cron - again, I don't want to run this as root.  Is there a non-polling, user-only way to do this with cron?

Using [FONT=Courier New]who[/FONT] is an interesting idea (thanks scorp123 for informing me of its existence! :) ).  But would that work here if it's run "on logout" by the user who is logging out?

[HR][/HR]

Actually, on second look, I'm concerned I may have created a [XY problem]("https://mywiki.wooledge.org/XyProblem") here.  Why I want this at the moment is, I'm experimenting with sshfs and I discovered if I mount the sshfs inside my home directory, it shows up in Thunar as a removable device.  But I'm creating the mount point directory on demand and I'd like it to go away after the sshfs is unmounted via Thunar's eject button, like happens for flash drive mount points the system creates under [FONT=Courier New]/media/<username>[/FONT] (or, if that's impractical or impossible, clean them all up on logout as described in the OP).

(I've also already tried just putting the mountpoints directories on a tmpfs, but then the mount no longer shows up in Thunar and the mount option to force that isn't supported by sshfs.)

---

### Post by scorp123 on 2021-06-07
> **halogen2 said:**
>  I don't want to run this as root.

Then don't.  :)
It was necessary in my case. As I said above: Tweak it as needed.


> **halogen2 said:**
>  But would that work here if it's run "on logout" by the user who is logging out? 

"who" checks if the user is logged in or not. So my example above doesn't care about "on logout". Only about "not logged in right now" or "logged in right now".


> **halogen2 said:**
>  I'd like it to go away after the sshfs is unmounted via Thunar's eject button 

Wait ... so you're not mounting those SSH locations via Thunar directly? You're mounting them *outside* of Thunar, e.g. via **/etc/fstab** or whatever...? Is there any reason for this?
What happens if you access those SSH locations directly via Thunar and don't mess with mounting SSHFS-anything by any other method?

---

### Post by HermanAB on 2021-06-07
Note that someone could simply ‘pull the plug’ without logging out.  So a cleanup script also has to run at login.  It is usually easiest to forget about the logout case and only run it at login/startup.

---

### Post by &amp;KyT$0P# on 2021-06-07
Ok, I managed to solve what I initially set out to do, and I think my more general question about running cleanup script on/after logout is also answered.

[HR][/HR]

First, for my specific goal of cleaning unused sshfs mountpoints:

I was looking through syslog to see if I could see some event to run cron job or systemd service.  And I noticed lines like this on unmount:
```
systemd[1]: home-me-some\x2ddir-themountpoint.mount: Succeeded.
systemd[1133]: home-me-some\x2ddir-themountpoint.mount: Succeeded.
```
The non-disk-cluttering way to hook this is not with a systemd service per se, but with a systemd template that uses [FONT=Courier New]BindsTo=[/FONT]

So here's an example showing the relevant facets of my [FONT=Courier New]~/.config/systemd/user/clean-user-sshfs-mountpoint@.service[/FONT]
```
[Unit]
Description=Clean leftover unused user sshfs mountpoints
ConditionPathExistsGlob=/home/me/some-dir/*
Before=%i.mount
BindsTo=%i.mount

[Service]
Type=oneshot
RemainAfterExit=yes
ExecStop=/full/absolute/path/to/my/cleanup/script arg1 arg2 argN...
```

Solution is then, I just need to have my mount script do [FONT=Courier New]systemctl --user start clean-user-sshfs-mountpoint@home-me-some\x2ddir-themountpoint[/FONT] after the sshfs mount succeeds.

[HR][/HR]

Second, for the question I asked in the OP:

The requirement was "run as user", not "set up as user and run as user".  If I have a script which functionality actually depends on running after user is logged out and which I can use root privileges to set up, scorp123 suggestion of using cron + who actually could work I think.  While I would prefer something that isn't polling, it seems no such option exists, and the bare-metal systems I have on hand can spare the resources (and for my VMs "on shutdown" would be just as fine, and I'm pretty sure that *can* be done in an event-based way in systemd).  And I can't believe I didn't before thought of making root use su/sudo for the "run as user" part! ](*,) Need to play with cron a bit to make sure that's possible in a cronjob environment.

> **HermanAB said:**
> Note that someone could simply &#8216;pull the plug&#8217; without logging out.  So a cleanup script also has to run at login.

Good point.  In my case this type of cleanup is handled by the mount script.

Anyway I learned some useful and interesting things from this thread.  Thanks all for the replies! :)

---

### Post by TheFu on 2021-06-07
If you want storage to automatically mount and umount, use **autofs**.  It works.  When storage isn't being accessed anymore, it gets umount'ed automatically.

systemd tried to make a workable solution in the /etc/fstab, but it sucks and never umount's storage.

---

