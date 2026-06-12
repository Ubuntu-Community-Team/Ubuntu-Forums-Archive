---
title: "vmtools wont install :("
date: 2006-07-17
forum: General Help
---

### Post by jn1167 on 2006-07-17
Ive looked around a little but couldnt really find what I needed.  I just installed Ubuntu using vmware and i cnt figure out exactlly how to install vmtools.

I have been messing with it for a while now and figured i would just go for it and ask you people how I can get this done without ripping my eyeball out of the socket ;)

I tried a few different things but still havent got it working.  Now it says that there is a previous version of vmtools installed.

Can one of you people get me going?  This is my first real poke a linux so Im sort of a noob.

Thanks :)

---

### Post by Doctor DEA on 2006-09-16
Iv'e just reached this part and am facing the same issue...

Now it looks like its up to us two, to figure this out and post the answers for others that may face this same issue in the future.  :D

---

### Post by kuja on 2006-09-17
So, you're using vmware server then I presume?
Does the menu thing VM -> Install VMWare tools not work?

I just took a look through the vmware manual, and came across this in the Ubuntu 6.06 section:

> 
VMware Tools
Be sure to install VMware Tools in your guest operating system. For details, see the manual for your VMware 
product or follow the appropriate link in the knowledge base article at 
[www.vmware.com/support/kb/enduser/std_adp.php?p_faqid=340](www.vmware.com/support/kb/enduser/std_adp.php?p_faqid=340).
NOTE     You must use the tar installer to install VMware Tools in Ubuntu Linux.


I'm not 100% sure what that means, but perhaps the two of you should look into it.

---

### Post by PriceChild on 2006-09-17
Taken from [http://pubs.vmware.com/vi3/bsa/BSA_Creating_VMs.12.7.html](http://pubs.vmware.com/vi3/bsa/BSA_Creating_VMs.12.7.html)

>  
         [FONT=Arial]**To install or upgrade VMware Tools**[/FONT]       
                                                       1    
                                         From VirtualCenter, power on the virtual machine.
                                        
                                                       2    
                                         When the guest operating system starts, choose Virtual Machines > Install VMware Tools.
                                        
                                                       3    
                                                          From inside the virtual machine, click Yes to launch the InstallShield Wizard.
                                        
                                                       •
                                         If you have autorun enabled in your guest operating system (the default setting for Windows operating systems), a dialog box appears.
                                        
                                                       •
                                         If autorun is not enabled, run the VMware Tools installer. Click Start > Run and enter D:\setup.exe, where D: is your first virtual CD-ROM drive.
                                        
                                                       4    
                                         Follow the onscreen instructions. 
                                        
                                                       •
                                         On Windows Server 2003, the SVGA driver is installed automatically, and the guest operating system uses it after it reboots. 
                                        
                                                       •
                                         After you install VMware Tools, Windows 2000 and Windows XP guest operating systems must be rebooted to use the new driver.


These instructions seem to be taylored to a windows client... however i'll bet that the first couple of steps will help you, the rest being obvious.

---

### Post by David Corrales on 2006-09-17
If you're installing VMTools for linux, you'll need to install the compiler and linux-headers inside your Ubuntu guest.

---

### Post by dstaudt on 2006-09-17
I think if the directory '/usr/lib/vmware-tools' exists, the installer balks.  Might try deleting this directory.

Note, the vmware-config-tools.pl script that comes with VMWare Workstation 5 seems to be obsolete as far as later Ubuntu versions (Dapper and Edgy) and will fail to compile the VMWare tools.  I believe you can obtain an updated script from VMWare (if you have proper support.)  The latest VMWare server script works fine.

The general steps are:

- In Synaptic, install 'build-essential' and 'linux-headers-<architecture>' i.e. 'linux-headers-386'

- From the VMWare 'VM' menu, select 'Install VMWare tools...'.  This will cause a virtual CD to auto-mount.  Note, usually the first time it does this, for me the contents of the mount are unreadable/usuable, and I have to Eject, and 'Stop installing VMWare tools' and re-do 'Install VMware tools...'

- Browse the virtual CD and open the tar.gz version of the VMWare installation stuff

- Extract  the 'vmware-tools-distrib' folder somewhere (like the Desktop)

- From the terminal, change into the vmware-tools-distrib directory and run 'sudo ./vmware-install.pl' Follow the prompts, the defaults are generally what you want.

- If everything works fine, you can run 'vmware-toolbox'.  Note this has to be running at all times for the VMWare tools functionality like mouse-grab/ungrab, so you may want to add the command to your Sessions startup list.

Upgrades that include a new kernel will likely require you to re-run vmware-config-tools.pl before the Tools will work, which will require that the new kernel headers be present.

---

### Post by AndyCooll on 2006-09-17
From my experience VMware Tools only installs if the image has a recognised CD-drive as part of its configuration. If it doesn't, you'll need to add one.

:cool:

---

### Post by sped44 on 2006-10-05
I was just able to get this working. Here is how I did it. Running Kunbuntu 6.06 with VMware Workstation 5.0.0.

$uname -a
This told me my kernel was 2.6.15-27-686

$sudo -s
#aptitude install gcc make linux-source-2.6.15 linux-headers-2.6.15-27-686

From the VMware menu, select VM->Install VMware Tools. This will put a CD icon on your desktop. Copy the VMwareTools-5.0.0-13124.tar.gz to your desktop. From command line run

#cd ~/Desktop
#tar -zxvf VMwareTools-5.0.0-13124.tar.gz
#cd vmware-tools-distrib

At this point you should read the README file in the doc dir. After that run

#~/Desktop/vmware-tools-distrib/vmware-install.pl

Keep hitting enter to accept the defaults. At some point it will ask if you want to complile the vmhgfs module. Hit enter to select the yes default. This is where you need to have make, gcc and the kernel headers installed from above. I don't think you need the kernel source or not but I had it and it worked. If you did things properly you should be able to accept all the defaults and it should go off without a hitch. At the end it will tell you whether is was sucessfull or not. You'll have to restart X and you can run the following command to get the vmxnet nic module working:

#/etc/init.d/network stop
#rmmod pcnet32
#rmmod vmxnet
#depmod -a
#modprobe vmxnet
#/etc/init.d/network start

You should now be able to run:
#vmware-toolbox
A GUI will pop up and you can set some options.

---

