---
title: "Font Viewer"
date: 2016-07-05
forum: General Help
---

### Post by MadMonkey1966 on 2016-07-05
Can anyone help me find out why Font Viewer has stopped working. For some reason it has decided to stop displaying fonts for me....... :confused:
I find it the easiest way of adding new fonts to Ubuntu as i am not very good in the Terminal (though i am trying to teach myself), and i often use different fonts in Blender & Gimp.
I can download a font easy enough, but when i try to open it in Font Viewer, it seems to try to open it, then hangs for a few seconds, and then it closes again.
Is there a way to un-install it maybe and re-install Font Viewer ?? Unless someone has a better idea ?

Thanks in advance..... :D

---

### Post by QDR06VV9 on 2016-07-05
What Desktop are you using?
To install 
Manually

There are various locations in GNU/Linux in which fonts can be kept. These locations are defined in **/etc/fonts/fonts.conf; standard ones include /usr/share/fonts, /usr/local/share/fonts, and ~/.fonts.**

The easiest way to install a truetype font is to press alt-F2 and enter the following code (this will open nautilus in the right directory):

```
gksu nautilus /usr/share/fonts/truetype
```

Then create a new directory, name the directory  whatever you like (choose a name that you remember) and copy the fonts  into that directory 
If you need to backup your personal fonts, you should use the **~/.fonts/** folder. To create the folder and install the font "Example.otf": 
```
sudo mkdir -p "~/.fonts/truetype/choose_a_font_folder_name_here"
sudo cp Example.otf "~/.fonts/truetype/choose_a_font_folder_name_here"
```Not  always needed, but finally you can additionally rebuilding the font  information files by pressing alt-F2, mark 'run in terminal' so you can  see the progress and entering the following code: 
```
sudo fc-cache -f -v
```

---

### Post by MadMonkey1966 on 2016-07-05
Sorry, i am using Ubuntu 16.04 LTS

---

### Post by QDR06VV9 on 2016-07-05
Unity, Mate, XFCE, LXDE, Gnome?

---

### Post by MadMonkey1966 on 2016-07-05
Oh. sorry again, i am using Unity

---

### Post by QDR06VV9 on 2016-07-05
No need to be sorry:)
My above post should help then with the right syntax.
But just my way of doing this..and i have not used any font-viewer to install fonts for a number of years now.
I build a folder inside my home Directory if it is not there already named ".fonts" and just throw the font files (.otf and .ttf) I want in there.
And then for good measure I rebuild the font cache by way of
```
sudo fc-cache -f -v
```
And There you go..font installed.
But yes you could try to remove the font-viewer app and try to reinstall it.
If there are any errors post them back here.
Kind Regards

---

### Post by Dennis N on 2016-07-05
> Unless someone has a better idea ?

Have you tried **Font Manager**?

package name in 16.04 repository: font-manager

---

### Post by MadMonkey1966 on 2016-07-05
When i hit alt-F2 and put in 
gksu nautilus /usr/share/fonts/truetype

nothing happens, well it does not seem to.

Anyway, i opened Terminal and done 

sudo mkdir -p "~/.fonts/truetype/myfonts" (myfonts was a name i chose)

but when i look in .fonts all i have in there is .  ..  Library  Read Me.txt

Should there not be a Directory called truetype ? 
Sorry, i did say i am not very good in the Terminal. I get lost.

---

### Post by MadMonkey1966 on 2016-07-05
Thanks Dennis, i did Install font manager, but when i click on a downloaded font, it does not give me the option to open it in Font Manager.

If i could open fonts in there then i could save them from there i guess, unless i am missing something.

Still can not understand what made Font Viewer just stop working ](*,)

---

### Post by &amp;KyT$0P# on 2016-07-05
Don't enclose the ~ in quotes if you want it to expand to the path to your home directory.  You literally created a directory named ~ (containing the specified sub-folders) in whatever your shell's cwd was.

EDIT Also in general try to avoid use of sudo/root when working inside your home directory.  The idea of these folders is that they're writable by you the user, not just root.

---

### Post by MadMonkey1966 on 2016-07-05
Thanks Halogen, removed the quotes that worked :)

---

### Post by QDR06VV9 on 2016-07-05
Your doing fine!
That new Directory or File named ".myfonts" will be where you add any new fonts you may need to have or plainly put where you add new fonts.
The other places as described by my post earlier will be where the fonts that came installed with Ubuntu.
So any new fonts that you need to install...just add the .otf or .ttf into that file now followed by
```
sudo fc-cache -f -v
```
And Dennis N has made a good suggestion also.
If you have any other problems just keep posting them here till we get you sorted out.

---

### Post by MadMonkey1966 on 2016-07-05
Thanks runrickus, i followed the instructions, and got my new folder, so thats all sorted, and i managed to put fonts i downloaded yesterday in there.

It didn't solve the issue with Font Viewer, but i guess i will just have to get more confident using the Terminal to save things in specific places when i need to. I am following a tutorial thing at the moment on basic Shell Commands, so hopefully i will get there. 

Many Thanks for everyones help.
Ian

---

### Post by QDR06VV9 on 2016-07-05
Your very welcome and we have one of the best communities on the web IMHO.
And you will as I did learn to love the "Terminal" over time.
Best Regards and happy bashing.

---

### Post by &amp;KyT$0P# on 2016-07-05
You're welcome! :KS

As for fixing Font Viewer, maybe the downloaded font(s) are the problem.  What happens if you rename the ~/.fonts directory (so that only "system" fonts are installed) and then try to run Font Viewer from a Terminal?
```
gnome-font-viewer
```

If that works, does it also work if you put back ~/.fonts (close Font Viewer first)?

---

### Post by MadMonkey1966 on 2016-07-05
Just to add. I was just looking in the Software Centre on my machine and under Installed i found Font Viewer as i would expect in System Applications BUT there have been 4 reviews written in the last couple of months all with pretty much the same problem. The last review before that was 2013.

Seems very odd to me that, why all of a sudden has this started happening..... ?? Something for someone to look into maybe :). As someone put in there, if you go into Terminal and type 
gnome-font-viewer

it will start.....

---

### Post by cgrs on 2016-07-06
Ughhh, I thought I was the only one...
You have 64bit version of 16.04, right? Because on the 32bit version this bug doesn't happen.
I'm so annoyed by this stupid bug I only want to find a solution :evil:

And, yes, incredibly the ```
gnome-font-viewer
``` works on Terminal.
Also I found that, if you keep the shortcut on your home folder and rename it to whatever other name, guess what. IT *beep* WORKS.
Sorry for being so mad at this, but it really freaks me out.

---

### Post by MadMonkey1966 on 2016-07-07
HI cgrs.....i agree with everything you say apart from one.....i am using 32 bits (its an old machine lol). I think it must have something to do with 16.04, i cant think of anything else.

---

### Post by rtimai on 2016-07-12
In response to MadMonkey1966's initial question, why Font Viewer has stopped working: 

I saw the same behavior as you described consistently in Ubuntu 16.04 Unity (amd64, radeon graphics if it matters.) I completely-removed and reinstalled gnome-font-viewer 3.16.2, with no change. Syslog showed Font Viewer was closing with the error: 

org.gnome.font-viewer[2398]: Unknown option --gapplication-service

I removed version 3.16.2, went to Sourceforge, downloaded the latest version 3.20.2  .deb file for amd64 (currently in the Proposed repo -- which I normally avoid using, but I made an exception in this case.) I installed it, and gnome-font-viewer is now working normally again. There may have been a configuration error in the version in the Xenial repository, I don't know, but anyway 3.20.2 fixes it. So far, the only problem I am seeing is I can't preview webdings -- other fonts are displaying fine, and I'm happy.

---

### Post by cgrs on 2016-09-07
Sorry for resurrecting the thread, but this issue got fixed (yay!):

[https://bugs.launchpad.net/ubuntu/+source/gnome-font-viewer/+bug/1607937 ]("https://bugs.launchpad.net/ubuntu/+source/gnome-font-viewer/+bug/1607937")

No longer "DBus" stuff on .desktop, or launching it from terminal :D

---

