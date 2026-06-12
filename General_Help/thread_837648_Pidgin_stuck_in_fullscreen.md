---
title: "Pidgin stuck in fullscreen"
date: 2008-06-22
forum: General Help
---

### Post by central419 on 2008-06-22
Hello Community,

I was doing something inside Compiz, but obviously I did something wrong.
I tried to make windows I maximize normally to not maximize completely, but rather only maximizing to 1 side of the screen. I know it sounds silly to do.
I tried to do this with the windows rules plugin.
When the changes took effect I realized it wasn't what I wanted:
All my windows were maximized completely, in full screen mode.
I turned the plugin off again and Nautilus went back to normal, in window mode.
Pidgin did not.
It's stuck in full screen mode, and thanks to AWN I'm still able to shut it off or move to another desktop.

My question: How do I toggle Pidgin back to window mode?

---

### Post by bthoward on 2008-06-22
Try holding alt and right clicking in the window.  Or right clicking on the title bar and clicking restore.  Does it just not respond to these?

---

### Post by central419 on 2008-06-22
The titlebar is not existing, I see the menu though.

Alt+Ctrl+Button1 gives me the rotate-cube. But it does not make pidgin go back to window mode.

Any other ideas?

---

### Post by central419 on 2008-06-22
Might reinstalled pidgin help?

---

### Post by central419 on 2008-06-24
> **central419 said:**
> It's stuck in full screen mode
My question: How do I toggle Pidgin back to window mode?

I found the answer, after trying several things.
This is what I did:

I went into my home directory and pressed ctrl+H to show hidden files/folders.

I went into /.purple and opened up prefs.xml

You might want to make a backup of this file, before you edit anything in it.

Pidgin needs to be closed for this ofcourse.

I did a seurch inside the XML file for "height".
Second one that was found inside:

		<pref name='blist'>
			<pref name='show_buddy_icons' type='bool' value='1'/>
			<pref name='show_empty_groups' type='bool' value='0'/>
			<pref name='show_idle_time' type='bool' value='1'/>
			<pref name='show_offline_buddies' type='bool' value='0'/>
			<pref name='show_protocol_icons' type='bool' value='0'/>
			<pref name='list_visible' type='bool' value='1'/>
			<pref name='list_maximized' type='bool' value='1'/>
			<pref name='sort_type' type='string' value='alphabetical'/>
			<pref name='x' type='int' value='0'/>
			<pref name='y' type='int' value='0'/>
			<pref name='width' type='int' value='300'/>
			<pref name='height' type='int' value='600'/>
			<pref name='tooltip_delay' type='int' value='500'/>
		</pref>

Which is where my height and width were insanely high.
I changed those 2 values to something acceptable (as shown above) and saved the document.

Now I launched Pidgin, and it still came up maximized, but NOT fullscreen.
I dragged pidgin around and it went exactly to the size I specified in the xml document.

Hope this helps anyone.

---

