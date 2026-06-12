---
title: "copying all localization settings from one server to another"
date: 2008-02-04
forum: General Help
---

### Post by sybariten on 2008-02-04
OK, so i'm[COLOR="Red"] localization hell[/COLOR]. Again. And i hate it.

I have just set up a new server, we can call it **Eve**, and i want to have a working character set.  I have googled a bit, but not really found anyone with a similar setup.

Here's the problem: as i said, i have a new server. I also have an old server, we can call it **Adam**.
By some divine intervention, i have managed to set up the older with working swedish characters in my applications.

Here's the signal chain:

Win XP --> Putty --> ISO8859 --> Ubuntu/Adam --> GNU Screen --> IRSSI/Emacs/CenterICQ

I get swedish chars in my applications under screen, i also get swedish chars if i run them outside of screen. *I get correct **curses **drawing inside and outside of screen.*
The only real problem is that i think apt, and other system related applications, tend to write messages in swedish. Which is lame. The OS is in other words a bit swedish.

Now, the new server, Eve, is very similar to Adam, its connected right next to it in the LAN and the only real difference is that the Ubuntu version is up to date.
Problem description for Eve:

- I can type swedish chars "öäåÖÄÅ" in a shell, but its obvious that the first character gets picked up to be 'weird', it gets delayed unlike for instance "jjj" or "FFF"
- when i'm in GNU Screen, swedish chars öäåÖÄÅ look like pure garbage. in the shell.
- when running centericq, i cant even see any swedish characters
- if i run centericq from inside GNU Screen, all the curses linedrawing gets messed up
- if i run emacs, both under screen or in a plain shell, swedish chars look like garbage, but in a new way

etc.

I know that there are as many solutions to this as there are Ubuntu installations. Everyone seems to solve this differently, if they even manage. I know that you can for instance enter the specific applications and start confing things there.
[SIZE="4"][COLOR="Blue"][B]
All i want to know is -- how can i duplicate the environment from my old box, to my new? What variables do i want to look into, are there any packages i need?[/B][/COLOR][/SIZE]

Since it works on my old server, it should theoretically be possible to have the same experience on the new one. Cause its the same putty doing the SSH.
I know people tend to reccommend UTF in various siutations, but as i said, i am using ISO8859 (at least in putty) in the old setup, and it seems to work just fine.

---

### Post by sybariten on 2008-02-04
aargh i think we should forget it.
i was persuaded into running putty in UTF8 mode after all....   i'm pretty damn sure i've had a lot of problems with that earlier, but that actually seemed to solve most problems with the new server. 
Both swedish characters, as well as ncurses line drawing, work allright, even under GNU Screen.

Heres something interesting though: i was reccommended to look at the output from the *locale *command

```
old server:
LANG=sv_SE
LANGUAGE=sv_SE
LC_CTYPE="sv_SE"
LC_NUMERIC="sv_SE"
LC_TIME="sv_SE"
LC_COLLATE="sv_SE"
LC_MONETARY="sv_SE"
LC_MESSAGES="sv_SE"
LC_PAPER="sv_SE"
LC_NAME="sv_SE"
LC_ADDRESS="sv_SE"
LC_TELEPHONE="sv_SE"
LC_MEASUREMENT="sv_SE"
LC_IDENTIFICATION="sv_SE"
LC_ALL=

new server:
LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=
```

notice how the old machine has a variable "LANGUAGE" that is not present in the new one?

---

