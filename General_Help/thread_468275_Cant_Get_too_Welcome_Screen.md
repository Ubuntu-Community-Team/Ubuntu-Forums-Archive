---
title: "Cant Get too Welcome Screen"
date: 2007-06-08
forum: General Help
---

### Post by 13th_star on 2007-06-08
Hi I'm kinda new to Ubuntu and have only been using it for a little around 2 weeks, today I tryed to enable it so that I could login as the Root user to be able o edit the menu.lst in the boot/grub/ folder, only when I changed a few settings it went a bit funny on me every time I try to get into ubuntu I cannot get to the login screen all I see is my curser with the loading sign, and I even left doing that for an hour today hoping it would just do something.

anyways I know I have changed a seeting something I think its the tab after the one where you choose for The root user to be able to login. In most words I pretty much forgot what I pressed.

does anyone know how I can get back into ubuntu to change the settings back or maybe reset all the settings to default?


thanks I'll be greatful for the help.

---

### Post by logos34 on 2007-06-08
Do you have a copy of the ubuntu live cd handy?  cause you'll need it get into your files.

---

### Post by merlinus on 2007-06-08
You do not need to log in as root.  In fact, it is a good idea to NOT do this.

You can edit /boot/grub/menu lst by entering this in a terminal:

gksudo gedit /boot/grub/menu.lst

It will ask for your password, and then load the file in a text editor.

Anytime you need root access, you can use

sudo

or 

gksudo (for graphical interface work such as gedit)

in a terminal, followed by whatever it is you want to edit or accomplish.

-merlin

---

### Post by 13th_star on 2007-06-08
Yes its in my machine ready and waiting as we speak, dunno if this is a problem but I upgraded my copy of 6.10 to 7.04 a few days ago and my live cd is 6.10.

also I've been trying to boot from it but all I see is the options I have weather the disk is in or not.

I'll give a quick look in my bios settings to see if the cd-rom is set to boot first.

---

### Post by 13th_star on 2007-06-08
> **merlinus said:**
> You do not need to log in as root.  In fact, it is a good idea to NOT do this.

You can edit /boot/grub/menu lst by entering this in a terminal:

gksudo gedit /boot/grub/menu.lst

It will ask for your password, and then load the file in a text editor.

-merlin


damn!, thanks for letting me know I just wished I asked befor changing settings, I'm sure I enabled something under administration->login window.  something like that anyways. I just wish I could get back in there to change it.

---

### Post by logos34 on 2007-06-08
yeah, make sure the bios is set to boot cdrom first.

When you get to the menu highlight install and load the desktop.

Open a terminal (under Applications>accessories I believe).  You need to mount the root partition to access menu.lst.

Type:
**sudo fdisk -l**

This show all your partitions.  Find the one that is root.  (ending '...83  Linux'.) 

> [QUOTE]sudo mkdir /mnt/ubuntu
sudo mount -t auto /dev/**hdxy** /mnt/ubuntu   *replace 'hdxy' with the output from fdisk above.  Might be 'hda2'
cd /mnt/ubuntu/boot/grub
sudo gedit menu.lst[/QUOTE]

post it here if you can access the internet.  If not, look for a backup of menu.lst

**ls**

or use the nautilus file browser.

If there is one ('menu.lst_bak' or something similar) and it looks like the default, copy it to the current (edited) one.

Ex:
**sudo cp menu.lst_bak menu.lst**

Try that.  But hopefully you have the network going and we can look over the menu.lst first.

---

### Post by 13th_star on 2007-06-08
thats really my problem at the moment, the fact is I cannot getting my ubuntu becus I think I may of enabled something (think it could of been auto login) and now when I try to start ubuntu where I normal see the login screen all I get is my curser with a loading sign.

---

### Post by logos34 on 2007-06-08
yes, but we're only trying to mount the partition, not boot from it.  You shoudl be able to mount it, unless something else is all awry.

---

### Post by logos34 on 2007-06-08
Or are you having trouble setting the bios to boot from the cdrom?

---

### Post by 13th_star on 2007-06-08
no I can boot from the cd, I just dont really understand why when none of my files are on it, and what is it you mean by mounting it? I went into the mounting manager and I had no idea what I was doing.

I've got a
 hd1
hd2
hd3
hd4 linux partion
hd5 linux files are based at
hd6 swap file 

the first 3 are for my windows xp as I've got them both on my laptop.

its just getting annouying cus I have to keep coming back here and there, I'm not bothered about the mun.lst file anymore I know qhat I'll be doing with that its just the logging in part when I start up ubuntu

---

### Post by logos34 on 2007-06-08
ok, I see what you saying now.  I glanced over your initial post to quickly it seems.  So you're just getting the spinning wheel and it never loads the login screen.  Did this perchance happen 'Logon window' program (System>Applications>logon window)?  There's a 'security' tab where you can 'enable automatic logon'.  Is that where you were?

---

### Post by 13th_star on 2007-06-08
yes that is the one, I think I enabled that when also clicking the tick box allowing administrators or something like that to login, I just forgot to put the top auto login back.

---

### Post by logos34 on 2007-06-08
> **13th_star said:**
> yes that is the one, I think I enabled that when also clicking the tick box allowing administrators or something like that to login, I just forgot to put the top auto login back.

[ATTACH]34761[/ATTACH]

If that's it the config file is located at 
**/etc/gdm/gdm.conf**

---

### Post by logos34 on 2007-06-08
I'm thinking that instead of editing gdm.conf or gdm.conf-custom by hand, it might be safest (from the ubuntu live disk) to cd over to the root partition, then run s**udo gdmsetup**, which will call up the Logon window gui as shown above.

---

### Post by 13th_star on 2007-06-08
so your saying I should load up the disk and run that, then from there open the turminal type in sudo gdmsetup, and change the settings there. will that only change it on the disk thou or on the partition aswell?

---

### Post by logos34 on 2007-06-08
no, that actually won't work after all--I just tried and can't get it to pull up gdmsetup from /usr/sbin/ on the mounted root partition--it just calls up the one on the CD.  

So, you'll have to edit it by hand (again from the live CD).

It says to make changes to gdm.conf.custom.  I'm reading over it right now...

---

### Post by 13th_star on 2007-06-08
> **logos34 said:**
> no, that actually won't work after all--I just tried and can't get it to pull up gdmsetup from /usr/sbin/ on the mounted root partition--it just calls up the one on the CD.  

So, you'll have to edit it by hand (again from the live CD).

It says to make changes to gdm.conf.custom.  I'm reading over it right now...


well I'm sure gonna make sure I dont do this again lol, so how am I meant to be able to edit gdm.conf.custom using the live cd?

---

### Post by logos34 on 2007-06-08
ok, I think all you have to do is clear out any changes in gdm.conf-custom.  Changes made in the Logon Window Preferences is written to -custom file.  So using mine as an example, there are two changes shown--one to enable remote logon and the other a custom logon window backgriound picture. 
> ...

NOTE: Lines that begin with "#" are considered comments.
#
# Have fun!

[daemon]

[security]

[xdmcp]
**Enable=true**

[gui]

[greeter]
[B]GraphicalTheme=backcountry-skiing
GraphicalThemedColor=#6a6fd7[/B]

[chooser]

[debug]

[servers]



To restore to default just clear it:

> NOTE: Lines that begin with "#" are considered comments.
#
# Have fun!

[daemon]

[security]

[xdmcp]

[gui]

[greeter]

[chooser]

[debug]

[servers]

Your's will have among other things an entry under [Daemon] and [Security] something like this:
> 
[Daemon]
**AutomaticLoginEnable=true**

[security]
**AllowRoot=[B]true**[/B]

So boot to the CD and follow my instructions above but after you mount the root partition forget the menu.lst stuff and type:

**sudo gedit /mnt/ubuntu/etc/gdm/gdm.conf-custom**

Then edit it described above.

Hopefully that'll do the trick!

---

### Post by 13th_star on 2007-06-08
Hey it didnt work when I tryed doing it from the live CD but then I went into recovery mode and changed a few paths to the files you gave me and yippy its all done and fully working, I even edited the menu.lst while I was there lol.

thanks very for taking the time to help :)

---

### Post by logos34 on 2007-06-08
Nothing like a happy ending!  

Have fun with Ubuntu.  And get some shuteye--it's nearly dawn over there!

---

### Post by 13th_star on 2007-06-09
Hey I will do, and yeah I was damn tired last night lol.

---

