---
title: "VMware Workstation"
date: 2005-04-27
forum: General Help
---

### Post by squidy37 on 2005-04-27
I've downloaded vmware (VMware-workstation-5.0.0-13124.i386.rpm), turned it into a .deb using 'alien -d', then installed it using 'dpkg -i'... The problem is, how do I run VMware?! I've googled around and found the command 'vmware-toolbox &', but that command did nothing.  Any help will be great!

---

### Post by squidy37 on 2005-04-27
it seems that the 'alien -d' did not work correctly.

> 
dongmin@dongmin:~$ vmware &
/usr/bin/vmware: line 85: /etc/vmware/locations: No such file or directory
/usr/bin/vmware: line 183: /lib/wrapper-gtk24.sh: No such file or directory
/usr/bin/vmware: line 183: exec: /lib/wrapper-gtk24.sh: cannot execute: No such file or directory
[1] 30234
[1]   Exit 126                vmware
dongmin@dongmin:~$


does anyone know how to get vmware on ubuntu?

---

### Post by bored2k on 2005-04-27
[http://www.vmware.com/support/ws5/doc/ws_install_linux.html](http://www.vmware.com/support/ws5/doc/ws_install_linux.html)

You should have gotten the .tgz

---

### Post by squidy37 on 2005-04-27
ohh i c.. i will go do that now ^^ thank you!

---

### Post by rothbart on 2005-04-28
[QUOTE=bored2k][http://www.vmware.com/support/ws5/doc/ws_install_linux.html](http://www.vmware.com/support/ws5/doc/ws_install_linux.html)

You should have gotten the .tgz[/QUOTE]
 Agreed, the tgz is easier.  When done, you can run vmware-config.pl to set it up for your kernel (most likely won't already be set up), then just vmware to run it.  I'm not running the 5.0 version but I imagine it's the same as the 4.5x that I'm running.

I posted earlier but got no bites.  Once you get it up and running, I'd be curious (if you're planning on installing Windows) if you can get DVD Decrypter to run within VMware and have it successfully use your DVD drive (provided you have one).  :)  If so, I'd appreciate some info on how you accomplished it.

---

### Post by bored2k on 2005-04-28
[QUOTE=rothbart]Agreed, the tgz is easier.  When done, you can run vmware-config.pl to set it up for your kernel (most likely won't already be set up), then just vmware to run it.  I'm not running the 5.0 version but I imagine it's the same as the 4.5x that I'm running.

I posted earlier but got no bites.  Once you get it up and running, I'd be curious (if you're planning on installing Windows) if you can get DVD Decrypter to run within VMware and have it successfully use your DVD drive (provided you have one).  :)  If so, I'd appreciate some info on how you accomplished it.[/QUOTE]
 Of course decrypter works like that. Most of us dont even use it through vmware, we open it with wine or crossover, giving it more RAM to work with ;).

---

### Post by kisain on 2005-04-28
um few questions...........
ok i blunderd my way thru settin up vmware and and setting up (leaves bad tast in mouth) windows xp no service pack.......i update to directx 9.0c and then i install ragnarok.......and i get the error cannot initiate d3d or (iforget) and then the program  
crashes......i go to it's settings and no video card shows up and than i go into devices in windows and it tells me that it's some sort of adapter from vmware.
i had the problem also before installing fmware as well.......is there a way to fix this?
or is this vmware not a "emulator" but the real mcoy?

if ya have any questions just ask....
thanx for ya help 
kisain

ps how do i fix bunny?

---

### Post by benplaut on 2005-05-14
[QUOTE=kisain]um few questions...........
ok i blunderd my way thru settin up vmware and and setting up (leaves bad tast in mouth) windows xp no service pack.......i update to directx 9.0c and then i install ragnarok.......and i get the error cannot initiate d3d or (iforget) and then the program  
crashes......i go to it's settings and no video card shows up and than i go into devices in windows and it tells me that it's some sort of adapter from vmware.
i had the problem also before installing fmware as well.......is there a way to fix this?
or is this vmware not a "emulator" but the real mcoy?

if ya have any questions just ask....
thanx for ya help 
kisain

ps how do i fix bunny?[/QUOTE]

as for bunny, put [*center] tags around him [/center] (take out the asterick)

not sure on the VMware  :roll:

---

