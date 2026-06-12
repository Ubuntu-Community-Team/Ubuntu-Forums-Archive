---
title: "Session failed to start when logging into ubuntu 16.04"
date: 2018-07-31
forum: General Help
---

### Post by neo34rd on 2018-07-31
Hi all,

I have an unresolved issue described here in the askubuntu website
[https://askubuntu.com/questions/1061044/cant-start-session-at-login-screen](https://askubuntu.com/questions/1061044/cant-start-session-at-login-screen)

The problem is essentially I used a command to clean up and uninstall "broken or unused packages" and I ended up installing my ubuntu-desktop and ubuntu-session.
I tried reinstalling both but I end up with 
> `E: Unable to correct problems, you have held broken packages.`

I have tried the following string of commands:

> `sudo apt-get upgrade -f` (-f was the only way to get this command to execute)
`sudo apt-get update --fix-missing`
`sudo dpkg --configure -a`
`sudo apt-get install -f`

None of which helped to remove or fix the broken packages problem.

---

### Post by neo34rd on 2018-07-31
This has been fixed

   
[LIST]
[*]Ctrl+Alt+F1 on login screen
[*]install aptitude sudo apt-get install aptitude
[*]sudo aptitude install ubuntu-desktop
[*]follow instructions aptitude gives
[/LIST]
  Aptitude will downgrade/remove broken packages before proceeding with the install.

---

