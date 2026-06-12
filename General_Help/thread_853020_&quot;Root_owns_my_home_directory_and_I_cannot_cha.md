---
title: "&quot;Root owns my home directory and I cannot change it&quot;"
date: 2008-07-08
forum: General Help
---

### Post by rustyz on 2008-07-08
"Root owns my home directory and I cannot change it" 

is what my problem has been!

it apears to happen with the new distros... ala Hardy, the new Fedora, and Mint...

i have tried chowns, super user mode, some terminal commands and more...
any tips or thoughts!

i started a thread and that will show what has been tried before, and the results

[http://ubuntuforums.org/showthread.php?t=836807](http://ubuntuforums.org/showthread.php?t=836807)

thanks

rz

---

### Post by rustyz on 2008-07-08
i have taken out my hard drive on the computer that have been useing as a spare for all of these trys as a fix to this...

put in it my everyday computer, installed hardly again...

Root still owns my home...

i installed Gutsy over it, and not a problem... me/user is home!

i have used guided use entire disk for all of these instalations...

what can be the problem?

and how do i take ownership of my home on Hardy?

---

### Post by forger on 2008-07-08
chowns? :D

try this (**chown**, not chowns)
```
sudo chown -R $USER:$USER $HOME
```


For example, if your username is "myuser", then this command will set your current user as the owner of /home/myuser/

If you're trying to change the owner of the whole /home/ directory, that's **not** something I would suggest

---

### Post by rustyz on 2008-07-08
ran in terminal, and this is the result!

> chown: cannot access `/home/patrick/.gvfs': Permission denied


next! lol

---

### Post by sayakb on 2008-07-08
Boot into recovery mode from GRUB and after you are at the # prompt, type:
```
startx
```
See if the system starts. Now change the permissions for your home folder.

---

### Post by forger on 2008-07-08
> **rustyz said:**
> ran in terminal, and this is the result!
next! lol

:lolflag:
If that is the only problem, then sorry to disappoint you but you're **all done**!
That address is reserved for gvfs-fuse-daemon (more info: **apt-cache show gvfs-fuse**)

Check out your home directory:
```
ls -lR $HOME | less
```

Scroll down with "Page up/down keys or Space or arrow keys.. it will show you that you are the owner and group owner of all the other files. Press "q" to exit the less program when you're done and convinced :)

---

### Post by rustyz on 2008-07-08
LII

> Boot into recovery mode from GRUB and after you are at the # prompt, type:

semi-newb here

and 

> Now change the permissions for your home folder

---

### Post by tagra123 on 2008-07-08
Try

sudo chown -f -R patrick.patrick /home/patrick


The -f should make it quiet and not show  the error

---

### Post by rustyz on 2008-07-08
forger, happy you had a laugh! :lolflag:

if you look at my link on post, it will give you the info on the whats of my problem...

all i want to do is transfer some Data CD disks...

pics/docs/music ect...

all the last distros let me, just not Hardly! :confused:

just installing the few updates now...

OMG!!!

will give that a shot tagra ASAP!

---

### Post by forger on 2008-07-08
hm.. I thought chown continued on errors :(

That command should be ```
sudo chown -fR patrick:patrick /home/patrick
```

I hope you're using the commands as they are, they're case sensitive!
I still haven't understood the problem though, that post is too big to read, sorry :)

---

### Post by forger on 2008-07-08
So you mounted your home and it tells you root owns it?
An alternative:
```
gksu nautilus /home
```

It will fire up nautilus as root, do whatever you like, hope it helps
edit: you can transfer your files as root or even try to right-click on your folder and go to properties > permissions > change owner/group

---

### Post by rustyz on 2008-07-08
typed as shown, both of you...

and stil get permissions denied...

tried to set permissions from GUI, (read/write) and reverts back to none set

also, the clean new Hardly install...

the example file is locked in my home file!

Gutsy and Feisty... was not...

ran the ls -lR $HOME | less

and it shows 

drwxr-xr-x 2 patrick patrick 4096 2008-07-08 16:11 Desktop
drwxr-xr-x 2 patrick patrick 4096 2008-07-08 16:11 Documents
lrwxrwxrwx 1 patrick patrick   26 2008-07-08 16:02 Examples -> /usr/share/example-content
drwxr-xr-x 2 patrick patrick 4096 2008-07-08 16:11 Music
drwxr-xr-x 2 patrick patrick 4096 2008-07-08 16:11 Pictures
drwxr-xr-x 2 patrick patrick 4096 2008-07-08 16:11 Public
drwxr-xr-x 2 patrick patrick 4096 2008-07-08 16:11 Templates
drwxr-xr-x 2 patrick patrick 4096 2008-07-08 16:11 Videos

---

### Post by forger on 2008-07-08
Wait a second, **which** files are troubling you (full path please)?

You want to remove or copy these files?

---

### Post by rustyz on 2008-07-08
ok, heres the drill...

put in data cd, drag to desktop, files locked...

also, right click on my/home on desktop, go to permissions, and...

the permissions for patrick cannot be determined

---

### Post by forger on 2008-07-09
Are you booting from live cd or is Ubuntu hardy heron installed on your pc??

Home link on desktop is just a link :) Go to Places > Computer > Filesystem > home > right-click patrick, there's your home

Anyway, ok, Right click on Desktop > Create folder > Name it: **data**
Drag your files into folder data. When all the files are copied, do this:

```

sudo chattr -RV -uia $HOME/Desktop/data/*
sudo chown -hRv $USER:$USER $HOME/Desktop/data/*

```

(and I was right, there's not need for -f in chown)

Post the output back

---

### Post by rustyz on 2008-07-09
patrick@patrick-desktop:~$ sudo chattr -RV -uia $HOME/Desktop/data/*
chattr 1.40.8 (13-Mar-2008)
chattr: No such file or directory while trying to stat /home/patrick/Desktop/data/*


did as sugested...

and this is a installed system...

the first file i drag'd to Data File went ok, then the next file, became locked again!

edit, i dont know how that smiley got there!

---

### Post by forger on 2008-07-09
"No such file or directory"

**When all the files are copied**, after that, do the commands I gave you.
And be sure you made a folder **data**, not Data or DATA on the **Desktop**!

---

### Post by rustyz on 2008-07-09
>  retained as patrick:patrick
patrick@patrick-desktop:~$ 

and the files are stil locked inside of the data folder... rrrr!

that data folder is on my desktop...

and rebooted also...

i thank you so much for the time your putting in forger

---

### Post by forger on 2008-07-09
It's *really* weird.. by the way, you're copying from a cd?

I need to see the output of these commands, post back with the output:
```
ls -lRa $HOME/Desktop/data
lsattr -d $HOME/Desktop/data
lsattr -Ra $HOME/Desktop/data
```

And paste **all** the output, or save it in a text file and attach it

---

### Post by rustyz on 2008-07-09
yep, copying from a CD...

patrick@patrick-desktop:~$ ls -lRa $HOME/Desktop/data 
/home/patrick/Desktop/data: 
total 16 
drwxr-xr-x 4 patrick patrick 4096 2008-07-09 10:13 . 
drwxr-xr-x 3 patrick patrick 4096 2008-07-09 10:35 .. 
dr-xr-xr-x 2 patrick patrick 4096 2008-04-24 14:43 Backgrounds 
dr-xr-xr-x 2 patrick patrick 4096 2008-04-24 14:43 Panels 

/home/patrick/Desktop/data/Backgrounds: 
total 4648 
dr-xr-xr-x 2 patrick patrick   4096 2008-04-24 14:43 . 
drwxr-xr-x 4 patrick patrick   4096 2008-07-09 10:13 .. 
-r--r--r-- 1 patrick patrick 299969 2008-04-20 17:24 1_Ubuntu-Wallpaper-1024x786-JDJW.jpg 
-r--r--r-- 1 patrick patrick 130073 2008-04-21 17:55 50070-background.png 
-r--r--r-- 1 patrick patrick 120348 2008-04-20 08:54 65256-1.jpg 
-r--r--r-- 1 patrick patrick 136977 2008-04-21 18:08 65415-blue_ubuntu.jpg 
-r--r--r-- 1 patrick patrick 165751 2008-04-21 18:09 66107-simple_ubuntu.png 
-r--r--r-- 1 patrick patrick  84933 2008-04-20 07:49 76683-black abscract without logo.png 
-r--r--r-- 1 patrick patrick 390914 2008-04-23 13:16 ABSTRACT-CrunchyBranch_1680x1050.png 
-r--r--r-- 1 patrick patrick 124094 2008-04-21 08:23 Dark Hardy.jpg 
-r--r--r-- 1 patrick patrick 223230 2008-04-20 13:18 Flower.jpg 
-r--r--r-- 1 patrick patrick 262391 2008-04-20 08:42 Hardy-Simple Human 1600x1200.png 
-r--r--r-- 1 patrick patrick 205936 2008-04-20 14:16 kate holmes.jpg 
-r--r--r-- 1 patrick patrick 296926 2008-04-20 16:22 LDE.png 
-r--r--r-- 1 patrick patrick 482112 2008-04-20 14:20 lightbuntu.png 
-r--r--r-- 1 patrick patrick  30039 2008-04-20 08:54 Natalia Vodianova 01.JPG 
-r--r--r-- 1 patrick patrick  48184 2008-04-20 08:54 NATURE-Leaf_1920x1200.jpg 
-r--r--r-- 1 patrick patrick  45354 2008-04-21 18:19 slick .png 
-r--r--r-- 1 patrick patrick 797669 2008-04-22 16:35 toronto_nighttime_1280.jpg 
-r--r--r-- 1 patrick patrick 167666 2008-04-23 13:09 trademark.jpg 
-r--r--r-- 1 patrick patrick 488459 2008-04-20 13:26 Ubuntu_Dapper_Drake_by_djust.png 
-r--r--r-- 1 patrick patrick  34034 2008-04-20 14:17 Ubuntu_PartLines_Wallpaper_by_buriednow.jpg 
-r--r--r-- 1 patrick patrick  56623 2007-09-23 09:14 ubuntu_reflect.png 
-r--r--r-- 1 patrick patrick  42035 2008-04-20 14:16 Ubuntu_wallpaper_by_lethal2.png 

/home/patrick/Desktop/data/Panels: 
total 52 
dr-xr-xr-x 2 patrick patrick 4096 2008-04-24 14:43 . 
drwxr-xr-x 4 patrick patrick 4096 2008-07-09 10:13 .. 
-rw-rw-r-- 1 patrick patrick  351 2008-04-24 03:37 65966-version2.jpg 
-rw-rw-r-- 1 patrick patrick  206 2008-04-21 15:53 blk.png 
-rw-rw-r-- 1 patrick patrick 3993 2008-04-21 15:54 Dry.png 
-rw-rw-r-- 1 patrick patrick  161 2008-04-24 07:43 Gutsy.png 
-rw-rw-r-- 1 patrick patrick  917 2008-04-23 07:15 Ilumi12.png 
-rw-rw-r-- 1 patrick patrick 1038 2008-04-21 15:55 kickerbackground48dark.png 
-rw-rw-r-- 1 patrick patrick  600 2008-04-21 15:54 kickerbackground48.png 
-rw-rw-r-- 1 patrick patrick 2864 2008-04-21 15:55 Leopard.png 
-rw-rw-r-- 1 patrick patrick  171 2008-04-24 03:36 panel-bg-dark.png 
-rw-rw-r-- 1 patrick patrick  172 2008-04-24 03:34 panel-bg.png 
-rwxrwxr-x 1 patrick patrick 1788 2008-04-21 15:30 Silver.png 
patrick@patrick-desktop:~$ 
------------------ /home/patrick/Desktop/data 
patrick@patrick-desktop:~$ lsattr -Ra $HOME/Desktop/data 
------------------ /home/patrick/Desktop/data/. 
------------------ /home/patrick/Desktop/data/.. 
------------------ /home/patrick/Desktop/data/Panels 

/home/patrick/Desktop/data/Panels: 
------------------ /home/patrick/Desktop/data/Panels/kickerbackground48.png 
------------------ /home/patrick/Desktop/data/Panels/kickerbackground48dark.png 
------------------ /home/patrick/Desktop/data/Panels/Ilumi12.png 
------------------ /home/patrick/Desktop/data/Panels/. 
------------------ /home/patrick/Desktop/data/Panels/Dry.png 
------------------ /home/patrick/Desktop/data/Panels/panel-bg.png 
------------------ /home/patrick/Desktop/data/Panels/Leopard.png 
------------------ /home/patrick/Desktop/data/Panels/.. 
------------------ /home/patrick/Desktop/data/Panels/Gutsy.png 
------------------ /home/patrick/Desktop/data/Panels/blk.png 
------------------ /home/patrick/Desktop/data/Panels/65966-version2.jpg 
------------------ /home/patrick/Desktop/data/Panels/Silver.png 
------------------ /home/patrick/Desktop/data/Panels/panel-bg-dark.png 

------------------ /home/patrick/Desktop/data/Backgrounds 

/home/patrick/Desktop/data/Backgrounds: 
------------------ /home/patrick/Desktop/data/Backgrounds/LDE.png 
------------------ /home/patrick/Desktop/data/Backgrounds/slick .png 
------------------ /home/patrick/Desktop/data/Backgrounds/Ubuntu_wallpaper_by_lethal2.png 
------------------ /home/patrick/Desktop/data/Backgrounds/lightbuntu.png 
------------------ /home/patrick/Desktop/data/Backgrounds/ubuntu_reflect.png 
------------------ /home/patrick/Desktop/data/Backgrounds/Ubuntu_PartLines_Wallpaper_by_buriednow.jpg 
------------------ /home/patrick/Desktop/data/Backgrounds/1_Ubuntu-Wallpaper-1024x786-JDJW.jpg 
------------------ /home/patrick/Desktop/data/Backgrounds/. 
------------------ /home/patrick/Desktop/data/Backgrounds/66107-simple_ubuntu.png 
------------------ /home/patrick/Desktop/data/Backgrounds/50070-background.png 
------------------ /home/patrick/Desktop/data/Backgrounds/trademark.jpg 
------------------ /home/patrick/Desktop/data/Backgrounds/kate holmes.jpg 
------------------ /home/patrick/Desktop/data/Backgrounds/toronto_nighttime_1280.jpg 
------------------ /home/patrick/Desktop/data/Backgrounds/Hardy-Simple Human 1600x1200.png 
------------------ /home/patrick/Desktop/data/Backgrounds/.. 
------------------ /home/patrick/Desktop/data/Backgrounds/65415-blue_ubuntu.jpg 
------------------ /home/patrick/Desktop/data/Backgrounds/76683-black abscract without logo.png 
------------------ /home/patrick/Desktop/data/Backgrounds/Flower.jpg 
------------------ /home/patrick/Desktop/data/Backgrounds/ABSTRACT-CrunchyBranch_1680x1050.png 
------------------ /home/patrick/Desktop/data/Backgrounds/Dark Hardy.jpg 
------------------ /home/patrick/Desktop/data/Backgrounds/Ubuntu_Dapper_Drake_by_djust.png 
------------------ /home/patrick/Desktop/data/Backgrounds/NATURE-Leaf_1920x1200.jpg 
------------------ /home/patrick/Desktop/data/Backgrounds/65256-1.jpg 
------------------ /home/patrick/Desktop/data/Backgrounds/Natalia Vodianova 01.JPG 

patrick@patrick-desktop:~$

---

### Post by forger on 2008-07-09
I forgot the chmod :D

```
sudo chmod -R 644 $HOME/Desktop/data
```

let's hope this is the one that fixes it :)

---

### Post by rustyz on 2008-07-09
nope, 

said bash command not found

it would not let me drag the file to the data folder either...

and now it says cannot umount volume...

when i go to eject the disk...

---

### Post by forger on 2008-07-09
That's weird, that is a must-have command.

```
sudo apt-get install --reinstall coreutils
sudo chmod -R 644 $HOME/Desktop/data
```


(You can't eject the disc because the terminal is using it, if you close the terminal and all the open windows from the cd, then unmount it)

---

### Post by rustyz on 2008-07-09
coreutils 6.10 version installed no prob, just here we go again...

> :~$ sudo chmod -R 644 $HOME/Desktop/data
chmod: cannot access `/home/patrick/Desktop/data': No such file or directory
patrick@patrick-desktop:~$

i'm almost to the i surrender point, i aint gunna tho...

if your willing, i'm stil willing...

lets go to day one...

start fresh, i will delete data folder, make a new one and give me the exact pecking order...

i do see onther permissions problems poping up on the boards...

i just dont get why this is so simple on the last distros, just not the latest...

thanks again forger, lets forge on!

rz

ps, should i bother to learn how to install Hardly Heron from the manual installation, and maybe thats where the new distros problem lies, in the guided install?

wait til you see the Hardly Heron wallpaer in the making... rotfl

---

### Post by forger on 2008-07-09
ok, day 1:
```

sudo apt-get update
sudo apt-get install --reinstall ubuntu-desktop ubuntu-minimal ubuntu-standard sudo gksu login
sudo apt-get -f install
sudo dpkg --configure -a
```
It might take some time to finish

**[COLOR="Red"]Close the terminal[/COLOR] and open another one.**

[B]1) Don't be root at all times!
2) Paste the commands exactly as they are (CASE SENSITIVE!)[/B]

create the data folder with this:
```

cd $HOME/Desktop
[ -d data ] && sudo rm -rf data || mkdir data

```

Copy your files to the data folder with nautilus:
1) put in your cd
2) select the files you want
3) right-click on the files and select copy
4) go and open the data folder in Desktop, right-click and select paste

When **all** the files **are copied**, close the data folder window.

Now do the following in terminal:
```

sudo chattr -uia -lRa $HOME/Desktop/data
sudo chattr -uia -lRa $HOME/Desktop/data/*
sudo chown -hR $USER:$USER $HOME/Desktop/data
sudo chmod -R +rwx $HOME/Desktop/data
sudo chmod -R +rwx $HOME/Desktop/data/*

```

Your files should be ready for use in the data folder. Open the data folder window and double click on a file, it should open.

If not, format your home and root partition and reinstall ubuntu :)

---

### Post by rustyz on 2008-07-09
i'm doing a guided use entire disk re-install of hardly as we speak...

will do as perscribed!

if all else fails...

> If not, format your home and root partition 
 how?

iv'e only used the guided...

in non-geek please

treat me gently, as mentioned, semi-newb here... lol

i have learned loads, just not how to do a manual format...

thanks so, so much my friend!

rz

---

### Post by forger on 2008-07-09
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.psychocats.net/ubuntu/installing#partitioning](http://www.psychocats.net/ubuntu/installing#partitioning)
This is a great guide for partitioning

Well the manual formatting is recommended, unless the guided gives you separate partitions for root and home.
If you don't want to lose any time separating your home from your root partitions, then use the guided partitioning, it should work every time.

**BUT BE WARNED**, make sure you don't delete windows if you have them on the same disk! I have two hard drives, one for windows and one for ubuntu

By "root partition" I mean the / mount point, that's your main folder for your operating system and everything inside it - usually ext3
Apart from that, "home partition" is the /home mount point - also ext3
The last thing you need is a "swap partition" (mount point swap) - not ext3, but swap

I would give root ("/") 10 GB (10240 MB), swap 1 GB (1024 MB) and the rest of the space goes to home ("/home")

---

### Post by rustyz on 2008-07-09
new install done... guided, and here we go with the operation forger!

will report back soon!

rz

---

### Post by rustyz on 2008-07-09
[SIZE="7"]Bravo!!![/SIZE]

a job well done forger!!!\\:D/\\:D/\\:D/

now, i will have to see if this works with the other debian based distros...

dont see why it wouldn't...


thanks again Ubunbro!

rz

---

### Post by rustyz on 2008-07-09
forge, i just couldnt resist!

[IMG]http://img55.imageshack.us/img55/9646/hardlyheron1tg2.png[/IMG]

orig. art by monsteer deviantart

---

### Post by forger on 2008-07-09
nice wallpaper ;)
it's hardy heron, but hardly is good as well :D

---

### Post by rustyz on 2008-07-10
forger> it's hardy heronfor all we went through to do a simple task...

i still say "Hardly" Heron...

love my Gutsy

i hope the LTS team takes a look at this problem, and perhaps ads a fix on a update!

thanks again forger... 

now go help another!

rz

ps...

how does one make this thread solved?

---

