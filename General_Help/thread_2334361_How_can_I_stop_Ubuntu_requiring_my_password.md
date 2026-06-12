---
title: "How can I stop Ubuntu requiring my password?"
date: 2016-08-18
forum: General Help
---

### Post by james_beat on 2016-08-18
I've been using Ubuntu for many years, and I fully understand why it asks for a password before doing anything important.
I would never try to remove this feature under normal circumstances.

This case is different though - I am building a retro gaming console based on Retropie.
I'm using a pc and Ubuntu, because the Pi 3 doesn't have enough grunt to run an N64 emulator satisfactorily.

Whenever I tell retropie to shut down the console, it kicks me out to a terminal and I have to connect a keyboard and type in my password.
This is obviously far from ideal.

I followed this guide to install Retropie:
[https://github.com/retropie/retropie-setup/wiki/RetroPie-Ubuntu-16.04-LTS-x86-Flavor](https://github.com/retropie/retropie-setup/wiki/RetroPie-Ubuntu-16.04-LTS-x86-Flavor)

And it addresses this very issue:

*It is not possible to restart/shutdown if an sudo requests an password. To disable sudo password request add the line $user ALL=(ALL) NOPASSWD:ALL at the end of /etc/sudoers. Replace $userwith the name of your current user.*

I tried this, and it doesn't seem to have worked.
I also found another guide which suggested the same as above, but with $sudo instead of the username, but that didn't work either. I even tried it with both lines, but no luck.

Any ideas as to why this might no be working?

---

### Post by mastablasta on 2016-08-19
does it give any error?

can you show us the sudores file? and let us knwo the user name?
from Ask Ubutnu:
> 
[LIST=1]
[*]First, if your user has sudo privileges, you must enable its NOPASSWD option. Otherwise, sudo will ask for a password even when you don't have one, and won't accept an empty password.
To do so, open the sudoers configuration file with sudo visudo, and add the following line to the file, replacing david with your username:
```
david ALL=(ALL) NOPASSWD:ALL
```
Close the editor to apply the changes, and test the effect on sudo in a new terminal.
[*]Delete the password for your user by running this command, replacing david with your username:
```
sudo passwd david -d
[/LIST]

```

also see note if you use pkexec: [http://askubuntu.com/questions/281074/can-i-set-my-user-account-to-have-no-password](http://askubuntu.com/questions/281074/can-i-set-my-user-account-to-have-no-password)


also why do you need to "reconnect" after closing the console?

---

### Post by james_beat on 2016-08-19
I'm pretty sure I did exactly that (I tried a few things, but I'm pretty certain that was one of them).

I am at work right now, but I'll check when I get home.

What did you mean by why do I need to 'reconnect'?

Retropie has a shutdown menu, which should enable me to just select shut down and have the pc shut down.
Instead, when I select shut down, it closes retropie and brings me to the desktop with a terminal asking for my password. When I enter the password, the pc then shuts down as normal.

---

### Post by james_beat on 2016-08-19
I ended up just 'shotgunning' it - I set it to NOPASSWD for not just the one user, but for all the groups as well. Seems to have done the trick.

---

