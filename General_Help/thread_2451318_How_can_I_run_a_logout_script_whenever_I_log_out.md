---
title: "How can I run a logout script whenever I log out?"
date: 2020-10-01
forum: General Help
---

### Post by Paddy Landau on 2020-10-01
I want a specific script to run every time I log out, whether it's via *Settings > Power Off/Log Out > Log Out* (so the computer remains on) or *Settings > Power Off/Log Out > Power Off… > Restart* or *Power Off*.

It mustn't run if I merely Suspend or Switch User.

The script is extremely simple, quick, and just for the one user, not for any other user on the system.

The answers that I've found for Ubuntu 20.04 or Gnome 3 say to edit either ~/.bash_logout, which doesn't run (even if I make it executable), or /etc/gdm/PostSession/Default, but the folder /etc/gdm doesn't exist.

I've been searching for ages, but I can't find an answer.

How can I run a logout script when I log out?

I'm using Ubuntu 20.04 with Gnome 3.36.3.

---

### Post by ajgreeny on 2020-10-01
To some extent the possibilities for this, and how you might be able to do it will depend on what your script does, how long it takes, and how you currently shutdown.

I use a keyboard shortcut to shutdown my Xubuntu machine with the ***Super key (Windows) + Pause/Break*** keys which run command ***xfce4-session-logout --halt*** to which I could easily add a script to run first, then shutdown the machine.  I have no idea what command the shutdown button itself runs as I've not needed to find it but it may be possible for you to do something along the lines of my shutdown system if you can find out the command that you currently use.

If you can find the command for the method you use now just run your script but add the shutdown command as its final command.

---

### Post by dragonfly41 on 2020-10-01
I have found that AutoKey can be useful for such tasks.
Assign a hot key to run a custom python script in AutoKey saved in ~/.config/autokey/data/
Use subprocess in python script to run the command(s).

---

### Post by Paddy Landau on 2020-10-02
Thank you for your idea. I might have to take it up, although I was trying to avoid that.

The reason is that it's a bit more complicated…

Ubuntu 20.04 doesn't have a guest account, due to some problem that I don't understand. So, I've set up an account intended to be a guest account. On logging out, the script replaces the entire contents of the guest account with a mostly-empty template to reset the account (the template has been marked immutable). That's why I want this script to run on logout.

---

### Post by dragonfly41 on 2020-10-02
[COLOR=#000000]> On logging out, the script replaces the entire contents of the guest account with a mostly-empty template to reset the account (the template has been marked immutable). That's why I want this script to run on logout.

But .. can't you use AutoKey to run your script above (use python subprocess) and then logout?[/COLOR]

---

### Post by Paddy Landau on 2020-10-02
> **dragonfly41 said:**
> [COLOR=#000000]But .. can't you use AutoKey to run your script above (use python subprocess) and then logout?[/COLOR]
Probably I could, but because it's a guest account, I can't ensure that whoever uses it will use that autokey. I'd have to somehow tie the command it to the built-in menu options for logout, restart or power-down.

---

### Post by Tadaen_Sylvermane on 2020-10-02
I'm running Xubuntu so I don't have Gdm. Is it /etc/gdm3 by chance? I used to have some auto scripts there if I recall when I did use Gnome. Maybe typo or slight oversight?

---

### Post by norobro on 2020-10-02
> **Tadaen_Sylvermane said:**
> ... Is it /etc/gdm3 by chance? ...Yes.  [https://packages.ubuntu.com/focal/amd64/gdm3/filelist](https://packages.ubuntu.com/focal/amd64/gdm3/filelist)

I have a script in [COLOR=#000000]/etc/gdm3/PostSession/Default [/COLOR]that runs on logout.

---

### Post by Paddy Landau on 2020-10-02
@Tadaen_Sylvermane and @norobro

Thank you. First, a face palm for me, not thinking of looking at /etc/gdm3 :redface:

I've tested this.

/etc/gdm3/PostSession/Default works if I log out but don't restart. However, it fails to run if I restart.

So, it's part way there — it runs when logging out without restarting, but it doesn't run when logging out by restarting.

Do you have another idea?

---

### Post by norobro on 2020-10-02
Found a Redhat bug report that says that this was fixed upstream a year ago but it doesn't work for me either. [https://bugzilla.redhat.com/show_bug.cgi?id=1547158](https://bugzilla.redhat.com/show_bug.cgi?id=1547158)

Would a systemd service work? Something like this:```
[Unit]
Description=Run at reboot
DefaultDependencies=no
Before=reboot.target


[Service]
Type=oneshot
ExecStart=/path/to/reboot_script.sh
TimeoutStartSec=0


[Install]
WantedBy=reboot.target

```

---

### Post by oldfred on 2020-10-02
Are you sure you want to do this on shutdown?
What if I just pull plug, turn off power or a power failure. Do you have backup power with connection, so normal shutdown can occur?
If not may be better to have a start up script that does what you want.

---

### Post by HermanAB on 2020-10-03
Once you finally got it all sorted, you’ll realize nothing will run if someone pulls the plug.  

So you really should rather run these things on login.

BTW Are you sure this won’t work?
https://linuxconfig.org/how-to-enable-guest-session-on-ubuntu-20-04-focal-fossa-linux

---

### Post by Paddy Landau on 2020-10-03
> **norobro said:**
> Would a systemd service work? Something like this:…
I have no idea how to use systemd, or even what it is. Where would I put that code?
> **oldfred said:**
> Are you sure you want to do this on shutdown? … If not may be better to have a start up script that does what you want.
Good point. I want it done on logout, to delete sensitive information, and so maybe both shutdown (for normal closing) and startup (for power failures) would be best.
> **HermanAB said:**
> Are you sure this won’t work?
[https://linuxconfig.org/how-to-enable-guest-session-on-ubuntu-20-04-focal-fossa-linux](https://linuxconfig.org/how-to-enable-guest-session-on-ubuntu-20-04-focal-fossa-linux)
That's an interesting one. The thing is that it changes the display manager. What does that mean for my day-to-day work, currently Gnome 3? I don't understand the difference between a display manager and whatever Gnome 3 is. Also, if it doesn't work well, there are no instructions for how to revert. I'd hate to have to reinstall my entire system! I understand that LightDM doesn't entirely secure the guest, but I'll just have to live with that — there are no state secrets here.

---

### Post by dragonfly41 on 2020-10-03
> **Paddy Landau said:**
> I have no idea how to use systemd, or even what it is. Where would I put that code?

I spotted this yesterday when looking around. Might be relevant.

[https://linuxconfig.org/how-to-run-script-on-startup-on-ubuntu-20-04-focal-fossa-server-desktop](https://linuxconfig.org/how-to-run-script-on-startup-on-ubuntu-20-04-focal-fossa-server-desktop)

---

### Post by HermanAB on 2020-10-03
I have in the past switched out the Display Manager under Gnome and it continued to work without any issues.  For example, KDE and Gnome each have their own display managers and they are interchangeable.

---

### Post by Paddy Landau on 2020-10-03
> **dragonfly41 said:**
> I spotted this yesterday when looking around. Might be relevant.

[https://linuxconfig.org/how-to-run-script-on-startup-on-ubuntu-20-04-focal-fossa-server-desktop](https://linuxconfig.org/how-to-run-script-on-startup-on-ubuntu-20-04-focal-fossa-server-desktop)
Thank you, that was relevant.

After much googling and trying to understand the complexities of systemd (I really don't understand it, so I copied from examples on the internet), I now have the following.

[LIST]
[*]/etc/gdm3/PostSession/Default
Amended to run the script for the user only.
This runs only when the user logs off but does not shut down.
[/LIST]

[LIST]
[*]/etc/systemd/system/
Added a service to run the script both at boot and shutdown.
This runs every startup and shutdown, but not when the user logs off.
[/LIST]

This way, I've covered all bases.

Success!

Thank you, everyone, for your comments and ideas.

---

