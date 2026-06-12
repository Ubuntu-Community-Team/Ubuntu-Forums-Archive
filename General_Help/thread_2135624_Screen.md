---
title: "Screen"
date: 2013-04-14
forum: General Help
---

### Post by BrianBlaze on 2013-04-14
I am still a noob with screen but really love the way it works and how I cant move around my terminals while using ssh! My problem is that when I ssh into my server via the user I have allowed to ssh (using rsa keys) then I su into a different user that I use to actually execute scripts and such. When I am the second user I type...

```

minecraft@minecraft-VirtualBox ~/bukkitit $ screen -S Minecraft
Cannot open your terminal '/dev/pts/1' - please check.
minecraft@minecraft-VirtualBox ~/bukkitit $ ls -l /dev/pts/1
crw--w---- 1 blaze tty 136, 1 Apr 14 20:46 /dev/pts/1

```

I am guessing this means that because I ssh'd as blaze I can't start a screen as minecraft? That's as far as I understand so please someone open my mind to what is going on and why I can't start a screen like this...

thanks in advance

---

### Post by BrianBlaze on 2013-04-14
In 15 minutes figured out my own answer lol...


There are two simple ways of solving the issue without comprimising security.
 The first one is fairly simple. Set a (strong) password for the user  you would like to run screen as, and log in directly to that user. You  will now be able to start up a screen, as you now have the appropriate  permissions.
 The alternative is:
 
[LIST]
[*]Invoke the screen as root
[*]In the screen session: change (su) to the user you would like to run things under..
[*]Do stuff...
[*]Detach from the screen.
[/LIST]
 This works because the root/superuser will still be able to access any user's tty.

---

