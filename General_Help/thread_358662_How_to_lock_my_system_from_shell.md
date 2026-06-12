---
title: "How to lock my system from shell"
date: 2007-02-11
forum: General Help
---

### Post by ss0007 on 2007-02-11
H i,
I am wondering If there is any command to lock my Ubuntu Workstation directly from the terminal ?

Thx in advance ,

---

### Post by ss0007 on 2007-02-11
oops , If ur nt clear with my question , let me stretch it
 
If I ever wanted to lock my system , from the terminal , is there any built-in 
commands to do that ,so that I dont need to click the menu System->Quit and "Lock Screen" button ? 

Ofcourse , thanks in advance for your answers ,

---

### Post by Xappe on 2007-02-11
run all your tasks in screen and logout perhaps?

then just screen -r -d when you have logged back in

---

### Post by Xappe on 2007-02-11
ah, did not read that last post enough...

maybe some flag to xscreensaver or such could do what you want

---

### Post by ss0007 on 2007-02-11
some flag ? I am a newbie to linux . Could you please explain me with an example ?

---

### Post by g3k0 on 2007-02-11
Why not just use a hotkey like
Control - alt - L  
Its much easier than opening terminal and typing something in

---

### Post by ss0007 on 2007-02-12
All that I thought was to make a shortcut and put it in the top panel . So , I can click on it to lock my system . 
OfCourse , Ctrl+ALT+L is a handy , but I use my mouse so often than a keyboard and some of the programs like Azureus trap the keyboard shortcuts .   Moreover ,I thought  Linux has more things to do with console commands .

---

### Post by yopnono on 2007-02-12
sudo /etc/acpi/./lockbtn.sh

That will lock the screen

---

### Post by ss0007 on 2007-02-14
Thanks , ... 
Issue solved

---

