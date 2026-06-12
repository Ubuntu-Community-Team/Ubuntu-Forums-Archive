---
title: "Manpages not displayed in terminal on Ubuntu 18.04"
date: 2019-11-25
forum: General Help
---

### Post by smith73 on 2019-11-25
Hi,
I have some weird problem with manpages.
When putting ```
man command > file.txt
``` into a terminal, the usage content of a command seem to be output to the .txt file correctly.
Also putting ```
man command | more
``` into a terminal outputs the command description correctly with page scrolling capability.

However manpages seem to be broken when putting just ```
man command
``` to display the man content in the terminal directly.
The output in the terminal is the following:

```
/usr/bin/pager: 1: [: missing ]
At least one file or directory argument required.
Use --help to show usage.
411toppm: Reading (64x48):  -

P6
64 48
255
&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;---%k6S&#65533;K)RP&#65533;H&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;XXXX&#65533;&#65533;&#65533;&#65533;??&#65533;=:}&#65533;:j&#65533;l&#65533;1111&#65533;&#65533;&#65533;&#65533;5&#65533;.;&#65533;43~+B&#65533;:k&#65533;-&#65533;1&#65533;4<&#65533;>&#65533;1&#65533;3&#65533;&#65533;,&#65533;+&#65533;K.&#65533;&#65533;.0&#65533;&#65533;05&#65533;&#65533;5h&#65533;&#65533;h&#65533;&#65533;&#65533;&#65533;}&#65533;0a&#65533;0&#65533;D&#65533;I^&#65533;I3&#65533;&&#65533;:&&#65533;&#65533;L&#65533;&#65533;&#65533;R&#65533;&#65533;
     &#65533;N&#65533;
        &#65533;$&#65533;ccc$u'&#65533;$+q &#65533;+
&#65533;Oy

```

Then there go ~3 pages of similar human-unreadable text. And then there is a "help" descriptive content of "7z" displayed 3 times
And then the following is output in the terminal:

```
Unable to init server: Could not connect: Connection refused

(a11y-profile-manager-indicator:14805): Gtk-WARNING **: 23:25:52.853: cannot open display: :0.0
Yes
USAGE: aa-exec [OPTIONS] <prog> <args>

Confine <prog> with the specified PROFILE.

OPTIONS:
  -p PROFILE, --profile=PROFILE        PROFILE to confine <prog> with
  -n NAMESPACE, --namespace=NAMESPACE    NAMESPACE to confine <prog> in
  -d, --debug                show messages with debugging information
  -i, --immediate            change profile immediately instead of at exec
  -v, --verbose                show messages with stats
  -h, --help                display this help

xcb_connection_has_error() returned true
aconnect - ALSA sequencer connection manager
Copyright (C) 1999-2000 Takashi Iwai
Usage:
 * Connection/disconnection between two ports
   aconnect [-options] sender receiver
     sender, receiver = client:port pair
     -d,--disconnect     disconnect
     -e,--exclusive      exclusive connection
     -r,--real #         convert real-time-stamp on queue
     -t,--tick #         convert tick-time-stamp on queue
 * List connected ports (no subscription action)
   aconnect -i|-o [-options]
     -i,--input          list input (readable) ports
     -o,--output         list output (writable) ports
     -l,--list           list current connections of each port
 * Remove all exported connections
     -x, --removeall
```

So that to end the initial command operation I need to press ctrl+C to return to a normal command line.

There's also some weird behaviour of "7z". When I type ```
7z
``` in the terminal, I get a the same "--help"-type description of
7z command which I get by typing ```
7z --help
``` in the terminal. However after typing ```
7z
``` or ```
7z --help
```
into the terminal right after the first instance of ```
7z
``` or ```
7z --help
``` has been run, the text entered in the terminal is deleted,
so it basically seems as if the 2nd instance of these commands would serve as a backspace key. 
In order to "reset" the terminal and display the content of 7z again, I need to type any Ubuntu command like ls.

I (probably) didn't install 7z, as I successfully use Engrampa Archive Manager to open or unzip archives zipped by (probably) 7z on Windows.
I have no idea what's happening there, can there be some clues provided on how to display manpages content in the terminal correctly?

---

### Post by smith73 on 2019-11-25
It also seems that I can't edit the post.

I tried the following solutions with no success:

 sudo apt-get install -f man-db
  sudo apt-get --reinstall man-db
  sudo apt-get install man-db
  sudo apt-get update /var/lib/man-db -fix-missing
 
 sudo apt-get install manpages-dev
sudo apt-get install manpages-posix-dev


(didn't use root)

---

### Post by Frogs Hair on 2019-11-25
What's the output of the following?

```
man man
```

---

### Post by Holger_Gehrke on 2019-11-26
'man' checks whether the output is a terminal. If it is, it calls 'pager' to display the page. /usr/bin/pager is a symbolic link under control of the Debian alternatives system and normally points at another symbolic link in /etc/alternatives which points at /bin/less. less will handle gzip compressed files correctly. If pager is not available for some reason, man uses cat instead which can't handle compressed files, which is why you get unreadable junk. You can fix this for the moment by setting the variable MANPAGER and exporting it ('export MANPAGER=/bin/less'). In the long run you really should look into what happened to the alternatives system. See the man page for 'update-alternatives' for details.

And 'Engrampa' and 'File-Roller' are just graphical frontends without any capabilities for compression or decompression. They just calls the various compressors and decompressors to do the actual work.

Holger

---

### Post by smith73 on 2019-11-26
The output of "man man" in the terminal is the same as mentioned, only the pattern of the human-unreadable text is a bit different.

---

### Post by smith73 on 2019-11-26
There's the "less" command also broken. For example, the output of ```
apt-cache search python | less
``` in the terminal is the following:

```
/usr/bin/less: line 1: [: missing `]'
At least one file or directory argument required.
Use --help to show usage.
411toppm: Reading (64x48):  -

P6
64 48
255
```

Then there goes human-unreadable text and 3 instances of "--help"-type usage description of 7z.

Also after messing with the terminal to enter my previous posts there (which basically shouldn't imply anything serious, but the stuff described above),
my Ubuntu HP notebook took ~5-10 times longer to shutdown (5-7 minutes probably), which seems rather unusual after dealing only with manpages in the terminal. 

I'll try to tinker the /etc/alternatives, but for now I'd like to be sure that there's nothing "serious" with the system, as I regard manpages and the related stuff 
as a documentation only which shouldn't affect the system and other user programs' executables.
I'm just curious what could ever cause such a thing with manpages, when I interact with the system minimally for now, just perform bleachbit, disc space cleaning
and apt-cache searches.

I ran clamscan and it showed no files infected, although there's a persistent problem of "freshclam" to update the virus databases, showing access denied to some
clamav log files.

I ran regular Ubuntu updates via terminal and Welcome Mate screen and didn't perform an upgrade or file system check on this Ubuntu notebook since installation.

---

### Post by CatKiller on 2019-11-26
> **smith73 said:**
> I'm just curious what could ever cause such a thing with manpages, when I interact with the system minimally for now, just perform **bleachbit**,
Bleachbit is notorious for deleting random stuff that you actually need.

---

### Post by #&amp;thj^% on 2019-11-26
Just jumping in to add 

Apt supports regular expression, so you can use:
```

apt search ^python$
```

which looks for a package started with a **p **followed by **ytho** and ended to the **n**, (in other words: looks exactly for python).

or even limit your search to the package names using:
```

apt search --names-only python
```

---

### Post by #&amp;thj^% on 2019-11-26
> **CatKiller said:**
> Bleachbit is notorious for deleting random stuff that you actually need.

+1 Yep use with caution, I use it daily though, with both good and bad experiences.

---

### Post by Holger_Gehrke on 2019-11-26
Try 'file /usr/bin/less'. That should give you '/usr/bin/less: symbolic link to /bin/less' on a Ubuntu system behaving normally, and 'file /bin/less' should give you something like '/bin/less: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/l, for GNU/Linux 3.2.0, BuildID[sha1]=b6833fcefca2a3092ff6ebb73690ee50002c0322, stripped'. From the error messages you get I suspect you'll get something else, probably some kind of shell script. Check whether /bin/less exists and is the right kind of file and try calling it with the path, for example '/bin/less /etc/passwd'. And take a look at the file '/usr/bin/less' with an editor. 

Holger

---

