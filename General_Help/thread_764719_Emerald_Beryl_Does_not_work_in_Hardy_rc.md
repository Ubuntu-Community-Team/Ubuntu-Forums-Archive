---
title: "Emerald Beryl Does not work in Hardy rc"
date: 2008-04-24
forum: General Help
---

### Post by Linux_freek on 2008-04-24
](* ,)huh? why emerald is not working in hardy heron :( /.... or Is there any one who could run it in there comp :)

---

### Post by steveneddy on 2008-04-24
Emerald working here just fine.

Hardy

---

### Post by ricanelite on 2008-04-24
I have notice that none of the themes for Emerald are there. When I was running Gusty and installed Emerald I did a couple of commands in the Terminal for emerald the themes came up. Now those commands are not listed there. But Emerald is working fine just not showing none of the themes. Just had to search for it in [Gnome-Look.org]("http://www.gnome-look.org")

---

### Post by Linux_freek on 2008-04-24
hey did you do anything special :p cause it is installed but it does not apply the theme... :(although it worked when i use to be in 7.10 :(

---

### Post by ricanelite on 2008-04-24
yeah it installed fine for me went to package manager and installed Emerald but there is no themes. To select from you will have to get them from Gnome-Look

---

### Post by Zorael on 2008-04-24
You want to grab the emerald-themes package from the Feisty repositories if you want the standard bunch.

[http://packages.ubuntu.com/feisty/emerald-themes](http://packages.ubuntu.com/feisty/emerald-themes)

As for why it doesn't work for you (OP), please post the output of the following commands entered in a terminal.
```
$ compiz --replace &
$ emerald --replace &
```

Don't forget the ampersands (&). And when you're done, don't close the terminal via the X button; enter **exit** instead.

---

### Post by user481516 on 2008-04-25
> **Zorael said:**
> You want to grab the emerald-themes package from the Feisty repositories if you want the standard bunch.  I have a 7600gt AGP video card if that helps.

[http://packages.ubuntu.com/feisty/emerald-themes](http://packages.ubuntu.com/feisty/emerald-themes)

As for why it doesn't work for you (OP), please post the output of the following commands entered in a terminal.
```
$ compiz --replace &
$ emerald --replace &
```

Don't forget the ampersands (&). And when you're done, don't close the terminal via the X button; enter **exit** instead.


I have the same problem.  I could not be happier with the way compiz installed this time and the cube, 3d windows, etc...  BUT for some reason emerald wont apply a theme...  As far as the outputs for those commands I got this:

[1] 6208
briantadhorrocks@briantadhorrocks-desktop:~$ Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:02e0 (rev a2) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

and for the second command:

[2] 6254

Hope this helps.

---

### Post by user481516 on 2008-04-25
That was strange, after I did those commands, the window theme effects were applied for a second until I minimized the window and lost my title bar.  I restarted and now it is gone.

---

### Post by wolfe on 2008-04-25
I am having the same issue.  cannot change themes via the emerald control pane

---

### Post by jarektr on 2008-04-25
Hi guys I Have the same problem in hardy Can anyone help us please???

---

### Post by ErusGuleilmus on 2008-04-25
I had this same problem, until I ran the "$ emerald --replace &" command. It used my emerald themes, until I closed the terminal I ran the command in. To get around this, I went to System -> Preferences -> Sessions, and made a new session using the "$ emerald --replace &" command. It now applies the emerald theme you have selected at startup. It isn't really a fix, but it works for me.

Edit: I don't mean to insult anyones intelligences, but you do NOT want to the "$" to be part of the command you use in making a new session.

---

### Post by juventinoc10 on 2008-04-27
it worked when i did it briantadhorrocks emerald --replace &

---

### Post by mgmiller on 2008-04-27
What happens if, instead of using a terminal, you hit alt F2 to get the run application dialog and enter:
```
emerald --replace
```
in that?

---

### Post by vice1 on 2008-05-05
Goto Compiz Config Settings Manager (install if you haven't)

Scroll to “Window Decoration” setting. 

In the “Command” field replace whatever is there to:
emerald --replace

**Hope that works, i had the same problem and this worked for me.

---

### Post by Sub101 on 2008-05-05
all i did was add the command

```
emerald --replace 
```

to the startup programs. system--->sessions--->startup programs

then restart X (Crtl+Alt+Backspace) and it runs fine

---

### Post by Hamstermerc on 2008-05-05
I have a strange problem where on the advice of another thread i pressed F2 and entered "emerald --replace"  Now all my bars have gone funny and i prefered it the way it was before. Anyone know how to reverse this. (Running Hardy Heron)

---

### Post by Sub101 on 2008-05-05
posibly run
```
emerald --replace 
```
in a terminal and then close the terminal. This got rid of all my customizations but not sure if its a permanent fix

---

### Post by vice1 on 2008-05-05
After making changes to the compiz settings manager , window decorations - setting, you'd need to restart X

---

### Post by mgmiller on 2008-05-07
> **Hamstermerc said:**
> I have a strange problem where on the advice of another thread i pressed F2 and entered "emerald --replace"  Now all my bars have gone funny and i prefered it the way it was before. Anyone know how to reverse this. (Running Hardy Heron)

Enter the following command in the alt/F2 box:

```
gtk-window-decorator --replace
```

---

### Post by randal-r on 2008-06-26
If you are having trouble getting Emerald Themes to work with compiz under Hardy; try this.

Edit the file Compiz-Decorator

    usr/bin/compiz-decorator

You will notice a line of code stating - Emerald="No" 

Change the No to Yes , save and everything will work just fine.

---

### Post by DaymItzJack on 2008-06-26
[http://mirrors.kernel.org/ubuntu/pool/universe/e/emerald-themes/emerald-themes_0.2.1-0ubuntu1_all.deb](http://mirrors.kernel.org/ubuntu/pool/universe/e/emerald-themes/emerald-themes_0.2.1-0ubuntu1_all.deb) - deb file for all the emerald themes.

Taken from: [http://hacktivision.com/index.php/2008/06/07/how-to-enhance-ubuntu-8-04-hardy-heron-e?blog=2](http://hacktivision.com/index.php/2008/06/07/how-to-enhance-ubuntu-8-04-hardy-heron-e?blog=2)

---

### Post by m3alnemer on 2008-09-09
> **Sub101 said:**
> posibly run
```
emerald --replace 
```
in a terminal and then close the terminal. This got rid of all my customizations but not sure if its a permanent fix

Worked ! :)

Have been lazy to find the solution :lolflag:

---

### Post by anarkae on 2008-09-23
> **vice1 said:**
> Goto Compiz Config Settings Manager (install if you haven't)

Scroll to &#8220;Window Decoration&#8221; setting. 

In the &#8220;Command&#8221; field replace whatever is there to:
emerald --replace

**Hope that works, i had the same problem and this worked for me.

Thanks, that worked for me.
:guitar:

---

