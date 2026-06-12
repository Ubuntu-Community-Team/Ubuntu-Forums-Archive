---
title: "Help ..   I want to change easily.  -&gt; google-chrome.desktop"
date: 2015-12-29
forum: General Help
---

### Post by oklokl on 2015-12-29
^^
Hello .. ^^ .. The computer beginners
 Is there easily create a sentence below?
 I tried hard to make.
It will be made by studying my own.
 A little proud :D
 Anyway, thank you.:)






```
#Files need to be modified
sudo nano /usr/share/applications/google-chrome.desktop


#Objectives need to be modified
Exec=/usr/bin/google-chrome-stable %U

#Fixed appearance
Exec=/usr/bin/google-chrome-stable %U --incognito


#To back up the original icon (top back)
sudo cp /usr/share/applications/google-chrome.desktop $HOME
mkdir -p $HOME/backup_ico
sudo cp /usr/share/applications/google-chrome.desktop $HOME/backup_ico

#Recovering the original file
sudo cp $HOME/backup_ico/google-chrome.desktop /usr/share/applications


#Changes in incognito mode
sudo cp /usr/share/applications/google-chrome.desktop $HOME
sudo  cat $HOME/google-chrome.desktop | sed -e  's/Exec=\/usr\/bin\/google-chrome-stable  %U/Exec=\/usr\/bin\/google-chrome-stable %U --incognito/g' >  $HOME/google-chrome.desktop.new
sudo mv $HOME/google-chrome.desktop.new $HOME/google-chrome.desktop
sudo cp $HOME/google-chrome.desktop /usr/share/applications


#Returning again
sudo cp /usr/share/applications/google-chrome.desktop $HOME
sudo  cat $HOME/google-chrome.desktop | sed -e  's/Exec=\/usr\/bin\/google-chrome-stable %U  --incognito/Exec=\/usr\/bin\/google-chrome-stable %U/g' >  $HOME/google-chrome.desktop.new
sudo mv $HOME/google-chrome.desktop.new $HOME/google-chrome.desktop
sudo cp $HOME/google-chrome.desktop /usr/share/applications
```

[ATTACH=CONFIG]266453[/ATTACH]
Chrome completely shut down

---

### Post by CantankRus on 2015-12-29
If you are making the changes for a single user you can copy **/usr/share/applications/google-chrome.desktop** to **~/.local/share/applications** and make the changes
to the copied file without the need for elevated permissions.
"~/.local/share/applications/google-chrome.desktop" will override "/usr/share/applications/google-chrome.desktop" for that user.
Other users will continue to use "/usr/share/applications/google-chrome.desktop"
eg
```
cp /usr/share/applications/google-chrome.desktop ~/.local/share/applications
gedit ~/.local/share/applications/google-chrome.desktop
```

To return to default just delete **~/.local/share/applications/google-chrome.desktop**

---

### Post by oklokl on 2015-12-29
wow~
Thank you :D

```
# Create an incognito
cp /usr/share/applications/google-chrome.desktop ~/.local/share/applications
cat ~/.local/share/applications/google-chrome.desktop | sed -e 's/Exec=\/usr\/bin\/google-chrome-stable %U/Exec=\/usr\/bin\/google-chrome-stable %U --incognito/g' > ~/.local/share/applications/google-chrome.desktop.new
mv ~/.local/share/applications/google-chrome.desktop.new ~/.local/share/applications/google-chrome.desktop
sudo chmod 644 ~/.local/share/applications/google-chrome.desktop
sudo chown -R root:root ~/.local/share/applications/google-chrome.desktop

# Recovering
sudo rm ~/.local/share/applications/google-chrome.desktop
```

---

### Post by CantankRus on 2015-12-29
No problem.
Same applies for other .desktop files in /usr/share/applications
I have numerous custom .desktops in ~/.local/share/applications
where I have added unity quicklist items.

---

### Post by CantankRus on 2015-12-30
> **oklokl said:**
> wow~
Thank you :D

```
# Create an incognito
cp /usr/share/applications/google-chrome.desktop ~/.local/share/applications
cat ~/.local/share/applications/google-chrome.desktop | sed -e 's/Exec=\/usr\/bin\/google-chrome-stable %U/Exec=\/usr\/bin\/google-chrome-stable %U --incognito/g' > ~/.local/share/applications/google-chrome.desktop.new
mv ~/.local/share/applications/google-chrome.desktop.new ~/.local/share/applications/google-chrome.desktop
[COLOR="#FF0000"]sudo chmod 644 ~/.local/share/applications/google-chrome.desktop[/COLOR]

# Recovering
rm ~/.local/share/applications/google-chrome.desktop
```

Are you placing the .desktop file on your desktop?
No need to change permissions if using on the unity launcher.

---

### Post by oklokl on 2015-12-30
Not to the desktop (.desktop file)  do not have :)
I give permission.
Originally I wanted to just give the 644 root file properties.(sudo chmod 644)


Thank you so much..
It has been resolved well, thanks ^^
:D

---

