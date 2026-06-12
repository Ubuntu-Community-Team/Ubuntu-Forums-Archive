---
title: "how to edit Grub 2 in Ubuntu 12.10"
date: 2012-12-04
forum: General Help
---

### Post by oldtraveler on 2012-12-04
I would like to be able to edit options in Grub 2.  How?

---

### Post by GameX2 on 2012-12-04
The easy graphical way, install Grub-Customizer:

```
sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update
sudo apt-get install -y grub-customizer
```

---

### Post by dino99 on 2012-12-04
grub-customizer is not so stable :(  so try that genuine solution first:

```
sudo gedit /etc/default/grub
```

makes your tweak, then:

```
sudo update-grub
```

for more details, glance at the link below  :P

---

### Post by oldtraveler on 2012-12-04
Sorry, but I can't even find out how to open a terminal in Ubuntu 12.10

---

### Post by Mark Phelps on 2012-12-04
Click the Ubuntu symbol in the upper left.  That opens DASH.  Enter the word terminal --  and click the item that appears.

You can also go into the dash display window, open the Applications section and scroll down to the Terminal icon, and click that.

---

### Post by oldfred on 2012-12-04
Get a terminal by <ctrl_+alt+F1> & back to gui with ctrl alt f7
Also instructions on using Dash in Unity
[https://help.ubuntu.com/community/UsingTheTerminal/](https://help.ubuntu.com/community/UsingTheTerminal/)
In Ubuntu you start a terminal window with ctrl + alt + t
or via the menu Program -- Accessories -- Terminal

---

### Post by oldtraveler on 2012-12-04
This is crazy. Thanks to your help I got a terminal. When I tried a sudo it asked for my password.  When I tried to type my password, nothing happened. Confused.

---

### Post by GameX2 on 2012-12-04
That's normal, the password is just hidden for security.

Just type the password normally and confirm with Enter.
EDIT: I'm using Ubuntu since one year now, and I still have a bit of trouble with configuring GRUB manually from the files.  Wouldn't it be way easier to just use GRUB-Customizer for a begginner?  Just wondering.  Why is GRUB-Customizer not a good option / not stable?

---

### Post by oldfred on 2012-12-04
For most Grub Customizer is the better choice, but you still need to get to terminal to add the ppa then to install it.

If new it is best just to copy and paste commands from post to terminal, that way avoid typos as even spaces can be important.

Actually there are very few commands I know to type directly into terminal. Maybe something to do with the old in oldfred. :)

I look in my notes & copy & paste or use up arrow to see previous commands that it has saved.

---

### Post by uzumakifahim on 2012-12-04
> **dino99 said:**
> grub-customizer is not so stable :(  so try that genuine solution first:

```
sudo gedit /etc/default/grub
```makes your tweak, then:

```
sudo update-grub
```for more details, glance at the link below  :P

I've opened the file named "grub" from **etc/default** directory. Now I want to make my windows as default boot. How can I do that? I can't understand this file grub. Where to change and what to change?

---

### Post by oldfred on 2012-12-04
This is the old manual way, most now use grub customizer.

       [http://ubuntuforums.org/showthread.php?p=10720316](http://ubuntuforums.org/showthread.php?p=10720316)
    
You can use number or title in GRUB_DEFAULT=
Number count starts at 0, so whichever number it is in your menu will be the number to input.

Or you can use the exact title, best to copy.

       find your windows entry in grub.cfg and copy to grub default like this Vista entry - If you edit your windows command use the edited copy as this must match the title exactly:
gedit /boot/grub/grub.cfg
and copy into grub_default  here:
gksudo gedit /etc/default/grub
GRUB_DEFAULT=0
change to comment # or delete old and add new :
#GRUB_DEFAULT=0
GRUB_DEFAULT="Windows Vista (on /dev/sda1)"
Then do:

    sudo update-grub

---

