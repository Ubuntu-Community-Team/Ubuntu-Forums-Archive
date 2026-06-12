---
title: "Installing VMWare on Ubuntu 8.04 Server edition"
date: 2008-05-14
forum: General Help
---

### Post by nisarg on 2008-05-14
I was thinking on upgrading my 7.10 Server to 8.04 and installing VMWare Server on it.
One question though - can I run Vmware Server on Hardy without a "Desktop" installed? Or even on Gutsy for that matter, can you run VMWare server on a command-based Ubuntu Server 7.10/8.04? Does Vmware come with all required libraries and stuff? Or a way to get around it if I do not want to clutter my server with desktops and stuff.
I plan to run windows on it BTW.

Inputs appreciated, as always!
Cheers.

---

### Post by SpaceTeddy on 2008-05-14
yes, it does. I have not installed vm-ware on ubuntu server (yet), but i have done so on countless occasions with debians servers rangeing from sarge to lenny.

it is not painless tho. You will need to have the build-essentials installed, and need to apply the latest any-to-any patch. There are tutorials out there (even in this forum) on how to do it.

a simple search for "hardy vmware install" gave me this on the first page. it looks pretty right to me :)
[http://ubuntuforums.org/showthread.php?t=779934]("http://ubuntuforums.org/showthread.php?t=779934")

hope it helps

PS: you will need a vmware console for it to connect to the server and install windows. This cannot be done on the server itself, as it has no gui.

---

### Post by nisarg on 2008-05-15
thanks for your response. 
i am not too sure of vmware console? does this mean you can have 'VMWare Server' installed on an another machine, connect to the server and use it from there? then this would also make it impossible to actually use a windows VM  sitting at the server itself, i.e. directly? you are always kind of using it from a machine that has a "GUI" remotely or just for service purposes. 

> **SpaceTeddy said:**
> yes, it does. I have not installed vm-ware on ubuntu server (yet), but i have done so on countless occasions with debians servers rangeing from sarge to lenny.

it is not painless tho. You will need to have the build-essentials installed, and need to apply the latest any-to-any patch. There are tutorials out there (even in this forum) on how to do it.

a simple search for "hardy vmware install" gave me this on the first page. it looks pretty right to me :)
[http://ubuntuforums.org/showthread.php?t=779934]("http://ubuntuforums.org/showthread.php?t=779934")

hope it helps

PS: you will need a vmware console for it to connect to the server and install windows. This cannot be done on the server itself, as it has no gui.

---

### Post by n8behavior on 2008-06-29
the vmware server host does not need a GUI to host Windows-based VMs, or any guest OS that has a GUI.  VMWare  virtualizes the display hardware so the guest OS thinks it has real graphics hardware.  the console (the vmware client app) displays the GUI of the guest OS.  the console connects to remote servers via SSL, port 902 IIRC.  if you install vmware server on an OS with a GUI, the server and client can be on the same box.

---

### Post by SephirothLance on 2010-01-05
I know this thread is likely long since dead but I've spent the last few hours going through every resource I can find to resolve this issue with VMware Server 2.0.2 x64 on Ubuntu 8.04 Server.

I have the x64 tar-ball from vmware's website, go through the installation and configure scripts just fine, accepting the default values except for the administrative account name.  Downloaded the appropriate libraries, the linux-server-header files, everything compiles... After the installation procedure everything is in it's proper place.  Type vmware in the terminal, it spawns a web browser to which the reply is connection refused on port 8333. I try 8222, also refused.  I wonder if it's conflicting with my apache server (shouldn't be, but still) so I bring that down.  Still refused connection.  No firewall loaded.  

I do ```
ps -e | grep vm
```  - no VMware process are running.

I try the init scrips.  ```
/etc/init.d/vmware start
``` provides no output, it just skips a line and returns to the terminal prompt.  Same thing with ""/vmware-core  /vmware-mgmt everything.  I've completely removed every trace of the install several times, verified all of the appropriate libraries are there, tried some finagling with symlinks I've seen on other threads all to no avail.  If anyone has any idea why this may be happening I would appreciate it greatly.

---

