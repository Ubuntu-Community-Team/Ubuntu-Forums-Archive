---
title: "HELP Desktop folder lost it's name and now isn't recognized"
date: 2015-07-04
forum: General Help
---

### Post by Luxx on 2015-07-04
I need to restore my default Desktop folder in my Home folder. I was saving a text document in gedit and this is what happened:

FIle>Save As>Name: Yard care, to Desktop, hit save. The box blinked and the folder I was in was unnamed. 

It showed:
Save in folder [user] [  ]   That's the Home folder and a folder icon with no name. It did have the symbol of the Desktop folder on it, but that has disappeared now as well and it's just a plain folder in the Home folder.

I can't save anything to my Desktop folder from the save menu in any program now. I click on Desktop in the sidebar and it doesn't do anything. Trying to get to the Desktop folder in Nautilus doesn't work either. As far as my file manager is concerned, there is no Desktop folder. When I navigate to the Desktop folder in the Places menu I get the following error:

"Could not open location 'file:///home/v/%20%20'
Error when getting information for file '/home/user/  ': No such file or directory"

When this first happened I renamed the folder to Desktop, so at least I know where my Desktop stuff is, but Ubuntu can't find my Desktop folder, or doesn't recognize it as my Desktop. How can I fix this? 

And if anybody has a clue how this could have happened, please share some insight. I didn't think that could happen.

---

### Post by Luxx on 2015-07-04
Everything looks normal in the user-dir.dirs file, so I'm stumped. I don't understand why my computer isn't recognizing my Desktop folder when it is correctly specified in user-dir.dirs.

---

### Post by PaulW2U on 2015-07-04
Take a look at ~/.config/user-dirs.dirs. 

Has the time/date stamp been changed to something very recent? Does it look like this?:
```
# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"
```

I suspect that the file has been changed.

Take a look at:-
[http://askubuntu.com/questions/327669/files-and-folders-in-the-desktop-disappeared](http://askubuntu.com/questions/327669/files-and-folders-in-the-desktop-disappeared)
[http://askubuntu.com/questions/182917/desktop-folder-and-files-disappeared](http://askubuntu.com/questions/182917/desktop-folder-and-files-disappeared)

I'm not sure if the above will help but it's all I could find that might point you in the right direction. 

I have not tried to make any changes to any of my own systems so any changes that you make are made at your own risk. ;)

---

### Post by Luxx on 2015-07-04
Yes, user-dirs.dirs looks normal, but does have today's date on it.
I have no idea how simply saving a text file to the Desktop could cause the Desktop folder to be unnamed and then changed. 
Killing nautilus and then running it didn't help. There is another problem here. I thought restarting nautilus had made the Desktop folder work normally again. I was able to access my normal desktop from the home folder, so I put all my desktop folders in the default Desktop folder that was showing and killed and ran nautilus. ALL my files disappeared. Now everything I had on my desktop is gone. I accidentally cut instead of copied the files, so I have a blank folder where my backup should be.

---

### Post by Luxx on 2015-07-04
I tried putting another file on the desktop, killed nautilus again, and it's working fine with the new file on the desktop and I can even access the Desktop folder from the Places menu, but I still have no idea where the original files and folders went. They should still be there. I put them in the SAME folder that is now working, but there is no sign of them. Could Nautilus have put them somewhere else? Are they just deleted?

---

### Post by Luxx on 2015-07-04
PaulW2U, thanks for yur help. I guess I'm looking at data recovery at this point. I can't find any of my desktop files or folders in terminal, so I'm guessing they've been deleted. I still don't understand how saving a document in gedit could have corrupted my Desktop folder and broken it's function as the Desktop. And I don't know how or why Nautilus deleted all the files in that folder once, but didn't do it again later with new files.

---

### Post by Luxx on 2015-07-04
It seems the nature of the issue (as I was aware) has changed. I haven't lost my Desktop files after all, they have simply been moved to the Root Desktop folder instead of the user Desktop folder. So I opened Nautilus and the Desktop folder in the side menu is the ROOT Desktop folder, and it's the one that disappeared before. It should be my user Desktop folder. 

How I fixed it:

Opened Nautilus, ```
gksu nautilus
```created a folder, named it Dbackup.  I copied all the contents of the root Desktop folder to the Dbackup folder. I then selected and cut the Dbackup folder and navigated in Nautilus to computer/home/myuser and pasted Dbackup folder there. Then I unlocked the folder. Right-clicked the folder, selected properties, permissions tab, gave access to all. Closed Nautilus.

Opened my user's home folder from the Places menu, selected and cut contents of Dbackup and pasted in Desktop. Opened a terminal and killed nautilus ```
sudo killall nautilus
```

When nautilus restarted all my Desktop stuff was back, although rearranged alphabetically, which turns out to be kind of nice.

I'm wondering if forcing Nautilus to restart in terminal instead of letting it restart on it's own somehow kicked my Desktop folder to the Root folder when I was trying to fix the unnamed Desktop folder issue before.


This is similar to the suggestions in the links PaulW2U posted, but I had to find my stuff and put it where I could make this work.

---

### Post by PaulW2U on 2015-07-05
Glad you worked it out Luxx. While you've been working, I've been sleeping. ;)

Thanks for seeing it though to the end and keeping us updated. Your work will be archived for others to use if ever they find themselves in the same position.

---

