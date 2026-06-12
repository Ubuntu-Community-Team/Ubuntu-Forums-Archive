---
title: "Question about Nautilus file Display"
date: 2015-07-25
forum: General Help
---

### Post by offir on 2015-07-25
I do not know if this is the proper forum
If not then please delete or move


I recently installed Ubuntu 15.04

And I have a problem with Nautilus

When I open a folder
I Configuring the view to what is comfortable for me
Size of display of files
List or Icons

But it is not saved
I have to do it every time
Again

---

### Post by CantankRus on 2015-07-25
You need to configure in preferences.

---

### Post by offir on 2015-07-25
I forgot to add
I installed Cairo Dock

I do not have these options

---

### Post by CantankRus on 2015-07-25
With the nautilus window in focus, try the ctrl+p keyboard shortcut to open preferences.

**[COLOR="#FF0000"]Edit:[/COLOR]** Just tested in my 15.04 install and you are right.
May have to set preferences in the ubuntu session for now then log back into the cairo-dock session.
Probably needs something added/installed to startups for preferences to show.

---

### Post by offir on 2015-07-25
Is there a way to add this option ?
Or
Perhaps there is an option in compiz And I do not know

---

### Post by mc4man on 2015-07-25
nautilus has moved the preferences menu to an app menu which is available in a gnome session. For ubuntu sessions nautilus has been patched to return to the more traditional previous menus.
Other sessions will be without either.

Workaround 1 - use dconf-editor
Workaround 2 - enable a nautilus accel to open the pref menu using an unused keybinding.

Ex. - 
Open ~/.config/nautilus/accels file
Find the ; (gtk_accel_path "<Actions>/ShellActions/Preferences" "") line, add a binding between the "" & remove the ;


Shown in screen on highlighted line, using Ctrl+Alt+p as binding (ctrl is Primary), then quit/restart nautilus or log out/in. ctrl+alt+p will open menu when focus is on nautilus.

Or file a bug requesting that all not gnome sessions use the ubuntu version of nautilus - good luck with that...

---

### Post by CantankRus on 2015-07-25
Can confirm using mc4man's Workaround 2, I was able to bring up the
nautilus preferences in a cairo-dock session in 15.04.
Another alternative is to install and use **nemo** which I find better than nautilus anyway.

---

### Post by offir on 2015-07-25
> Workaround 1 - use dconf-editor
Workaround 2 - enable a nautilus accel to open the pref menu using an unused keybinding.

what is Workaround ?

> Open ~/.config/nautilus/accels file
Find the ; (gtk_accel_path "<Actions>/ShellActions/Preferences" "") line, add a binding between the "" & remove the ;



i copy and paste it in terminal
```
sudo ~/.config/nautilus/accels file
```
i got this
```
sudo: /home/offir/.config/nautilus/accels: command not found

```

i need to find this line ```
 ; (gtk_accel_path "<Actions>/ShellActions/Preferences" "") 
```
and make it like this ```
(gtk_accel_path "<Actions>/ShellActions/Preferences" "&") 
```
[COLOR="#FF0000"][SIZE=6]
?[/SIZE][/COLOR]


this is for add the  preferences menu [COLOR="#FF0000"]?[/COLOR]

---

### Post by CantankRus on 2015-07-26
Work around.....work around the problem, fix

**~/.config/nautilus/accels** is a text file so open in gedit.
```
gedit ~/.config/nautilus/accels
```

Search for **Preferences**
and insert your shortcut between the last 2 double quotes and remove the semi-colon; at the beginning of that line.
eg I used **<Primary>p** which is ctrl+p

---

### Post by offir on 2015-07-26
Thank you it works

I wrote this as you said
```
gedit ~/.config/nautilus/accels
```

enter this
```
(gtk_accel_path "<Actions>/ShellActions/Preferences" "<Primary>p")
```

remove this ```
;
```
save 

then 
```
nautilus -q && nautilus &
``` (Because for some reason I can not do[COLOR="#0000FF"] logout[/COLOR])

and now it works 
Thank you

---

### Post by CantankRus on 2015-07-26
ok good.
I couldn't logout either.
A terminal command to log you out is 
```
kill -9 -1
```

---

### Post by offir on 2015-07-26
I think it's because of the Cairo Dock But I'm not sure
Good to know this command
For two days I do a restart

---

### Post by CantankRus on 2015-07-26
Hi offir,
Was just looking at cairo-dock and found you can set a middle click action
on the logout applet to run the "kill -9 -1" command I gave earlier.
Edit the applet as shown in pic, then click apply.

---

