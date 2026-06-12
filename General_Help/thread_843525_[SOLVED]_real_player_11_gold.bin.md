---
title: "[SOLVED] real player 11 gold.bin"
date: 2008-06-28
forum: General Help
---

### Post by ramadan on 2008-06-28
I've downloaded this file from realplayer site as binary file, and i couldn't install it, how to install it or to make *.rm files work on ubuntu
every help is appreciated

---

### Post by chunchengch on 2008-06-28
[COLOR="Red"]$ chmod +x RealPlayer11GOLD.bin
$ sudo ./RealPlayer11GOLD.bin[/COLOR]

press [Enter] for all the questions during installation, then you can find the launcher in Application > Video and Sound

---

### Post by drs305 on 2008-06-28
> **ramadan said:**
> I've downloaded this file from realplayer site as binary file, and i couldn't install it, how to install it or to make *.rm files work on ubuntu
every help is appreciated

Look for my entry in the following thread. Come back here if you have questions. Also don't forget to save the installation folder since it has the only sure way to remove the app later.
[Real Player Installation]("http://ubuntuforums.org/showthread.php?t=807173&highlight=real+player+install")

---

### Post by vishzilla on 2008-06-28
I hope this [link]("https://help.ubuntu.com/community/RealPlayerInstallationMethods") helps you for reference if you have any problems.

Anyway you can go to the dir where the file is present and enter ```
chmod a+x RealPlayer11GOLD.bin
./RealPlayer11GOLD.bin
```

---

### Post by ramadan on 2008-06-28
> **chunchengch said:**
> [COLOR="Red"]$ chmod +x RealPlayer11GOLD.bin
$ sudo ./RealPlayer11GOLD.bin[/COLOR]

press [Enter] for all the questions during installation, then you can find the launcher in Application > Video and Sound


1. i opened the terminal and wrote chmod +X and drag drop the real player file>> enter >> no any message (seems cool)
2. i typed sudo and drag drop again the same file>> error message "There is no application installed for this file type"

so do i miss anything?

thnks for help

---

### Post by ramadan on 2008-06-28
guys the whole thing drives me nuts, where I supposed to place the file after downloading it
I've never see such thing

---

### Post by chunchengch on 2008-06-28
> **ramadan said:**
> 1. ...drag drop the real player file...
2. ...drag drop again...

Don't be so lazy, move your fingers to press some keys.

no matter where you place the .bin file you download, such as desktop or home folder, just open the terminal and cd to the directory where the .bin file is, then input these commands step by step.

[COLOR="Red"]$ chmod +x RealPlayer11GOLD.bin
$ sudo ./RealPlayer11GOLD.bin[/COLOR]

---

### Post by dizee on 2008-06-28
> **ramadan said:**
> 1. i opened the terminal and wrote chmod +X and drag drop the real player file>> enter >> no any message (seems cool)
2. i typed sudo and drag drop again the same file>> error message "There is no application installed for this file type"

so do i miss anything?

thnks for help
are you forgetting to put ./ before RealPlayer11GOLD.bin?

type it to be sure.
```
sudo ./RealPlayer11GOLD.bin
```

---

### Post by ramadan on 2008-06-28
my path is like this home/ramadan/desktop so i did the following
$ cd /home >> /home$  was fine
then $ cd /ramadan >> message " no such folder or file name"
am used to dos, i do know the console and i can do well in dos
i know the path but i can't get to it (dont know why) so to avoid this i drag and drop the file and pressed enter >> no message at all just the prompt move to another line so i assume that is good, but the next step was total failure.

by the way (./) is this dot necessary ( what does it stand for?)and do i need to enter the full path of the file in the second step?
N.B (please have a look at my avatar!)
you may give not an attention to a small detail
thanks for help

---

### Post by drs305 on 2008-06-28
in the terminal, type **ls**
if you don't see a response that includes **RealPlayer11GOLD.bin** in the list you are _not_ in the right place. do not drag and drop anything. we will do this all with the terminal.
if you see it, then type this exactly:
**chmod +x RealPlayer11GOLD.bin**
You should see a blue triangle symbol if you look at the file in nautilus.
Now type exactly (yes, including the ./ ):
sudo ./RealPlayerGOLD.bin

That will start the installation.
It will ask where you want to put the installation. Pick a location. /opt/realplayer is a good one.

Do you have IM capability? If so, send me a PM via this forum.

---

### Post by ramadan on 2008-06-28
i tried as you told me but no response as well
the file is on my desktop ( /home/ramadan/desktop) so how to get to it?
i do have messanger but dont know how to enable it

---

### Post by drs305 on 2008-06-28
> **ramadan said:**
> i tried as you told me but no response as well
the file is on my desktop ( /home/ramadan/desktop) so how to get to it?
i do have messanger but dont know how to enable it

type "ls" . What do you see as a result?
the command from anywhere should be "cd /home/ramadan/Desktop"
you must use the same case (capitalization)
....
cd Desktop
...
okay, you should be on the desktop.
type "**ls** and you should see "RealPlayer11GOLD.bin"
...

---

### Post by ramadan on 2008-06-28
ramadan@ubuntu:~$ ls
BONES.m2t  Documents  Music   Pictures  Templates        Videos
Desktop    Examples   Photos  Public    untitled folder  [www.bin](www.bin)
ramadan@ubuntu:~$
by the way  i renamed the file to [www.bin](www.bin) for easy handling

---

### Post by drs305 on 2008-06-28
> **ramadan said:**
> ramadan@ubuntu:~$ ls
BONES.m2t  Documents  Music   Pictures  Templates        Videos
Desktop    Examples   Photos  Public    untitled folder  [www.bin](www.bin)
ramadan@ubuntu:~$
by the way  i renamed the file to [www.bin](www.bin) for easy handling
No rename it back to RealPlayer11GOLD.bin
If you get tired of typing it, all you have to do is type the first two letters and hit the tab key.  then it will complete the entry for you .

and watch my previous post for instructions please

---

### Post by ramadan on 2008-06-28
I figure out one mistake: I've used "/" every time but now after /home i just used cd ramdan , cd Desktop and all if fine and for other issues,

---

### Post by ramadan on 2008-06-28
i renamed it to Realplayer11gold.bin,>> chmod a+x Realplayer11.gold
>> no response only the cursor moved to the second line
"ramadan@ubuntu:/home$ cd ramadan
ramadan@ubuntu:~$ cd Desktop
ramadan@ubuntu:~/Desktop$ chmod a+x Realplayer11gold.bin
ramadan@ubuntu:~/Desktop$ "

---

### Post by drs305 on 2008-06-28
Capitalization is important in linux. I don't know if it will make a difference here, but please rename it exactly: **RealPlayer11GOLD.bin**

Once again, to make sure you are in the same directory, type "**ls**  You should see RealPlayer11GOLD.bin listed. 

If so, once more to be sure:
**chmod +x RealPlayer11GOLD.bin**
If it works, the cursor will move to the next line and the prompt will be the same as on the line above it. 
example:  
~/Desktop: chmod +x RealPlayer11GOLD.bin   
~/Desktop:  

Once you have done that, type **exactly** or type the first 3 or 4 characters and press tab to complete:

**sudo ./RealPlayer11GOLD.bin**

It will start to install and you will see periods as it advances .......
When or if it stops for more than 2 minutes, hit ENTER.

At some point, it will ask where you want to install it. My recommendation is:
**/opt/realplayer**

Once it is installed, you will find it in the *Sound & Video Menu*

I have to leave now. Best wishes ramadan.

---

### Post by ramadan on 2008-06-29
i tried another file (original name) RealPlayer11GOLD.bin
the same problem.
at least I tried my best
thank you very much for help

---

### Post by dizee on 2008-06-29
right, for the simplest way just move it (the RealPlayer11GOLD.bin file) to your home folder.

open a terminal.

type chmod +x Rea and press the Tab button on your keyboard.
this will give you 
```
chmod +x RealPlayer11GOLD.bin
```

press enter. type sudo ./Rea and press tab.
```
sudo ./RealPlayer11GOLD.bin
```
follow the default options after pressing enter.

(the tab button autocompletes so you don't need to worry about typing mistakes.)

---

### Post by ramadan on 2008-06-29
thanks for your respone but i do copy and paste the name ( rename> copy)
I'll try to download the file again to avoid un-needed problems
thanks again'


i downloaded the file "realplay-11.1.0.1011-linux-2.6-glibc23-amd64.bin" no response as well

---

### Post by dizee on 2008-06-29
Just download the file to your home folder, and then you can copy and paste the commands I posted.

---

### Post by ramadan on 2008-06-29
this is the result:
ramadan@ubuntu:~$ chmod +x realplay-11.1.0.1011-linux-2.6-glibc23-amd64.bin 
ramadan@ubuntu:~$ ./realplay-11.1.0.1011-linux-2.6-glibc23-amd64.bin 
Extracting files for Helix installation........................

Welcome to the RealPlayer (11.1.0.1011) Setup for UNIX
Setup will help you get RealPlayer running on your computer.
Press [Enter] to continue...
Enter the complete path to the directory where you want
RealPlayer to be installed.  You must specify the full
pathname of the directory and have write privileges to
the chosen directory.
Directory:  [/home/ramadan/RealPlayer]:                         

You have selected the following RealPlayer configuration:

Destination:            /home/ramadan/RealPlayer

Enter [F]inish to begin copying files, or [P]revious to go
back to the previous prompts: [F]: F

Copying RealPlayer files...No write-permission to  /etc/profile.d ...skip.
Succeeded.
installing application icons resource...
installing document icons resource...
....Succeeded.
Configuring Mozilla...
Installing .mo locale files...
Setting selinux context...
/usr/share or /usr/bin no write-permission...skip.

RealPlayer installation is complete.
Cleaning up installation files...
Done.

but I still cant open *.rm files or start real player, it is on the video program list but i try to open it >> could not launch menu item, failed to execute child "realplayer" no such file or directory,
amazing!

---

### Post by drs305 on 2008-06-29
Hey, congratulations on getting it to install. Now that you know how to install it....

To correct your problem, I would suggest you uninstall it and then redo it with a slightly different approach.

First, go into the RealPlayer folder on your desktop and find the 'postinst' folder. Inside is a file to remove realplayer - I think it is called postuninst.sh  Double click and run that command to uninstall realplayer.

Next, reinstall it again, but this time do it as 'root' and using 'sudo'.

Go back to your desktop, and type (after the first few letters hit the tab key to complete it):
**sudo ./realplay-11.1.0.1011-linux-2.6-glibc23-amd64.bin**

When it asks 
```
You must specify the full
pathname of the directory and have write privileges to
the chosen directory.
Directory: [/home/ramadan/RealPlayer]: 
```
Use this:
**/opt/realplayer**

I think you will have better luck installing it this way.

---

### Post by ramadan on 2008-06-29
I did unistall as you told me, and wanna say that **I've learned many skills the past hours and very happy for that**( *full half* )
The result to last approach:

ramadan@ubuntu:~$ sudo ./realplay-11.1.0.1011-linux-2.6-glibc23-amd64.bin 
[sudo] password for ramadan: 
Extracting files for Helix installation........................

Welcome to the RealPlayer (11.1.0.1011) Setup for UNIX
Setup will help you get RealPlayer running on your computer.
Press [Enter] to continue...
Enter the complete path to the directory where you want
RealPlayer to be installed.  You must specify the full
pathname of the directory and have write privileges to
the chosen directory.
Directory:  [/opt/real/RealPlayer]: 

You have selected the following RealPlayer configuration:

Destination:            /opt/real/RealPlayer

Enter [F]inish to begin copying files, or [P]revious to go
back to the previous prompts: [F]: F

Copying RealPlayer files...Path setup done.
Succeeded.
installing application icons resource...
installing document icons resource...
...Succeeded.
Configuring Mozilla...
Installing .mo locale files...
Setting selinux context...
Succeeded.

RealPlayer installation is complete.
Cleaning up installation files...
Done.

When I tried to open it >> **could not launch menu item, failed to execute child process realplayer ( permission denied)**

Also when i try to open the folder >> no permission 
I've installed Ubuntu my self as root user!

---

### Post by drs305 on 2008-06-29
Try changing the folder ownership to yourself:
```
sudo chown -R ramadan:ramadan /opt/real
```

Are you starting realplayer by typing "**realplay**" in terminal?

---

### Post by ramadan on 2008-06-29
drs305 you are great guy, am really grateful to you
everthing is fine now:guitar:

am planning for opera installation soon so don't be much sure:)

---

