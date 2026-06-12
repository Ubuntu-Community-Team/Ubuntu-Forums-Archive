---
title: "Need some means of running script every startup and shutdown"
date: 2007-06-13
forum: General Help
---

### Post by toagu on 2007-06-13
Hi,
This is a generic Linux question I guess. I want to run  a specific set of commands (in this particular case load & unload truecrypt volumes) automatically every time the machine starts and shuts down. (This way, the encrypted volumes can be made available to anyone who logs into the machine) What are the files I need to create / modify for the same ?

Similarly, if I want to run something only at login & logoff of a specific user (e.g. my own personal encrypted data) what would be the equivalent files ?

TIA

---

### Post by arvevans on 2007-06-13
[INDENT]Hi,
[I]This is a generic Linux question I guess. I want to run a specific set of commands (in this particular case load & unload truecrypt volumes) automatically every time the machine starts and shuts down. (This way, the encrypted volumes can be made available to anyone who logs into the machine) What are the files I need to create / modify for the same ?

Similarly, if I want to run something only at login & logoff of a specific user (e.g. my own personal encrypted data) what would be the equivalent files ?

TIA[/I][/INDENT]

Running a script during boot or shutdown can be done by inserting the call to that script into the appropriate /etc/rc... file.  You will need to do a bit of personal research to understand which RC file runs when changing from one run level to another and where you can safely insert your scripts.   In the Ubuntu scheme of things you will find a set of directories in /etc that are named "rc#.d" where the "#" is a number between 0 and 6.

Running a script at user login is accomplished by including calls to that script program in the individual user's .profile file.

Arv
_._

---

### Post by toagu on 2007-06-13
Thanks Arv.  

Based on your tip, I dug out and read through the material here:
[http://www.debian-administration.org/articles/212](http://www.debian-administration.org/articles/212)
and have some idea now of how to go about it (for startup / shutdown). I will try it out and come back if I get stuck anywhere.

PS: Couldn't find anything yet for "logout" scenario (so that I can cleanly dismount the encrypted drive). Any suggestions there ?

---

### Post by HeadGeek on 2007-06-17
I'm looking for that too, and for the same reason. I've just managed to set up a TrueCrypt-encrypted home directory, automatically mounted when I log in (using the user password and a PAM module), but when I log out it stays mounted. I ran across a reference to a ~/.bash_logout script that's supposed to be run on logout, but I haven't had a chance to play with it yet.

The full description of how I got a TrueCrypt-encrypted home directory, if anyone's interested, can be found in three parts, [here]("http://geekblog.oakcircle.com/2007/06/16/encrypted-file-systems-part-1/"), [here]("http://geekblog.oakcircle.com/2007/06/16/encrypted-file-systems-part-2/"), and [here]("http://geekblog.oakcircle.com/2007/06/17/encrypted-file-systems-part-3/"). (The last one is the most important.) Don't worry, no advertising.

I'm quite proud of it. The information that allowed it wasn't easy to find, and I wanted to show other people how to do it too. :-)

---

### Post by ariel on 2007-06-19
My two cents: 

[http://polishlinux.org/howtos/truecrypt-howto/](http://polishlinux.org/howtos/truecrypt-howto/)

A quite recent tutorial on how to build a truecrypt-encrypted partition and have it mounted automatically ... but not using PAM :(

---

