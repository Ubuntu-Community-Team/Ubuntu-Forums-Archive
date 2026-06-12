---
title: "gedit"
date: 2006-08-05
forum: General Help
---

### Post by xander848 on 2006-08-05
whenever I type: "sudo gedit somefile" I never get anything...It does not even ask for password.

If i enter: "gedit somefile" it works so is this a problem with sudo?

---

### Post by Jagot on 2006-08-05
Are you doing this in Terminal or from the run prompt - alt+f2?

Try gksudo instead of sudo and see if the same thing happens.

---

### Post by xander848 on 2006-08-05
I'm doing this from a terminal. When using gksudo:

gksudo gedit /boot/grub/menu.lst
(gedit:7951): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

I tried this on 5 different files and sometimes it will ask for the password and sometime just give me that error.

---

### Post by taurus on 2006-08-05
What groups do you belong to anyway?  Type this from a prompt and make sure you are on both adm & admin...

```

id

```

---

### Post by xander848 on 2006-08-05
alex@alex-ubuntu:~$ id
uid=1000(alex) gid=1000(alex) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),106(lpadmin),110(scanner),112(admin),1000(alex)

yeah adm and admin are there

---

### Post by ciscosurfer on 2006-08-07
This is a bit off-topic, but I have a quesiton regarding Gedit as well. And I need to preface that this is a very, very nitpicky concern but annoying (at least to me) nonetheless. Also, I am aware of syntax Highlight Mode.

I am wondering if anyone can tell me how I can get my /etc/inittab (in this case, a normal text file) to look like this:

Image borrowed from Tom Adelstein, Linux Journal, "Linux in Government: Optimizing Desktop Performance, Part I" (hopefully he doesn't mind me using his image...)

[IMG]http://www.linuxjournal.com/articles/web/2005-05/8308/8308f2.png[/IMG]

---

### Post by h00s on 2006-08-07
> **ciscosurfer said:**
> I am wondering if anyone can tell me how I can get my /etc/inittab (in this case, a normal text file) to look like this:

This is not gedit, this is some editor run in terminal but I don't know what editor is it.

But, you can get similar highliting in gedit
in gedit, go to menu -> view -> highlight mode -> scripts -> sh

---

### Post by ciscosurfer on 2006-08-07
I forgot to mention that the pic was from a terminal editor (I don't know which one either).  And I've used the highlight mode before (in fact the script > sh mode.  But I want more spiffy colors.  I will do further research on the terminal editor.  Thanks anyway!

---

