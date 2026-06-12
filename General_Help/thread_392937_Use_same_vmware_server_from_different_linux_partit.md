---
title: "Use same vmware server from different linux partitions"
date: 2007-03-25
forum: General Help
---

### Post by jmvidalvia on 2007-03-25
I have 4 partitions: XP, Kubuntu Dapper, Ubuntu Edgy and Xubuntu Edgy (my prefered)
I use Ubuntu partition for testing: I installed there VMWare Server, and shared a folder with Samba.
Now I realize how convinient it is, so I don't need to reboot any more if I need to use XP applications.
But I feel lazy to install again the XP virtual machine under Xubuntu, my main system.
¿do you thing I can use the XP Virtual Machine I already have in Ubuntu from the Xubuntu partition?
Obviously that partition is already mounted in /media/
Thanks a lot!

---

### Post by scxtt on 2007-03-25
sure you can, i have all my VMs on a different hard drive alltogether ...

---

### Post by jmvidalvia on 2007-03-25
It works great!
Thank-you
Last time with so many partitions: form now, my main Xubuntu and VMware with everything, included XP for Office (I'm sorry...:( )

---

### Post by jmvidalvia on 2007-03-27
Now everything is working I have a different problem: I run out of free space in the partition where I saved the .vmx file with my XP, so if I want to move the system from here to a different partition, ¿what should I move?
Just .vmx file?
All /var/lib/VirtualMachines folder?
Thanks a lot!

---

### Post by scxtt on 2007-03-27
if you have a directory that contains all your VMs (like /home/vmware) and you have multiple VMs in /home/vmware (like /home/vmware/windows_xp and /home/vmware/ubuntu) you'll want to move the ENTIRE directory somewhere new ... you'll then have to "reregister" the VM again w/ "vmware" (either via the GUI or CLI)

CLI command: vmware-cmd -s (un)register /path/to/VirtualMachine.vmx 

unregister it 1st:
/usr/bin/vmware-cmd -s unregister <OLD config_file_path>

then register it again after the move:
/usr/bin/vmware-cmd -s register <NEW config_file_path>

---

### Post by jmvidalvia on 2007-03-28
I understand it is the same if I use the GUI, throught the window I enclosed as a png, with the browse button, right?
Just last question, about snapshots.
I tried this usefull facility, as I had a mistake with an XP installation: i just revert to previous snapshot, and it worked nicely.
The question is, ¿how many snapshots can you keep? ¿just the present system and the previous snapshot?
I realize that in /var/lib/VM/... I find files with 001 and files with 002. I understand they correspond to the snapshots I took. If I go on with more snapshots, ¿will they be 003, 004 etc.? As I run out of space I wouldn't like my folder to grow continuously...
I enclose a second png with my folder.
Thanks a lot!

---

### Post by scxtt on 2007-03-28
yeah, if you browse to a .vmx file that isn't registered, that will allow it to be registered ... i just brought it up on the off-chance you used vmware-cmd to start/stop VMs ( i do :) ) ...

as far as snapshots go, i imagine you can take as many of them as your physical HDD can handle ... i'm not sure what kinda of management vmware does w/ snapshots, but i'd imagine it was well thought out ... i don't use them myself, tho i might if i make some hi-level change to a VM ...

---

### Post by jmvidalvia on 2007-03-28
Thank you very much!
Are you saying you start VM's throught the terminal?
I would like that, (I very much prefer to use alias in terminal to start programs)
¿can you tell me how to?
Many thanks!

(last question, I promise)
:)

---

### Post by scxtt on 2007-03-28
ask as many ?s as you want :) ...

vmware-cmd /path/to/VirtualMachine.vmx start

vmware-cmd /path/to/VirtualMachine.vmx getstate (is it on or off?)
vmware-cmd /path/to/VirtualMachine.vmx getuptime (how many seconds has the VM been powered up?)

you can also use **vmware-cmd /path/to/VirtualMachine.vmx stop {soft/hard}** (the soft is like telling the VM to gracefully shutdown, hard is like pulling the plug - and i think it requires VMWare tools be installed on the VM) ...

---

### Post by jmvidalvia on 2007-03-28
Thank you very much!
By the way, don't you sleep in Ohio?
:)

---

### Post by jmvidalvia on 2007-03-28
Hi!
It's me again,
I tried:
vmware-cmd /media/hda3/home/jm/vmware/Windows\ XP\ Professional\ 2/Windows\ XP\ Professional\ 2.vmx start

First It showed me permission problems. As I moved my .vmx from the source to a new partition I assumed I had to do: *chmod u+x*. I did.
No more permission problems, but..
VMware starts (I see the process typing *top* in a terminal), but I have no way to go there, I don't know how to access the window...
:( 
Got any idea?
Thanks again!

---

### Post by jmvidalvia on 2007-03-28
If then I type:
vmware
Then the window opens with the VM already running.
I understand the *vmware.cmd* starts the system and *vmare* opens the console.
:confused: 
Enough for me: it's fine!
Thanks.

---

### Post by scxtt on 2007-03-28
i sleep, but just "weird" hours ... since a work from 4pm to 12am (2nd shift IT work) ...

for me, i don't need a console up all the time - so i start the VMs via the CLI and connect to them either through SSH w/ X-forwarding (linux based VMs) or RPD (windows-based VMs) ... if you're always going to use the console, then you might as well just stick w/ the vmware GUI for everything ...  but i do a lot of work w/ them away from the console, so i prefer to do it the other way ... nice to have choices tho :)

---

### Post by jmvidalvia on 2007-03-29
Thanks you very much.
I like the idea of having the XP machine working with no GUI and connecting to it througth SSH.
I'll try to learn somewhere...
Good luck!

---

### Post by jmvidalvia on 2007-04-10
Hi again!
Back again.
I am learning a lot.
I instaled Ubuntu Server in my vmware.
Now I can access to it through ssh I realize that there's no need to open the GUI for vmware.
My problem is that I start the server by doing:

vmware-cmd /media/hda3/home/jm/vmware/Ubuntu/Ubuntu.vmx start

and it works, but the server keeps waiting for the login (usr + psswrd), so it doesn't mount eth1 so I cannot acces through ssh.

¿how do you solve this?

Same problem when I shutdown it by doing through ssh:

sudo shutdown -hP now

The server seems to close, but in vmware remains open and I can not start a new session till i close the host.

¿any idea? Thanks a lot!

---

### Post by scxtt on 2007-04-10
you may not have eth1 "checked" to start @ boot?

as for shutdown, what happens if you do:

[indent]vmware-cmd /media/hda3/home/jm/vmware/Ubuntu/Ubuntu.vmx stop[/indent]

does it completely turn off?

---

### Post by jmvidalvia on 2007-04-11
Solved whwn starting!
But when doing..

from server: sudo shutdown -hP now
from remote:  vmware-cmd /media/hda3/home/jm/vmware/Ubuntu/Ubuntu.vmx stop

then:

VMControl error -8: Invalid operation for virtual machine's current state: Make sure the VMware Server Tools are running

As far as I know I couldn't install VMware Server Tools in Ubuntu-server, although I couls in XP (boths guest, of course)

:confused: 

Thanks again!


PS: by the way, how do people put console text in a nice box within this forum, I couldn't find it!

---

### Post by scxtt on 2007-04-12
i can see it hinging on vmware-tools ... you should be able to install it - i was able to for Xubuntu and ubuntu server, even gentoo, i think ...

use [ code ] what i want in a text box [ /code ] (minus the spaces) to put things in a text box ...

---

### Post by jmvidalvia on 2007-04-12
I shall insist then.
Thank you!

---

### Post by jmvidalvia on 2007-07-11
Is there any text command to open the console with the host?
I mean, ok, I run
```
vmware-cmd /media/hda3/home/jm/vmware/Ubuntu/Ubuntu.vmx start
```
and the virtual machine starts.
But, do I have to go to menu-vmconsole-select host-select running machine-etc if I want to open the window to operate with GUI?
Isn't there something like..
```
vmware-cmd /media/hda3/home/jm/vmware/Ubuntu/Ubuntu.vmx console
```
Thanks a lot!

---

### Post by scxtt on 2007-07-11
i don't believe there's a way to do that w/ **vmware-cmd** - i think you'd have to install something like *vmware-server-console* on the box you want a GUI connection to your VMs from - then you connect over the network ... but i don't know of anyway to launch a GUI viewer (that's not "vmware") from the CLI, you'd just generally use some GUI tool from the VM (like vnc or rdp, etc.) ...

---

