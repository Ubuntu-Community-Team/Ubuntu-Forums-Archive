---
title: "devilspie geometry not setting windows where i want them"
date: 2007-12-30
forum: General Help
---

### Post by 0okami on 2007-12-30
Im having an issue getting devilspie working the way i want it. 

I am trying to get a terminal positioned to the top right hand side of my screen. 

my ~/.devilspie/DesktopConsole.ds file reads as follows: 
```

(if
        (matches (window_name) "DesktopConsole")
        (begin
                (set_workspace 1)
                (below)
                (undecorate)
                (skip_pager)
                (skip_tasklist)
                (wintype "utility")
		(geometry “400×300+0-22”)

         )
)

```

Every time i make changes to the geometry, it seems to affect nothing. 

Example: 
(geometry “400×300+1000-1000”) Does nothing
(geometry “400×300-1000+1000”) Does nothing
(geometry “400×300+500-500”) Does nothing
(geometry “400×300-500+500”) Does nothing

They all make my transparent terminal window stay at the top left. I want it to the top right... Any ideas? 

Screenshot attached.

~0okami
ubuntu 7.10

Any help greatly appreciated.

---

### Post by dlegend on 2007-12-30
What is your screen resolution? Try this:

```

(if
        (matches (window_name) "DesktopConsole")
        (begin
                (set_workspace 1)
                (below)
                (undecorate)
                (skip_pager)
                (skip_tasklist)
                (wintype "utility")
		(geometry “400×300+600+30”)

         )
)

```

It should be setting width as 400, height as 300, moving it to the right 600 and down 30. This would be optimal for 1024x768 resolution (because 600 + 400 = 1000, 24 pixels to touch the right edge of the screen)

---

### Post by 0okami on 2007-12-30
> **dlegend said:**
> What is your screen resolution? Try this:

```

(if
        (matches (window_name) "DesktopConsole")
        (begin
                (set_workspace 1)
                (below)
                (undecorate)
                (skip_pager)
                (skip_tasklist)
                (wintype "utility")
		(geometry &#8220;400×300+600+30&#8221;)

         )
)

```

It should be setting width as 400, height as 300, moving it to the right 600 and down 30. This would be optimal for 1024x768 resolution (because 600 + 400 = 1000, 24 pixels to touch the right edge of the screen)

Ok, i tried it by typing (geometry &#8220;400×300+600+30&#8221;)  and it didn't move. Screen res is 1024x768
So i copied and pasted the same code mentioned above and now its saying this: 
> ookami@navi:~$ devilspie

** (devilspie:17417): WARNING **: Error in parsing: Unexpected token encountered: 226
Cannot parse /home/ookami/.devilspie/DesktopConsole.ds: Unexpected token encountered: 226
No s-expressions loaded, quiting
ookami@navi:~$ 




This is the content as the moment: 
```

(if
        (matches (window_name) "DesktopConsole")
        (begin
                (set_workspace 1)
                (below)
                (undecorate)
                (skip_pager)
                (skip_tasklist)
                (wintype "utility")
		(geometry &#8220;400×300+600+30&#8221;)

         )
)

```

Only difference i see are the quotation marks... and if i match all quotation marks, Its still in the same place. Top left corner.

---

### Post by dlegend on 2007-12-30
Did you try closing your terminal window then opening it again? This would do it (to make sure the settings are reapplied):

> 
killall devilspie
killall gnome-terminal
devilspie
gnome-terminal --window-with-profile=DesktopConsole



Yeah the only difference in the code I gave you was the geometry size. I just copied yours and put it into the code box as an example.

---

### Post by 0okami on 2007-12-31
nope. still ending up in the same spot. 

I killed all processes and checked in the system monitor to make sure they were not running, loaded two terminal windows, in one i typed: 
devilspie

and in the other i typed 
gnome-terminal --window-with-profile=DesktopConsole

A new terminal window opened integrated onto the desktop... as it should, but its like the only settings that work are the size...it refuses to be relocated to the right side of my screen where i want it.

---

### Post by dlegend on 2007-12-31
Hmm I'm not sure then.. Here's my DesktopConsole.ds file if it helps:

```

(if
	(matches (window_name) "daniel@Se7en: ~ - daniel@Se7en: ~")
	(begin
		(stick)
		(below)
		(undecorate)
		(skip_pager)
		(skip_tasklist)
		(wintype "utility")
		(geometry "954x100+30+630")
	)
)

```

I have mine set up so the console title is set differently because it'd change to user@computer whenever I logged in and wouldn't apply my settings correctly. You can see a picture of my setup here:

[http://www.programming-designs.com/misc/12-27-07_1.png](http://www.programming-designs.com/misc/12-27-07_1.png)

Edit: Are you using "x" for the size of the window? It looks like from your post that it is a different character. Or maybe that is just something to do with the post conversion?

> 
(geometry &#8220;400×300+600+30&#8221;)
versus
(geometry &#8220;400x300+600+30&#8221;)


---

### Post by 0okami on 2007-12-31
Im using what ever gets outputted from the keyboard when i strike the X key. ^_^ 
Should it be lowercase or upper case? 

and about the window name can you elaborate more on that?

---

### Post by dlegend on 2007-12-31
> **0okami said:**
> Im using what ever gets outputted from the keyboard when i strike the X key. ^_^ 
Should it be lowercase or upper case? 

and about the window name can you elaborate more on that?

I put lowercase X in mine. I guess that isn't the issue then (just wanted to be sure). As for the window_name issue I posted about it originally at this thread: [http://ubuntuforums.org/showthread.php?t=652173](http://ubuntuforums.org/showthread.php?t=652173)

I didn't get any answers but was able to find the problem. The problem only occurs when the terminal is being launched automatically on start up. The terminal is somehow changed to "username@computer: ~" regardless of what I set the title to in the profile. I posted my solution to the problem in that thread as well.

Anyway, back to your problem. Have you read this how-to thread? [http://ubuntuforums.org/showthread.php?t=202249](http://ubuntuforums.org/showthread.php?t=202249)

I did a lot of reading through the posts to finally get my configuration set up correctly. There might be some unknown factor that is playing into this such as compiz settings or something else.

---

### Post by 0okami on 2007-12-31
here's something that worked for me... 

```
#!/bin/sh

if ps -A | grep -e " devilspie$" > /dev/null; then
	killall gnome-terminal &
	killall devilspie &
else
	gnome-terminal --window-with-profile=DesktopConsole --geometry=80x35+10-0 --working-directory=/home/$USER &
	devilspie&
fi



```

That was made into a file called load_devilspie.sh
gave it execute rights
and set it into session load (start up)

All is good now. I can position the window where ever by modifying the geometry settings in the sh file.

---

### Post by KuraKai on 2008-03-14
Ok I am having issues with geometry also, I figured it would better to post it here since it relates somewhat with it. My issue is that geometry, maximize, etc. refused to touch the bottom ten-twenty pixels of my screen!
```

(if
	(is (window_name) "Warcraft III")
	(begin
		(undecorate)
		(geometry "1280x800+0+0")
	)
)

```
The window spawns in the top left below the top panel, the borders are removed and it gets resized to almost full screen. But the problem is there is a 10-20 pixel gap at the bottom.

[http://i54.photobucket.com/albums/g82/Kura_Kai/Screenshot.png](http://i54.photobucket.com/albums/g82/Kura_Kai/Screenshot.png)

---

