---
title: "how do i unisntall something with make and compile ?"
date: 2007-04-19
forum: General Help
---

### Post by froyd on 2007-04-19
Hi, 
Im new in the forum please let me know if im posting in the wrong place. I've search the whole net before trying to post here so im gonna expose my problem.

I've tyring to install a nice looking dock, but, i had sucess with none of them, i tried pretty much everything, from avant to kiba dock ( kooldock, akamarudock , etc...)
Each one of the docks i tryed comes up with a different problem, but the one i really wanted to try was kiba-dock, but, adding the repos and installing through apt-get did not worked for me. I get segmentation fault core dumped. 
So i found this page:

[http://ubuntu1501.blogspot.com/2007/04/install-kiba-dock-oncedgy-eft.html]("http://ubuntu1501.blogspot.com/2007/04/install-kiba-dock-oncedgy-eft.html")

It was simple so i tryed and guess WHAT?!?! IT WORKED.....

but , when i started playing with the config, i found out that depending on teh config the dock would freeze and crash making it unusable.... now ... I WANT TO UNINSTALL it...

I know apt-get remove whatever, but i have no clue how can i uninstall this , since i did the whole, MAKE, compile all this stuff .... i went into gaim #ubuntu , peps told me to MAKE UNINSTALL but the make uninstall apparently worked fine but removed nothing.

So i need just two things ( if its not asking much )

Help uninstalling the kiba-dock that i currently have ...
And at least some guidance towards a good or a working dock ( kiba preferred )

Thx a lot at least for reading my post!

Regards,

Fred

---

### Post by zeekay on 2007-04-19
Did you ran make uninstall as root? With the "sudo" I mean.

---

### Post by autocrosser on 2007-04-19
First: see if it was installed in /usr/local or one of it's sub-directories
Next: look in your user folder for the **[COLOR=#000099]kiba-dock[/COLOR]** folder
 
You should also look in Sessions to see if it is set-up for auto-start.
 
Items in /usr/local need sudo permissions to remove. In a term: sudo nautilus
you will be prompted for your password
you cxan then nav just like normal, but remember: YOU CAN NOW DELETE ANYTHING!!!
 
So be carefull!!!

---

### Post by froyd on 2007-04-19
Thx all for the quick response !!

Here we go, yes i did the SUDO MAKE UNINSTALL

Heres the output

```

froyd@froyd-laptop:~/kiba-dock$ sudo make uninstall
Password:
Making uninstall in akamaru
make[1]: Entering directory `/home/froyd/kiba-dock/akamaru'
 rm -f '/usr/bin/akamaru'
make[1]: Leaving directory `/home/froyd/kiba-dock/akamaru'
Making uninstall in dock
make[1]: Entering directory `/home/froyd/kiba-dock/dock'
 rm -f '/usr/bin/kiba-dock'
make[1]: Leaving directory `/home/froyd/kiba-dock/dock'
Making uninstall in gset-kiba
make[1]: Entering directory `/home/froyd/kiba-dock/gset-kiba'
 rm -f '/usr/bin/gset-kiba'
 rm -f '/usr/share/kiba-dock/gset-kiba.glade'
make[1]: Leaving directory `/home/froyd/kiba-dock/gset-kiba'
Making uninstall in icons
make[1]: Entering directory `/home/froyd/kiba-dock/icons'
 rm -f '/usr/share/icons/hicolor/128x128/apps/kiba_128.png'
 rm -f '/usr/share/icons/hicolor/16x16/apps/kiba_16.png'
 rm -f '/usr/share/icons/hicolor/24x24/apps/kiba_24.png'
 rm -f '/usr/share/icons/hicolor/48x48/apps/kiba_48.png'
 rm -f '/usr/share/icons/hicolor/64x64/apps/kiba_64.png'
make[1]: Leaving directory `/home/froyd/kiba-dock/icons'
Making uninstall in utils
make[1]: Entering directory `/home/froyd/kiba-dock/utils'
 rm -f '/usr/bin/kiba-icon-editor.py'
 rm -f '/usr/bin/kiba-systray.py'
 rm -f '/usr/bin/populate-dock.sh'
 rm -f '/usr/share/kiba-dock/kiba-icons.glade'
make[1]: Leaving directory `/home/froyd/kiba-dock/utils'
Making uninstall in files
make[1]: Entering directory `/home/froyd/kiba-dock/files'
 rm -f '/usr/lib/python2.4/site-packages/SimpleGladeApp.py'
 rm -f '/etc/gconf/schemas/kiba.schemas'
make[1]: Leaving directory `/home/froyd/kiba-dock/files'
make[1]: Entering directory `/home/froyd/kiba-dock'
make[1]: Nothing to be done for `uninstall-am'.
make[1]: Leaving directory `/home/froyd/kiba-dock'


```

Now if i LS the directory everything still there , i dont know if i can remove it but my guess is Yes right ?

Second part!

I can go to /usr/local/bin and delete files there.
There is the gset-kiba and kiba-dock, o i guess im deleting them right ?

Ill wait some responses before i do anything.

No need to worrie about the sessions commands are not there :D

Thx for everything!

Any good guidance in a new dock, or where can i get to try the latest kiba-dock ?

---

### Post by Gannin on 2007-04-19
There's also a program called Checkinstall that should be in the repositories.  To use Checkinstall, you ./configure and make something like normal, then when it comes time to install it, you type "sudo checkinstall make install".  After answering a few basic questions, this will create and install a .deb package of the software you just compiled, so later on removing it would be just as easy as removing any other .deb package.

Even though you've already installed the software you've compiled, if you re-install it using Checkinstall, the files from the package will overwrite the files you installed manually, and then when you remove the package, it'll remove all the files that got installed.

---

### Post by froyd on 2007-04-19
Ok cool,

I Like the checkinstall but where will the .deb file reside and how do i uninstall it using this .deb!

Thxs!

---

### Post by Captainm on 2007-04-19
The .deb file will apear in the folder you did the checkinstall stuf. You can then just uninstall by typing ```
sudo apt-get remove packagename
```

---

### Post by froyd on 2007-04-19
Really cool stuff this checkinstall, from now on everything will be checkinstalled :D

So i did that, created the .deb file .... but, when removing here is what i get, and all the files still there, they didnt get removed :(

```

froyd@froyd-laptop:~$ sudo apt-get remove kiba
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libopenexr2c2a imlib11 libarts1c2a kdelibs4c2a mplayer-skins kdelibs-data
  libmp4v2-0 liblualib50 libavahi-qt3-1 xloadimage docker sox imlib-base
  liblua50 libimlib2 libjpeg-progs libakamaru0 kiba
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  kiba
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking, 713kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 161997 files and directories currently installed.)
Removing kiba ...
froyd@froyd-laptop:~$ 


```

---

### Post by froyd on 2007-04-19
and i can still run the program :(

Anyway is it ok if i just delete this directory and delete the /usr/local/bin files for it ?

EDIT: I JUST DID IT!

THX EVERYBODY FOR UR TIME!

---

### Post by Gannin on 2007-04-19
You're welcome :).  I'm glad it worked out for you.

---

### Post by ronacc on 2007-04-19
in the future if you need to uninstall something you have built . just go to the directory you did the build in and run ./make uninstall ( assuming ofcourse you didn't delete the build files)

---

### Post by Gannin on 2007-04-20
He tried that before and he said it didn't work for him.  The problem with that method is you have to keep around the build files all the time.  When you use Checkinstall, not only can you uninstall the program just like any other .deb, but you can also save the .deb that Checkinstall generated to either reinstall it later, or even install the program on a different computer.

---

