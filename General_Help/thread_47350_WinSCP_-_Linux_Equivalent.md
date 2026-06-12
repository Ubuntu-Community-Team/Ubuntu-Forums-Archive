---
title: "WinSCP - Linux Equivalent?"
date: 2005-07-08
forum: General Help
---

### Post by Kudos on 2005-07-08
Hey, 
After recently switching to ubunutu, i haven't been able to find an app for linux that performs similar functions to WinSCP. I can only connect to my remotely hosted website using ssh2, and i need a client that is friendly and has support for compression.

/k

---

### Post by rmjokers on 2005-07-08
Have you tried nautilus or konqueror?  Both of these file managers support file transfers over ssh.  I am not sure about compression support though.

To connect using nautilus:

Places->Connect to Server
choose SSH and appropriate settings
A link will appear on your desktop

To connect using konqueror:

fish://user@host
or
sftp://user@host

You can easily bookmark the site for easy access in the future.

---

### Post by jasmuz on 2005-07-08
[QUOTE=Kudos]Hey, 
After recently switching to ubunutu, i haven't been able to find an app for linux that performs similar functions to WinSCP. I can only connect to my remotely hosted website using ssh2, and i need a client that is friendly and has support for compression.

/k[/QUOTE]
 Check here:

[http://linuxshop.ru/linuxbegin/win-lin-soft-en/table.shtml](http://linuxshop.ru/linuxbegin/win-lin-soft-en/table.shtml)

---

### Post by opi on 2005-07-08
[QUOTE=Kudos]WinSCP. [/QUOTE]

Nautilus.
Konqueror.
sftp.
yafc.

---

### Post by Kudos on 2005-07-09
[QUOTE=opi]Nautilus.
Konqueror.
sftp.
yafc.[/QUOTE]
 Sadly none of the gui clients mentioned have ssh support.
Essentially what i need is: ssh, compression and a gui. Thats it, linux has to have something

/k

---

### Post by desdinova on 2005-07-09
[QUOTE=Kudos]Sadly none of the gui clients mentioned have ssh support.
Essentially what i need is: ssh, compression and a gui. Thats it, linux has to have something

/k[/QUOTE]
#
Read up on using the Fish KIOSLAVE with konqueror - that does what you want.

---

### Post by SeeSchloss on 2005-07-09
Isn't WinSCP just an SCP clone ?

What's the problem with using scp ? Do you prefer a GUI application ?

---

### Post by Kudos on 2005-07-09
[QUOTE=SeeSchloss]Isn't WinSCP just an SCP clone ?

What's the problem with using scp ? Do you prefer a GUI application ?[/QUOTE]

I don't even know what SCP is tbh. I far prefer using a gui, it's what i'm used to.

/

---

### Post by crashtest on 2005-07-09
I don't think anyone mentioned gftp.  gftp *does* have ssh - I use it quite often.  Nice little graphical program, if you're looking for a winscp equivalent.

---

### Post by ecadre on 2005-07-09
[QUOTE=desdinova]#
Read up on using the Fish KIOSLAVE with konqueror - that does what you want.[/QUOTE]


I second that. Konqueror does all that ssh file stuff with fish://

Konqueror can also do sftp

Your username and password can be automatically (and securely) saved in kwallet.

I use it every day.

---

### Post by mariuss on 2005-07-09
Nautilus does support SFTP (even though it says SSH), and most SSH servers will also support SFTP.

Did you try Nautilus and it did not work for you?

---

### Post by SeeSchloss on 2005-07-10
[QUOTE=Kudos]I don't even know what SCP is tbh. I far prefer using a gui, it's what i'm used to.

/[/QUOTE]
 Ah, I don't know GUI tools for that (maybe "secpanel" ? though I didn't try it) but I guess there's enough suggestions from other people to find one you like.

scp goes with ssh and sftp, it works just like cp but between different machines :

```
scp local-file remote-user@remote-host:path/to/remote-file
scp remote-user@remote-host:path/to/remote-file local-file
```

---

### Post by isw on 2006-05-27
gftp works fine! Nice GUI (similar to WinSCP), supports SSH2.

apt-get install gftp

---

### Post by jis on 2006-10-29
> **crashtest said:**
> I don't think anyone mentioned gftp.  gftp *does* have ssh - I use it quite often.  Nice little graphical program, if you're looking for a winscp equivalent.

gFTP does not use SCP and SFTP protocols, but WinSCP does. Is there a better WinSCP equivalent?

---

### Post by mariuss on 2006-10-29
Just use Nautilus. It used to have problems when you were overwriting files, but it seems to work fine now.

Also, if you don't mind using the command line then have a look at sshfs, it mounts a ssh connection as a local folder.

---

### Post by jis on 2006-10-29
I don't have Nautilus installed; I am Thunar user since I use Xubuntu.

Great idea that sshfs. I ran sshfs, but I got this message:
"fuse: failed to exec fusermount: Permission denied"
There is not that message, if I run by sudo. But it is not very nice: I can not even cd to the local directory in command line after that. But if I run thunar by gksudo, I can use the directory. Not very safe way, I think. (I guess you have to use fusermount to unmount the local directory.)

P.S. Somebody said that SSH2 includes support for SFTP, and SSH1 includes support for SCP. However, I couldn't connect by gFTP with SSH2; it complained: "Error: An incorrect password was entered". Maybe the server requires SCP.

---

### Post by jis on 2006-10-31
Today, after reboot, I tried sshfs again, with super-user priviledges, but now I get message:
"fusermount: failed to open /dev/fuse: No such file or directory". Strange.

---

### Post by jis on 2006-10-31
> **jis said:**
> Today, after reboot, I tried sshfs again, with super-user priviledges, but now I get message:
"fusermount: failed to open /dev/fuse: No such file or directory". Strange.

Re-installing fuse-utils helped. (I had problems during shutdown before: I got message that said that "Umounting local filesystems failed". My partitions are mostly XFS.)

---

### Post by jis on 2006-10-31
I added my user name as a user in fuse group. Then I logged out and back in.

---

### Post by bsussman on 2006-10-31
> **Kudos said:**
> Sadly none of the gui clients mentioned have ssh support.
Essentially what i need is: ssh, compression and a gui. Thats it, linux has to have something

/k

excuuse me, nautilus and konqueror certainly do support ssh.

nautilus in obvious syntax (type ssh://someothersystem ) and konqueror using the cute but totally functional syntax that replaces 'ssh' with 'fish'

---

### Post by aconbere on 2006-10-31
As was mentioned before, WinSCP is a copy of the BSD/Linux SCP command (Secure Copy).  Scp works much the same way that cp does from the command line with some added ssh overhead.  The general look is something like

:# scp <source file> user@remote_machine:<destination>

the man pages for scp will illuminate further the nuances and power of this command.

:# man scp

~ Anders

---

### Post by kabronkline on 2006-11-17
Because of a Windows SSH implementation at my university, I simple used wine to install WinSCP3... works like a charm, but here is the catch:

By default the WinSCP3 launcher installed on the desktop will have in its properties a command which is:
```
wine 'C:\Program Files\WinSCP3\WinSCP3.exe'
```

Change it by prefixing it with "wine " like this:
```
sudo wine 'C:\Program Files\WinSCP3\WinSCP3.exe'
```


Run WinSPC, specify sudo password if needed... enjoy hours of SCP fun. ;)

---

### Post by TrinitronX on 2007-06-08
good thing WinSCP works under wine.  I couldn't seem to find a GUI scp client that had a synchronize function like WinSCP does.  Synchronize alone is totally worth having to use wine.

---

### Post by sparkster666 on 2007-06-08
I use winscp wine but it crashes alot I cant live without it though

---

### Post by mariuss on 2007-06-08
Just use the command line. rsync works great if you want to synchronize folders.

---

### Post by daschmidty on 2007-06-08
just for the record, gftp does support ssh. On the top of the screen with all of the login info pulldowns, pick the one that says ftp and you can change it to ssh2, at which point it is almost identical to winscp.

---

### Post by sparkster666 on 2007-06-13
The transfers are allot slower I dont know why

---

### Post by tagra123 on 2007-06-13
> **daschmidty said:**
> just for the record, gftp does support ssh. On the top of the screen with all of the login info pulldowns, pick the one that says ftp and you can change it to ssh2, at which point it is almost identical to winscp.


Awesome!

Thanks 

I mentioned gftp earlier in this thread. I'll give it a try. I never even looked for it there. Too spoiled by the cli I guess.

---

### Post by stenioramos on 2007-10-04
There's a gui solution for linux. It's called SecPanel! :)
Take a look at:
[http://themediahost.de/secpanel/](http://themediahost.de/secpanel/)

Have Fun!

---

### Post by Gfiles on 2008-01-09
Hi People,

I use filezilla that has a GUI interface and ssh support.

just search for filezilla in synaptics and install. it is quite easy to use.

---

### Post by Rob Loach on 2008-04-13
[WINE Information about WinSCP]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1285").

---

### Post by mwtoews on 2008-05-25
I've had good success with wine+winscp. I recomend downloading the standalone version (e.g., winscp413.exe), then make a shortcut to the comand "wine winscp413.exe" or something like that).

That said, I'd love to have an equivalent of WinSCP nativley for the linux-like world. Nothing out there is quite of the same quality/features (syncronizing, etc.). Now, if there were only something to convince Martin to port it over ... (or someone else).

---

### Post by altonbr on 2008-06-26
Has anyone tried secpanel? What type of GUI is that? 1995 era? (Edit: ahh, Tcl/Tk, the only other program I know that uses that is aMSN and they dropped that and picked up Emesene's Python/GTK gui)

It doesn't compare to WinSCP, sorry.

As for WinSCP over wine, I run the standalone version but it won't let me drag and drop. How do you transfer files with it?

Also, if your server only has ssh but not SFTP or SCP (or whatever weird combination there may be) you can use Konqueror/KDE and the fish:// protocol.
Suchas:
fish://user@host

---

### Post by akrus on 2008-07-07
You may use Krusader as well.

---

### Post by rickatnight11 on 2008-07-07
Just stumbled across this thread.  Ubuntu's Nautilus file explorer works just fine.  Places->Connect to Server and select SSH.  Works great with my iPhone.

---

