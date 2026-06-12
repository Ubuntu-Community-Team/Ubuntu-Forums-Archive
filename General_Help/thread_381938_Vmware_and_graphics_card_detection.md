---
title: "Vmware and graphics card detection"
date: 2007-03-11
forum: General Help
---

### Post by jimbob on 2007-03-11
I have XP running as a Vmware machine under Ubuntu.

Everything works great except XP is unable to detect my graphics card (Nvidia Geforce 6600) showing the dreaded yellow question mark in the device manager.

I have read some threads hinting that this to be expected. How come XP finds all the other hardware in my machine?  Is it only the graphics card that is not accessible?
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by Bachstelze on 2007-03-11
The hardware in a virtual machine is virtual as well, so the graphics "card" of your vm has absolutely *nothing* to do with your GeForce 6200.

To install drivers for it, install VMware Tools - from the VM menu.

---

### Post by jimbob on 2007-03-11
I can't seem to find a Vmware menu that says anything about vmware-tools.

Please, where is it?
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by Bachstelze on 2007-03-11
File Edit View Host **VM** Tabs Help

=> Install VMware Tools

---

### Post by jimbob on 2007-03-11
I do not have a header like that.   All I see when I bring up Vmware is a header that has only one box that says *Player*

Perhaps you have the desktop?

---

### Post by dexter on 2007-03-11
Isn't there any information about this problem on the vmware site ? And a driver for windows that resolves this ?

---

### Post by tikbjamin on 2007-03-13
The info provided by HTL is correct but you need to have the vm running,  Not only must you bring up vmware but you have to also start your guest OS (XP?).

TBJ

> **jimbob said:**
> I can't seem to find a Vmware menu that says anything about vmware-tools.

Please, where is it?
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by Bachstelze on 2007-03-13
He seems to have VMware Player. What I said will work in Workstation/Server but not Player. As far as I know, you can't install VMware Tools in VMware Player, you have to find a vmx file that already has it installed.

---

### Post by jaechild on 2008-01-30
Excuse the ignorance:-? I have the same problem and am also battling to fix it.
If  the graphics card in vmware is virtual does that mean it will never recognise my physical cards capabilities? If it doesn't, what settings does it use???
You mentioned a vmx file with the settings in it already, where can I find this???

---

### Post by jimbob on 2008-01-30
I switched to VirtualBox by Innotek  about 8 months ago and have been extremely pleased with that implementation over VMware.

If I were you I would do the same.

---

### Post by jaechild on 2008-01-30
Thanks I'll give it a try and let you know how it goes!

---

