---
title: "Issues installing Maya 8"
date: 2006-09-05
forum: General Help
---

### Post by Tashamon on 2006-09-05
I need to create a dir in /var but I don't have "permission".  Can someone tell me how I can create one or gain that accessibility?

---

### Post by orb9220 on 2006-09-05
Did u run a gksudo nautilus should do the trick.

---

### Post by hw-tph on 2006-09-05
When you purchase Maya 8 you get installation support. Call the Autodesk support and they should be happy to help.


Håkan

---

### Post by GeneralCody on 2006-09-05
SOmething tells me that not everyone actually buys Maya8. It's like two months salery for the unlimited version...](*,) 

To create folders in /var you can do that as root via sudo...

GC

---

### Post by hw-tph on 2006-09-05
> **GeneralCody said:**
> SOmething tells me that not everyone actually buys Maya8. It's like two months salery for the unlimited version...](*,)

Then perhaps they should. There is a trial version if you cannot afford the Full/Unlimited versions. Besides, how many user purchase Maya and similar tools themselves? Most users get their tools from their employer.

Or is piracy considered OK when you "can't afford" something?


Håkan

---

### Post by taurus on 2006-09-05
> **Tashamon said:**
> I need to create a dir in /var but I don't have "permission".  Can someone tell me how I can create one or gain that accessibility?

```
sudo mkdir /var
```

---

### Post by genjix on 2007-04-07
> **hw-tph said:**
> Then perhaps they should. There is a trial version if you cannot afford the Full/Unlimited versions. Besides, how many user purchase Maya and similar tools themselves? Most users get their tools from their employer.

Or is piracy considered OK when you "can't afford" something?


Håkan

Sure is. Especially when you're some poor Brazilian who wouldn't get the chance to ever use that software. Alot of countries don't have anti-piracy laws or tolerate it.

---

### Post by albsen on 2007-04-15
> **hw-tph said:**
> When you purchase Maya 8 you get installation support. Call the Autodesk support and they should be happy to help.


Håkan

This isn't as smart as you think it is, if you've read the installation requirements. Because I can't see any ubuntu there ... only suse and redhat

so please don't cry for the police if someone is asking for help.

---

### Post by alienpioneer on 2007-04-30
You need to install flexlm license right?

 Open terminal and :

 sudo mkdir /var/flexlm
 sudo cp /home/xxx/aw.dat /var/flexlm

 where you have to replace xxx with the name of your user directory...One thing else that you should keep in mind is to make a tmp directory.In Windows that directory is C:\Documents and Settings\(current user)\Local Settings\Temp.To do that :

 sodo mkdir /usr/tmp

 and to make that writeable for all users

 chmod -R 777 /usr/tmp

 If it still crashes on renders you should link the maya default tmp from /home/xxx/.../tmp with the new one witch you created:

 ln -s  /home/xxx/.../tmp    /usr/tmp

 Now some openGl issues.I have a nvidia video card (with nvidia you shouldn't encounter problems runing graphics apps) and in my /usr/lib/ i have libGl.so.9775  .We have to make it the default libGl with this:

   sudo rm -rf /usr/lib/libGL.so
   sudo ln -s /usr/lib/libGL.so.9775    /usr/lib/libGL.so

 After that try to put your window controls to ctrl or win tast instead of alt, because you need the alt for working in maya...You should also write this in your maya.env file :

 MAYA_MMSET_DEFAULT_XCURSOR;

 From this point everithing should work fine...Some may realise that after reboot libGL will point back at the default libGL.I don't have a solution right now for that...

---

### Post by SteelToad on 2007-05-05
hi there, I am having trouble installing maya. 

I followed your instructions, but have a problem when trying to run maya. The installation seemed to go fine but when i try to run it using: 

sudo /usr/autodesk/maya8.5/bin/./maya.bin 

( I get this error )

/usr/autodesk/maya8.5/bin/./maya.bin: error while loading shared libraries: libirc.so: cannot open shared object file: No such file or directory



I have tried searching the network for 'libirc.so' using aptitude but find nothing.

I am pretty new to linux so am a little lost, any help you could give would be appreciated.

---

### Post by cosmobreton on 2007-05-12
:) sure:)

1. FIRST      sudo apt-get install csh
2. THEN      /usr/autodesk/maya8.5/bin/Maya8.5

:popcorn:

---

### Post by SteelToad on 2007-05-26
thanx cosmobreton, it now works beautifully :D

---

