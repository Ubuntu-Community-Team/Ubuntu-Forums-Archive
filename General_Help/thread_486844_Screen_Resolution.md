---
title: "Screen Resolution"
date: 2007-06-28
forum: General Help
---

### Post by DrEmpire on 2007-06-28
i used envy to install my nvidia drivers,then change my resolution settings in the nvidia settings in system tools but everytime i restart the computer the resolotion goes back to 1024x768   from 1280x1024 which is the resolotion i would like to use, any idears on how to have the resolotion on 1280x1024 every time i boot up the pc or will i need to change it my self everytime?

---

### Post by Nate53085 on 2007-06-28
When you change the resolution, do you check the little "Make default for this computer" checkbox?

---

### Post by DrEmpire on 2007-06-28
yes i have tried setting it as defualt but the system>prefs>screen resolution dont seem to work for me at all so i use applications>system tools>nvidia settings
 any idears out there i have read about this problem before but the help there dident help me

---

### Post by jimbob on 2007-06-28
If the above doesn't work, take a look in your /etc/X11/xorg.conf file in the Screen section, Subsection Display, Modes line.

If the first of the modes listed is not  "1280x1024" add it as the first and then restart the computer.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by Nate53085 on 2007-06-28
you * could* take a look at /etc/X11/xorg.conf and remove all resolutions exept for the one you want.  This is dirt. Be very careful and back up your Xorg file.  Note that if you screw it up you can stop X from starting and will have to restore the backup in a text environment

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.BAK
```

```
sudo gedit /etc/X11/xorg.conf
```

```
**Remove offending text and or replace offending text with the resolution you want, save and exit**

**Restart X (restarting your computer works fine)**
```

Then if you are left with broken x, get to a terminal and type

```
sudo cp /etc/X11/xorg.conf.BAK /etc/X11/xorg.conf
```

---

### Post by DrEmpire on 2007-06-28
yes thank you that worked but i did forget to ask about the refresh rate im currently on 75 but whould like to use 60 do i use the same method as before to change the refresh rate?

---

### Post by DrEmpire on 2007-06-28
ignour my last post i just went on ahead and edited the file and it worked, is it true tho that ubuntu can ruin a monitor with a bad refresh rate?

---

### Post by jimbob on 2007-06-28
I have read that in many places (mostly monitor manuals) however I have never heard of anyone who actually did it.  Most modern monitors will refuse to use a rate that is ouside their limits and post an "out of scan range" message on the screen.

As long as you stick to a scan range that is recommended by the monitor manufacturer as published you should be OK.

This would apply to any OS, we don't want Ubuntu to get a bad rap do we?
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by DrEmpire on 2007-06-28
no we dont want ubuntu to get a bad rap, and i agree you are right my monitor does say a message out of range or something as such if i was to put the refresh rate to high as ive done with some games :O), i was just woundring just incase 

ask a qestion and get what you want

---

