---
title: "few problems with a new install"
date: 2007-08-06
forum: General Help
---

### Post by stlouis1 on 2007-08-06
well, i hope im asking in the right place cuz im using kubuntu, but the kubuntu forum seems so much smaller than this one, so i thought i ask here.

im a somewhat new linux user, i used fedora 4/6/7 before, and they always crapped out on me right when i was getting somehwere. so i decided to try kubuntu cuz i like KDE, make the transition a little easier on a windows user. im running it on an inspiron 9300

anyway, i have a few small problems

1. ntfs drives dont mount, and i know i have the ntfs libraries installed

2. mtpfs, i cant get my zen vision to mount. but i can workaround that for now with gnomad and amarok

3. i cant login as the root to install any games. tried to install quake 4, ut2k4, and eduke, but then i cant copy the data files into the folders. on fedora i had to install them all as root

4. i can get my bluetooth mouse to work, but it wont reconnect automatically after reboot, so i have to connect it through the consol every time.

and i've done some research on these in teh forums and tried alot of stuff i found, just cant figure these out. once i can figure these out, im planning on getting a new 400gb hard drive and switching to linux on my desktop as well, so help me convert here guys

thanks, serge

---

### Post by AlexThomson_NZ on 2007-08-06
Hi- welcome to the forum! :)

1. Maybe a bit vague there, but if you run 'dmesg' it should give you some clues as to why it had trouble mounting.  I'm guessing the entry in fstab is wrong

2. Sorry, no idea! 

3. You can run commands on the console as root with the 'su' command (ie. 'su ./install_quake4_script.sh') (I hope that was what you meant)

4. You can add things to the startup by using 'sessions' in the Gnome menu.  Not sure off hand about KDE, but if you look in the menu under administration (or similar) there should be a KDE equivalent (any KDE users that can help here?)

---

### Post by stlouis1 on 2007-08-07
well, i fixed my bluetooth reconnect issue with the info i found [here]("http://http://kubuntuforums.net/forums/index.php?topic=10126.0")

and my ntfs problem with my external drive, well, it used to be the drive in my laptop with my vista install, just needed to mount it so i could pull my docs off again. i connected it to my windows pc and did the safely remove hardware bit, and it worked. so i know i dont have a problem there. 

i will need to download the ntfs-tools package or whatever its called , i read about a command in there to fix the partition or whatever so i wouldnt have to connect it to a windows pc. but again, no big issue, i got what i needed

now all i need to really figure out is how to get my zen to mount with mtpfs, might post in another forum for that if i cant find any more help searching. then i can get onto some gaming

---

### Post by clum on 2007-08-07
3. The command is called sudo, not su. su would also do the job, but it is disabled by default in Ubuntu. In order to enable it, type sudo passwd root, and then enter the current user's password, and then make a password for root which can then be accessed with su.

---

### Post by AlexThomson_NZ on 2007-08-07
Bah!  Quite right 'sudo' not 'su'

---

### Post by stlouis1 on 2007-08-07
thanks, i did figure out the sudo +command and then enter password

it was bugging the shiz outta me cuz i was using fedora and i was used to typing su once, and not having to sudo everything.

i would kind of like to figure out how to enable the root account so i can log into it from the login screen. i was used to starting new login sessions on fedora to install games, i found it easier to login as root and install a couple games. its just easier for through gui than it is with a console.....keeps things simple

---

### Post by backflop on 2007-08-07
You can enable a root login through System>Administration>Login Window. Then under the Security tab check the box labeled Allow System Administrator Login. Then at the login type root then password.
That is what you do for Gnome anyway, I forgot you were using KDE, but I'm sure there is something similar for your desktop environment.

---

### Post by stlouis1 on 2007-08-07
i think i found something here anyways
[http://www.ducea.com/2006/06/21/ubuntu-how-to-enable-the-root-account/](http://www.ducea.com/2006/06/21/ubuntu-how-to-enable-the-root-account/)

gonna give it a go when i get home

---

### Post by AlexThomson_NZ on 2007-08-08
> **stlouis1 said:**
> i would kind of like to figure out how to enable the root account so i can log into it from the login screen.....keeps things simple

Works well in Windows doesn't it? ;)

---

### Post by stlouis1 on 2007-08-08
it absolutely does. and being as i work tech support, and the number of people i tell to create user their own user accounts and not use the built in admin........i should know better

but really, i just want it enabled for installing certain programs here and there, not to use as my main account

i did figure my way around it with sudo........and i figured out what i was doing wrong trying to install ut2004, needed to use teh sh command with the installer. that was mostly why i wanted to use the root account....guess i dont need it anyway

i think ima go to chapters and grab a couple linux books. im tired of windows, if you know windows, u work in a call center for 13$ and hour, its bs.....if u know linux, big companies move you and your family to new countries to work big money

---

