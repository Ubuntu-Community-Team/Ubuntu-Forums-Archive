---
title: "installing flash using terminal"
date: 2005-10-05
forum: General Help
---

### Post by squbuntu on 2005-10-05
i have downloaded flash 7 for linux, however in the readme it tells me to type in 
'- From the command line, type ./flashplayer-installer to run the installer.'

where can i find the command line to even type this in?

confused: 

thanks for any help :

---

### Post by Pettman on 2005-10-05
[QUOTE=squbuntu]i have downloaded flash 7 for linux, however in the readme it tells me to type in 
'- From the command line, type ./flashplayer-installer to run the installer.'
where can i find the command line to even type this in?
confused: 

thanks for any help :[/QUOTE]
I you just want flashplayer plug-in for mozilla it can be found in synaptic.

---

### Post by Hairy_Palms on 2005-10-05
just right click and select "open terminal" 
then u can get it by typing "sudo apt-get install flash-nonfree"
if u definately want to use the downloaded version then open a terminal and
then type "cd /home/whereverflashinstallerissaved"
then type ./flash-installer

---

### Post by az on 2005-10-05
[QUOTE=Hairy_Palms]just right click and select "open terminal" 
then u can get it by typing "sudo apt-get install flash-nonfree"[/QUOTE]


That is flashplugin-nonfree and it is in the universe repository.  It would be easier to install this package using synaptic.  You will need to enable the multiverse and universe repositories to do that.  Just click on "repositories"
Enable those two.  Update and the search for flashplugin-nonfree and install it....

---

### Post by sleeper414 on 2008-05-22
1.goto the adobe website and download the .tar to your desktop.

2. open the folder and double click on the installer

3. a window will give you an option to run it in terminal.choose that

4. follow the prompts in terminal. and you will be up and running in a few seconds!

worked for me!

---

