---
title: "VirtualBox in Edgy - Sound, Resolution"
date: 2007-02-26
forum: General Help
---

### Post by vav on 2007-02-26
Hi,

I just installed Virtualbox in Edgy and then used my restore CD to install XP on it. Works great, with network connection and all that, but I had a few questions:

1> How can I exchange data between the XP on VirtualBox and the native Edgy?
2> How can I increase the screen resolution beyond 1024x768? (1680x1050 would be nice!) This is essential for the type of app I need the XP on VirtualBox for in the first place (EDA)
3> Sound doesnt work... I tried enabling audio in VirtualBox settings, and set it to ALSA. But Windows refuses to show a volume control!

Thanks

---

### Post by PartickThistle on 2007-02-26
```
VBoxManage sharedfolder     add <vmname>|<uuid>
                            -name <name> -hostpath <hostpath>
                            [-transient]
```

For example: 
```
user@localhost: $ VBoxManage sharedfolder add /home/username WindowsXP - name MySharedFolder -hostpath /home/vav
```
Do this **before** booting the VM.

Install the VirtualBox tools **after** Windows for your video problem.   Not 100% sure it will work, as I've not used Windows in VB.

3. The VB tools might resolve this, too.

4. Read [the documentation](http://www.virtualbox.org/download/UserManual.pdf) - it has everything and more that you need to know :)

---

### Post by vav on 2007-02-27
Ok after some confusion I finally located the Guest Additions ISO (/opt/VirtualBox...). Now I can resize the VirtualBox window and the XP screen resolution auto-adjusts! Very snazzy :P


Havent figured out the sound drivers yet though. And the Vboxmanage stuff didnt work right out of the box... will update as stuff works!

---

### Post by vav on 2007-02-27
Sound worked on double reboot (hehe)

The addition of the shared folder seems to get accepted, but the folder doesnt show up anywhere in Windows... :(
The Virtualbox shared folders link in network places is unusable :(

---

### Post by vav on 2007-02-27
I tried to use Virtualbox over NX Server. When try to run Win XP, it pops up a window saying spawning session... 0%
This window doesnt go away! Also, once this happens I cant logout of my session on the client!! I have to force a terminate, which messes with my NX server, so that I have to restart my host machine :(

---

### Post by vav on 2007-02-27
Here's a screenshot - logged in over NX server, running XP in Virtualbox on edgy on the host machine. So at least from an ubuntu  :guitar:  NX client it works well.

---

### Post by vav on 2007-03-02
Mounting your linux folders in windows:

before starting the Windows session, I had to type:
VBoxManage sharedfolder add "WinXP" -name "LinData" -hostpath /Data/
<-----------command----------><session><---mountname><--pathOnLinux?       

as suggested before in this thread.

However, after booting windows, there is an additional step:
Go to 'Map network Drive' and type \\vboxsvr\LinData
                                                   <server> <mountname>

Lastly, whether windows can write to the LinData folder or not will be decided by the permissions for the /Data folder on Linux. So I did:
sudo chmod 777 /Data

PS: Saving the windows session instead of shutting down sometimes loses connection to the drive. Reboot to fix.

---

