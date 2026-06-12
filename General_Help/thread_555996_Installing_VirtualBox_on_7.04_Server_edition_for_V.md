---
title: "Installing VirtualBox on 7.04 Server edition for VRDP use"
date: 2007-09-20
forum: General Help
---

### Post by Jose Catre-Vandis on 2007-09-20
Aim: to install a command line system, using the 7.04 server edition, and then to install Virtualbox on it, so that I can run VMs using VRDP and access them remotely using rdesktop on client machines.

PART I
Installing the 7.04 server edition is easy, so I'll skip that.

PART II
Installing VirtualBox is much more difficult, but I got it done in the end as follows. But what I want to know is if there is a better way to do this, e.g. install a desktop 7.04 and strip it back, or reduce all the items I had to install. Not had a chance to do extensive testing on all the variations.

If you are running a headless server, login via ssh (you may need to install openssh-server after the initial install), if not work from the command line at the PC

first off, install lots of kernel/sources stuff
###install needed linux components

```
sudo apt-get install linux-source
sudo apt-get install make gcc build-essential
sudo apt-get install xen-headers #[choose the version you need, in this case - 2.6.19-4-server]
sudo apt-get install xen-headers-2.6.19-4-server
sudo apt-get install linux-headers-$(uname -r)
```

#Bridging Utilities
If you are planning on bridging your network interface, install these two packages as well
[sudo apt-get install bridge-utils
sudo apt-get install uml-utilities[/code]


###install virtualbox (may fail at this stage)

```
sudo nano /etc/apt/sources.list #[add vbox repository]
deb http://www.virtualbox.org/debian feisty non-free #[add this line and save file]
wget http://virtualbox.org/debian/innotek.asc
sudo apt-key add innotek.asc
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install virtualbox

(you will be asked to install loads of dependencies as well)

###Picked this section up from virtualbox.org forums, as applied to Debian Etch - credits "Ingo"
(on a second attempt at this with a fresh server install, I did not need any of this section)

cd /usr/src
sudo adduser tim src
sudo tar -xvjf linux-source-2.6.20.tar.bz2
sudo ln -s linux-source-2.6.20 linux
sudo cp /boot/config-$(uname -r) linux/.config
cd linux
sudo make oldconfig
sudo make vmlinux
sudo make oldconfig && make prepare (optional?) if above doesn't work!
```

#####retry setup of virtualbox if necessary

```
sudo /etc/init.d/vboxdrv setup

you may need to try compile again if it doesn't work first time (credits bohdi zazen :))
```

and it should successfully compile and load vboxdrv.

You then need to add your username to vboxusers (you should have got a warning) :

```
sudo adduser username vboxusers
```

I also added myself to the uml-net group in the same way, due to my tap interface setup. You shouldn't need to do this if you are simply using NAT
(If you haven't installed uml-utilities this group won't be there :))
```
sudo adduser username uml-net
```

###Logout and login again (to make the new group assignments work)

and with any luck Virtualbox is installed and running. You can then install a VM from the command line, start it up, and access the VM remotely. I did a clone of an existing VM and copied it over to the server, to save time and make life easier.

PART III
Installing a VM in a headless server on the command line

(Credits to Virtualbox help for some of this!)
We'll use Windows XP as the example VM

On the headless server create the following directories:
```
sudo mkdir ~/.VirtualBox

(if not already there)
```
```
sudo mkdir ~/.VirtualBox/VDI
```

Then copy your WinXP.vdi file over

```
cp /path/to/your/vdi/WinXP.vdi ~/.Virtualbox/VDI
```

On the headless server/at the command line, create a new virtual machine:
```
VBoxManage createvm -name "Windows XP" -register
```
Create the settings (read the help file if you want alternatives)
```
VBoxManage modifyvm "Windows XP" -memory "256MB"-acpi on -boot1 dvd -nic1 nat
```

Use this as well if you are using host interface, you will need to replace "tap1" with the name of your interface!
```
VBoxManage modifyvm "Windows XP" -nic1 hostif
VBoxManage modifyvm "Windows XP" -hostifdev1 tap1 
```

Add your VDI file as the first virtual hard disk of the new VM:
```
VBoxManage modifyvm "Windows XP" -hda "WinXP.vdi"
```

[COLOR="Sienna"][INSERT][/COLOR]
#########################################################
If you need to create a new vdi and carry out an OS installation, follow these steps instead of just copying a vdi file over from somewhere else:

Create a virtual hard disk for the VM (in this case, 10GB in size) and register it with VirtualBox:
```
VBoxManage createvdi -filename "Windows XP.vdi" -size 10000 -register
```
Set this newly created VDI file as the first virtual hard disk of the new VM:
```
VBoxManage modifyvm "Windows XP" -hda "Windows XP.vdi"
```
Register the ISO file that contains the operating system installation that you want to install later:
```
VBoxManage registerimage dvd /full/path/to/iso.iso
```
Attach this ISO to the virtual machine, so it can boot from it:
```
VBoxManage modifyvm "Windows XP" -dvd /full/path/to/iso.iso
```

I found I got double mouse problems during the installation, but you can get by through moving the "mice" around so that you can click in the right places!

Installing VBox Additions is a bit of a fiddle this way, but if you register the iso in the same way as for the OS iso above, and then attach it you should be good to go, but you will have to browse to the iso and run the executable. The additions iso should be found here: /usr/share/virtualbox/

#############################################
[COLOR="Sienna"][END OF INSERT][/COLOR]

Start the virtual machine using VBoxVRDP:
```
VBoxVRDP -startvm "Windows XP"
```
If everything worked, you should see a copyright notice. If, instead, you are returned to the command line, then something went wrong.
On the client machine, fire up the RDP viewer and try to connect to the server. Assuming an Ubuntu client:
```
rdesktop -a 16 my.host.address
```

Advice is you should set your VM to run in 16m colours to match the rdesktop call

---

### Post by bodhi.zazen on 2007-09-28
This is an amazing How-to.

Do you mind if I link it to the UDSF VirtualBox wiki page : 

[http://doc.gwos.org/doku.php/doc:office:virtualbox](http://doc.gwos.org/doku.php/doc:office:virtualbox)

---

### Post by Jose Catre-Vandis on 2007-09-29
> **bodhi.zazen said:**
> This is an amazing How-to.

Do you mind if I link it to the UDSF VirtualBox wiki page : 

[http://doc.gwos.org/doku.php/doc:office:virtualbox](http://doc.gwos.org/doku.php/doc:office:virtualbox)

Not at all :) Some credits do need to go to VirtualBox help file :)

---

### Post by Jose Catre-Vandis on 2008-03-03
Found a bit more to add to this that might help:

My howto requires a login via ssh to run the headless VMs, if you try to logout it kills the VMs. We need a way of starting up the VM and then leaving the ssh session. There is another thread on the forum that shows how to start a VM at boot, wihout logging in, but it is way to complicated for me! This way requires a simple ssh command and off you go. For example:
> ssh remoteHost 'VBoxVRDP -startvm "Windows XP Pro" >~/.VirtualBox/Machines/"Windows XP Pro"/Logs/VBoxVRDP.log 2>&1 &'

where 

"remotehost" is the name of your host server
"Windows XP Pro" is the name of your VM
"~/.VirtualBox/Machines/"Windows XP Pro"/Logs/" is the path to your Logs directory for your VM

This works perfectly, and you can still login and out to the host server via ssh without disturbing the VM

credits to Ingo on the VirtualBox forum (he knows everything!)  :)

[EDIT] A few more tips when using rdesktop:

You can use the following to launch your VM in full screen
```
rdesktop -fa 16 my.host.address
```
and to get out of full screen
```
CTRL+ALT+ENTER
```
If you want a windowed vm but without the windows decorations (with the right resolution still looks like full screen :))
```
rdesktop -Da 16 my.host.address
```
If you are using a Windows OS that requires CTRL+ALT+DELETE to logon, you first need to click in the rdesktop window to give it focus, then I have found that using the combination
```
CTRL+ALT+DEL   or    ALT+RIGHTCTRL+DEL
``` works through rdesktop

[EDIT]
More findings:

I have an X server installed on my server, even though I rarely use it. I used the server edition and installed xcfe on top for occasions when I might need a gui. This I believe allows me to ssh -X into the server and run graphical programs on my client PC, so I can run the VirtualBox graphical front end in order to edit virtual machines. What to do:

First login to the server via a terminal with the X argument:
```
 ssh -X username@servername
```
Enter password
then type in the terminal
```
VirtualBox
```
You should get the VBox graphical interface up on your desktop, showing all your virtual machines and this allows you to amend settings via gui.

What I do not know is whether this will work without X and and a gui installed on a server

---

