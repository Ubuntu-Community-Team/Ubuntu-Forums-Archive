---
title: "Xfce in Xubuntu: Desktop icons reset/rearrange (in VirtualBox at least)"
date: 2016-04-24
forum: General Help
---

### Post by SamInside on 2016-04-24
[SIZE=3]**tl;dr:** Xubuntu LTS 14.04.4, 64-bit, with "stock" Xfce4. I run in VirtualBox the same OS, and every time I boot the VM, its desktop icons reset/rearrange their positions. The host machine doesn't have this problem.[/SIZE]
_


I use *Xubuntu Desktop 14.04.4 (64-bit)* and it works fine on my host machine.
In my guest (*Xubuntu* again, same version) running in *VirtualBox* I have this problem where the desktop icons reset / rearrange their position every logoff / reboot.
The only difference between the two systems I can think of is that the virtual one has a different screen resolution.

Anyway, I have done some searching, and there are **a lot** of results from Google about this and similar problems. It looks like there is this bug (or these bugs?) around since 2012!
Some of the bug reports exist since 2013/2014 and have posts up to 2016 and the bug is still written as non-fixed:
[https://bugs.launchpad.net/ubuntu/+source/xfdesktop4/+bug/1335492](https://bugs.launchpad.net/ubuntu/+source/xfdesktop4/+bug/1335492)
[https://bugs.launchpad.net/ubuntu/+source/xfdesktop4/+bug/1190990](https://bugs.launchpad.net/ubuntu/+source/xfdesktop4/+bug/1190990)

Looks like it's one of those problems that sometimes happens and sometime doesn't, and that not all users seem to experience.

Still, this particular problem being such a stupid thing, I can't just wrap my head around this situation, which looks just way too weird to me.
There are various workarounds, which I don't even want to try, because come on...
Bottom line is: I don't want to spend an entire day browsing the internet for this stupid bug only to find no solution or to find that I just had to e.g. click one single thing to solve it; I'm therefore asking if there is someone out there that knows all the background story on this problem(s) and that can possibly shed some light on it, and helping me find a "true" solution, and not insane workarounds for such a stupid bug.

I just hope in some kind of amendment that all this is not really what it seems to be (an absurd bug existing since 2012) and that the problem is way more simple and easily solveable.

Thanks.

---

### Post by ajgreeny on 2016-04-24
The only answer I know of if you want desktop icons/launchers to remain static is to position them then, make the configuration file in your home which governs this immutable with ```
sudo chattr +i .config/xfce4/desktop/icons.screen*
```  I am not sure if you can do that to the .config/xfce4/desktop/ folder itself to stop any further icons.screen files being created but you might like to try that.

This has to be run with sudo as root in spite your ownership of those icons.screen* files; if you subsequently need or want to move (or remove) icons you will have to reverse that command with ```
sudo chattr -i .config/xfce4/desktop/icons.screen*
```
Following making the icons.screen* files immutable they should remain where they are, but even if an odd one should move, for example if you add another temporarily, you can bring them all back to the correct place with F5 whilst on the desktop.

It's a bit of a workaround, and not a real fix, I know, but it is all we seem to have at present.

---

### Post by SamInside on 2016-04-24
Believe it or not, it doesn't work.
Printing the content of the .rc file I can see that it kept the correct coordinates for the icons, and still after reboot the icons are messed up: it therefore completely ignored the file.
Weird.
Funny thing is that I don't have this problem outside of VirtualBox. Hrmmmm...

---

### Post by ajgreeny on 2016-04-24
I have an install of Xubuntu 16.04 in VBox but without any icons/launchers on the desktop.

I'll add some and see what happens on a reboot or logout and then report back soon, but not tonight.

---

### Post by SamInside on 2016-05-09
Bump, I really wouldn't know what to add.
In VirtualBox it doesn't work, outside VirtualBox it does. Tried changing themes and configs, tried the *chattr* trick. Tried using "F5".

---

### Post by David_Pratt on 2016-11-15
Hmmm. Same thing on my Manjaro Xfce VM.

---

### Post by &amp;KyT$0P# on 2016-11-15
I see the same problem, but on my host machine.  It's mitigated with the xfdesktop 4.12 but still not fully fixed.  I just gave up and wrote a script to deal with it -
```
#!/bin/ksh

# Small script to restore xfdesktop layout, which gets wiped
# when a new session is started.

cd ~/.config/xfce4/desktop
for i in `ls`;do
  cat ~/.xfce-desktop-layout > $i
done

cd

# xfdesktop --reload cause it to crash after period of time after.
# Workaround: Quit, then (in background) relaunch
# seems to be fixed in xfdesktop 4.12...
xfdesktop --reload

```

Get your desktop in a good layout, then find which config file in [FONT=Courier New]~/.config/xfce4/desktop[/FONT] has it.  Copy that one to [FONT=Courier New]~/.xfce-desktop-layout[/FONT].

Now, next time you see the issue, just run the script and your desktop will go back to normal.

For more information on what the script is doing, run [FONT=Courier New]man xfdesktop[/FONT]

---

