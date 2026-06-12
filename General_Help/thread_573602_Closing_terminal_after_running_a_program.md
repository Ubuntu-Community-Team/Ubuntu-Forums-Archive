---
title: "Closing terminal after running a program"
date: 2007-10-11
forum: General Help
---

### Post by kylebaked on 2007-10-11
I would like to know if there is a way to exit out of the terminal after running a program through it. For example, if I were to sudo synaptic through the terminal, I would want synaptic to open, and the terminal to close.

Or even better, is there something similar to pressing windowskey+r in windows, where a run dialog pops up and I can type a program in there to run it?

Also: I am looking for a calender program that I can use as an agenda and keep track of events.

Thanks.

---

### Post by markp1989 on 2007-10-11
press alt+f2 and a run prompt will come  , and i think that in the prompt its better to run gksu synaptic instedof sudo synaptic

---

### Post by Het Irv on 2007-10-11
> **kylebaked said:**
> I would like to know if there is a way to exit out of the terminal after running a program through it. For example, if I were to sudo synaptic through the terminal, I would want synaptic to open, and the terminal to close.

Or even better, is there something similar to pressing windowskey+r in windows, where a run dialog pops up and I can type a program in there to run it?

Also: I am looking for a calender program that I can use as an agenda and keep track of events.

Thanks.
Eudora has an event manager that is tied to the calander under Date/time.
Click date time and the double click a day and see where it takes you

---

### Post by bhavi on 2007-10-11
Press alt+f2 to open up the run dialog box (similar to that in windows)

---

### Post by overlord.gaurav on 2007-10-11
Try this:
```
gksu synaptic&
```

---

### Post by Lord Illidan on 2007-10-11
Type this :

```
command & disown & exit
```

Substitute command by the name of any command you like, be it sudo synaptic or firefox.

---

### Post by kylebaked on 2007-10-11
thank you guys for the quick responses.

Is there a way to change global hotkey? I would like altf2 to use the windows key instead.

Also, is there a standalone program for my calander problem? I don't need any more email software.

Thanks

Edit: Thank you Lord Illidan. 
Edit Edit: I found a program called remind to help me with my dates.

---

### Post by Lord Illidan on 2007-10-11
> **kylebaked said:**
> 
Is there a way to change global hotkey? I would like altf2 to use the windows key instead.


Sure, System->Preferences->Keyboard Shortcuts

---

### Post by Dark Hornet on 2007-10-11
you can always hit "Ctrl D" to close out the terminal session.  In addition, you can put a "&" at the end of your command, and this should allow you to close the terminal without closing the program you just opened....good luck.

---

### Post by dpar on 2007-10-11
sunbird
for the calendar program, or korganizer. Both in the repos.

---

### Post by fajifazeel on 2008-07-14
thanks alot

---

