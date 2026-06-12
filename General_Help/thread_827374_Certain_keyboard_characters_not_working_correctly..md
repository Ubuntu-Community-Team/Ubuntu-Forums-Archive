---
title: "Certain keyboard characters not working correctly."
date: 2008-06-12
forum: General Help
---

### Post by Sadistic Tribble on 2008-06-12
Like the title says. For the `, ~, ^, and ´ keys, I have to press the key twice before the character will appear. The **double** quote key will not work at all, and appears as ¨. (this is a small line at the top of the character, in case any of you see it differently).

Im (oops, there it goes again) using a generic keyboard with 108 keys, including a F11 key and three special ones above the arrow keys that I never use.

I have tried several different kb configurations in System> Preferences> Keyboards to no avail. I have also used several dell configurations with my mom&#347; dell keyboard, also with the same error, which leads me to believe the error is in the way Hardy is handling my keyboard. Also, I have a dual boot between Hardy and winXP, in which system the keyboard works fine.

Does any1 else have the same error? Does any1 know how to fix it? I´m trying to program and whenever I need to use a string I have to copy and paste the double quote character from somewhere else! :confused::confused::confused:

Also, sorry if this has already been posted but I searched for anything about Hardy and keyboards and didn´t see my error.

---

### Post by tamoneya on 2008-06-12
you can remap them manually with: ```
sudo apt-get install xkeycaps
xkeycaps
```

---

### Post by Yuki_Nagato on 2008-06-12
Just as a follow up, did you click anything funny when installing the Operating System?  I know I played around with some of those East Asian setups, and their punctuation is placed completely different.

---

### Post by Sadistic Tribble on 2008-06-12
xkeycaps worked for me.

I'm not sure if I did anything weird during install. I had to reinstall several times to get my dual-boot working.

---

### Post by oarion7 on 2008-06-12
I would continue (or try again) trying other keyboard layouts. Because based on the problems you are having it's obviously trying to use an international layout. That's what I don't like about international layouts and why I don't use them, it tries to use ['] as an accent mark and you always have to type it twice and backspace once to even use it normally. Make sure that in your options when you're switching to the other layout, you are setting this new layout as the default and not just an alternate layout and then restart gnome.

EDIT: Nevermind I see you resolved the issue. I wish I knew about xkeycaps before I remapped my entire keyboard layout manually though! Haha, oh well a good learning experience at least :)

---

### Post by DannyB2 on 2008-06-12
> **Sadistic Tribble said:**
> Like the title says. For the `, ~, ^, and ´ keys, I have to press the key twice before the character will appear. 

I am having this same problem.

I installed Ubuntu 8.04 Server.  Then I installed the Kde desktop.  (Not Kubuntu desktop.)

I don´t think it is an Xkeycaps issue.  The same thing happens on the text console (not Xterm) after pressing Ctrl-Alt-F1 thru F6.

At the text console, for example, if I press a double-quote, then after I press the next character, the quote appears, but not the next character.  This behavior is different than under X.  Under X I must hit the key twice for it to appear.

Is there a way to reconfigure the keyboard like I did during original installation?

---

### Post by oarion7 on 2008-06-12
What keyboard layout are you using? Is it USA? (preferences--> keyboard --> layouts) Many of the International or non-English latin-based keyboards have these features built in by default.

---

### Post by DannyB2 on 2008-06-13
> **oarion7 said:**
> What keyboard layout are you using? Is it USA? (preferences--> keyboard --> layouts) Many of the International or non-English latin-based keyboards have these features built in by default.

It is a standard US keyboard.  The entire hardware was previously running SuSE Linux 9.1 for four years nonstop.  (Yes, ancient.  That's why I upgraded.)

I don't know what layout the software thinks I'm using.  BTW, I'm using KDE desktop on top of Ubuntu Server.  But as mentioned, my problem applies to the text consoles as well, so it is NOT just an X-window problem.

Is there a file to look at, or a command to use to see what the keyboard layout is?

Could I have made a mistake during installation?  I don't want to do a complete reinstallation if possible.

Thanks.

---

### Post by DannyB2 on 2008-06-14
I was able to straighten out the console keyboard problem by doing...

sudo dpkg-reconfigure console-setup


Next, sometime, I will look at fixing it in the gui.  But Im not so worried about that.

---

### Post by DannyB2 on 2008-06-15
I was able to straighten out the gui keyboard problems by doing...

sudo -i
cd /etc/X11
cp xorg.conf xorg-conf-backup-2008-06-15-01
dpkg-reconfigure xorg-xserver
exit


One more thing...
In fixing both the console and gui keyboard problem, I picked the generic pc-104 keyboard, which of course, is what I am using.

---

