---
title: "Starting another X session from the  X session"
date: 2016-08-22
forum: General Help
---

### Post by kloszard on 2016-08-22
Hi, I know I can:

1. Switch to another tty e.g. tty1
2. Log in and type to run a game:

```
xinit /usr/bin/steam steam://rungamid/339800 -- :1 vt1
```

or Steam client:

```
xinit /usr/bin/steam -- :1 vt1
```

or WM/DE (Window Manager / Desktop Environment)

```
xinit /usr/bin/mate-session -- :1 vt1
```

in a separate  X session.


Yet, I don't know how to do it directly from a running X session. Has anyone know how to do it?

---

### Post by Bashing-om on 2016-08-22
kloszard; Hello;

Maybe this way :
Be aware I do not use lightdm as the (D)isplay (M)anger .

stat another instance of an Xsession on a different display:
```

ctl+alt+f2
startx -- :1
ctl+alt+f8

```

[INDENT]works for me in what I do.

[INDENT][INDENT]it is a thing
[/INDENT][/INDENT][/INDENT]

---

### Post by kloszard on 2016-08-23
Thanks for your quick response, but startx is a kind of a wrapper over xinit so your method is a lot like mine.

I would rather like to know if it is possible to run another session directly from my desktop environment to avoid switching to a tty and giving login credentials.

---

### Post by ventrical on 2016-08-23
Iv'e been trying and trying and trying ...but to no avail without qemu and thats not what we are looking for. LXC containers allows a reasonable facsimile of a desktop but that is still a VM.

Regards.

---

### Post by #&amp;thj^% on 2016-08-23
> **ventrical said:**
> Iv'e been trying and trying and trying ...but to no avail without qemu and thats not what we are looking for. LXC containers allows a reasonable facsimile of a desktop but that is still a VM.

Regards.

+1
Here is a little more information: [https://mostlylinux.wordpress.com/troubleshooting/ttysessions/](https://mostlylinux.wordpress.com/troubleshooting/ttysessions/)
And the father in me... warns to be very careful here...LOL No offense meant.
Not what you were looking for obviously, but useful none the less.

---

### Post by kloszard on 2016-08-23
@ [URL="https://ubuntuforums.org/member.php?u=1140838"][B][COLOR=#DD4814][B]ventrical
[/B][/COLOR][/B][/URL]
Huh, I know it could be done in previous releases because I found the threads below... and the solution was not related with these virtualization things you mentioned:
 
[https://ubuntuforums.org/showthread.php?t=51486](https://ubuntuforums.org/showthread.php?t=51486)
[https://ubuntuforums.org/showthread.php?t=2330506](https://ubuntuforums.org/showthread.php?t=2330506)

but /etc/X11/Xwrapper.config is no longer available so the how-to from 1st link is surely outdated. In the second thread a guy complies that his old scripts stopped working on ubuntu 16.04.

You know, I want a script or activator on my desktop that will run a game/steam/WM in another tty. Is it still possible in Ubuntu?

@ 1fallen - your link is kind of vaguely related with my question, but there's an interesting historical background in the Appendix section  :-)

---

### Post by ventrical on 2016-08-23
> **kloszard said:**
> @ [URL="https://ubuntuforums.org/member.php?u=1140838"][B][COLOR=#DD4814][B]ventrical
[/B][/COLOR][/B][/URL]
Huh, I know it could be done in previous releases because I found the threads below... and the solution was not related with these virtualization things you mentioned:
 
[https://ubuntuforums.org/showthread.php?t=51486](https://ubuntuforums.org/showthread.php?t=51486)
[https://ubuntuforums.org/showthread.php?t=2330506](https://ubuntuforums.org/showthread.php?t=2330506)

but /etc/X11/Xwrapper.config is no longer available so the how-to from 1st link is surely outdated. In the second thread a guy complies that his old scripts stopped working on ubuntu 16.04.

You know, I want a script or activator on my desktop that will run a game/steam/WM in another tty. Is it still possible in Ubuntu?

@ 1fallen - your link is kind of vaguely related with my question, but there's an interesting historical background in the Appendix section  :-)

Thank you for  bringing this to my attention.  On one of my main  upgraded systems I had been using;

```

startx

```

after creating the file .xinitrc in the /Home directory.

 I would use razorqt DE or xmonad DE and they worked flawlessly for what I needed them for.

 All I had to do was open Ctrl+Alt+F1 or F2 .. and I could have multiple desktop sessions working concurrently!!

```

startx -- :1

```


but that now is broken and not working. This is  a real discouragement. Lemme see what I can come up with.  I need to investigate why this busted during upgrade.

Take a look at this link...  [https://www.maketecheasier.com/run-multiple-x-sessions-without-virtualization](https://www.maketecheasier.com/run-multiple-x-sessions-without-virtualization)

Regards..

---

### Post by ventrical on 2016-08-23
[s]Had it working perfect in 15.10. Will not work in 16.04 virgin install (nor upgraded) nor will it work in trusty (upgraded). I think this is a maintainer problem and I don't have a cracker jack work-a-round atm but I'll keep trying.

Regards..

edit:

Look at this link:  [https://journalxtra.com/linux/desktop/multiple-desktops-on-one-linux-pc-now-thats-greedy/](https://journalxtra.com/linux/desktop/multiple-desktops-on-one-linux-pc-now-thats-greedy/)

and this does not work either.[/s]

I had entered the desktop name incorrectly. It is;

```

razor-session

```
to be edited in to .xinitrc  file in /home directory.

regards..

---

### Post by ventrical on 2016-08-23
Well.. I don't know how I did it  but I was just experimenting and I decided to make this .xinitrc file:

> 
exec firefox
exec razor-session
exec mate-session


 and I went to Ctrl+Alt+F1 , logged in and entered:

```

startx -- :1

```

and sure enough firefox came up as a stand alone program .. this done on an ubntu-desktop upgrade of xenial.

@grahammechanical .. if your reading this .. yep . .it can be done ! :)

I am using firefox in X atm. Will try some games.

Regards..

---

### Post by ventrical on 2016-08-23
Yep .. ran the little arcade game chromium bsu .. works awesomely.  I think you can execute  startx from desktop terminal but have to be root and you have to assign  a vt2. vt3 or etc.. I had some problems there .. but  can be worked around I'm sure.

 If you run firefox in lone terminal it is best to create a new_user name and use that session because if you are using you standard admin account it will open with all those configs with layered sessions and so has to be re-booted.

Regards..

---

### Post by kloszard on 2016-08-24
> **ventrical said:**
> Yep .. ran the little arcade game chromium bsu .. works awesomely.  I think you can execute  startx from desktop terminal but have to be root and you have to assign  a vt2. vt3 or etc.. I had some problems there .. but  can be worked around I'm sure.

 If you run firefox in lone terminal it is best to create a new_user name and use that session because if you are using you standard admin account it will open with all those configs with layered sessions and so has to be re-booted.

Regards..

Yeah, I know. If I created a dedicated account for gaming "gamer" I could even switch to another user with "Logout -> Switch to another user" and login to "gamer" using Display Manager. Then i could have my main acount under CTRL-ALT-F7 and  gamer account under CTRL-ALT-F8. However, I would have to set Steam account and Wine prefix (and perhaps other gaming software) for multiple users which is an additional effort and potentially a waste of disk space.
Running as root from terminal emulator also doesn't work. Apart from that, it is a bad idea cause all programs started from such an xsession would run with root privileges.

The solution would be using this how-to i posted before if it worked in the current ubuntu ([https://ubuntuforums.org/showthread.php?t=51486](https://ubuntuforums.org/showthread.php?t=51486)).
They assigned an authorization key - MIT-MAGIC-COOKIE-1 to user's account so that xserver let the user run a session without giving credentials and from the current desktop.
Normally, these magic-coockies are used to authorize connections to Xserver on remote desktops so that the user could run GUI applications remotely. The trick was to use it locally.

Perhaps some forum user who is familiar with these xauth program, authorizations and MIT-MAGIC-COOKIEs could fit this how-to to the current ubuntu release or, at least, say if it is possible at all.

---

### Post by kloszard on 2016-08-24
HI, previously I wrote:
> Running as root from terminal emulator also doesn't work.

Actually it does and I found the problem I encountered is a bug reported as [1562219]("https://bugs.launchpad.net/ubuntu/+source/xinit/+bug/1562219"). Starting X in another tty from another X should work without any configuration and with normal user privileges. Running it as in an original question is a sort of workaround. 

Thank you all for your help.

Should I mark the thread as solved? I have an answer but bug is not resolved. :-)

---

### Post by ventrical on 2016-08-24
I would leave the thread open for others or until the bug is resolved. There might yet be another workaround.

Regards..

---

