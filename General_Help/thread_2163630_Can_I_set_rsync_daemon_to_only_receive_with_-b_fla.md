---
title: "Can I set rsync daemon to only receive with -b flag?"
date: 2013-07-19
forum: General Help
---

### Post by dumb_question on 2013-07-19
Research scientist here, not a sysadmin. I am setting up a server running the rsync daemon. Various user machines (that I do not control, other than to install a scheduled script) will periodically automatically connect to submit files for it to back up. They will mostly be Windows machines, using cygwin to run rsync only at times when they are expected to be idle, so I can't have the server try to pull the files, they have to be pushed from the user's machine. I would like to ensure that all operations take place with -b flag set (backup mode). This is because users generally don't modify these files and I can live with the inefficiency or set exceptions for those rare cases - we are mostly backing up new data in entirely new files. My assumption is that if a bunch of files are suddenly modified, it's either because someone has been infected with ransomware that has encrypted them, or some black hat (or a$$hat) is messing with the user's machine, and either way I don't want any overwriting going on.

I will set the -b flag on the scheduled cygwin-rsync operation, however this means that control of this behaviour resides on the Windows machine that I don't fully trust not to be hacked or virus ridden. Is there any way to set the rsync daemon on the server that is receiving the files to operate with the -b flag set no matter what the user machine tries to do? I.e. if my user's machine gets hacked by some script kiddie who decides to mess up all their files, and then remove the -b flag from my script so the backups are overwritten, I want my server to ignore that and operate in backup mode anyway.

We subsequently have "proper" offsite backup of the server with snaphsots and restore points etc, so please don't tell me to do that instead - it's happening, but again it's being done by other people on machines I don't control. I would like to harden *my* link in the chain as much as possible in case everyone else drops the ball, because I'm the one who needs that data to stay intact.

Is there any way to force this behaviour?

---

### Post by nerdtron on 2013-07-19
[FONT=book antiqua]Not yet tested but why not set an alias for the rsync command? This way,  when you run just plain rsync, it will default to "rsync -b". Ths
[/FONT]
[FONT=book antiqua]```
alias rsync='rsync -b'
```

To confirm the alias, you can try the rsync or the type alias in the terminal to list the currently in effect aliases
This change is temporary and changes are lost[/FONT] [FONT=book antiqua]when you reboot or close the terminal.
More reading on how to make it permanent. [/FONT]http://ubuntuforums.org/showthread.php?t=1653127

---

### Post by dumb_question on 2013-07-19
My concern with this approach is that the control still resides on the untrusted machine, rather than the trusted machine - it has been obfuscated, and realistically my users are not likely to be the subject of a targeted attacker who would drill down into things like that, but nevertheless it seems like there must be an option to set that control on the receiving machine, as that is the one that has to decide whether to implement -b or not. Anyone know if the rsync daemon could check what options the user had set and ignore requests that do not include the -b flag?

---

