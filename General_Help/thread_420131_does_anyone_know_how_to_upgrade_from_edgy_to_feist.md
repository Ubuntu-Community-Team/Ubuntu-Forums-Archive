---
title: "does anyone know how to upgrade from edgy to feisty using cd"
date: 2007-04-23
forum: General Help
---

### Post by marshall.robert on 2007-04-23
hello, i put feisty on VMware and i like it, so i want it on my harddrive :D
the only catch is that i want to do an upgrade using the cd due to my wireless not working under Ubuntu. i put edgy onto a vmware machine, set it all up, made some folders and such in a user account, then when to put feisty on, and there was a form that said somethng to do with user accounts, but i never saw my one on edgy. is it possible to upgrade to feisty using the disk? if so can someone pleeease tell me how? :)

many thanks -rob

---

### Post by des4ij on 2007-04-23
gksu "sh /cdrom/cdromupgrade" 

source: [http://www.ubuntu.com/getubuntu/upgrading#head-0aee739ab0dfe9702a69ee3d316f5926d5d31807](http://www.ubuntu.com/getubuntu/upgrading#head-0aee739ab0dfe9702a69ee3d316f5926d5d31807)

---

### Post by marshall.robert on 2007-04-23
cheers, didnt think of looking on the actual ubuntu.com site

-rob

---

### Post by mojoman on 2007-04-23
Sure you can. This is how *I* would have done it. 

Get your CD with Feisty ready and open a terminal. 

In the terminal enter:
```

sudo EDITOR /etc/apt/sources.list
```

Substitute EDITOR with whatever editor you use (in Ubuntu, many use gedit, in Xubuntu, nano or mousepad, in Kubuntu, kate). Comment out all lines with # (unless they already have one). This will prevent the system from reading those lines because you won't be using them but it's still easy to restore, should you want to. Save and exit the editor. In case you didn't know, the file you just edited was the sources.list which tells your computer where to get software. Right now it can't get any, since it doesn't read any lines in that file. Let's change that. 

In the terminal, now enter:

```

sudo apt-cdrom add
```

It'll ask for your password. Enter it and follow the instructions (like "enter disc", "press enter" and so forth. it'll ask if you want to add more than one CD but since Feisty is on one CD you don't).

Now, you got the CD added as a repository and the CD is the only software source enabled.

Enter in the terminal:

```
sudo apt-get update
```

You should get a confirmation that it finds the CD (It'll probably ask for it)

Now, you should have access to the Feisty packages and there are two ways to go about this upgrade (*I think* - comforting to hear, isn't it? ;)  ).

Option one would be to continue with the terminal. I updated from Breezy to Dapper this way and it worked just fine but it was quite a while ago but I think I just had to enter:

```
sudo apt-get -u dist-upgrade
```
If I'm not mistaken, you have to do this twice and then re-boot and everything should be golden. If it's not, I'm not in anyway responsible. Let's face it, I hardly take responsibility for my own actions, let alone yours ;) 

The other way would be to go through the update manager, which I think is loacted in the menu (don't know for sure because I never ran Edgy, I went straight from Dapper to Feisty with a clean re-installation myself). You might be able to make changes in the sources.list there as well and add the CD too. I never use it so I couldn't really say. 

Here is an howto from the wiki as well.
[https://wiki.ubuntu.com/EdgyReleaseNotes#head-b07f8bdf28ae0444c03e1a61110c683c77e56cd0](https://wiki.ubuntu.com/EdgyReleaseNotes#head-b07f8bdf28ae0444c03e1a61110c683c77e56cd0)

Have a look around at the forum, especially in the installation and upgrade section. There might be other ways to go about this and it's always a good idea to see what problems others have encountered. Post back if anything is unclear and I'll see what I can do.

/mojoman

Edit: damn I write slow...

---

