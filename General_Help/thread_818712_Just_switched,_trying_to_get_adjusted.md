---
title: "Just switched, trying to get adjusted"
date: 2008-06-04
forum: General Help
---

### Post by pilate on 2008-06-04
Hey I've got a Vostro 1500 running 8.04, and save for a few issues, it's running great. I even installed a new bluetooth module and it recognized it quicker than XP did. 
I've got a few questions about getting the thing just right. This is my first time really giving linux a shot and I think this may be the time I stay.

1)This may be a firefox thing but when I highlight the address bar or the search box and click my cursor into the box, to start typing, it doesn't highlight all the text like it does on my XP side. Is there a way to change it so it does?

2)If I don't move the mouse constantly the screen dims. I like the dimming, but it happens too fast. Any way to make it wait longer before dimming?

3)When I play a video clip, it looks pretty choppy, and the audio quality isn't that great. I tried it with the default video player that came installed with Ubuntu, and also with VLC. I'm sure you'll need more information about this one, but I'm not sure what to tell you, so please let me know.

4)How do I set up my own hot keys? For example I would like to press win+t and have a terminal window open up.

5)Each time I restart my computer the brightness goes down. I would like it to stay at the spot I set it to last

6)I have all my media(docs, video, music) in a separate partition than my windows partition. How can I make things like Documents, Music, etc. under Places to point to the folders in this other partition instead of where they point now

Thank you for the help. Let me know if I left out something important or if I put this in the wrong spot.

---

### Post by lisati on 2008-06-04
Welcome to Ubuntu.

> **pilate said:**
> 2)If I don't move the mouse constantly the screen dims. I like the dimming, but it happens too fast. Any way to make it wait longer before dimming?
You might want to start by checking the Screensaver settings. These can be found on the System->Preferences menu.

> **pilate said:**
> 4)How do I set up my own hot keys? For example I would like to press win+t and have a terminal window open up.
You can set some "hotkeys" - it's called "Keyboard Shortcuts" - again, this is on the System->Preferences menu.


> **pilate said:**
> 5)Each time I restart my computer the brightness goes down. I would like it to stay at the spot I set it to last
This *might* be helped with the screensaver settings. (See my answer to #2)

Hope these ideas help.

---

### Post by pilate on 2008-06-04
> **lisati said:**
> 
You might want to start by checking the Screensaver settings. These can be found on the System->Preferences menu.

I haven't found anything in the Screensaver settings to adjust the dimming feature. It just adjust the idle feature.

> 
You can set some "hotkeys" - it's called "Keyboard Shortcuts" - again, this is on the System->Preferences menu.

I couldn't find anyway to add new shortcuts. All I could find was ways to edit existing shortcuts.

> 
This *might* be helped with the screensaver settings. (See my answer to #2)



Thanks for the welcome
Same as before, couldn't really find anything here or in the power settings.

---

### Post by doorknob60 on 2008-06-04
> 3)When I play a video clip, it looks pretty choppy, and the audio quality isn't that great. I tried it with the default video player that came installed with Ubuntu, and also with VLC. I'm sure you'll need more information about this one, but I'm not sure what to tell you, so please let me know.

What video card do you have? Did you install the restricted drivers? If not, go to System > Administration > Restricted Drivers Manager (I think it might be called hardware Drivers or something like that in 8.04).

> 6)I have all my media(docs, video, music) in a separate partition than my windows partition. How can I make things like Documents, Music, etc. under Places to point to the folders in this other partition instead of where they point now

Open the file manager to your home folder, and delete the Music, Documents, Pictures, and all those folders (assuming they're empty). Then, browse to where your files are currently located in a new window, and drag the folders over to your home folder while holding down ALT, and choose Link here. Then, rename the linked folders to what they were originally called before you deleted them (Music, Pictures, Documents, etc). That should do it :)

---

### Post by Pjotr123 on 2008-06-04
Welcome!  :-)

You might find this to-do list handy:
[http://ubuntutip.googlepages.com/thefirstthingstodo](http://ubuntutip.googlepages.com/thefirstthingstodo)

Greeting, Pjotr.

---

### Post by Ameneon on 2008-06-04
The screen brightness I believe is a BIOS setting. I can't recall the 1500's BIOS at the top of my head but check there (F2 when starting the system) whether there are brightness settings and adjust as needed. I don't know if Dell have any own applications bundled for Ubuntu as they do on Windows (or whether you bought the machine with Ubuntu or installed it later), in Windows there is an application called Quickset that adjusts those things as well, something you could look for in your menus if this is a Dell-installed Ubuntu or you've installed any Dell software since the time of purchase.

As for shortcuts, there's an app called Ubuntu Tweak which I believe you can get at getdeb.net which allow you to add your own shortcuts, I'm sure there's a CLI way to do it as well (prolly in some etc folder) but I'm as of yet not all that familiar with the exact system files in Linux.

---

### Post by pilate on 2008-06-04
Awesome. That took care of a bunch of problems. I'll have to check the bios to see about the dimming.
Got the restricted driver for my nvidia card, and video seems a lot better. Any way to make that icon in my taskbar go away though? The one that lets me know I'm using a restricted driver?
Is there a way to have a harddrive auto-mount when I log on, without having it display an icon on the desktop?
Can I edit what shows up in the Places list?

---

### Post by alzyee on 2008-06-04
> **pilate said:**
> 
Can I edit what shows up in the Places list?

When in the File Browser drag folders into the side pane. If it is not displayed it is under View menu.

> **pilate said:**
> Is there a way to have a harddrive auto-mount when I log on, without having it display an icon on the desktop?

I would find the UUID partition you want to mount replace sda1 with what you need
```
sudo vol_id -u /dev/sda1
```


edit /etc/fstab with 
```
sudo gedit /etc/fstab
```

if the partition is ntfs a the line below should work 
```
UUID=10187A7F187A639E /media/disk ntfs-3g defaults,locale=en_US.utf8 0 0
```

or if you would rather use the /dev/... 
```
/dev/sda1 /media/disk ntfs-3g defaults,locale=en_US.utf8 0 0
```

The advantage of the UUID is that it will not change where with several drives the location in /dev might

---

