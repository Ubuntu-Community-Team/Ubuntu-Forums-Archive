---
title: "What is &quot;usr/bin/scribe&quot;?"
date: 2008-02-01
forum: General Help
---

### Post by Endolith on 2008-02-01
I've got a process called "usr/bin/scribe" that is maxing out my processor.  I don't actually have a file with that name, and apt-file doesn't find anything.  Anyone know what it is?

---

### Post by gvartser on 2008-02-01
Scribe is a utility for controlling the grimoires in your codex, and the spells in your grimoires.

Info gotten from:
[http://dufflebunk.homeip.net/~dufflebunk/sorcerer/docs/sourcemage-docs/usr.sbin.scribe.src.html](http://dufflebunk.homeip.net/~dufflebunk/sorcerer/docs/sourcemage-docs/usr.sbin.scribe.src.html)



/g

---

### Post by Endolith on 2008-02-01
> **gvartser said:**
> Scribe is a utility for controlling the grimoires in your codex, and the spells in your grimoires.

Interesting.  It's not a program I can actually run, and it's not a file that actually exists.  "usr/bin/scribe" is the name of the process, like "firefox-bin" is the name of Firefox's process.

---

### Post by gvartser on 2008-02-04
Nah /usr/sbin/scribe is a script file.

You can view the file by typing:
```
sudo more  /usr/sbin/scribe
```

But what it is used for I do not know. The text I wrote in my previous post was a quote that i found using Google. Didn't tell me much, but I thought that it maby could help you out..

Best regz,
/g

---

### Post by Endolith on 2008-02-04
> **gvartser said:**
> Nah /usr/sbin/scribe is a script file.

It's not a file on my drive.

> You can view the file by typing:
```
sudo more  /usr/sbin/scribe
```

/usr/bin/scribe: No such file or directory
/usr/sbin/scribe: No such file or directory

---

### Post by gvartser on 2008-02-05
Ohh sry i wrote it wrong..

It should be 
```
more /usr/bin/scribe
```



/g

---

### Post by Endolith on 2008-02-05
> **gvartser said:**
> It should be 
```
more /usr/bin/scribe
```

I did that too. :)  Still not a file.

---

### Post by Zwack on 2008-02-05
Try the following incantation

```

sudo find / -name scribe -print -exec file {} \;

```

That should find it unless...

It could be that somebody has managed to get a rootkit on your server and that scribe is part of that rootkit.  Does it persist over a reboot?  Do some programs (top) show it while others (ps) don't?  does ls not show it, but echo /usr/bin/scr* lists it?  If so then you may well have a rootkit.  I would suggest running a live CD (any distro) and running chkrootkit from that distro.  

If you have one then the best bet is to take off and nuke the site from orbit...

Z.

---

### Post by Endolith on 2008-02-05
> **Zwack said:**
> Try the following incantation

```

sudo find / -name scribe -print -exec file {} \;

```

It would be nice if the command line provided some sort of feedback to indicate it's processing, since I can't hear the hard drive churning from this far away.  :)

---

### Post by Zwack on 2008-02-05
> **Endolith said:**
> It would be nice if the command line provided some sort of feedback to indicate it's processing, since I can't hear the hard drive churning from this far away.  :)

It is the Unix way... Don't tell me when it's working, only tell me when it's broken...

In this case find is searching your hard drive for a program called scribe.  If it finds it it will run file on it, and print the name.

It's possible as I've stated that you have a root kit, and if you do it might be trying to hide where it is (by replacing some binaries) so you can't see /usr/bin/scribe because those binaries have been written to ignore it.  The echo /usr/bin/scri* trick works because your shell interprets that and expands it.  So if ls doesn't see /usr/bin/scribe then echo probably will...

```

$ echo /usr/bin/scri*
/usr/bin/script /usr/bin/scriptreplay
$ 

```

Neither of my Ubuntu machines have /usr/bin/scribe on them, but I don't have everything installed so that doesn't mean that it doesn't exist.

Other options that might be worth trying are

strings /usr/bin/scribe | more

and just

file /usr/bin/scribe

I hope that this helps,

Z.

---

### Post by PeterJS on 2008-02-05
Do you have the scribes package installed? /usr/bin/scribe looks like it should be the Scribe Text editor for gnome. If you've got that installed, you might try uninstalling that, if it's not installed that lends credence to the it's a nasty no good root kit theory.

---

### Post by Endolith on 2008-02-05
> **Zwack said:**
> It is the Unix way... Don't tell me when it's working, only tell me when it's broken...

You mean "don't tell me if it's working *or* if it's broken.  Just leave me in the dark, plz".

> In this case find is searching your hard drive for a program called scribe.  If it finds it it will run file on it, and print the name.

I figured that out.  I know better than to copy and paste random commands.  :)

> It's possible as I've stated that you have a root kit, and if you do it might be trying to hide where it is (by replacing some binaries) so you can't see /usr/bin/scribe because those binaries have been written to ignore it.

Remember that this is the process's *name*, not necessarily a file name.  It could be something that reports its process name wrongly, for all I know.

By analogy:

[LIST]
[*]The command "/usr/bin/firefox" starts the process named "firefox-bin"
[*]The command "???" starts the process named "/usr/bin/scribe"
[/LIST]

Better would be if I see it running again, figure out what command started it or what files it's using?  I don't know how to do that.

---

### Post by Zwack on 2008-02-05
If the process is running you can try 

```

sudo lsof -p <process id>

```

to get a list of files that it has open.  If it's reporting itself as /usr/bin/scribe then presumably it is /usr/bin/scribe or it is malicious.  It's very unusual for a process to report itself as something other than what it is.

In the case of firefox the firefox start up shell script does some very unusual stuff (if it determines that it is being run remotely and a local copy of firefox is being run then it opens a new tab in the local copy instead for example...).  Thus firefox reports itself as firefox-bin because that is the actual binary that is actually running.

Z.

---

### Post by Zwack on 2008-02-05
> **Endolith said:**
> You mean "don't tell me if it's working *or* if it's broken.  Just leave me in the dark, plz".

Better would be if I see it running again, figure out what command started it or what files it's using?  I don't know how to do that.

If it's broken then it stops... If it's still running it's not broken and it is working.  If you're really curious you could use strace to list the system calls that it makes...

```

sudo strace -p <process_id>

``` 

But unless you're a programmer it might not be all that helpful (and even if you are)... but it will at least show you that it's working.

If it shows up in ps then the ppid should show you what process spawned it.  It could just have been a runaway process from something else...

Z.

---

### Post by Endolith on 2008-02-05
> **PeterJS said:**
> Do you have the scribes package installed?

I do.

>  /usr/bin/scribe looks like it should be the Scribe Text editor for gnome.

The file is /usr/bin/scribe**s**

---

### Post by gvartser on 2008-02-06
There is another quick find locator utility called locate.
Need to update the index first though..

```
sudo updatedb
```

And then search the file:
```
locate scribe
```

But I guess that you didn't get any results on your previous "find" query so this will probably also present you with nothing.

Just thought to share a nice utility, that very quick.

/g

---

### Post by Endolith on 2008-02-06
I was having network problems yesterday and couldn't re-check this. 

Just now I re-installed Scribes and ran it, and, lo and behold, /usr/bin/scribe appeared in *top*.  If I remember correctly, they changed the name of the project to *Scribes *a while ago so as not to conflict with another named *Scribe*.

---

