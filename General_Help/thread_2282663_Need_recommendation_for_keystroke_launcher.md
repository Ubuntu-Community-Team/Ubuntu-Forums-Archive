---
title: "Need recommendation for keystroke launcher"
date: 2015-06-16
forum: General Help
---

### Post by RayTomes on 2015-06-16
I am a new ubuntu user on version 14.04.2

On Win-XP I used a program called Blue Vade Hotkey. It allowed me to set up a couple of dozen applications that could be called up by a single keystroke (I used Win-I for Irfanview, Win-E for an Editor etc etc). This saved me a lot of time on all my commonly used applications.

I may be using the wrong search term but I can't find anything similar in the software library. Does anyone know of something similar to that. The only thing that I found is launchy which requires a lot more keystrokes to get to an application.

---

### Post by Lars Noodén on 2015-06-16
Go to System Settings -> Keyboard -> Shortcuts -> Launchers
Then you can add in the shortcut you want linked with the appropriate command.

---

### Post by RayTomes on 2015-06-16
Thanks you Lars. OK, dummy alert. I get to the place that you say but can't seem to create a shortcut despite reading the help info.

Perhaps first I should ask what is a good set of keystrokes that I should use that aren't already used, e.g. ctry-super or ctrl-super-shift or whatever. Is there one set reserved for the user?

Next, having chosen a keystroke, I can't seem to get it set up. Suppose that I want to make a keystroke something-W (where something is say ctrl-shift-super) to load LibreOffice Writer. Does "LibreOffice Writer" go in the first field and the keystroke in the second one, or is the first field just a label and "LibreOffice Writer" goes in second? Whatever I can't get it to happen.

---

### Post by kerry_s on 2015-06-16
add button is just for name & command, after that you click on the right side & press your keys.

if you want to launch several apps at once, you'll need to make a script & use that for the command.

---

### Post by RayTomes on 2015-06-16
Thanks Kerry. It was the click on the right side that I hadn't got. Managed to set one up. But I am not sure that I understand what goes in the 2nd field. I just put "LibreOffice Writer" but when I do the keystroke nothing happens. Does it need some path or something?

OK, standard Ubuntu does just what I want (when I get to understand it).

---

### Post by RayTomes on 2015-06-17
So, I have ...

Name: LibreOffice Writer
Command: LibreOffice Writer
keystroke set to ctrl-shift-super-W

Only trouble is that when I do that keystroke nothing happens!!!

---

### Post by deadflowr on 2015-06-17
For the record the command to launch writer would be
```
libreoffice --writer
```
all small characters.

You can easily find out a command by opening up the file manager "Files"
go to Computer in the left side pane, go to usr then share then applications.
The applications folder will show icons for all the installed applications that have icons.
(if that makes sense)
Simply right click on an icon and it will show a line for command listed.
You should be able to just copy and paste from there to the shortcuts.

Edit: see post below this for properer way.
I forgot to add go to properties.

---

### Post by kerry_s on 2015-06-17
the way i find the command is to use the filemanager to go to /usr/share/applications right click on the icon-> properties
you'll see the command.

---

### Post by deadflowr on 2015-06-17
Yeah, I forgot to put "go to properties".
Step 1 open >> step 3 profit.
Doh!

---

### Post by RayTomes on 2015-06-17
Thank you Deadflower and Kerry. I managed to get it to work. Had to remove the %U off the copied text "libreoffice --writer %U" which I assume is the file to load. I am away.

---

### Post by CantankRus on 2015-06-17
You may also like to try kupfer.
Kupfer is a launcher and learns your favourite apps.
I launch kupfer with ctl+menu keys and then I only need to type in the first one or 2 letters to 
start an application.
[**_[COLOR="#B22222"]Using kupfer[/COLOR]_**]("http://engla.github.io/kupfer/help/generalusage.html")

---

