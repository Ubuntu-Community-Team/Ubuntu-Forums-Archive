---
title: "[SOLVED] Need guidance and solution on two issues"
date: 2008-06-24
forum: General Help
---

### Post by djmoore85 on 2008-06-24
Hey there, just have a couple quick questions. I created a profile for my wife, to help transition her to using my machine, and want to know how I can share my picture folder between the two accounts. I have set permissions to almost every possible configuration. How do I make my picture folder accessible to her when she is logged into her profile? Second question, is there a way to make the Gnome panel fall to the background when windows are opened up so that when they are maximized without going fullscreen the panel is behind them? Thanks in advance for any help

---

### Post by Mikecore on 2008-06-24
> **djmoore85 said:**
> Hey there, just have a couple quick questions. I created a profile for my wife, to help transition her to using my machine, and want to know how I can share my picture folder between the two accounts. I have set permissions to almost every possible configuration. How do I make my picture folder accessible to her when she is logged into her profile? Second question, is there a way to make the Gnome panel fall to the background when windows are opened up so that when they are maximized without going fullscreen the panel is behind them? Thanks in advance for any help

You could change your picture file permissions at the command line like this

```

sudo chmod 777 /home/your_name/Pictures


```

problem is its not a very secure thing to do. but your the admin

or you could do what I do and thats create a new folder under / and chmod that one then just add a short cut to it in gnome ( in her account ) and then you can share info with other users without having to worry about your account getting hosed up. I'm sure there are even better ways thats just what I do. As for the menu question not sure you can do that with nautilus window manager.

---

### Post by plucky on 2008-06-25
Second question, is there a way to make the Gnome panel fall to the background when windows are opened up so that when they are maximized without going fullscreen the panel is behind them?


You can **Autohide** the panels,which means they allow window to be full screen size and will appear when the mouse pointer moves over the panel.

Right click on a panel and select **Properties** and tick **Autohide**.


Good Luck

---

### Post by djmoore85 on 2008-06-25
Thanks for the help. The panel issue is resolved as far as it is the best I'll get, but I cannot yet get the picture file shared yet. Is there a directory to copy it to that is common between both accounts?

---

### Post by p_quarles on 2008-06-25
> **djmoore85 said:**
> Thanks for the help. The panel issue is resolved as far as it is the best I'll get, but I cannot yet get the picture file shared yet. Is there a directory to copy it to that is common between both accounts?
You can create a symlink (symbolic link, or shortcut) in her home directory that points to the directory you wish to share. E.g.:
```
ln -s /home/you/photos /home/wife/name_of_shortcut
```
Assuming that the permissions are correct on the shared folder, it will now show up in both users' home directories.

---

### Post by djmoore85 on 2008-06-26
Ok, I got the shortcut to work fine, but have a new snag come up. The picture icons are shown with an "X" and a padlock next to them. How do I unlock them to allow my wife permission to view?

**EDIT** Ok, panic time I tried to move the shortcut, I got a message saying "error: can't move due to no such directory or something" and now have no I idea where my pictures went I cannot find any of my picture files? I couldn't have erased them, where did they go??!!

---

### Post by nunki on 2008-06-26
Ok lets try finding the pictures based on their name. From a terminal type
```

find /home -type f -name "*.jpg" 2 > /dev/null

```

Im assuming these were .jpg. If they were not, then change the extension to whatever they were.

---

### Post by djmoore85 on 2008-06-26
Not working, keeps telling me 

```
daniel@Daniel-7:~$ find /home -type f -name "*.jpg" 2 > /dev/null
find: paths must precede expression
Usage: find [-H] [-L] [-P] [path...] [expression]
daniel@Daniel-7:~$ 
```

---

### Post by nunki on 2008-06-26
> **djmoore85 said:**
> Not working, keeps telling me 

```
daniel@Daniel-7:~$ find /home -type f -name "*.jpg" 2 > /dev/null
find: paths must precede expression
Usage: find [-H] [-L] [-P] [path...] [expression]
daniel@Daniel-7:~$ 
```

Odd just try 
```

find /home -type f -name "*.jpg"

```

---

### Post by djmoore85 on 2008-06-26
Couldn't find them even doing "/" instead of "/home" but luckily by some miracle of God I still had the whole folder on my flash drive from before I upgraded to 8.04. Thanks for the help everyone, guess I learned something new to not do. The switch form Windows has been relatively painless, definitely lessons learned here and there. Thanks again everyone. Now I just need to figure out how to get my wife's account to be able to use the pictures

---

### Post by nunki on 2008-06-26
Heres what I would do. Create a group called "shared" then create a folder under /
```

sudo groupadd shared
sudo mkdir /shared
sudo chmod 2770 /shared
sudo chown root:shared /shared

```
Now add your user and your wifes to the shared group 
```

sudo usermod -a -G shared daniel
sudo usermod -a -G shared <wifes user name>

```
Youll probably need to logout and back in at this point

Now copy your pictures to the shared area
```

cp -r /path/to/pictures /shared

```

Now make sure everything under shared has group read,write, execute permissions
```

sudo chmod -R 770 /shared

```

Now she could either navigate to /shared to view the pictures, or you could create a symlink to the shared area. If someone else becomes a user on your computer, you could add them to the shared group and they would be able to view the shared area as well.

---

### Post by p_quarles on 2008-06-26
I hope you mean you learned to back up your data before doing anything to it. :)

In any case, I'm not really sure what you said you did. The target directory disappeared after you tried to move the symlink? Can you double check and confirm this?

---

### Post by djmoore85 on 2008-06-26
Hey yall. Seems exloring has found me a solution. Yes I believe I deleted my /home/../Picture directory after trying to drag-and-drop the symlink to a different location. I broke open my book of Ubuntu commands that I have layin around and tried every find, locate and search command I could find. No pictures existed. Yes, before I upgraded I had all my pictures, sounds and finicky-hardware drivers backed up. Luckily I haven't yet deleted these files. After restoring my Picture folder I went through and changed the access ability to myself and my wife, and for whatever reason that made the symlink begin working without a flaw. I still don't understand why changing file permissions before wouldn't work for my wife's account to access it. In the end it came to tweaking groups and folder permissions so the symlink would work. Thanks again everyone, I love the support throughout the forums

---

