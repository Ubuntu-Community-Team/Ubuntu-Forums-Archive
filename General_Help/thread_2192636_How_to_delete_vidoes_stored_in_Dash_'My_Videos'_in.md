---
title: "How to delete vidoes stored in Dash 'My Videos' in 12.04?"
date: 2013-12-09
forum: General Help
---

### Post by cybrsaylr on 2013-12-09
When I right click Dash Home > Videos, My Videos shows 19 recently viewed vids. 
How do you delete/erase those vids stored in My Videos?

---

### Post by monkeybrain20122 on 2013-12-09
Go to System Settings > Privacy to delete history from the beginning. In 13.04 and 13.10 there are more fine grained controls for you to exclude files from certain directories from being logged, but as far as I can remember those options were not present in 12.04 (I could be wrong as I have upgraded long time ago, check the settings)

---

### Post by deadflowr on 2013-12-09
> **monkeybrain20122 said:**
> Go to System Settings > Privacy to delete history from the beginning. In 13.04 and 13.10 there are more fine grained controls for you to exclude files from certain directories from being logged, but as far as I can remember those options were not present in 12.04 (I could be wrong as I have upgraded long time ago, check the settings)

Yep, that's how you do it.
The unfortunate thing is that the delete history from beginning of time will remove everything else as well in the recently used listings.
So if you have been using several apps or files and open the dash and see them in the recent sections, they will be gone, at least until you open them up again.

---

### Post by cybrsaylr on 2013-12-09
OK guys I knew about System Settings > Privacy. Did that and the videos and music files were not removed. They still remain. 
In 12.04 there is 'All' for a choice not 'beginning'. Clicked 'All' and tried to delete a couple times not nothing was removed in Dash.

I vaguely recall you have to go deeper into the OS to remove them but can't recall what is needed.


PS: I also turned off the 'record activity' switch in Privacy long time ago.
These were old files that still remain in Dash and I believe they are harder to remove.

---

### Post by monkeybrain20122 on 2013-12-09
You may have to reboot or logout.

If it still doesn't work, try this:

I found a screenshot for the privacy settings in 12.04 [http://landoflinux.com/linux_ubuntu_privacy_settings_1204.html](http://landoflinux.com/linux_ubuntu_privacy_settings_1204.html)

1.Try first check the do not record option for video and then exclude the Videos folder

2.delete history

3.rename the videos you don't want appear in the dash (assuming that they are in the Videos folder), it can be something simple like changing a small letter to capital.

4 log out or reboot

It should work because if the file no longer exists in your system the  dash won't show it (e.g if you view some files from an usb, it will show  up in the dash only as long as the usb drive is attached) Since you  have renamed the files the old ones no longer exist and the new ones are  not being logged because of the exclusions in step 1. Step 2 should not be necessary, but what the heck, you clean your history already. :)

---

### Post by cybrsaylr on 2013-12-09
monkeybrain20122 thanks. Will give that a try.

---

### Post by cybrsaylr on 2013-12-09
Renamed Videos to, Videos 1 and that wiped out the vids being held in Dash!
So that worked.

Now Music in Dash (right above Videos) shows ~100 songs and ~100 albums in Dash!
How do they get removed?

---

### Post by monkeybrain20122 on 2013-12-09
Set do not record option to Music folder
Change folder name to Music-1 
Don't open the music files in it !
Change it back to Music
:)

Edited: If after this operation the Music folder no longer shows up in Nautilus, go to your home, choose view hidden files in Nautilus (or Ctrl + h)  open .config and edit usr-dirs.dirs to change

XDG_MUSIC_DIR="" 

back to

XDG_MUSIC_DIR="$HOME/Music"

---

### Post by deadflowr on 2013-12-09
There is a file that holds the info
~/.local/share/zeitgeist/activity.sqlite
You can delete that.
Don't worry, it regenerates.

Edit: If it doesn't regenerate, it's probably because you have the record off.

---

### Post by cybrsaylr on 2013-12-09
> **deadflowr said:**
> ~/.local/share/zeitgeist/activity.sqlite
You can delete that.
Don't worry, it regenerates.

Edit: If it doesn't regenerate, it's probably because you have the record off.

Those files are baaaccccck!

Indeed it does regenerate.

Shutdown last night.
Bootup today, go into Dash and those videos I thought were deleted last night are back in spite of having record off in Privacy.

Zeitgeist jogs my memory. 
Believe zeitgeist is the culprit and is storing those vid and music files. Played around with zeitgeist in the past but forgot how to maneuver about with it.

---

### Post by monkeybrain20122 on 2013-12-09
It seems that renaming the Video folder is not going to work because as soon as you change back to the original name the files come back. It is like if you unplug a usb the files in it are gone from the dash but when you plug it back the dash remembers somehow. So you have to first set exclude the Video folder from recording activities and then rename those files and keep their new names.

---

### Post by cybrsaylr on 2013-12-10
OK. Tried another angle. Renamed Videos folder in Home back to its default name. 
Then created a new Vids folder right next to the Videos folder in Home. Moved all Video files to the new Vids folder, leaving Video folder empty and Dash now shows all those regenerated files gone again! 

 Privacy is set to exclude audio and video files and the Record Activity switch is turned off......will keep my fingers crossed and see how this works.

---

### Post by monkeybrain20122 on 2013-12-10
It won't work unless you have excluded the Vids folder from privacy settings BEFORE you move the files from Videos to Vids, for otherwise activities in Vids would be recorded.

If you want to live with the default Videos folder having a different name, you could have done:
Create a new folder named Vids
Exclude it from privacy settings
Rename Vids to Vids-1
Rename Videos to Vids
then delete Vids-1
Reboot/logout. 

That should work too (without moving files). The hard part is if you want to keep the folder's name.

---

### Post by cybrsaylr on 2013-12-10
> **monkeybrain20122 said:**
> It won't work unless you have excluded the Vids folder from privacy settings BEFORE you move the files from Videos to Vids, for otherwise activities in Vids would be recorded.

Did exclude the Vids folder from privacy settings BEFORE I moved the files from Videos to Vids and so far it has worked. 

Don't mind having a Videos and Vids folder in Home, so will consider this solved.

---

