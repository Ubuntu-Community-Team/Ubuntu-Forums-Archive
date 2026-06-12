---
title: "beryl &amp; workspace switcher (wont turn cube)"
date: 2007-01-18
forum: General Help
---

### Post by STREETURCHINE on 2007-01-18
my workspace switchers have stopped rotating the desktop cube for some reason,
worked fine last night before i went to bed,woke up this morning went to turn the cube no luck.

it still turns with the scroll wheel.

and i never made any adjustments,i had a look through the settings but since the switchers just worked when i installed beryl i have no idea where to look.

any body know how to fix this(no big drama just curious):-D

---

### Post by STREETURCHINE on 2007-01-18
still curious......

and sometimes it fails to find the gstreamer pluggins,and outher times it finds them,,,,:rolleyes:

---

### Post by STREETURCHINE on 2007-01-18
now it is expieriencing random crashes ,after running so well for so long ,how come it just starts to break

---

### Post by allwin on 2007-01-18
Don't know if you noticed, but just today there was an automatic update of Beryl to 0.1.5.  Could you have put that on without realizing it?  I was surprised that it came up in the update notification dialogue already!

---

### Post by STREETURCHINE on 2007-01-18
that may be what is going on i have set security updates to automatic,but outher than that i have had no updates showing today.

i think when beryl starts it is still 0.1.4 so i dont really know ,but it seems strange for things to go wrong suddenly with no change to the setting..

---

### Post by doobiest on 2007-04-11
**I'm moving this to a new post as this thread is old**

I have the same issue.. Or at least similar symptoms.

My current workspace settings are:

4 workspaces, which is reflected in the workspace switcher.

4 sides to the cube

Here's what I've noticed:

Rotating the cube from side 1 through 4, does not show a progression in the workspace switcher. Instead, the workspace switcher always shows workspace 1 being selected, but the preview of windows shown in workspace 1 keep updating while im changing the sides of the cube.

Manually picking workspace 1 through 4 in the workspace switcher does not rotate the cube, instead it takes me to blank workspaces. In other works, If I put a windows on each side of the cube, then navigate using the workspace switcher from workspace 1 through 4, i'm presented with blank workspaces, it does not show me the "cube's" workspaces.

Conclusion:

The cube's workspaces and gnome's native workspaces are operating independantly.

More Details:

-I'm using Feisty, so hey it's Beta

-This did work the other day

-Beryl doesnt load inherently for me when gnome starts, I had to set beryl up manually to load on gnome start up

-Reason for the manual setting is because under 'Desktop Effects', when 'Workspaces on a Cube' is selected, it does not work for me.. no cubing.

-Also, I had to apt-get Beryl, it did not appear to be built into Feisty, even though the option to supposidly enable it through "Desktop Effects' was there by default.

-The furthest I went to verify if Beryl comes natively with Feisty was to go to a bash prompt, type in beryl and beryl-manager, and notice that the command was not found.

-The taskbar shows all applications on any cube, even though the taskbar's settings are set to show only tasks on the current workspace

-Adjusting the number of workspaces in the workspace switcher from 4 - 5 does not increase the number of sides to the cube

-Adjusting the number of sides to the cube in Beryl Manger from 4 -5 DOES increase the number of workspaces in the workspace switcher

I'll continue to investigate but any help would be welcome.

---

### Post by SanoDiMente on 2007-06-08
I have the same problem of doobiest
beryl and the workspaces switcher seem working independently.
Each one do not make any change in the other one.
What may I do?
Thanks for yr help

---

### Post by phaed on 2007-06-18
I had the same problem and solved it the following way:

In the Beryl Settings Manager, make each of these settings have the designated value:

Horizontal Virtual Size: 4
Vertical Virtual Size: 1
Number of Desktops: 1

For some reason those values were off for me (the vertical virtual size was set to 13!).  I restarted Beryl and voila, Beryl's workspace switcher (the undivided box) showed up and worked perfectly.

This might work for you.

---

### Post by process91 on 2007-08-17
This is the full explanation as I have figured it. The workspace switcher and beryl aren't working independently, they're working codependently. Think of workspaces and faces of the cube as separate entities. Each workspace could be considered one cube. For instance, in the workspace switcher if you put in two workspaces and your cube was set to have 4 sides then you would have two cubes which four sides each, giving you a total of eight desktops. With beryl and the desktop cube, each workspace becomes it's own cube.

Not to beat a dead horse, but if you had two workspaces and opened windows in one and switch to the other you could open more windows and switch between them as you would normally. You could even put windows on different faces of the cube and it would keep the location of each window even when switching workspaces.

To help create the effect most people are after (a single cube with four faces) the settings are below:

Horizontal Virtual Size: 4
Vertical Virtual Size: 1
Number of Desktops: 1

However, you can tweak this out to your heart's content. The horizontal virtual size setting will increase the faces of the cube. The Number of Desktops will create more workspaces, each with their own cube. I'm not 100% sure if the vertical virtual size does anything useful, although it does change the workspace switcher to show two rows even though it doesn't seem to allow me to switch to it. I have these settings:

Horizontal Virtual Size: 6
Vertical Virtual Size: 1
Number of Desktops: 2

Which gives me two workspaces each with an 3-d hexagon of virtual desktops.

---

