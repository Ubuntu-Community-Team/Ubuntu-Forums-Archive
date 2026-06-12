---
title: "Can't edit a schema .xml file even with sudo"
date: 2017-11-01
forum: General Help
---

### Post by donsevilla on 2017-11-01
Hi all

(I should point out I still consider myself just above the newbie stage.)

I am trying to manually edit schema .xml files to prevent Caja from automounting usb drives. (Ultimately, I'd like to be able to inspect an unknown usb drive while locked up in a sandbox or VM, but, first thing's first).

I can't for the life of me figure out why I can only open the files in read-only mode. I can't save a modified copy in the directory either. Its as if neither sudo (with and without -H) and gksu have any power, like Thor lost his hammer. 

1. What am I not understanding? Why can sudo not override a read only restriction like this?

2. How then can I access these files to edit them (files listed below).

Also, I have firejail enabled. I have run ```
sudo pluma /path/to/file
``` and ```
firejail --noprofile pluma /path/to/file
```. Still, files are read only. 

3. Is firejail an/the issue here?

Oh, also searching "media-handling" on Caja and choosing "open as administrator" does nothing. Like it never happened, nothing launches. 

Some (?irrelevant?) extra detail:[INDENT]a couple of weeks ago I tried to install VirtualBox 5.2.0 Oracle VM VirtualBox Extension Pack- totally failed and screwed up the existing usb settings of my guests.

I installed rkhunter and after getting the usual flags I tried to view the log - couldn't get in. 

Similarly, about a week ago I noticed my microphone was switched on, unusually - *probably* from me with a clumsy click on the panel, but I thought I'd check system log, and I couldn't. 
[/INDENT]

Its probably just my ignorance, but I can't help but feel that I'm locked out of part of my machine. Websearches aren't helpful. 

Can you help?

Many thanks - B.

Files:
/usr/share/glib-2.0/schemas/org.gnome.desktop.media-handling.gschema.xml
/usr/share/glib-2.0/schemas/org.mate.media-handling.gschema.xml

Ubuntu Mate 16.04 LTS recently updated.
MATE Desktop Environment 1.12.1

---

### Post by deadflowr on 2017-11-01
> Also, I have firejail enabled. 
System wide?
And with what sort of parameters?
>  Is firejail an/the issue here?
Maybe.
Is the file system properly mounting read/write or is it erroring and moving into the default error mounting of read-only?

But aside from that:
> /usr/share/glib-2.0/schemas/org.gnome.desktop.media-handling.gschema.xml
/usr/share/glib-2.0/schemas/org.mate.media-handling.gschema.xml
Never edit those files directly.
Instead create override files for the section you want to set.
Basically simply to create.
Make a file called something like 99_media-handling.gschema.override
And in the file place the dconf location like
[B][org.gnome.desktop.media-handling]
[/B]
then add the name and default value of which ever setting you wish to have overridden, like
[B]automount=false
[/B]
So the end result would look something like this
```
[org.gnome.desktop.media-handling]
automount=false
```

Now you should be able to add multiple entries for differing dconf directories, or simply create multiple override files for each different directory.
(org.gnome being one directory and org.mate would be another, if that makes sense.)

The trickier part for you is you need to save it in the /usr/share/glib-2.0/schemas directory.
Then it's a matter of compiling the schemas which is simply a one and done command:
```
sudo glib-compile-schemas /usr/share/glib-2.0/schemas
```

More here:
[https://developer.gnome.org/gio/stable/glib-compile-schemas.html]("https://developer.gnome.org/gio/stable/glib-compile-schemas.html")

---

### Post by donsevilla on 2017-11-01
**EDIT - tl;dr override files are created as per Deadflowr's instructions, complied, but still not working.**

Thanks Deadflowr

> Never edit those files directly.
Instead create override files for the section you want to set.

Oh.

Thanks for that. Still problems, unfortunately. 

The automount behaviour is operating fine - read/write, no errors - its just that I don't want it. I'd like to be able to plug something in and e.g. mount it within a firejailed Caja, or (if I can get the extensions pack to install properly) browse its contents in a Virtualbox VM.

I've had a crack at the override files, meanwhile. First - or penultimate - issue was to get them into the right directory.

```
me@computer:~$ sudo cat > /usr/share/glib-2.0/schemas/testfile.txt
bash: /usr/share/glib-2.0/schemas/testfile.txt: Permission denied
```

Firejail is applied as per [firecfg on their wordpress pages]("https://firejail.wordpress.com/features-3/man-firecfg/").  

I tried creating a file in .../schemas/ using the --noprofile and --private=/usr/.../schemas/ arguments on firejail, but permission was denied, same as using Pluma. So, its not firejail per se.

After changing to root directory* and working the options for firejail, I got *some* things to work. 

(* Meh - this was news to me. For those who come after this looking for their own solutions, please see my workings in the block below. I needed a work-around even then).

I now have two override files, (containing commands just as you indicated):

99_mate_media-handling.gschema.override
99_gnome_media-handling.gschema.override

both in /usr/share/glib-2.0/schemas

(I also tried previously a single file with both override commands, but it didn't work).

The compile command - run as root and as user - doesn't work. No error message, just a return to a new command prompt.

I have restarted the machine, and still no cessation of the automount behaviour. 

(Request to developers - this has *got* to be easier...).

Help, please. 

Gratefully

B.

[U]
Wrestling with write privileges and firejail:[/U]

For all those who will read this later searching for your own solutions, you need to use 

```
sudo -i
```

normal password, then watch for the prompt to display root@yourcompter. (Be careful here, I guess.)

I had to create and edit 99_media-handling.gschema.override on the root Desktop, using pluma via sudo, overriding firejail:

```
root@mycomputer:~/Desktop# firejail --noprofile pluma /usr/share/glib-2.0/schemas/99_media-handling.gschema.override
Parent pid 30327, child pid 30328
The new log directory is /proc/30328/root/var/log
Child process initialized in 22.87 ms
Warning: an existing sandbox was detected. /usr/bin/pluma will run without any additional sandboxing features
```

Edited as suggested above, so the file reads:
```

[org.gnome.desktop.media-handling]
automount=false

[org.mate.media-handling]
automount=false
```

Then I copied it from Desktop to /usr/share/glib-2.0 with the cp command. (I think firejail only works on desktop or GUI funtions, so these bash commands are unaffected).

File is definitely there, but compiling has no effect - automount still active. I've run that compile command in root *and* my usual login - no error message, just back to a command prompt.

So I removed that file, (use the rm command) and by similar processes split the two override commands into separate files:[INDENT]99_mate_media-handling.gschema.override
99_gnome_media-handling.gschema.override
[/INDENT]
 
Ran the compile command and... nothing.

So, this can get your files into the right place with firejail in full swing, but it can't be all right. Caveat emptor...

---

### Post by donsevilla on 2017-11-02
Update:

So I found a media-handling subcategory in dconf-editor (a GUI tool that launches with that command from terminal) that I'd missed before:

>org>gnome>desktop

That's different from >desktop>gnome.

>org>gnome>desktop offers ~6 checkbox options, the first one being 'automount'. It was unchecked. The information says it addresses org.gnome.desktop.media-handling. Further, it talks about the behaviour of the file manager Nautilus, not Caja, which is the only file manager I *see* operating on Ubuntu Mate. 

At this point, USBs still automount, however.

But you won't be surprised to find out that scrolling down revealed a >mate entry, so by making the same modification to the autoremove option in >mate>desktop>media-handling, hey presto - NO AUTOMOUNTING!

Thanks again to Deadflowr for the orientation and terminology. What I'd like to know is why the override-compile option seemed to work on the gnome but not the mate key. (Disclaimer - there's a chance I unchecked the gnome automount function with dconf-editor before, but by now everything is a muddle. In which case, the compile instruction consistently didn't work at all).

---

### Post by steeldriver on 2017-11-02
Just FYI

```

sudo cat > /usr/share/glib-2.0/schemas/testfile.txt

```

runs `cat` with elevated privileges, but executes the shell redirection `>` with the privileges of the ordinary user - that's the permission that is being denied here

---

### Post by donsevilla on 2017-11-02
Ah, great - thankyou!

---

