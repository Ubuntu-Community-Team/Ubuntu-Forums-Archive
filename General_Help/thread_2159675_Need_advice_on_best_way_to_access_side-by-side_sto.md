---
title: "Need advice on best way to access side-by-side storage computer"
date: 2013-07-04
forum: General Help
---

### Post by vcrpcant on 2013-07-04
Hi,

I have two ubuntu machines
the first machine is my desktop
the second, is used to save a huge movie and mp3 collection

I mounted the second machine on the first one using "Places / Connect to Server / SSH"
up to here, everything is fine

the problem is that when I use Nautilus to copy big folders inside the SSH mount (for example, size more than 1GB) it takes a lot more time comparing when I copy that same folder inside in the disk in my desktop

I guess what happens is Nautilus in my desktop downloads the data from the second machine and then uploads it again to it, instead of copying directly inside the second machine, thus taking much more time :(
Can somebody confirm if this is what is happening?
if so, is there a different way of making it work?

Finally, and if you still got pacience, could you elaborate if this also happens when using NAS?
Would it be a good idea to turn that second computer to a NAS?
And if so, can you give some advice? :confused:

---

### Post by vcrpcant on 2013-07-04
This guy had the same problem:
[URL="http://ubuntuforums.org/showthread.php?t=1467297"]http://ubuntuforums.org/showthread.php?t=1467297
[/URL]
This one also:
[http://ubuntuforums.org/showthread.php?t=1514052](http://ubuntuforums.org/showthread.php?t=1514052)

---

### Post by HiImTye on 2013-07-04
a workaround could be to use rsync with this flag[quote=man rsync]-x, --one-file-system
don't cross filesystem boundaries[/quote]you could write up a nautilus script to copy/move your files with rsync
[http://linux.die.net/man/1/rsync](http://linux.die.net/man/1/rsync)
[https://help.ubuntu.com/community/NautilusScriptsHowto](https://help.ubuntu.com/community/NautilusScriptsHowto)[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by vcrpcant on 2013-07-04
> **HiImTye said:**
> a workaround could be to use rsync with this flagyou could write up a nautilus script to copy/move your files with rsync
[http://linux.die.net/man/1/rsync](http://linux.die.net/man/1/rsync)
[https://help.ubuntu.com/community/NautilusScriptsHowto](https://help.ubuntu.com/community/NautilusScriptsHowto)

Thanks for the tip :)

I'm a user of nautilus scripts, but I don't have much knowledge about rsync
I've only used rsync in the terminal, more or less like this:
$ rsync -r /folder1/file1 /folder2

Doing this with nautilus scripts while creating a new folder at the same time is going to be a challenge for me

I will try to find out how to get this working, but if somebody wants to contribute, please do :o

---

### Post by steeldriver on 2013-07-04
How about just opening a command line ssh session (rather than actually mounting the remote filesystem via sshfs), and then copying *locally* as though you were on on the remote computer?

Or if you are not comfortable using command line cp, you could do 

```
ssh -X user@machine2
```

(SSH with X forwarding) and then starting a remote file manager session which just *displays *on your local desktop

```
nautilus &
```

---

### Post by vcrpcant on 2013-07-05
> **steeldriver said:**
> How about just opening a command line ssh session (rather than actually mounting the remote filesystem via sshfs), and then copying *locally* as though you were on on the remote computer?

Or if you are not comfortable using command line cp, you could do 

```
ssh -X user@machine2
```

(SSH with X forwarding) and then starting a remote file manager session which just *displays *on your local desktop

```
nautilus &
```

That's a very good idea, I've tried it and it works! Thanks! :p

Also, i've tried opening other programs like Firefox and OpenOffice and they work just like being at the 2nd machine! It's great! :D

---

