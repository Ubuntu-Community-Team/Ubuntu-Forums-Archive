---
title: "How to install Nvidia cards"
date: 2008-04-30
forum: General Help
---

### Post by theboris on 2008-04-30
I spent about a year trying to get the desktop effects working with an Nvidia card. and i ran into alot of trouble!but i did it and heres how...
=============================================================================
                        HOW TO INSTALL NVIDIA CARDS
=============================================================================
ubuntu 8.04 is out now and it has added alot of drivers so try that first...
-----------------------------------------------------------------------------
-----------------------------------------------------------------------------
1/ Alot of people use envy ( which works very well on a new install ) // i tried envy when i had ubuntu intalled for about a month and it didnt work but i re-installed and did it straight away and effects were working away!//

you can get envy by searching "envy" on google.
-----------------------------------------------------------------------------
-----------------------------------------------------------------------------
2/ try searching "nvidia" in the add/remove programs or package manager... there cud be something on the new drivers.( also hardware drivers ) 

to get to the add/remove click |applications| then |add/remove|

to get to package manager click |system| |administrator| |synaptic package manager| 
-----------------------------------------------------------------------------
-----------------------------------------------------------------------------
3/ try doing a search for the nvidia driver download ( make sure its for linux ) save it to the desktop and then press |ctrl| |alt| |f2| this will bring u to a login without x running. log in and then browse to the file u downloaded( desktop ) and run it by something like sudo "filename"
-----------------------------------------------------------------------------
-----------------------------------------------------------------------------

there hope it works... and if anyone has more ways please comment them!


theboris

=============================================================================
                                  THE END 
=============================================================================

---

### Post by Zorael on 2008-04-30
A few pointers. :>
[list][*]Envy is now included in the repositories, package name **envyng**. You don't need to search for nvidia packages in Synaptic if you used it.
[*]To set up your /etc/X11/xorg.conf file to work with Compiz, first make a backup of it, then enter the following in a terminal.
```
$ sudo nvidia-xconfig -d 24 --allow-glx-with-composite --add-argb-glx-visuals --randr-rotation
```
[*]Restart your computer after having installed new drivers. But if you only make modifications to the above mentioned xorg.conf file, you can just restart X (Ctrl+Alt+Backspace) to apply the changes.[/list]

---

### Post by lswest on 2008-04-30
also, when you install the drivers(via option #3), you probably have to run ```
sudo /etc/init.d/gdm stop
``` from the tty1 screen (after the ctrl + alt + F2)to kill the Xserver, otherwise the install will fail.

---

