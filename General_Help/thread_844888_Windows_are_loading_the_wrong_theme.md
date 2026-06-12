---
title: "Windows are loading the wrong theme"
date: 2008-06-30
forum: General Help
---

### Post by psyopper on 2008-06-30
So I have a weird issue today. It seems that Gnome isn't remembering my theme selection properly. When I open an application it loads with something that looks like the "Redmond" theme from Feisty even though I have the Human-Clearlooks theme selected in the Appearance Preferences.

Here's where it gets strange. Gnome knows the correct theme! If I open Appearance and select Human Clearlooks it will update the window with the correct theme and the window will retain that theme until closed. If I reopen the application it then defaults back to the Redmond theme.

This happened after I installed the LINsta Orange theme from gnome-look:

[http://www.gnome-look.org/content/show.php/OrangeLiNstaBlackPlastic?content=62434](http://www.gnome-look.org/content/show.php/OrangeLiNstaBlackPlastic?content=62434)

Just to give you an idea, I took a few screenshots. 

The one named "open.png" shows a newly opened Thunderbird with the wrong theme loaded, even though the Appearance says it should be Human-Murrine and the Appearance window is clearly using the correct theme.

The second shot named "after.png" is the same setup after re-selecting the Human-Murrine theme. This one clearly shows both windows using the same theme. 

Differences include window color (the "wrong" theme is greyer) and Slider bar (the "wrong theme doesn't have handles and is generally uglier).

Any input? 

Ironically, if I select the theme I was originally playing with (that I wound up not liking so much) all the windows open with the correct theme.

The third screenshot is of the Appearance window on a fresh load (close and reopen) after taking the above screenshots. Notice it has reverted back to the Redmond like theme even though it shows that the Human Murrine theme is selected.

---

### Post by psyopper on 2008-06-30
I just went through Synaptic and reinstalled the following items:

gtk2-engines-murrine
gtk2-engines-pixbuf
gtk2-engines-ubuntulooks
human-icon-theme
human-theme
ubuntu-gdm-themes
gnome-themes

The problem persists. This did not resolve it for me.

---

### Post by samsmartguy on 2008-06-30
Maybe you didn't install the following items properly
gtk2-engines-murrine
gtk2-engines-pixbuf
gtk2-engines-ubuntulooks
human-icon-theme
human-theme
ubuntu-gdm-themes
gnome-themes

---

### Post by psyopper on 2008-06-30
So, after more experimenting it seems that the problem is only with the Human themes:

Human, Human-ClearLooks and Human-Murrine.

Also, Nautilus always loads the correct theme. All other apps load what appears to be the Redmond theme. One caveat to all of this - I am running Compiz with Emerald, so in essence I am really only loading the theme controls and icons. 

Any other theme I select loads properly and new apps open with the selected theme properly. The problem is limited to these three themes themselves. What do they have in common? Icons is all I can think of, but each stores the icons independantly of each other. Or do they?

[EDIT] So I made a custom theme by loading the Mist theme and customizing it with the Human icons and saving it. When I switch to a broken theme it stays broken and when I go to my custom theme it works properly. This (I would presume) rules out the icon set as the problem.

---

### Post by psyopper on 2008-06-30
Bump...

Wow, no-one knows what to do with this? Surprising!

Am I posting this in the wrong forum maybe? Should this be in the Beginners Forum? Not sure where else it belongs.

---

### Post by slightlybartfast on 2008-07-28
I'm sorry psyopper I cant help, but I have a similar problem...except that only the Appearance window gets themed, and it stays themed.

The window borders change on any window, but when I go and change the icons and controls nothing changes on any other window.

I hope someone can help :(

This image shows that the icons and the controls don't change.
[ATTACH]79252[/ATTACH]

---

### Post by slightlybartfast on 2008-07-30
BUMP

Please

---

### Post by komoto on 2008-09-12
I've got this same issue.

I change to a new theme, and it applies it to everything currently open.  After that only Nautilus retains the theme, everything else get's a plain redmond-like theme.  Log out and back in again & all my theme changes are lost.

-Kom

---

### Post by komoto on 2008-09-12
Found a solution (to my problem at least).

It appears to be the Darklooks GTK theme that causes the issues.  There is a bug in it which is detailed here:
[http://jaysonrowe.wordpress.com/2008/07/01/darklooks/](http://jaysonrowe.wordpress.com/2008/07/01/darklooks/)

The link also includes a simple fix, which is essentially:

Open ‘/usr/share/themes/Darklooks/gtk-2.0/gtkrc’ in your favorite text editor and go down to line 181

Change from this...

```
bg[NORMAL] = @tooltip_bg_color
fg[NORMAL] = @tooltip_fg_color
```

to this...

```
bg[NORMAL] = @tooltips_bg_color
fg[NORMAL] = @tooltips_fg_color
```

If you don't know how to edit the file I suggest you do this:
In the menu, click: **Applications -> Accessories -> Terminal**

Then type:
```
sudo gedit /usr/share/themes/Darklooks/gtk-2.0/gtkrc
```

Scroll down to line 181 (you should see which line you are on in the status bar)

Append an 's' to "tooltip" on the two lines.

Save and exit.

It should all work now.

-Kom

---

### Post by an93l on 2008-09-23
thanks for the fix and all the hard work finding it, I had the same problem that was so anoying i just havent been able to work till it was fixed so thanks again.

---

### Post by komoto on 2008-09-23
No problem.

-Kom

---

### Post by webmiester on 2009-03-20
Hi, Im on Ubuntu 8.10...

It's happening to me too.  Im using the Human theme but it would occasionally load the icons from the Gnome theme...

What's really interesting though is that the computer seems to know it has made a mistake becuase when I click on system>Preferences>Appearance, the computer would suddenly log out and go into the log-in screen.  After loging in again, it would display the correct themes

---

### Post by carlossl on 2010-09-07
Hi, I know it's been two years since this thread was opened, but I installed Karmic one week ago because its kernel is the only one that works with my laptop.

I'm having the same issues with my GTK engines, did someone find a solution to this problem? I [opened another thread here]("http://ubuntuforums.org/showthread.php?t=1570064") explaining my situation, hoping that someone can help me in the Gnome section.

---

