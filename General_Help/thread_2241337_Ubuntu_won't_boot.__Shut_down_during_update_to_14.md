---
title: "Ubuntu won't boot.  Shut down during update to 14"
date: 2014-08-25
forum: General Help
---

### Post by bdh2991 on 2014-08-25
I was updating ubuntu from 12 to 14 and computer shut down while the update was still going.  Now ubuntu is stuck on the load screen (with ubuntu in the middle and the little orange dots underneath).  I tried a few option in the recovery mode but nothing seems to work.  Should I kiss my ubuntu partition goodbye and do a clean install or is this fixable?

---

### Post by Bashing-om on 2014-08-25
bdh2991; Hi ! Welcome to the forum .

It's ubuntu, it is always fixable. Fixing depends on how much time, effort, and trouble shooting one will go through.

let's get an idea of "how much trouble" it may be to fix.
See if you can boot to a Command Line Interface:

Boot ubuntu and as soon as the bios screen clears depress and hold the right shift key -> grub boot menu;
With the latest non-recovery kernel entry highlighted press the 'e' key for edit mode -> boot options screen;
Arrow down and across to the terms "quiet splash" and replace them with the term "text" - without the quotes ;
Key combo ctl+x to continue the boot process to a text terminal (TTY1).

Can you login here with your username and password ( when password is entered, there is no response to the screen. Enter password blindly and hit the enter key) ?

If you can login then we can run a few commands to insure the integrity of the system and get ya back up on the desk top.

[INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT][/INDENT]

---

### Post by bdh2991 on 2014-08-25
Ok, so doing what you suggested i was able to login and just use the command line. I tried 'startx' but the screen just went black.  I did see all my files but I wasn't able to open a text editor or anything (not sure if that information is useful to you)...  Whats next?

---

### Post by Bashing-om on 2014-08-25
bdh2991; Hey hey ;;

Is that good news or what ! ..

Ok there are a couple of avenues we can take at this point.

May I suggest we do try and start the desktop, and see what errors the system generates:
The correct code to do so for a standard install of (u)buntu is:
```

sudo service lightdm start

```
So, What results ?
Depending, next we look at the graphics situation.

If you have rebooted, will have to go through the grub edit routine once more to get to the CLI .

Still just feeling our way around.

[INDENT][INDENT]where there is life
[INDENT][INDENT][INDENT][INDENT]there is hope
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bdh2991 on 2014-08-25
a quick screen of text came up then the screen just stayed black and the desktop gui didn't open....is it possible my graphics drivers got messed up or deleted?

also, i believe gnome is my default desktop interface...Not sure if that could be causing a problem...

---

### Post by Bashing-om on 2014-08-25
bdh2991; OK;

Yeah to both.
Gnome desktop the command does differ:
```

sudo service gdm start

```

And yes in my mind that a graphics driver is broken. - and maybe several other things -
Terminal commands:
```

lspci -nnk | grep -iA3 vga
sudo lshw -C display

```
But would sure be nice to have access to the GUI desktop so you could just copy/paste the output.


[INDENT][INDENT]even a poke in the dark
[INDENT][INDENT][INDENT]can shed some light on something
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bdh2991 on 2014-08-25
[IMG]http://i58.tinypic.com/11hvyw7.jpg[/IMG]

'sudo service gdm start' just return 'gdm stop/waiting' in the terminal

Hopefully this will help...this is the most this laptop has booted into windows in a lonnnggg time

---

### Post by Bashing-om on 2014-08-25
bdh2991; Shucks;

Well, we have good 'ole solid Intel graphics, and the Intel driver is loaded, the notification  'gdm stop/waiting' and not starting says to me there are problems at the xserver level.

And a picture is indeed worth a thousand words !

Let's try this, see if we can get the upgrade to complete:
```

sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg --configure -a

```

reboot and see if the GUI comes up.

[INDENT][INDENT][INDENT]maybe yes,
[INDENT][INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bdh2991 on 2014-08-25
Seems like some progress was made....Ubuntu started like normal so i went to login and once i get passed the login screen, nothing appears on the desktop accept my wallpaper and soon after an error dialog window pops up and says 'system program error' (or something to that effect).  The only options on the pop up are cancel and report problem...I tried to load it with default ubuntu GUI and with gnome GUI (same error both times).  It does show ubuntu 14.04, on the login screen though so it seems as if it did finish the update.

---

### Post by Bashing-om on 2014-08-25
bdh2991; Making progress,

as you say. Not so bleak now, huh ?

OK, boot to that GUI desktop:
key combo ctl+alt+t to get a terminal here.
Post back the results:
```

echo $DESKTOP_SESSION
apt-cache policy ubuntu-desktop

```
and let's see what you are working in.

[INDENT][INDENT]where do we go from here
[/INDENT][/INDENT]

---

### Post by bdh2991 on 2014-08-25
Sorry but keyboard shortcuts aren't working either it seems.... also tried f12 for guake terminal but no luck

---

### Post by Bashing-om on 2014-08-25
bdh2991; Humm ..

What results from terminal command:
```

sudo dpkg-reconfigure -phigh xserver-xorg

```

Reboot and try and start either of the environments you have installed ( lightdm or gdm ??}
OR is the initial install "ubuntu-Gnome" ?

Either way, let's see what happens.

[INDENT][INDENT]maybe yes ?
[/INDENT][/INDENT]

---

### Post by bdh2991 on 2014-08-25
didn't seem to have an effect at all....no output to screen after running the command and still same response after rebooting and logging in...

---

### Post by Bashing-om on 2014-08-25
bdh2991; Humm ??

Kinda in a quandary as we do not know the desktop environment that you have ?

Did you do a standard ubuntu install  and then add/change the desktop ?
Did you initially install something like say ubuntu-Gnome ?

Can we revert back to say unity as the desktop ?

What environment are we trying to fix here ?

[INDENT][INDENT][INDENT]sometimes I just do not know
[/INDENT][/INDENT][/INDENT]

---

### Post by bdh2991 on 2014-08-25
i had just regular ubuntu 12 default desktop, after that i had downloaded and installed gnome 3 i think.  Then once i accidently shut down after halfway through install ubuntu 14 this happened.  To this point the only thing that loads on the screen after logging in is the wallpaper and the mouse pointer....not dock or icons or keyboard shortcut functionality.  Hopefully I made things more clear?

---

### Post by bdh2991 on 2014-08-25
i had just regular ubuntu 12 default desktop, after that i had downloaded and installed gnome 3 i think.  Then once i accidently shut down after halfway through install ubuntu 14 this happened.  To this point the only thing that loads on the screen after logging in is the wallpaper and the mouse pointer....not dock or icons or keyboard shortcut functionality.  Hopefully I made things more clear?

---

### Post by Bashing-om on 2014-08-26
bdh2991; Yeah;

I think we can deal with that.
If you agree, I have in mind to re-install unity - the default (u)buntu desktop. To that end to get us a working environment;
can you get a console ?
At the GUI login screen does the keycombo crl+alt+F1 get a consol;e ( terminal ), and can you log in there ?

[INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT][/INDENT]

---

### Post by bdh2991 on 2014-08-26
Yes i'm able to pull up the console and login from there

---

### Post by bdh2991 on 2014-08-26
Not to be hasty, but i just tried: 

sudo apt-get update
sudo apt-get install ubuntu-desktop

It stated that it was already the newest version and didn't need to be installed

---

### Post by Bashing-om on 2014-08-26
bdh2991; Welp;

That was a good thought.

Let's try this from that console:
```

sudo apt-get install dconf-tools
DISPLAY=:0 dconf reset -f /org/compiz/
setsid unity

```

Reboot - for this instance - for the change to take effect.

[INDENT][INDENT]try try again
[/INDENT][/INDENT]

---

### Post by bdh2991 on 2014-08-26
all i got was a screen full of errors...excuse the glare in the picture 


[IMG]http://i62.tinypic.com/2886k6.jpg[/IMG]

---

### Post by bdh2991 on 2014-08-26
small update: i rebooted and ran the commands again and now it is stuck on 'Loading plugin: opengl' ... i'll try to post asap if anything else happens

---

### Post by Bashing-om on 2014-08-26
bdh2991; Humm ??

Now that one I have never encountered !

Is that result from the 2nd or 3rd command ? 
Maybe should have stopped lightdm first ? 

[INDENT][INDENT]sometimes I just do not know
[/INDENT][/INDENT]

---

### Post by bdh2991 on 2014-08-26
This came up after 'setsid unity'... I tried running the same command again and i didn't get the same error but it just froze up on 'Loading plugin: opengl' so i'm guessing something killed the process for some reason

---

### Post by Bashing-om on 2014-08-26
bdh2991; YUK'

Valid command, so All I can surmise is a conflict with what other DE is installed. Let's see if we can identify that other DE:
```

apt-cache policy ubuntu-desktop
cat /etc/lightdm/lightdm.conf
cat /etc/gdm/gdm.conf.
cat /etc/X11/default-display-manager

```

Then it is homework time for me, to know how to remove it from the system and restore unity.

[INDENT][INDENT]poke at it long 'nuff
[INDENT][INDENT][INDENT][INDENT]somthin is gonna give
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bdh2991 on 2014-08-26
Here are the results:

[IMG]http://i62.tinypic.com/1zzp16s.jpg[/IMG]

Just to bring to attention, the second command had a typo in it that's why i ran it again at the end.

---

### Post by bdh2991 on 2014-08-26
also 'cat /etc/X11/default-display-manager' returns 'usr/sbin/lightdm' ... forgot the capitol x

---

### Post by Bashing-om on 2014-08-26
bdh2991; Well ..

Well I can confirm that the correct/latest desktop is installed.
And as well;
I looked on a standard install of 14.04, and yeah the path is changed from earlier releases:
But I do not see it pointing us in a reasonable direction:
```

cat /etc/lightdm/user.conf

```
My files:
```

#
# User accounts configuration
#
# NOTE: If you have AccountsService installed on your system, then LightDM will
# use this instead and these settings will be ignored
#
# minimum-uid = Minimum UID required to be shown in greeter
# hidden-users = Users that are not shown to the user
# hidden-shells = Shells that indicate a user cannot login
#
[UserAccounts]
minimum-uid=500
hidden-users=nobody nobody4 noaccess
hidden-shells=/bin/false /usr/sbin/nologin
###################

AccountsService:
"cat /etc/pam.d/accountsservice"

#%PAM-1.0
# Must use substack here, so the success of pam_unix will still
# cause our pam_pin to run
password   substack      common-password
password   optional      pam_pin.so

```

Hate to say it, but I do not perceive any value to what we are seeking here.

How bout we take a shotgun to this and see what results ?
```

sudo apt-get purge ubuntu-desktop
sudo apt-get install ubuntu-desktop

```

Reboot and (fingers crossed) you'll get a desktop again.

[INDENT][INDENT]maybe yes
[/INDENT][/INDENT]

---

### Post by bdh2991 on 2014-08-26
Nothing happened....I'm not sure if having gnome and xfce as options is screwing up the default ubuntu desktop

---

### Post by bdh2991 on 2014-08-26
At this point it may just be better to recover my ubuntu files from my windows partition and reinstall ubuntu

---

### Post by Bashing-om on 2014-08-26
bdh2991; Welp;

I hate to say I do not know, so I say We can find out, given enough time. But apparently I do not know how to find out if other desk top managers are installed:
"apt cache policy ubuntu-desktop" seems to indicate the system is not aware of any but ubuntu.

A quick way to check for xfce4:
```

ls -la /home/<user-name>/.config/xfce4

``` I do not have Gnome installed, so I can not verify that one.

Let's see if others can chime in here and offer their advise.
We can find out
[INDENT][INDENT][INDENT]presently, I do not know
[/INDENT][/INDENT][/INDENT]

---

### Post by bdh2991 on 2014-08-26
I know i have gnome and xfce installed for sure.  I'm going to try get rid of them so that there is just ubuntu and then see what happens.

---

