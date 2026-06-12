---
title: "how do I execute two commands on one line??"
date: 2008-05-02
forum: General Help
---

### Post by itix on 2008-05-02
I'm kind if lazy, and I want my djmount to start automatically but I can't get it working properly. the two command lines are:

1) *modprobe -l -t /home/itix/Media fuse*
and
2) *djmount /home/itix/Media*

I tried 1) && 2), but that did not work. It is supposed to be fit into Xubuntus autostarted applications form...

Thanx in advance =)

---

### Post by Monicker on 2008-05-02
hrmm. Did you get any errors when you tried command1 && command2 ?


Also, modprobe requires root privileges. How was that specified?

---

### Post by howlingmadhowie on 2008-05-02
generally you can use

```
command1 & command2
```

or

```
command1 && command2
```

the difference is, that with two &s the second command is only executed if the first is successful.

---

### Post by itix on 2008-05-02
modprobe did not require root privileges on my xubuntu when I executed it from command line...
When I do 1) && 2) in terminal, everything is fine. The item from autostart though did not work very well unfortuantely.

---

### Post by bodhi.zazen on 2008-05-02
There are several options.

comand1; comand2

This executes commands sequentially : ```
comand1; comand2
```

AND = && ~ This executes command 2 only if command 1 is successful (no errors)
```
comand1 && comand2
```

OR = || ~ This executes command 2 only if command 1 fails (errors)
```
comand1 || comand2
```

In your case I would think you want &&

---

### Post by itix on 2008-05-02
> In your case I would think you want &&
Yeah, thanx, I tried that but it failed.
I think that I want to execute them sequentially actaully, and I do program C so I know what these commands mean, I just didn't think of using ";"
I'll try that now...

EDIT: Didn't work :(

---

### Post by itix on 2008-05-02
I was thinking... sice I copy-pasted the EXACT line from the terminal that worked in the terminal, what might be the difference??

---

### Post by bingoUV on 2008-05-02
What is your modprobe command supposed to do? I see that with these options , modprobe will just list some modules on the standard output. How does running it as autostarted command help you?

---

### Post by itix on 2008-05-02
modprobe loads some FUSE-thingish thing and mounts it to /home/itix/Media. djmount then mounts my upnp media server to that directory. It works perfectly in command line with separate lines and on single line, but not as autostarted. This is for my Eee PC from which I use the media from the media server which is on this computer.

---

### Post by jw5801 on 2008-05-02
> **itix said:**
> I was thinking... sice I copy-pasted the EXACT line from the terminal that worked in the terminal, what might be the difference??

Shouldn't be much difference at all I wouldn't think. Does "djmount" need a terminal to run in? Maybe try:

xterm -hold -e "modprobe -l -t /home/itix/Media; djmount /home/itix/Media"

You'll need to replace 'xterm -e' with your preferred terminal emulator and the switch it needs to take an argument to execute. Dunno if other terminal emulators have the 'hold' option, that basically makes it not kill the window once the process you tell it to run exits. That way you should be left with a terminal with some output, or nothing at all. Nothing at all obviously means nothing was run, otherwise there may be errors you can debug. If it runs fine with a terminal then you may need to background it when you call it (append an '&').

---

### Post by bingoUV on 2008-05-02
that is fine, but -l lists modules and -t restricts this listing to a specific directory. How is this printing of the list on the standard output going to help you in mounting your files?

---

### Post by itix on 2008-05-02
Sorry everybody who have helped me. I made a huge fatal typo in the original post
The first command line was "modprobe -l -t /home/itix/Media **fuse**"

I am TRULY sorry :oops:

Note: It still was the correct command line in the terminal and in the autostarted applications so my problem still exists.
jw5801, trying your fix now...

---

### Post by itix on 2008-05-02
Ok, jw5801:
I got an output from xterm (since xfce4-terminal didn't have the -hold option) reading: "*Charset: successfully initialized charset='UTF8'*" which is the correct output, but my /home/itix/Media folder is empty. There is no MediaTomb folder there as it is when I run the commands through the terminal as usual. Since the output is from djmount, at least djmount initialized correctly.

---

### Post by robertchahine on 2008-05-02
did you try the pipes

```
command 1 | command 2
```

---

### Post by unutbu on 2008-05-02
itix, perhaps save the following as 'media-mount'

```
#!/bin/bash
env > ~/media-mount.out
/sbin/modprobe -l -t /home/itix/Media fuse
/path/to/djmount /home/itix/Media
```

Make it executable:

```
chmod 755 media-mount
```

Then try autstarting media-mount. The 'env' command will put the environment variables in ~/media-mount.out. It might provide a clue why things are not working.

---

### Post by itix on 2008-05-02
This is the output from media-mount.out:
```
SSH_AGENT_PID=5128
SHELL=/bin/bash
USER=itix
GNOME_KEYRING_SOCKET=/tmp/keyring-eMwUfL/socket
SSH_AUTH_SOCK=/tmp/ssh-iEWmBz5098/agent.5098
SESSION_MANAGER=local/itix-eeepc:/tmp/.ICE-unix/5098
USERNAME=itix
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
DESKTOP_SESSION=default
GDM_XSERVER_LOCATION=local
PWD=/home/itix
LANG=en_US.UTF-8
GDMSESSION=default
SHLVL=1
HOME=/home/itix
LOGNAME=itix
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-R5GE1G51Um,guid=c54212b4728ff55624b83400481b57f0
XDG_DATA_DIRS=/usr/local/share/:/usr/share/:/usr/share/gdm/
WINDOWPATH=7
DISPLAY=:0.0
XAUTHORITY=/home/itix/.Xauthority
_=/usr/bin/env

```


Also, sorry for the delay. I was down at the grocery store... had to go before they closed.

---

### Post by unutbu on 2008-05-02
Let's just go with the hypothesis that for some reason you have root powers at the terminal, but don't have root powers under autostart. We can test this hypothesis by editing /etc/rc.local:
```

gksudo gedit /etc/rc.local
```

Insert the two lines:

```
/sbin/modprobe -l -t /home/itix/Media fuse
djmount /home/itix/Media
```

*ABOVE* the line "exit 0".

Reboot the machine. rc.local is run at boot time as root. If that works, then at least we can suspect  the problem has to do with root privileges.

---

### Post by itix on 2008-05-02
I have xubuntu (on the Eee) and mousepad won't open the file =(

---

### Post by unutbu on 2008-05-02
Did you try 

```
gksudo Mousepad /etc/rc.local
```

I don't know if Mousepad is capitalized or not...

---

### Post by itix on 2008-05-02
I suppose that the script was supposed to add my upnp server to media, but it didn't. I just wish I had some means of entering my media server fast, because the command lines won't stay in the shell memory forever :(

---

### Post by itix on 2008-05-09
If it might be of any help to anyone, my launcher that I created on the desktop didn't work either, even with the option "run in terminal" ticked. I tried the gksudo prefix as well but no results.
The gksudo box didn't even appear when I tried the launcher. I think this is somthing global. 

I've also tried running my commands in the xfce4-terminal (and autostart and launcher) as root, but all it gives me is the blue line [COLOR="Navy"]Charset: successfully initialized charset='UTF8'[/COLOR] which is what I allways get, but it doesn't mount my UPnP server to the local computer which is wierd. At least the two lines still work quite well in the terminal as itix user...
I bet it's some extremely trivial that I haven't thought about or forgot ](*,)

---

### Post by trickyD on 2008-05-12
I went down the /etc/fstab route. I added the following line to the end:

[FONT="Courier New"]djmount	/media/Media-Servers fuse ro,allow_other 0 0[/FONT]

Works a treat if I run "mount -av" from the command line; but it wasn't mounted at boot. I notice that /etc/init.d/mountall.sh contains the following line:

[FONT="Courier New"]mount -a -t noproc,nfs,nfs4,smbfs,cifs,ncp,ncpfs,coda,ocfs2,gfs[/FONT]

The obvious next step was to try: [FONT="Courier New"]mount -a -t fuse[/FONT] - again, this works at the command line, but doesn't work if I add fuse to the list of filesystem types to mount at boot in the line above.

So I guess the question is: can I mount filesystems that require fuse support at boot, if so, what's the right part of the boot sequence (hit me with the big hint stick here, guys) and hence the right file to fire off the mount command?

Is there something critical I'm forgetting here? :???:

Ta,

TD.

---

### Post by itix on 2008-05-12
I wonder if we should start a new thread about this since the title of this thread is quite misleading...
My problem still remain non the less :(

I tried your fix but it was the same results here...

---

### Post by trickyD on 2008-05-14
Yep; I agree - new thread is probably the way to go here!

TD

---

