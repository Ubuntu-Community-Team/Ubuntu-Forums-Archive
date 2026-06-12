---
title: "Is it possible to use Firebox and Thunderbird from Windows in Wubi?"
date: 2007-06-02
forum: General Help
---

### Post by Romanus81 on 2007-06-02
I use Firefox and Thunderbird in Windows, is it possible that I can have Wubi share these? So my messages in Thunderbird and my favorites in Firefox are the same?

---

### Post by ago on 2007-06-02
Yes you can copy the favorites over, it's only on file, we have a migration-wizard to automatically import those settings for you but it is not ready yet.

---

### Post by tuxcantfly on 2007-06-02
from what I see, you want to share the files, not import them? In that case, make a symlink from /media/host/Documents\ and\ Settings/yourusername/Application\ Data/Mozilla to .mozilla (for firefox) and another from /media/host/Documents\ and\ Settings/yourusername/Application\ Data/Thunderbird to .mozilla-thunderbird (for thunderbird)

you can create the symlinks with the file browser (right-click, make link in nautilus), or with the command ln -s (targetdir) (symlink)

---

### Post by Romanus81 on 2007-06-03
Thank you, but I'm kind of new to Ubuntu, I just got Wubi a few days ago, is there an FAQ or something that can help me make the symlink?
I just want to share the profiles so that my favorites on firefox and my messages on Thunderbird are shared, I've heard that I would need to partition FAT32, but I am not sure how to do that, would the symlink make it unnecessary? If I do need to partition FAT32, how would I do that safely?

---

### Post by Romanus81 on 2007-06-03
any extra advice would be appreciated.

---

### Post by tuxcantfly on 2007-06-03
there's no need to use a FAT32 partition, here's how you do it (by the way you'll lose any emails or bookmarks on the ubuntu install, make sure you back them up beforehand if you need to):

open up a terminal (Applications -> Accessories -> Terminal)
type this in:

```
rm -r .mozilla
rm -r .mozilla-thunderbird
ln -s /media/host/Documents\ and\ Settings/yourusername/Application\ Data/Mozilla .mozilla
ln -s /media/host/Documents\ and\ Settings/yourusername/Application\ Data/Thunderbird .mozilla-thunderbird
```

make sure you substitute your windows username for "yourusername" in the commands above

---

### Post by Romanus81 on 2007-06-04
It created the links, I got a message confirming it after I typed all that in, but I can't get firefox or thunderbird to start, I click on it and it says "Starting Firefox" on the bottom bar, nothing pops up, and the cursor changes to the loading cursor, and after about 5 or 6 seconds it just closes. 
I might have just typed something in wrong, is there a way I can restore the firefox files?

---

### Post by ago on 2007-06-04
> **Romanus81 said:**
> It created the links, I got a message confirming it after I typed all that in, but I can't get firefox or thunderbird to start, I click on it and it says "Starting Firefox" on the bottom bar, nothing pops up, and the cursor changes to the loading cursor, and after about 5 or 6 seconds it just closes. 
I might have just typed something in wrong, is there a way I can restore the firefox files?

Not sure how FF/TB cope with windows specific settings/plugins. Start with an empty profile (FF will create one for you) then only symlink the file you really need, like bookmarks.html.

---

### Post by Romanus81 on 2007-06-04
If I try to do anything to firefox or thunderbird, I just get this message,
"files list file for package `firefox' contains empty filename "
I've tried reinstalling it in synaptic and in the add/remove package manager.

---

### Post by tuxcantfly on 2007-06-04
> It created the links, I got a message confirming it after I typed all that in

You didn't type it in right, you're not supposed to get any message if you typed it in correctly; that was an error message. See the instructions below for creating symlinks, they should be easier to follow.

> Not sure how FF/TB cope with windows specific settings/plugins. Start with an empty profile (FF will create one for you) then only symlink the file you really need, like bookmarks.html.

Neither the firefox nor profile doesn't have any issues with windows-specific settings, I have my firefox and thunderbird set up exactly like this and it works fine; the symlink is likely broken, that's what's causing the issue. Open a terminal, and type in:

```
file .mozilla
file .mozilla-thunderbird
```

does it say "broken symbolic link" anywhere? If so, you didn't enter the command in correctly. Instead, just do it manually with the file manager. First delete the existing symlinks:

```
rm -r .mozilla
rm -r .mozilla-thunderbird
```

Then open the file manager, Places -> Computer
Then click Filesystem
Then click media
Then click host
Then click Documents and Settings
Then click on the folder that has the name of whatever your username in windows is
Then click Application Data
Then right-click Mozilla, and click "Make link"
Then right-click Thunderbird, and click "Make link"
Then move the links that were created to your user's home directory (/home/yourusername)
Then rename the link to the Moziila folder to .mozilla, and rename the link to the Thunderbird folder to .mozilla-thunderbird

Then enter this command to make sure the symlinks were properly created
```
file .mozilla
file .mozilla-thunderbird
```

Now it shouldn't say anything about "broken symbolic link"; if it does, repeat the instructions above
Now start up firefox and thunderbird, it shouldn't have any issues

---

### Post by Romanus81 on 2007-06-05
Ok, I got it to work. Thanks for your help.
I had to do it a little differently, for future reference if anyone else needs it.
Go into the windows firefox folder using the file browser
(/media/host/Documents and Settings/[usename]/Application Data/Mozilla/Firefox/Profiles)
Right click your profile and select "make link"
Open another browser and go to the Ubuntu firefox folder
(/home/[username]/.mozilla/firefox/) (the folder wasn't visible, so I had to type it into the file browser. 
And click and drag the link from the windows folder to the ubuntu folder.
Rename the link so it is just xxxxxxx.default (the x's are different for everybody)
Exit out of firefox
Edit profiles.ini
Where it says path=xxxxxxx.default, change it to
Path=/home/[username]/.mozilla/firefox/xxxxxxxx.default
and change isrelative=1 to isrelative=0
save and open firefox.

---

