---
title: "Add Script before safely remove usb drive"
date: 2007-07-02
forum: General Help
---

### Post by rushrtb2112 on 2007-07-02
I would like to run a script when i click on "Safely Remove" of a removable drive.  Is this possible to do, and if so, is there any documentation on how to do this?

---

### Post by bmorency on 2007-07-02
> **rushrtb2112 said:**
> I would like to run a script when i click on "Safely Remove" of a removable drive.  Is this possible to do, and if so, is there any documentation on how to do this?

What kind of script  do you need to run before removing it?

you can probably just run your script and then open the terminal and type "sudo umount /dev/sda" or the drive could be mounted as another device.

---

### Post by rushrtb2112 on 2007-07-02
I run truecrypt on a usb key and i wanted to hook into  the gui of ubuntu's safely remove so that if someone else is using the machine or i forget that i have the truecrypt volume is mounted it will disconnect that before unmounting the key.

---

### Post by BlackAnthrax on 2007-07-02
I use a lot of scripting to automate tasks like this. What I would do is create a script that looked like this:

truecrypt -d /path/to/truecryptvolume
umount /dev/whateveryourusbdriveisrighthere

you would have to run it as root, such as opening terminal, typing sudo bash /path/to/script

you should create a .scripts in your home dir

you could name the script "truecryptumount"

so unmounting it would look like

sudo bash /home/yourname/.scripts/truecryptumount.sh

It will require some fooling around, but it should bring the process down to several seconds

---

### Post by rushrtb2112 on 2007-07-02
I knew I could do it through the terminal but i didn't know if there was a way to listen for the events of the OS to see when the "Saftely Remove" action was clicked.  Thanks for the help everyone.

---

