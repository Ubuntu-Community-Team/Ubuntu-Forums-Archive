---
title: "Trouble with sudo apt-get-upgrade"
date: 2015-10-29
forum: General Help
---

### Post by texsas on 2015-10-29
Hi

When I type sudo apt-get-upgrade I get a error message in the end:

```
dpkg: warning: parsing file '/var/lib/dpkg/available' near line 10382 package 'libudev1':
 `Depends' field, reference to `libdbts-1-3':
 implicit exact match on version number, suggest using `=' instead
dpkg: warning: parsing file '/var/lib/dpkg/available' near line 10382 package 'libudev1':
 `Depends' field, reference to `libdbts-1-3':
 version value starts with non-alphanumeric, suggest adding a space
dpkg: error: parsing file '/var/lib/dpkg/available' near line 10382 package 'libudev1':
 `Depends' field, reference to `libdbts-1-3': version contains ` '
E: Sub-process /usr/bin/dpkg returned an error code (2)


```
Line 10382 in '/var/lib/dpkg/available' :

```
Depends: libc6 (>= 2.17), libcgmanager0, libdbts-1-3 (?= 1.0.2(, libnih-dbus1 (>= 1.0.0), libnhh1 (>= 1.0.0)

```I`m not quite sure what to do?

---

### Post by Bashing-om on 2015-10-29
texsas; Hello ;

I do believe that the '?' is an invalid syntax in this invocation . The package manager says so, and if you look at other stanza's as reference, none others have a '?' in any field.
What I would do is backup the present file ( standard operating procedure !) :
```

sudo cp /var/lib/dpkg/available /var/lib/dpkg/available-old

```
And in my favorite text editor edit the file and remove the '?' . To edit this file requires admin privileges ( gksudo or pkexec ) .

Reboot to clear memory and reset ..
Now what results :
```

sudo apt update
sudo apt upgrade

```

Maybe that one instance is the only error.

[INDENT][INDENT][INDENT]maybe yes
[/INDENT][/INDENT][/INDENT]

---

### Post by QIII on 2015-10-29
*Moved to **General Help***

Forum Feedback & Help is for help with the software/behavior of the Forums.

Cheers.

---

### Post by texsas on 2015-10-29
Did this, and got a couple of more errors. Fixed them, and now it works :)

Thanks!!

QIII; sorry for that! I was thinking wrong on that one

---

### Post by Bashing-om on 2015-10-29
texsas; Great !

Pleased to be of some small help.
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]Oh Yes we can
[/INDENT][/INDENT]

---

