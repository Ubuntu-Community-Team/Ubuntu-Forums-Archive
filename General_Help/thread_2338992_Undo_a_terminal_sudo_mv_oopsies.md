---
title: "Undo a terminal sudo mv oopsies"
date: 2016-10-03
forum: General Help
---

### Post by grandkodiak2 on 2016-10-03
So I was trying to move my android sdk download from instructions on the website which included the command:

sudo mv ~/Documents/Downloads/android-studio /usr/local/

(for some reasons I couldnt cut and paste in the usual file manager so I went ahead and did so)

Unfortunatly, it went in as 

sudo mv ~ /Documents/Downloads/android-studio /usr/local/

with a space between ~ and /Documents.... it ran a bit then crashed unitiy which auto restarted, and now its all a mess, all my icons, favs, etc moved along with everything else, but i just want to be sure how to undo this before going forward. i hate the command line moving anything. 

can someone confirm the undo command to move it all back where it supposed to be? i'm not familiar with what the file system looked like before things moved.

am i just moving the usr/local/<my username> to /home/<username> ?

so is it:

sudo mv ~/user/local/<my username>/ /home/<my username>/

or where more then just the home folder moved...

---

### Post by grandkodiak2 on 2016-10-03
I also noticed all my conky widgets are missing, as well as all my chrome favorites and settings...??

---

### Post by Jimysbil on 2016-10-03
By giving the command
```
sudo mv ~ /Documents/Downloads/android-studio /usr/local/
```
with the space between [COLOR=#ff8c00]~[/COLOR] and [COLOR=#ff8c00]/Documents/Downloads/android-studio [/COLOR]is like executing:
```
sudo mv {path for file or folder 1} {path for file or folder 2} {destination directory}
```
the character [COLOR=#ff8c00]~[/COLOR] represents your home directory.
So you could move it back by using the command:
```
sudo mv /usr/local/{your username}/ /home/{your username}
```
Don't add a slash at the end of the [COLOR=#ff8c00]/home/{your username}[/COLOR] in case the folder already exists.
But I think you should first terminate your graphical interface by pressing ctrl+alt+f1 and typing the command:
```
sudo service lightdm stop
```
just to avoid possible conflictions.

I assume your [COLOR=#ff8c00]android-studio[/COLOR] folder should be moved into the right place.So if you want to be able to move this folder from your account without you need root previlages (except if you want to move it in some other system folder) you have to change permissions.In order to change permissions for full access on this folder,subfolders and files (read,right,execute) from everyone type:
```
sudo chmod -R 777 {your folder path}
```
In case you want to be the owner of that folder with everything it has inside type:
```
sudo chown -R {your username}:{your group name} {directory path}
```

**If some applications recreated your home directory and saved some new settings I would suggest you erase your new created home directory before you move back the old one to avoid conflictions.If you want to do this type:
```
sudo rm -rf {your new homedirectory path}
```
[COLOR=#ff0000]**Be extremely careful if you use rm command (expecially with root previlages) or you could destroy your hole system.**[/COLOR]

---

