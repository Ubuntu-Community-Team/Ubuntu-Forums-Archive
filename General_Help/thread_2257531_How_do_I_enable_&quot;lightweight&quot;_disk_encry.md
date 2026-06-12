---
title: "How do I enable &quot;lightweight&quot; disk encryption password screen permanently?"
date: 2014-12-20
forum: General Help
---

### Post by m4x2 on 2014-12-20
Hey,

I finally managed to install Lubuntu 14.10 on an old PC of mine.
Now I have another problem:
 I encrypted my whole hard drive and there are 2 different password screens at system startup.
I am getting the first one if I just boot my PC normally, its a graphical more complicated one in comparison to the other. But I am not able to enter the password at this screen (already tried different kinds of keyboards - also PC/2 keyboards).
If I get to that screen and just turn off the pc and start it again, I'm getting to the GRUB Bootloader screen.
After choosing "Ubuntu" there, I get to a graphical lightweight screen where I'm finally able to enter the password.

So my question: How do I enable this lightweight screen permanently?

regards

---

### Post by sudodus on 2014-12-20
Did you install encrypted disk and encrypted home? In that case you should have two barriers, and the passwords are separate. You enter a passphrase to the first barrier (encrypted disk) and a password (like in normal unencrypted systems) to log in and at the same time open the encrypted home.

During installation [I think] you were prompted to enter a password (for login) and later on a passphrase (for the encrypted disk) according to this link (instructions for testing, but also good for regular usage:

[http://iso.qa.ubuntu.com/qatracker/milestones/325/builds/82591/testcases/1439/results](http://iso.qa.ubuntu.com/qatracker/milestones/325/builds/82591/testcases/1439/results)

```
Boot up the image
    System boots to 'Select Language'
Select Install Ubuntu and press Enter
    System displays 'Select Location'
Select location and press Enter
    The default for your location and language should already be selected.
Select the layout you wish to use on the keyboard and press Enter
    The default for your location and language should already be selected.
Add a hostname for the machine and press Enter
    You should be prompted for your name
Type in your name and press Enter
    You should be prompted for a user name
Type in your user name and press Enter (you can accept the default if you wish).
    You should be prompted to enter a password
[COLOR=#ff0000] * Add a password and press Enter[/COLOR]
    You should be prompted to confirm ( If you entered a weak password, confirm that you want to keep it or select no and enter a stronger one).
Confirm password and press Enter
    You should be asked if you wish to encrypt your home directory
Select Yes for encrypted home directory and press Enter
    You should see confirmation of your time zone
Verify that the pre-selected time zone is correct or select your time zone and press Enter
    You will be presented with formatting options
Select Guided - use entire disk and set up encrypted LVM and press Enter
    You should see an option to select a disk to install on
Select the disk to use and press Enter
    You should be asked to confirm the action
Select Yes to accept the changes and press Enter
    You should be asked to enter an encryption passphraser
[COLOR=#ff0000] ** Enter an encryption passphrase and press Enter[/COLOR]
    You should be asked to confirm your passphrase
Confirm your encryption passphrase by entering it again and press Enter
    You should be asked to specify an amount of the volume group to use for guided partitioning
Specify an amount of the volume group to use for guided partitioning and press Enter
    You should see a request to confirm writing the changes to disk
Select Yes to accept the changes and press Enter
    You should see a request for http proxy information
Input http proxy info or press Enter
    Wait for a while - The install may seem like it has locked at a percentage but is actually working in the background. You can check and see if it is working by switching to tty4 (alt + f4).
Select Yes to install grub boot loader to master boot record and press Enter
    You should see a request to confirm date and time
Select Yes to setting your clock to utc and press Enter
    You should be requested to remove the CD / USB key
Remove the CD / USB key and press Enter
    This should then reboot the machine
Log in and check the desktop is installed
    You should be able to log in and the desktop should be displayed
Ask the machine to reboot
    Machine should reboot
Login and check the system installed correctly
    Menus should be displayed 
```

---

### Post by m4x2 on 2014-12-21
I installed encrypted disk and encrypted home.
But it seems that there are 2 different screens for password entrance of DISK decryption.
The graphical more heavy screen appears by default, I only get to the lightweight screen if I start Lubuntu via the GRUB bootloader.

regards

---

### Post by sudodus on 2014-12-21
Do you remember the passphrase which [s]might[/s] should be different from the log in password?

---

### Post by sudodus on 2014-12-21
Maybe you can take photos of the screen with each of the interfaces, make a reply here, 'go advanced', and add the pictures as attachments to the reply.

---

### Post by m4x2 on 2014-12-21
Okay here are the pictures:

Mid: Graphical more heavy screen which appears by default in "normal" boot:
Left: After a restart i'm getting to the GRUB bootloader where I choose Ubuntu
Right: Lightweight password interface where I'm able to enter the Password

[ATTACH=CONFIG]258714[/ATTACH][ATTACH=CONFIG]258715[/ATTACH][ATTACH=CONFIG]258716[/ATTACH]

And yes, of course I know the passphrase ... ;D

regards

---

### Post by sudodus on 2014-12-21
You are right, both of those two interfaces belong to the encrypted disk. I have been iso-testing 'Lubuntu encrypted disk' several times, and the 'Mid: Graphical more heavy screen which appears by default in "normal" boot' is what I get, and it works for me. Are you uisng some German letter (in the passphrase), that is not in the standard ASCII table, and that it is rendered differently in the two interfaces, for example [SIZE=3]**üäö**[/SIZE]?

---

### Post by m4x2 on 2014-12-21
Im not able to enter the password at the graphical more heavy screen. I already tried several keyboards.
On the other hand, if I try to enter the password on more lightweight screen it works.
I just want the lightweight screen to appear by default.

regards

---

### Post by sudodus on 2014-12-21
I'm slowly understanding one more bit each time :-P

It seems that you have different screen graphics in the two instances, and there might be a problem with the screen settings with the 'more heavy screen'. Maybe you can try to change the graphics according to this link

[https://help.ubuntu.com/community/Grub2/Setup](https://help.ubuntu.com/community/Grub2/Setup)

Edit the file /etc/default/grub

```
sudo nano /etc/default/grub
```

> [I][B]
#GRUB_TERMINAL=console[/B][/I] 


[LIST]
[*]Uncomment  to disable graphical terminal. This may provide help if the GRUB 2 menu  is too large or unreadable. It also may help when using the  GRUB_HIDDEN_TIMEOUT feature. 
[/LIST]

so make it

```
GRUB_TERMINAL=console
```

run ```
sudo update-grub
``` and reboot

---

### Post by m4x2 on 2014-12-21
That worked perfectly, thanks for your help! ;)

regards

---

### Post by sudodus on 2014-12-21
Congratulations :KS

I'm glad that I could help you.

---

