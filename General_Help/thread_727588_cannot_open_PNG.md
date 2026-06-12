---
title: "cannot open PNG"
date: 2008-03-17
forum: General Help
---

### Post by lawls on 2008-03-17
This is the message I get when I open a PNG
[IMG]http://i26.tinypic.com/wlf31w.png[/IMG]

I've tried reinstalling EOG, with no luck, but none of my programs can open them anyway.
The only way I can open them is by renaming the file. But after a few minutes, I get that message again.

I haven't installed anything. I did download an icon set from gnome-look. One of the icons was broke, and it seemed after that all the other PNG files stopped working too. I deleted all of the icons.

---

### Post by gobbles414 on 2008-03-18
> **lawls said:**
> This is the message I get when I open a PNG
[IMG]http://i26.tinypic.com/wlf31w.png[/IMG]

I've tried reinstalling EOG, with no luck, but none of my programs can open them anyway.
The only way I can open them is by renaming the file. But after a few minutes, I get that message again.

I haven't installed anything. I did download an icon set from gnome-look. One of the icons was broke, and it seemed after that all the other PNG files stopped working too. I deleted all of the icons.

Have you installed all available updates for your system? PNG files should work in a default installation of Ubuntu. So something has definitely gone wrong on your PC. One possible solution that you can try is to remember the most recent time that PNGs displayed correctly in your Ubuntu, and then uninstall all of the packages/programs that you've installed since then. You can get a list of what programs were installed when by going *System => Administration => Synaptic => Package Manager => File => History*. I recommend that you use the **complete removal** option in Synaptic -- right-click on each of the packages that you want to uninstall --and then restart your PC. Or, you can always just reinstall Ubuntu from the LiveCD.

Does this help?

---

### Post by lawls on 2008-03-18
Yes, my system is up to date. PNGs have been working up until last night. The most recent installations have all been updates.
My PNGs still work...
The thumbnails still show up in nautilus. When I try to open them though, I get that message. 

When I rename the picture from something like..
wallpaper.png to wallpaper1.png
or wallpaper.png to wallpaper.PNG
I **can** open it with any program again
But then it'll stop working once I close nautlius, and I have to rename it to open it.

This all happened after I downloaded an icon set and tried to view a corrupted icon (which happened to be a png)

Sorry if this sounds rude, but don't you think reinstalling the whole OS because of a minor problem like this would be ridiculous? But thanks for your help anyway :)
Still need help though >_<

---

### Post by gobbles414 on 2008-03-19
> **lawls said:**
> Yes, my system is up to date. PNGs have been working up until last night. The most recent installations have all been updates.
My PNGs still work...
The thumbnails still show up in nautilus. When I try to open them though, I get that message. 

When I rename the picture from something like..
wallpaper.png to wallpaper1.png
or wallpaper.png to wallpaper.PNG
I **can** open it with any program again
But then it'll stop working once I close nautlius, and I have to rename it to open it.

This all happened after I downloaded an icon set and tried to view a corrupted icon (which happened to be a png)

Sorry if this sounds rude, but don't you think reinstalling the whole OS because of a minor problem like this would be ridiculous? But thanks for your help anyway :)
Still need help though >_<

I assume that you've tried deleting the corrupted PNG icon. If not, delete it and as many related files/packages as you can from your PC. Also, right-click on a PNG file in Nautilus and go *Properties => Open With*. What's selected there? Maybe you should change the default program for PNG files. Does this problem exist in other user account in your Ubuntu? If none of these thoughts are helpful, you can try running the following maintenance routines in the command line. Restart you PC once they've completed successfully:

[I]sudo apt-get --purge autoclean
sudo apt-get --purge autoremove
sudo run-parts -v /etc/cron.daily
sudo run-parts -v /etc/cron.weekly
sudo run-parts -v /etc/cron.monthly[/I]

Regarding reinstalling the entire OS -- Of course, I encourage you to wait until others in this forum have had a chance to offer their suggestions before you take such drastic action. But, sometimes it's more efficient to reinstall an operating system than it is to spend hours trying to fix a hard-to-solve problem. This is especially true in cases where the cause of the problem is known and can be avoided -- such as your broken icon. Another factor to consider is the fact that Ubuntu 8.04 will be released in April. If you cannot solve this problem by April, then at least you'll have a newer version of Ubuntu to try. :)

---

### Post by lawls on 2008-03-20
The problem is Nautilus.
I don't know why I couldn't open them with GIMP before, but I'm able to open them in any program though Nautilus with "Open with." I only get the message when I double-click a PNG.
I reinstalled Nautilus and everything associated with it (that came up in synaptic) but I still have problem.

---

### Post by gobbles414 on 2008-03-20
> **lawls said:**
> The problem is Nautilus.
I don't know why I couldn't open them with GIMP before, but I'm able to open them in any program though Nautilus with "Open with." I only get the message when I double-click a PNG.
I reinstalled Nautilus and everything associated with it (that came up in synaptic) but I still have problem.

Very strange indeed... At least you've discovered a temporary workaround.

---

