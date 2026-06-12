---
title: "ubuntu 2 kde upgrade fail"
date: 2014-02-02
forum: General Help
---

### Post by keith14 on 2014-02-02
[COLOR=#000000]Hi,[/COLOR]
[COLOR=#000000]well I tried to get kde to check out okular, things were go ok until 98% complete and update aborted. Commands used:[/COLOR]
[COLOR=#000000]>sudo add-apt-repository ppa:kubuntu-ppa/backports[/COLOR]
[COLOR=#000000]>sudo apt-get update[/COLOR]
[COLOR=#000000]>sudo apt-get install kubuntu-desktop[/COLOR]
[COLOR=#000000]This took hours to fail can I pick-up from failure or just restart?[/COLOR]
[COLOR=#000000]Thanks,[/COLOR]
[COLOR=#000000]Keith


[/COLOR]

---

### Post by Bucky Ball on 2014-02-02
>sudo apt-get install kubuntu-desktop

That's all you needed. Restart. In fact, if you wanted to try Okular, it is availabe in the repositories without installing KDE, although it will drag in a few packages.

---

### Post by keith14 on 2014-02-02
Hi,
  Ok I just stepped off a cliff somehow. on re-boot machine returns to ubuntu. no surprise but there is no cursor. It's there just not visible. I'm writing this in the win8 boot. I went into safe boot and selected packages repair, did not notice anything getting altered nor did the cursor return. How do I get cursor visible again. I have very limited mobility in ubuntu.
thanks,
Keith

---

### Post by keith14 on 2014-02-02
I found this online:
[COLOR=#3F4549][FONT=Helvetica Neue]Open the Terminal[/FONT][/COLOR]
[COLOR=#3F4549][FONT=Helvetica Neue]cd /etc/modprobe.d/[/FONT][/COLOR]
[COLOR=#3F4549][FONT=Helvetica Neue]gksudo gedit options.conf[/FONT][/COLOR]
[COLOR=#3F4549][FONT=Helvetica Neue]In the text editor, type: options psmouse proto=imps[/FONT][/COLOR]
[COLOR=#3F4549][FONT=Helvetica Neue]Save the file and close it.[/FONT][/COLOR]
[COLOR=#3F4549][FONT=Helvetica Neue]sudo modprobe -r psmouse[/FONT][/COLOR]
[COLOR=#3F4549][FONT=Helvetica Neue]sudo modprobe psmouse

Does it seem correct? I can open xterm and type so I think I can try it.[/FONT][/COLOR]

---

### Post by Bucky Ball on 2014-02-02
Well, I would give it a try and see if works. I would advise doing this first, though:

sudo cp /etc/modprobe.d/options.conf /etc/modprobe.d/options.conf.backup

... then, if things go pear-shaped:

sudo mv /etc/modprobe.d/options.conf.backup /etc/modprobe.d/options.conf

Should always make a backup of important files before tweaking. ;)

---

### Post by keith14 on 2014-02-02
Hi,
found this online: gsettings set org.gnome.settings-daemon.plugins.cursor active false
it seemed a little safer than the one I posted last so I tried it. The syntax was not liked so I changed it to:
set org.gnome.settings-daemon.plugins.cursor active false
This did not work, even after reboot. I then set it to true and rebooted again but still the same the mouse is not visible.

---

### Post by keith14 on 2014-02-02
Hi,
 This is not an odd thing that happened. I see a lot of posts on line with similar problems but the fixes for them has has worked for me. 
There is no options.conf file under etc/modprobe.d
desktop settings are seemingly the same with the exception of no cursor and when I open an xterm it reverted to the dreaded purple back ground. I think it was white initially, I had changed it to green and black cursor some time ago.
I'm continuing to look on line for a resolve.
Please help if you can.
Thanks,
Keith

---

### Post by keith14 on 2014-02-03
Hi,
was able to reset mouse settings to default in uniy tweak but made no change.
I tries to load gnome latest but the load failed. re-re-running capturing log file.
sudo apt-get update && sudo apt-get install gnome-shell ubuntu-gnome-desktop >gn.log 4>>gn.log

---

### Post by keith14 on 2014-02-03
[COLOR=#000000]I think If I could get this to install I'd be able to get cursor back.

sudo apt-get update && sudo apt-get install gnome-shell ubuntu-gnome-desktop >gn.log 2>>gn.log[/COLOR]
below is the failure to complete gnome install:
Err [http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/](http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/) saucy/main gnome-themes-standard amd64 3.10.0-0ubuntu1~saucy1
  Connection failed
Failed to fetch [http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/pool/main/g/gnome-themes-standard/gnome-themes-standard_3.10.0-0ubuntu1~saucy1_amd64.deb](http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/pool/main/g/gnome-themes-standard/gnome-themes-standard_3.10.0-0ubuntu1~saucy1_amd64.deb)  Connection failed
Failed to fetch [http://ubuntu.mirrors.pair.com/archive/pool/universe/g/gnome-color-manager/gnome-color-manager_3.8.3-1_amd64.deb](http://ubuntu.mirrors.pair.com/archive/pool/universe/g/gnome-color-manager/gnome-color-manager_3.8.3-1_amd64.deb)  Connection failed
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by mastablasta on 2014-02-03
> **keith14 said:**
> [COLOR=#000000]I think If I could get this to install I'd be able to get cursor back.

sudo apt-get update && sudo apt-get install gnome-shell ubuntu-gnome-desktop >gn.log 2>>gn.log[/COLOR]
below is the failure to complete gnome install:
Err [http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/](http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/) saucy/main gnome-themes-standard amd64 3.10.0-0ubuntu1~saucy1
Connection failed
Failed to fetch [http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/pool/main/g/gnome-themes-standard/gnome-themes-standard_3.10.0-0ubuntu1~saucy1_amd64.deb](http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/pool/main/g/gnome-themes-standard/gnome-themes-standard_3.10.0-0ubuntu1~saucy1_amd64.deb) Connection failed
Failed to fetch [http://ubuntu.mirrors.pair.com/archive/pool/universe/g/gnome-color-manager/gnome-color-manager_3.8.3-1_amd64.deb](http://ubuntu.mirrors.pair.com/archive/pool/universe/g/gnome-color-manager/gnome-color-manager_3.8.3-1_amd64.deb) Connection failed
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

have you tried following terminal's suggestion?

sudo apt-get update 

or 

sudo apt-get update --fix

---

### Post by keith14 on 2014-02-03
yes tried the --fix-missing and it worked. I slide further down now. and need to log in to get no cursor.

yes, and it worked, now have to login to get no cursor. curios, I click install updates it finds them but does not install them. I ask it to.

I've more choices, if I log into gnome I get a cursor and wallpaper but that's it. not sure where I am now need to play around a little

I posted this now 3x I don't see them so I will try again.
Yes I did try the --fix-missing it worked. I have to login to get no cursor. I have choices where to go if I choose ubuntu there no cursor, gnome selection has cursor and wall paper that's it.

---

### Post by claracc on 2014-02-03
I think all your problems come from having installed kde-desktop ( failed installation as I understand from your post) from a repository ppa in backports without need to install okular (which is in the current ubuntu repositories). Please see: [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

I would recommend, first purge the ppa repository for kde taht you have added, then purge completely kde-desktop. For this two tasks, you can follow advise in this link:

[http://askubuntu.com/questions/343124/how-to-remove-kde-desktop-from-ubuntu](http://askubuntu.com/questions/343124/how-to-remove-kde-desktop-from-ubuntu)

After rebooting, see if you can enter normally in your original desktop (unity?), if no, try to reinstall it: see [http://askubuntu.com/questions/95458/how-do-i-reinstall-unity](http://askubuntu.com/questions/95458/how-do-i-reinstall-unity) for help.

Then you can simply install okular with command:(no extra repositories needed as far as I know)

```
sudo apt-get install okular
```

---

### Post by mastablasta on 2014-02-03
> **claracc said:**
> Then you can simply install okular with command:(no extra repositories needed as far as I know)
```
sudo apt-get install okular
```
KDE desktop packages might still get pulled in if this is okular a KDE app (which i think it is).
however, you are correct there is no need to use backports as kubuntu-desktop can be installed from software center. obviously install went wrong or was incomplete/corrupted.
furthemore it is also not necessary to install the whole desktop environment or distribution if you only want one applicaiton. onyl the necessary packages. which packages to install is all handled by package manager (software center / apt-get  ...)
purging might not be as easy as removing kubuntu-desktop package.
have a look: 
[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)
[http://www.psychocats.net/ubuntu/pureubuntu](http://www.psychocats.net/ubuntu/pureubuntu)

---

### Post by Bucky Ball on 2014-02-03
@claracc and mastablasta: I more or less said all that in post #2. ;)

It didn't, and doesn't, of course get us any closer to solving the current issue, though.

---

### Post by claracc on 2014-02-03
Yes, it is true, I have seen post number 2, and you have yet advised poster how to solve problem.

But as I see that poster is "bumping his head against a wall", i.e.: 

```
yes tried the --fix-missing and it worked. I slide further down now. and need to log in to get no cursor.

yes, and it worked, now have to login to get no cursor. curios, I click install updates it finds them but does not install them. I ask it to.

I've more choices, if I log into gnome I get a cursor and wallpaper but that's it. not sure where I am now need to play around a little

I posted this now 3x I don't see them so I will try again.
Yes I did try the --fix-missing it worked. I have to login to get no cursor. I have choices where to go if I choose ubuntu there no cursor, gnome selection has cursor and wall paper that's it
```

For this reason I tried to put the information a little more clear.

---

