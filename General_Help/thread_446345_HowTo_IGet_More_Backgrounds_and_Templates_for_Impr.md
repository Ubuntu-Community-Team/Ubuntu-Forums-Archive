---
title: "HowTo IGet More Backgrounds and Templates for Impress."
date: 2007-05-16
forum: General Help
---

### Post by johnattahoe1233 on 2007-05-16
If you are like me, you probably want to use Ubuntu as much as possible, but you still had to boot into windows, use a slow third party solution (Crossover, VMWare), to use Powerpoint merely because of the amount of backgrounds offered due to OOImpress. Now, as I am sure many of you have heard before, that StarOffice also includes a lot of presentation backgrounds. This tutorial will show you how to make OpenOffice have all of StarOffice Impress's backgrounds and templates. 

Go to [http://www.sun.com/software/star/staroffice/get.jsp](http://www.sun.com/software/star/staroffice/get.jsp), and download the StarOffice 8 trial. 
Make sure to select Linux as your platform.


For some people the installer doesn't work. I am one of those people. Luckily, the command part still works.


Open a terminal window. 


Type "gksu gnome-terminal"


enter your password in the dialog box to start a root terminal. 


cd to the directory to where StarOffice8 trial installer was saved. Firefox saves to the desktop by default, so for most this would mean this command should be typed into the terminal. 

"cd /home/" + your_username_here + "/Desktop"


Type : "chmod a+x " and then the filename of the downloaded file into the terminal. 


Type : "sh " + the_downloaded+file

Go through the default options until the gui installer pops up. If the gui installer is a blank form don't worry. 
Exit it in any case.

Now, cd to this directory 
"cd /var/tmp/unpack_staroffice/RPMS"

Install alien if it is not installed already by typing

"apt-get install alien"

After alien is installed, type the following. 

"alien *.rpm" 

Then, type this in

"dpkg -i *.deb", and StarOffice8 trial will be installed. 

now, type in these commands

"cp /opt/staroffice8/share/template/en-US/presnt/* /usr/lib/openoffice/share/template/en-US/presnt"

if it asks you to overwrite files, tell it no by pressing n

"cp /opt/staroffice8/share/template/en-US/layout/* /usr/lib/openoffice/share/template/en-US/layout"

same as last step regarding overwriting files. 

Congratulations! You now have the full assortment of StarOffice8 Impress backgrounds
avalible to you.

---

