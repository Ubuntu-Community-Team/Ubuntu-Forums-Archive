---
title: "vmware server requires root"
date: 2007-01-10
forum: General Help
---

### Post by rpkehoe on 2007-01-10
In order to setup vmware to directly access a partition, I ran vmware as root (sudo) and now I very much wish that I hadn't.  After running at the command line, I realized that root had claimed the config files, so I changed permissions back to my account.  This got me back into vmware, but when I go to open my existing vm, I get:

Unable to add virtual machine "/home/ryan/vmware/Windows XP Professional/Windows XP Professional.vmx" to the inventory: No permission to perform this operation

Ok, so root claimed the .vmx file, easy enough - sudo chown ryan /home/ryan right? Nope, same answer.   Run as root, everything is fine a good (except that it is running as root of course).  I have tried re-installing, this had no effect.

Any suggestions?

---

### Post by interurban on 2007-01-10
try this:

```
chown -r ryan [filename or directory]
```the -r includes files in subdirectories as well

---

### Post by rpkehoe on 2007-01-11
Sorry, I left the switch out of my code, I actually did run it with -R.

---

### Post by cephlon on 2007-02-10
hey, I'm getting the same error on a new Virtual Machine of mine. 

Unable to add virtual machine "/home/cephlon/VM Machines/Windows XP Professional/Windows XP Professional.vmx" to the inventory: No permission to perform this operation

Did you ever find a solution?

---

### Post by ayubmalik on 2007-02-21
Hello there,

I got the same error when I initially installed VMware. I think installed it as sudo by mistake when I installed XP. If I did not run it as sudo I got the following error..."

Unable to add virtual machine ... to the inventory: No permission to perform this operation


Heres the workaround I got to running vmware without having to run as sudo/root.

[LIST=1]
[*]Run [FONT="Courier New"]vmware[/FONT] as sudo from terminal i.e type  [FONT="Courier New"] **sudo vmware** [/FONT]
[*]Connect to your VM e.g. Local Host
[*]Open the virtual machine you would to run as normal user e.g "Windows XP Home"  (on my pc)
[*]Click "Edit virtual machine settings". A settings window should appear
[*]Click on the "Options" tab at the top
[*]On the "Permissions" option, uncheck "Make this virtual machine private"
[*]Click "OK" and exit [FONT="Courier New"]vmware[/FONT]
[*]type the following command  [FONT="Courier New"]**cd ~/.vmware**[/FONT] and press enter
[*]type the following command [FONT="Courier New"]**sudo chown  user:user ***[/FONT] (where user is **your** login name)
[*]now start [FONT="Courier New"]**vmware **[/FONT]and you should be able to run the VM
[/LIST]

Hope this helps!

Ayub

---

### Post by keinhaar on 2007-03-17
Just wanted to say, that the previous solution worked perfectly for me. thanks!

---

### Post by djieno on 2007-03-27
I had this error too and the solution didn't work since i had to change the owner and access rights for the vm by:

sudo chown -R [user] [/path/vm]
sudo chmod 755 [/path/vm]

And this worked nicely. 

Bud now I cannot open the vmware console anymore as a user from [application][system tools][vmware server console]. I assume this has to do 'step 9)type the following command sudo chown user:user * (where user is your login name)'. I CAN open this as root:

sudo vmware

Question: How do i change it back so I can start it as a user instead of 'root'? :confused: 

I tried installing the vmware console again, didn't work. Uninstalling vmware server and installing also without luck.

---

### Post by djieno on 2007-04-04
I solved it by:

user=djieno ;-)

(use sudo if you need to)

root@tafelpc:/# *chmod 777 /home/djieno/.vmware/preferences*
root@tafelpc:/# *chmod 777 /home/djieno/.vmware/favorites.vmls*

/home/djieno/.vmware/preferences                    [owned by user djieno]
/home/djieno/.vmware/favorites.vmls                 [owned by user root] 

I had still good results with 644 rights:

*root@tafelpc:/# chmod 644 /home/djieno/.vmware/preferences*         
*root@tafelpc:/# chmod 644 /home/djieno/.vmware/favorites.vmls*      

If you have to change ownership:

*chown djieno /home/djieno/.vmware/preferences*

Greetings Djie

---

### Post by JLAudioFan on 2007-04-25
> **ayubmalik said:**
> Hello there,

I got the same error when I initially installed VMware. I think installed it as sudo by mistake when I installed XP. If I did not run it as sudo I got the following error..."

Unable to add virtual machine ... to the inventory: No permission to perform this operation


Heres the workaround I got to running vmware without having to run as sudo/root.

[LIST=1]
[*]Run [FONT="Courier New"]vmware[/FONT] as sudo from terminal i.e type  [FONT="Courier New"] **sudo vmware** [/FONT]
[*]Connect to your VM e.g. Local Host
[*]Open the virtual machine you would to run as normal user e.g "Windows XP Home"  (on my pc)
[*]Click "Edit virtual machine settings". A settings window should appear
[*]Click on the "Options" tab at the top
[*]On the "Permissions" option, uncheck "Make this virtual machine private"
[*]Click "OK" and exit [FONT="Courier New"]vmware[/FONT]
[*]type the following command  [FONT="Courier New"]**cd ~/.vmware**[/FONT] and press enter
[*]type the following command [FONT="Courier New"]**sudo chown  user:user ***[/FONT] (where user is **your** login name)
[*]now start [FONT="Courier New"]**vmware **[/FONT]and you should be able to run the VM
[/LIST]

Hope this helps!

Ayub

Thanks Ayub, that worked like a charm!!

---

### Post by okhascorpio on 2007-04-28
didn't work for me :(  , actually i been messing arround changing ownerships and permissions

/usr/bin/vmware
/usr/lib/vmware/
/var/lib/vmware/
/home/user/.vmware/
etc.etc.etc. :shock: 

and now i totally lost the idea of which file should have root and which should user access.. :-( 

also lost system tools menue icon for the vmware,  ](*,)  
i hate openning terminal and typing "sudo vmware"
Pleeeeezzzz...someone help me out...

---

### Post by okhascorpio on 2007-04-28
I hope there be a magical "revert" button, to set everything to default. :biggrin:

---

### Post by vandorss on 2007-10-19
This occurs when you have a VM with the same name and location already in /etc/vmware/vm-list and/or vm-list-private.

In my case I had created and deleted (using rm-rf) several virtual machines.

When some time later I re-used the same name this error popped up.

The way I got around this:

Stop vmware. Then:

cd /etc/vmware
sudo vi vm-list
(delete the lines for VMs that no longer exist in /var/lib/vmware/Virtual Machines
(save)

Do the same for vm-list-private.

Start vmware and try opening the VM again. Should work now,

Rgds,
Ralf

---

