---
title: "ownership of GDM"
date: 2007-02-22
forum: General Help
---

### Post by tawniteamo on 2007-02-22
I installed ubuntu via the alternate install (because the desktop requires 192 RAM for install and I only have 128) and I could not update with Synaptic, only the update manager. I was having trouble with Synaptic (it would try and force me to insert the edgy cd) and I installed all posibble updates via the update manager, and shutdown. I resatarted to the following message:

"Server Authorization Directory (daemon/ServAuthDir) is set to /var/lib/gdm but is not owned by user root and group gdm. Please correct ownership or GDM configuration and restart GDM."


and I have no clue what to do. I am a complete noob, so if anyone answers, please be detailed. Thank you.

---

### Post by Muzik83 on 2007-02-23
If that error message is correct, then you need to make the /var/lib/gdm look like this when you do an ls -l
drwxrwx--T   2 root gdm     4096 2007-02-17 17:43 gdm

if the drwxrwx is wrong, type
sudo chmod 1770 /var/lib/gdm

if the root is wrong, type 
sudo chown root /var/lib/gdm

if the gdm (next to root) is wrong, type
sudo chgrp gdm /var/lib/gdm

The next is the size and modified date, they may be different

if you dont have a gdm folder... you could try making it but its probably a bigger problem
sudo mkdir /var/lib/gdm
then follow the above steps to make it the right permissions, owner and group.

To restart GDM (the last step according to the instructions) is
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
(you can also try /etc/init.d/gdm restart ...but i find that doesnt always work as expected)

Hope this helps
-sean

---

### Post by tawniteamo on 2007-02-23
> **Muzik83 said:**
> If that error message is correct, then you need to make the /var/lib/gdm look like this when you do an ls -l
drwxrwx--T   2 root gdm     4096 2007-02-17 17:43 gdm

if the drwxrwx is wrong, type
sudo chmod 1770 /var/lib/gdm

if the root is wrong, type 
sudo chown root /var/lib/gdm

if the gdm (next to root) is wrong, type
sudo chgrp gdm /var/lib/gdm

The next is the size and modified date, they may be different

if you dont have a gdm folder... you could try making it but its probably a bigger problem
sudo mkdir /var/lib/gdm
then follow the above steps to make it the right permissions, owner and group.

To restart GDM (the last step according to the instructions) is
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
(you can also try /etc/init.d/gdm restart ...but i find that doesnt always work as expected)

Hope this helps
-sean




I am a complete noob and this is one of my first problems with linux. I am nowhere near understanding what to do.

---

### Post by Muzik83 on 2007-02-24
Hey, here are some exact instructions on what to do:
Type ctrl+alt+f1 to get to a terminal ... this wont be as scary as it sounds!
Log in with your username and password in text mode.  You should end up with a prompt yoruser@yourhost:~$
type sudo -i
type chown root:gdm /var/lib/gdm
type chmod 1770 /var/lib/gdm
type /etc/init.d/gdm stop
type /etc/init.d/gdm start

You should see your GUI now (hopefully)

---

### Post by tawniteamo on 2007-02-24
when I enter my login and password ( I know it pretty well since I use the same for almost everything) it gives me the following error message:

-bash: /dev/null : Permision denied

---

### Post by tawniteamo on 2007-02-24
oh, and when it is starting up, it gives me the boot screen and if I press ctrl+alt+del it boots multiple times faster

---

### Post by jerrykenny on 2007-02-24
Tawnit,

re your last post . . . 

the boot process is being delayed by an overfancy splash-screen.

To disable this . . . . once you have logged on, . . . . have you ? . . .. type in a terminal

sudo gedit /boot/grub/menu.lst


look at the entries in the automatic-list thingy . . . 

remove the word SPLASH

---

### Post by tawniteamo on 2007-02-24
> **tawniteamo said:**
> when I enter my login and password ( I know it pretty well since I use the same for almost everything) it gives me the following error message:

-bash: /dev/null : Permision denied

no, I cannot get into terminal.

---

### Post by az on 2007-02-24
> **tawniteamo said:**
> when I enter my login and password ( I know it pretty well since I use the same for almost everything) it gives me the following error message:

-bash: /dev/null : Permision denied

Your system is borked.  Start again from the beginning.  Something went wrong, it may be hardware related, but your system is not normal.  From the start, you should not have to much around with permissions for GDM by hand.  Something is therefore wrong.

---

### Post by tawniteamo on 2007-02-25
similar things have happened both times I installed with the alternate install, does this mean I should just give in and get the neccesary ram for ther desktop install?

---

### Post by az on 2007-02-25
Does the cd pass the integrity check?  Check your hard drive for bad sectors and test all your ram.  Use badblocks and memtest86.

sudo badblocks -s /dev/hda1

and you run memtest from the cd, or the installed system (from the grub menu).

---

### Post by tawniteamo on 2007-02-28
I've reinstalled at least four times and every time I do it the same way yet I get different results. Sometimes it is grub error 18, sometimes it works normally until I download ANYTHING from the web, and sometimes it will get past the loading screen and it gives me command line with no GUI, but when I log in it says:
            bash: /dev/null : Permision denied
all down the screen. I will run those tests now Az.

---

### Post by tawniteamo on 2007-02-28
um... I can't seem to run badblocks, I guess I'm entering it in the wrong spot or sumthing, and memtest comes back fine. do you believe it would solve the problem if I switched drives? I have several small spare drives to test with. and I also get the erro acpi cannot find rsdp

---

### Post by MockY on 2007-03-12
> **Muzik83 said:**
> If that error message is correct, then you need to make the /var/lib/gdm look like this when you do an ls -l
drwxrwx--T   2 root gdm     4096 2007-02-17 17:43 gdm

if the drwxrwx is wrong, type
sudo chmod 1770 /var/lib/gdm

if the root is wrong, type 
sudo chown root /var/lib/gdm

if the gdm (next to root) is wrong, type
sudo chgrp gdm /var/lib/gdm

The next is the size and modified date, they may be different

if you dont have a gdm folder... you could try making it but its probably a bigger problem
sudo mkdir /var/lib/gdm
then follow the above steps to make it the right permissions, owner and group.

To restart GDM (the last step according to the instructions) is
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
(you can also try /etc/init.d/gdm restart ...but i find that doesnt always work as expected)

Hope this helps
-sean

I have tried everything that it says, over and over again but I still get this messgae:
> 
Server Authorization directory (daemon/ServAuthDir) is set to /var/lib/gdm but this does not exit. please correct gdm configuration and restart GDM


It simply doesn't make sense. Have any other ideas?

---

### Post by MockY on 2007-03-12
I can boot by typing startx, but I get various error messages and all the text is in squares. I can surf and everything is displayed just fine in the browser, but everything in the OS is displayed with squares.  I have tried to reinstall gdm but it does not fix the problem.

Please, I can't be the only one with this error.

EDIT:

I solved it by running

```

sudo chmod 4755 /var

```

---

