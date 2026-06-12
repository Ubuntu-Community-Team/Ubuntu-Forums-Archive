---
title: "Problems with sudo gedit (only gedit works)"
date: 2007-05-16
forum: General Help
---

### Post by loathsome on 2007-05-16
Hi there,

```
loathsome@penguinbox:~$ gedit /etc/ram.txt
# above works
# this dont:
loathsome@penguinbox:~$ sudo gedit /etc/ram.txt

```

.. it just stand there, does nothing. I have to CTRL + C myself to get bash control again. What can I do about this? I tried reinstalling the gedit package.

Thanks:KS

**UPDATE!** This problem is now solved.

> **THIS PROBLEM IS NOW SOLVED**

Thanks for your help everybody! The problem occurred when I manually blanked out /etc/network/interfaces to workaround [_Feisty's boot bug_](http://ubuntulinuxtipstricks.blogspot.com/2007/04/yesterdays-update-slow-boot.html), including the following lines:
```
auto lo
iface lo inet loopback
```

I shouldn't have removed those lines.

Sweet! :KS

---

### Post by ezrollers on 2007-05-16
Have you tried using gksudo instead?

---

### Post by loathsome on 2007-05-16
Yes.

gedit loads up then, but instantly crashes, and I have to do a killall to quit it.

[http://img525.imageshack.us/img525/2820/snapph7.png](http://img525.imageshack.us/img525/2820/snapph7.png)

Thanks for your reply.

---

### Post by bapoumba on 2007-05-16
Any error message in the terminal ?

---

### Post by loathsome on 2007-05-16
Acutally not ...

---

### Post by loathsome on 2007-05-16
Bump.

What's weird, is that this worked perfectly yesterday, and I can't remember do have done anything special. Please help ...

---

### Post by aysiu on 2007-05-16
I think someone already asked you this, but what's the output of this command? ```
gksudo gedit
``` And have you tried this? ```
sudo chown -R loathsome:loathsome /home/loathsome
``` More details here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by loathsome on 2007-05-16
Hi,

The output is what you can see in the link above; nothing. Just a blank gedit window. Just tried to take ownership (chown) of my /home/loathsome, but that didn't help either.

Thanks for your help!

---

### Post by loathsome on 2007-05-16
Ah, wait! I forgot the -d parameter (DEBUG). Here's the output;

```
loathsome@penguinbox:~$ gksudo -d gedit
No ask_pass set, using default!
xauth: /tmp/libgksu-7Kst6z/.Xauthority
STARTUP_ID: gksudo/gedit/1307-0-penguinbox_TIME31184630
cmd[0]: /usr/bin/sudo
cmd[1]: -H
cmd[2]: -S
cmd[3]: -p
cmd[4]: GNOME_SUDO_PASS
cmd[5]: -u
cmd[6]: root
cmd[7]: --
cmd[8]: gedit
buffer: --
buffer: -(gedit:1308): GnomeUI-WARNING **: While connecting to session manager:-
buffer: -Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.-
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
brute force GNOME_SUDO_PASS ended...
No password prompt found; we'll assume we don't need a password.

```

**PS:** What's the difference between sudo and gksudo?

---

### Post by loathsome on 2007-05-16
**UPDATE**:

I just noticed that if I put myself in the "root" group, it works flawlessly. The errors still appear, though. Should I just stay in the root group, or is this not preferred? 

Many thanks.

---

### Post by supertux on 2007-05-16
no dont put yourself in the root group, that can be dangerous as then you have root privileges. Does gedit work with gksudo ?

---

### Post by loathsome on 2007-05-16
No, as I've stated multiple time before.

Argh. This also happens with "user-setting". I'm starting to consider a fresh reinstall (LIKE I DID YESTERDAY!!), and if things won't work then, it's back to good "ol'" Vista.

---

### Post by loathsome on 2007-05-17
Bump.

This is driving me nuts!!

---

### Post by bapoumba on 2007-05-18
> **loathsome said:**
> Ah, wait! I forgot the -d parameter (DEBUG). Here's the output;

```
loathsome@penguinbox:~$ gksudo -d gedit
No ask_pass set, using default!
xauth: /tmp/libgksu-7Kst6z/.Xauthority
STARTUP_ID: gksudo/gedit/1307-0-penguinbox_TIME31184630
cmd[0]: /usr/bin/sudo
cmd[1]: -H
cmd[2]: -S
cmd[3]: -p
cmd[4]: GNOME_SUDO_PASS
cmd[5]: -u
cmd[6]: root
cmd[7]: --
cmd[8]: gedit
buffer: --
buffer: -(gedit:1308): GnomeUI-WARNING **: While connecting to session manager:-
buffer: -Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.-

<snip>

brute force GNOME_SUDO_PASS ended...
No password prompt found; we'll assume we don't need a password.

```

**PS:** What's the difference between sudo and gksudo?

sudo is to get admin privilege in a CLI and gksudo in GUI.

```
:~$  gksudo -S -d gedit
No ask_pass set, using default!
xauth: /tmp/libgksu-DsDvhx/.Xauthority
STARTUP_ID: gksudo/gedit/6223-0-scorpio_TIME8854389
cmd[0]: /usr/bin/sudo
cmd[1]: -H
cmd[2]: -S
cmd[3]: -p
cmd[4]: GNOME_SUDO_PASS
cmd[5]: -u
cmd[6]: root
cmd[7]: --
cmd[8]: gedit
buffer: -GNOME_SUDO_PASSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS-
brute force GNOME_SUDO_PASS ended...
Yeah, we're in...

```
So your cookie was accepted, but not your password (logged into GNOME to test it, same output with xfce).

Which ubuntu version are you using ?
run gconf-editor, go to > Apps > gksu > is sudo mode ticked ?
Are you on English locales ?
Do you use proprietary video drivers ?

/me relogin into xfce ;)

---

### Post by loathsome on 2007-05-18
Yes, sudo mode was ticked, yes I'm on English locales and .. ur, I don't know about the drivers. I've got an Intel GMA950 GPU, and just installed the newest Feisty release - didn't have to install a single driver myself.

Yes, XFCE is great, but right now I prefer GNOME ;) Thanks for your reply!

---

### Post by loathsome on 2007-05-18
What's wrong with setting myself as a root user, btw? And WHY does it work when I do that?

I'm going to bash my head several times against something now. ](*,)

---

### Post by bapoumba on 2007-05-18
Hello :)
I've googled quite a bit about your errors. Nothing so far. Looks like your pwd entered in the GUI box does not get accepted. That's what I am looking at. But I do not know much about all that. 
Anyone ?

---

### Post by loathsome on 2007-05-18
Hi there.

I reinstalled Ubuntu (fresh) yesterday, and sudo gedit worked fine - until this morning. I've now (Again; Yes) reinstalled Ubuntu, and sudo gedit works fine **atm**. This is weird.

Here's the output from gksudo -d
```
loathsome@penguin:~$ gksudo -d gedit 
No ask_pass set, using default!
xauth: /tmp/libgksu-2i66Ac/.Xauthority
STARTUP_ID: gksudo/gedit/7304-0-penguin_TIME598671
cmd[0]: /usr/bin/sudo
cmd[1]: -H
cmd[2]: -S
cmd[3]: -p
cmd[4]: GNOME_SUDO_PASS
cmd[5]: -u
cmd[6]: root
cmd[7]: --
cmd[8]: gedit
buffer: --
buffer: -(gedit:7305): GnomeUI-WARNING **: While connecting to session manager:-
buffer: -Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.-
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: -- single driver myself.

Yes, XFCE is great, but right now I prefer GNOME Thanks for your reply!
6 Hours Ago 06:30 AM
bapoumba 	
Quote:
Originally Posted by loathsome View Post
Ah, wait! I forgot the -d parameter (DEBUG). Here's the output;

Code:

loathsome@penguinbox:~$ gksudo -d gedit
No ask_pass set, using default!
xauth: /tmp/libgksu-7Kst6z/.Xauthority
STARTUP_ID: gksudo/gedit/1307-0-penguinbox_TIME31184630
cmd[0]: /usr/bin/sudo
cmd[1]: -H
cmd[2]: -S
cmd[3]: -p
cmd[4]: GNOME_SUDO_PASS
cmd[5]: -u
cmd[6]: root
cmd[7]: --
cmd[8]: gedit
buffer: --
buffer: -(gedit:1308): GnomeUI-WARNING **: While connecting to session manager:-
buffer: -Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.-

<snip>

brute force GNOME_SUDO_PASS ended...
No password prompt found; we'll assume we don't need a password.

PS: What's the difference between sudo and gksudo?
sudo is to get admin privilege in a CLI and gksudo in GUI.

Code:

:~$  gksudo -S -d gedit
No ask_pass set, using default!
xauth: /tmp/libgksu-DsDvhx/.Xauthority
STARTUP_ID: gksudo/gedit/6223-0-scorpio_TIME8854389
cmd[0]: /usr/bin/sudo
cmd[1]: -H
cmd[2]: -S
cmd[3]: -p
cmd[4]: GNOME_SUDO_PASS
cmd[5]: -u
buffer: --
brute force GNOME_SUDO_PASS ended...
No password prompt found; we'll assume we don't need a password.

```

Looks like the error is still there, tought; gedit opens up perfectly. The same with "users-admin", which seems to stop working the exactly when gedit does.

---

### Post by loathsome on 2007-05-18
I believe this has something to do with GNOME itself, actually. Because when both users-admin + gedit stops working, I can not restart X (or whatever it is) by pressing CTRL + ALT + backspace. It does restart, but it freezes. In my fresh install this works fine now.

I think there's something I'm doing later on that causes this; Either some drivers, codecs or something. I will continue to investigate.

---

### Post by loathsome on 2007-05-18
And theeere we go. Just restarted my laptop, without installing a single program etc - and we're back to the good ol' freezing gedit + users-admin.

CRAP!

**Edit;** sudo gedit DOES work, but it takes like .. five minutes to load.

---

### Post by bapoumba on 2007-05-18
Hmmm... Did you run:
```
sudo dpkg-reconfigure xserver-xorg
```
to set up your video drivers ?

You can give it a try. Keep the default answers when you do not know. Select with <space>.
resart X with CTRL-ALT-Backspace.
It should be able to detect your video card and the proper drivers (I have an old savage, not detected upon install, and now its okay).

Sorry, I cannot give you a definite fix, just guesses...

---

### Post by loathsome on 2007-05-18
Hi,

Thanks for all your help. I have a massive "find" here. It seems like this happens only when I'm wireless connected to a network. My wifi card's name is "Intel PRO/Wireless 3945", and it shows up under "restricted drivers".

Here's a test I just did: (#-comments are of course edited in)

```

loathsome@penguin:~$ gksudo gedit
loathsome@penguin:~$ gksudo gedit
# gedit loads fine
#joining wireless now ..
loathsome@penguin:~$ gksudo gedit
# gedit crashes
loathsome@penguin:~$ sudo killall gedit
loathsome@penguin:~$ echo DAMN

```

So there it is. What can I do about this? I mean, It's a bit of bother to disable my internet everytime I'm going to edit a file / restart X-server etc.

Thanks a lot!

---

### Post by loathsome on 2007-05-18
Would a driver reinstallation help?

---

### Post by loathsome on 2007-05-18
edit; *posted in wrong thread*

---

### Post by loathsome on 2007-05-18
**THIS PROBLEM IS NOW SOLVED**

Thanks for your help everybody! The problem occurred when I manually blanked out /etc/network/interfaces to workaround [_Feisty's boot bug_](http://ubuntulinuxtipstricks.blogspot.com/2007/04/yesterdays-update-slow-boot.html), including the following lines:
```
auto lo
iface lo inet loopback
```

I shouldn't have removed those lines.

Sweet! :KS

---

### Post by dannyboy79 on 2007-05-24
I have the exact same problem. are you saying that your gedit would freeze and then your entire X would freeze shortly there after? I have been going in circles trying to resolve this, I thought it was the nvidia drivers, BUT it's happening with vesa. I even tried a solution of editing the powernowd function so to stop cpu freq scaling and just make it so that cpu is 100% all the time btu that still hasn;t fixed it. This is sickening, Fiesty to worthless to me!!!! So you're sure you didn't change anything else?????? Because this wouldn't make sence, you stated that a fresh install the problem occurs and a fresh install would have the loopback in the interfaces file so what else did you do to resolve this?????? PLEASE help, I am ready to cry. 
:-)

---

### Post by loathsome on 2007-05-26
> **dannyboy79 said:**
> I have the exact same problem. are you saying that your gedit would freeze and then your entire X would freeze shortly there after? I have been going in circles trying to resolve this, I thought it was the nvidia drivers, BUT it's happening with vesa. I even tried a solution of editing the powernowd function so to stop cpu freq scaling and just make it so that cpu is 100% all the time btu that still hasn;t fixed it. This is sickening, Fiesty to worthless to me!!!! So you're sure you didn't change anything else?????? Because this wouldn't make sence, you stated that a fresh install the problem occurs and a fresh install would have the loopback in the interfaces file so what else did you do to resolve this?????? PLEASE help, I am ready to cry. 
:-)

Hi,

I'm 100% sure that it was the "loopback"-lines that caused this. Sorry if this doesn't work for you, but I'm unable to help you any further. When I did a fresh install I would automatically clean out the *interfaces file*, to resolve a known boot bug in Feisty. The bug is still solved when removing everything except the loopback stuff. Do you still have the problem with e.g. the LiveCD?

---

### Post by dannyboy79 on 2007-05-26
My problem was documented here: [http://ubuntuforums.org/showthread.php?t=454394](http://ubuntuforums.org/showthread.php?t=454394)

Well UPDATE FROM ME.

I am happy to inform everyone that a fresh install of Fiesty (no other hardware changes) has fixed the issue of the frozen commands when using gksu or gksudo which would eventually bring gnome-session and or X-server and or gnome-panel to it's knees. Meaning I could only exit to a tty or ssh into the box to restart it. So it obviously had something to do with something I installed along the way. Apps include pretty much everything in Automatix2, rkhunter, chkrootkit, tripwire, Exim4 and then sendmail, samba as a local master browser, and ssh. I can't think of much else I installed. Obviously the nvidia from the restricted modules manager, then the 100.xx.xx which both had this freeze. Then the freeze even occured in nv and vesa so who knows what the cause of it was I am just glad it's gone and I'll be sure to check it before and after every single I install!!!

There are 2 errors I am getting now that I am not applying any boot options like noapic or nolapic, they are:

[ 2.937741] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU1._PDC] (Node df85989c), AE_BAD_HEADER
[ 2.937854] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU2._PDC] (Node df8597fc), AE_BAD_HEADER

We'll see how it goes from here.

---

