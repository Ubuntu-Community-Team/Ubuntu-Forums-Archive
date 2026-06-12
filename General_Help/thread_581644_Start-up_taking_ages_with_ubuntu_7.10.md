---
title: "Start-up taking ages with ubuntu 7.10"
date: 2007-10-19
forum: General Help
---

### Post by vampire666eng on 2007-10-19
I made a freash install of ubuntu 7.10 (Standard personal computer version) on a system with windows Xp already installed (dual boot).

The start up is fast and responsive, then I configure my network (setting the network card to static ip), I reset the system and then the start up is really slow (after I insert username and password). After I insert username and pw the screen goes orange and it stays like that for quite a bit, then the top and lower bar appear but in white without any text or icon, then the drives are mounted on the desktop and after that (some minutes of apparently no operations...no activity on hard disk), finally also the bars appear correctly and the background image. What could it be?
Is there a way to tell what could it be? (before I had ubuntu 7.04 and I had no such problem).

Then again all the programs and process I start....are slow compared to ubuntu 7.04 (I had compiz fusion also on that system).

Thanks.

EDIT: My specs are:

AMD64 3000+
2GB RAM
Geforce 6600GT 128MB RAM

I partitioned the ubuntu system:
5GB "/"
3GB "swap"
12GB "/home"

EDIT2:
[B]
EDIT:; Now I'm receiving the following error:

"Error: The panel encountered a problem while loading "OAFIID: Gnome_fastuserswitchapplet". Do you want to delete the applet from your configuration?"[/B]

---

### Post by jayaramk on 2007-10-19
even its the same problem for me tooo.... i tooo nmeed a solution for this??? whats the problem.... i disabled the virtual effects in appearance.. but still it continues the same

---

### Post by vampire666eng on 2007-10-19
So this is the behavior I'm encountering after I log in inserting username and pw:

- orange desktop,

- then top and lower bar appear (with the text and icons), but the screen remains orange and no drive mounted (and nothing can be clicked),

- then the top and lower bar suddently become white with no text and icon, the drives are mounted on the desktop, and the desktop backgrond image is loaded,

- then finally the top and lower bar became visible,


[B]EDIT; Now I'm receiving the following error:

"Error: The panel encountered a problem while loading "OAFIID: Gnome_fastuserswitchapplet". Do you want to delete the applet from your configuration?"
[/B]
Of course I chose to not delete.

---

### Post by sad_iq on 2007-10-21
Same problem here....so I'm just gonna wait for an explanation or a fix that solves the problem. In the mean time...just subscribing to this thread!!! Choosing Delete doesn't fix the problem, after a reboot the same message appears!!!

---

### Post by vampire666eng on 2007-10-21
Well done. Thanks for posting here.
Eventually some will look at this thread and check what is wrong.;)

---

### Post by por100pre1 on 2007-10-21
If there's only one user in your Ubuntu system you can remove the applet without any loss. Try reporting a bug: [https://bugs.launchpad.net/bugs/+filebug](https://bugs.launchpad.net/bugs/+filebug)

---

### Post by sad_iq on 2007-10-21
i just installed the kubuntu-desktop package and all works well under kde...no bugs there, deleting the applet doesn't solve the problem(on my system at least), it still appears after a logout!!!

---

### Post by dejongm on 2007-10-22
The following post fixed the problem for me:

[http://ubuntuforums.org/showthread.php?t=568870](http://ubuntuforums.org/showthread.php?t=568870)

<snip>

sudo apt-get update
sudo apt-get install ubuntu-desktop gdm
sudo /etc/init.d/gdm start

</snip>

---

### Post by scurl on 2007-10-22
thank you! this fixed the error problem for me!

---

### Post by vampire666eng on 2007-11-26
I got if fixed. More info here:
[http://ubuntuforums.org/showthread.php?p=3842786#post3842786](http://ubuntuforums.org/showthread.php?p=3842786#post3842786)

---

### Post by gilf on 2008-01-16
I'm adding information here in case it may help in determining the cause of the problem:

This morning one of our Samba networked Ubuntu computers had the error message:

> "Error: The panel encountered a problem while loading "OAFIID: Gnome_fastuserswitchapplet". Do you want to delete the applet from your configuration?"

The workstation is a plain vanilla Ubuntu 7.10 i386 install which has been working for about a month. No updates have been applied yet. It is networked with Samba. Two users are installed on this workstation.

One major network change was instituted last night -- we went from DHCP to static IPs. Systems were tested last night and the network was functional. This is a home network with a dialup connection, and we turn the network (workstations router and modem) off when not in use.

A nautilus bookmark exists on the problem workstation for a Samba shared file folder on another workstation.

When the workstation was started this morning, the routers and modem were turned off, as was the computer with the shared Samba file.

The error message appeared twice after two hard reboots. It appeared about a minute after the desktop was up.

A third attempt at booting was succesful and did not show the error message -- the router, modem, and shared folder workstation had been started BEFORE the reboot.

I'm wondering whether this problem is related to STATIC configured networks which are unresponsive, or unconnected.

I notice some additional evidence here (static IP, network non-functional, same error message):

[http://ubuntuforums.org/showthread.php?t=632755](http://ubuntuforums.org/showthread.php?t=632755)

---

