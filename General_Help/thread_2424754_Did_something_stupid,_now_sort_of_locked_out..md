---
title: "Did something stupid, now sort of locked out."
date: 2019-08-14
forum: General Help
---

### Post by lazlow13 on 2019-08-14
Ok, I was trying to redesign my basic desktop. I still prefer the old gnome 2 style. Been down the mate/cinnamon routes and there were issues(just don't ask).  So I installed gnome-tweaks (? or something close to it) and added a couple of extensions (dock something, workspace something)(standard repos, nothing squirely) . I noticed that after I turned them on I had lost the workspaces on the right(hit activities to get them to show) and everywhere else(everything else still worked fine). So I figure it had disable the stock one and a log out would activate the new one. Lets me log in, mouse moves around but does nothing, and the keyboard is the same. Tried a reboot to same effect. It will let me "deactivate" the screen saver (un-blank it to show desktop).So, how do I get out of this one?ThanksEdit: 18.04

---

### Post by cruzer001 on 2019-08-14
> So I installed gnome-tweaks (? or something close to it) and added a couple of extensions (dock something, workspace something)(standard repos, nothing squirely) .
Way too many _somethings_ in your request.  Disable all extensions and see if that helps.

---

### Post by lazlow13 on 2019-08-14
So how do you disable the extensions without access to the desktop?

---

### Post by cruzer001 on 2019-08-14
Ctrl + Alt + t
Will that bring up a terminal?
I use FireFox, so here's how it's done in FF.
In terminal enter:
```
firefox
```
Go to gnome extensions site and disable from there.
This wont work without the gnome ext plugin in FF or whatever browser you use.

---

### Post by lazlow13 on 2019-08-14
As I stated in my original post. Keyboard and mouse are dead once you have logged in. The extensions were installed via the package manager.

---

### Post by cruzer001 on 2019-08-14
Are you familiar with recovery mode?

[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

---

### Post by cruzer001 on 2019-08-14
Here we go, reconfigure the shell

[https://askubuntu.com/questions/67764/how-to-remove-and-reinstall-gnome-3/67771#67771](https://askubuntu.com/questions/67764/how-to-remove-and-reinstall-gnome-3/67771#67771)

Edit
One last thing and I got to go,

At the login screen you can also press "Ctrl+Alt+F1" and that will take you to Console.  To leave console "Ctrl+Alt+F7" or just reboot code: sudo reboot.

Its text only, but thats all you need to run commands.

[https://askubuntu.com/questions/506510/what-is-the-difference-between-terminal-console-shell-and-command-line](https://askubuntu.com/questions/506510/what-is-the-difference-between-terminal-console-shell-and-command-line)

---

### Post by lazlow13 on 2019-08-14
I got into a session at the login screen (never thought about trying there, just at the desktop).When I enter gnome-tweaks or firefox it spits out a xwindows(xorg?) error. Went to find the install disk. Found my Redhat 3.0 (not RHEL 3.0, but the earlier one, 1996?). Found my Os/2 2.4 beta floppies. By the time I found the Bionic disks, I decided with all the different desktops that I had installed and removed that I would be better off just doing a clean install. Now the trick will be trying to make the changes I want without repeating whatever happened. Hopefully it was just a conflict with some ruminant from one of the other desktops. Thanks for the help.

---

### Post by lazlow13 on 2019-08-14
So wound up with the same lockout after the fresh install. Eventually I discovered that two packages were needed but not installed for some reason.[.......]"python-q-text-as-data"{........]"python3-q-text-as-data"[........}installed those and regained control(normal).  Now lets see how many more times I can shoot myself in the foot.{.......}As a side note, how do I keep this forum from reformatting my posts? Of all the forums I use, this is the only one that does this.

---

### Post by cruzer001 on 2019-08-14
It's a learning process, too many desktops can have ill effects.  A reinstall is a sure way to clean it all out.  I show those two python packages as not installed, don't know whats up with that.

Maybe something like GnomeBoxes would be of interest to you.  With virtual machines you can test and experiment without ever putting your primary installation at risk.
```
sudo apt install gnome-boxes
```
[https://www.lifewire.com/guide-to-gnome-boxes-2202073](https://www.lifewire.com/guide-to-gnome-boxes-2202073)

Don't forget to mark your thread as solved.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by again? on 2019-08-14
First thing to check is the graphical session you are logging into.
Session selection is available after inputting your login name.
[ATTACH=CONFIG]283794[/ATTACH]

If you mess up, you can reset a lot of settings by running a dconf command.
Login to the console as you did previously at the greeter and run....
```
dconf reset -f /org/gnome/
```

Also if/when you can login in to a graphical session you can use gnome-tweaks to reset settings or disable shell extensions.
[ATTACH=CONFIG]283795[/ATTACH]

---

### Post by lazlow13 on 2019-08-15
The only session left was ubuntu. The dconf reset would have been really handy. Ran across Gnome-flashback-session(in standard repo). It seems to have gotten me to about 90% of where I want to be.Unfortunately when it rains it pours. Lost internet last night. It is not unusual with my ISP, so I just shrugged it off. A couple of hours later a neighbour said his was up.  Huh-mm. Could ping the router but not connect. Turns out that my NAS, which has had the same static IP for 3-4 years, up and decided it had to have an address that was assigned to another device and was pretty persistent about it. Enough so that it locked/overloaded/whatever the router. That took a few hours to track down and straighten out. At least the router was not fried. Edit: This reformatting of posts is a PITA.

---

### Post by lazlow13 on 2019-08-15
Add blocker was blocking the advanced control panel.

Thanks

---

