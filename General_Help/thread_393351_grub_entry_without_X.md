---
title: "grub entry without X?"
date: 2007-03-25
forum: General Help
---

### Post by Mateo on 2007-03-25
Is it possible to make a grub entry that loads ubuntu, but doesn't load X?  sometime I think I might want to keep my computer on while I'm at work, but just the terminal to do some tasks (like recording a radio stream, or recording mythtv shows, cron jobs, etc).  if I know in advance that I don't need the GUI, it would be nice to load straight to terminal, since it should load faster and you wouldn't have to stop X manually.  is this possible or beyond the capabilities of grub?

---

### Post by undertherift on 2007-03-26
I believe that if you append a '3' to your kernel line, you will boot in run level 3. Run level 5 starts X11 (and the gui).

so your kernel line would say 
kernel blah blah root=/dev/hda blah blah **3**

And then everything else stays as it is.

Let me know if you need more help with it, we can customize it for multiple grub entries. 

Alternatively, you could setup ssh, so that you could log in from work w/out gui  (and then, who cares if the gui is started?)

---

### Post by Mateo on 2007-03-26
it didn't work.  this is the entry I made:

```
title		Ubuntu, kernel 2.6.20-13-386 (command line)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-13-386 root=UUID=ecdaa542-3247-4c3e-a636-1f3364a23575 ro quiet splash 3
initrd		/boot/initrd.img-2.6.20-13-386
```

loaded GUI.

---

### Post by undertherift on 2007-03-26
Ok, i found that out when i was working with another distro.  Just to test where EDIT how things work, can you open a terminal and put in
```
sudo /sbin/telinit 3
```

It should drop you out of X and into a terminal.  From there, sudo /sbin/telinit 5 should bring you back to X.

I'm basically making sure that ubuntu/linux is as its supposed to be, and we've just got a problem with our grub entry.

Let me know.

EDIT:  I just found this thread.  Look at the last post. Apparently, even in run-level 3 (which i thought meant no X), gdm starts up (that login screen).  So you have to tell it not to start at run-level 3. That SHOULD solve the problem, and allow you to keep your grub entry as is. 

[http://ubuntuforums.org/showthread.php?t=66420](http://ubuntuforums.org/showthread.php?t=66420)



Again EDIT:  Don't follow his steps exactly... cause then it will always boot to run level three, if you set it that way in /etc/inittab.  So i would say, remove the symbolic link  /etc/init.d/rc3.d/S13gdm, and that should be it. keep that grub entry as is.

---

### Post by Ramses de Norre on 2007-03-26
Ubuntu uses 2 as its default runlevel. All other runlevels are identically when not modified (except for 0, 1, 6 and S of course).
So what you can do: install sysv-rc-conf and use it to disable X (so gdm or kdm service) for a certain runlevel (3, 4 or 5, don't touch the others!) and make a grub entry identically to your normal entry (which boots to runlevel 2) and append the number of the runlevel you changed to it.

Sidenote: I'm not sure the number appending works, it did on dapper but on edgy I can't append '1' to go to single user mode, I must append single...
Try it out and ask again (or search google) if it doesn't work.

---

### Post by Mateo on 2007-03-26
Ramses de Norre:

would this disable X from being used at all?  I just want X to not startup.  I'd like to still be able to start it manually later, without restarting the computer.  If this is not possible then I might just not do anything.  but i'll try your suggestion anyways.

---

### Post by Ramses de Norre on 2007-03-26
Yes, you can still start it. sysv-rc-conf lets you configure which services are started automatically when starting up the computer.

You can execute **sudo /etc/init.d/gdm start** or the same with kdm to start them later.
Set all other stuff the same between runlevel 2 and the one you're editing to make them identical for all other stuff (which is the default).

---

### Post by Mateo on 2007-03-26
didn't work anyways.  maybe the number appending doesn't work any more.

---

### Post by Mateo on 2007-03-26
here's another thread where a user says number appending doesn't work:

[http://ubuntuforums.org/showthread.php?t=307277](http://ubuntuforums.org/showthread.php?t=307277)

---

### Post by Ramses de Norre on 2007-03-26
It seems to be a known bug with upstart, as described [here](https://launchpad.net/ubuntu/+source/upstart/+bug/85014).
You could try the workaround suggested there.

---

### Post by Mateo on 2007-03-26
workaround doesn't work for me.  i'll try and find something else.

---

### Post by Mateo on 2007-03-28
this is the rc.default file that is supposed to make this work:

```
start on stopped rcS

script
        runlevel --reboot || true

        if grep -q -w -- "-s\|single\|S" /proc/cmdline; then
            telinit S
        elif grep -qE -- "[[:space:]]+[0-9][[:space:]]+" /proc/cmdline; then
            RL="$(grep -Eo -- "[[:space:]]+[0-9][[:space:]]+" /proc/cmdline)"
            if [ -n "$RL" ]; then
                telinit $RL
            else
                telinit 2
            fi
        elif [ -r /etc/inittab ]; then
            RL="$(sed -n -e "/^id:[0-9]*:initdefault:/{s/^id://;s/:.*//;p}" /etc
/inittab || true)"
            if [ -n "$RL" ]; then
                telinit $RL
            else
                telinit 2
            fi
        else
            telinit 2
        fi
end script
```

anyone with feisty know what's wrong with that?

---

### Post by Mateo on 2007-03-28
ok, I think i have it on runlevel 3 now.  when I run the command 'runlevel' it says this:

```
matthew@matthew-desktop:~$ runlevel
3 2

```

which I think means that i'm on 3 now, and was on 2 previously.  so the script is fixed. However, it still loaded up X.   In the sysv-rc-conf program, I have gdm off for run level 3.  Is there another program to disable?

---

