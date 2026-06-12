---
title: "Writing a Script to execute commands?"
date: 2015-02-15
forum: General Help
---

### Post by RocketPenguin on 2015-02-15
First off, i am unsure if this is the right or wrong place to post this, a sorry in advance if it isn't.
I have never written a script, so bare with me. What i need to do, is make two scripts that i can click on from the desktop, will both open their own terminal (And stay open until i manually close it) and run the given lines.
For the first one, i have to manually run this:
> 
cd home/pi/PiBits/ServoBlaster/user
sudo ./servod
 
For the second:
> 
cd ~/scratchClient
python crs/scratchClient.py -c servoblaster

How would i do this? I read a few things about putting "xterm -e" and such in front of it, but none of that works for me...

---

### Post by nerdtron on 2015-02-15
not sure it you are not getting any error though but I suggest you put the full path on scripts instead of relative paths. Just to make sure that the terminal really knows the path of the script you want to run. Make sure the script is also executable if you use the ./ and finally, it's better to use explicitly tell the terminal which shell you want the script to run.

If servod is a bash script.
```
 /bin/bash /home/pi/PiBits/ServoBlaster/user/servod
```
if it's not bash, then just make it executable and let is run for itself.
```
 /home/pi/PiBits/ServoBlaster/user/servod
```

As for the python script:
```
 python /home/username/scratchClient/crs/scratchClient.py -c servoblaster
```

---

### Post by RocketPenguin on 2015-02-15
> **nerdtron said:**
> not sure it you are not getting any error though but I suggest you put the full path on scripts instead of relative paths. Just to make sure that the terminal really knows the path of the script you want to run. Make sure the script is also executable if you use the ./ and finally, it's better to use explicitly tell the terminal which shell you want the script to run.

If servod is a bash script.
```
 /bin/bash /home/pi/PiBits/ServoBlaster/user/servod
```
if it's not bash, then just make it executable and let is run for itself.
```
 /home/pi/PiBits/ServoBlaster/user/servod
```

As for the python script:
```
 python /home/username/scratchClient/crs/scratchClient.py 
```
What i am trying to do, is make the two things i need to run icons on the desktop, and so when i connect to the device on a tablet with VNC, i don't have to enter in commands, i can simply double tap the scripts from the desktop, have them start, and if needs be, restart one or both. For the python script, how would the -c servoblaster be added? This is vital. What would i enter into a text editor/ssh client when creating the script to create two such desktop icons?

---

### Post by yetimon_64 on 2015-02-15
> ...i can simply double tap the scripts from the desktop, have them start, and if needs be, restart one or both. 

I would write up the scripts as nerdtron notes, and then rather than double clicking the script itself set up a desktop configuration file to activate the script.

eg 1. In your /home/<username>/bin folder store the actual script that contains the start command and make it executable, for this example I'll name the first script "servod".

2. Open gedit and put the following in a file

```

[Desktop Entry]
Type=Application
Name=ServoBlaster
Comment=Start the servod script to run ServoBlaster.
Exec=servod
Icon=
Terminal=false
NoDisplay=true
```

3. Save the file /home/<your-username>/.local/share/applications/servoblaster.desktop and set it executable. 
Right click > Properties > Permissions tab, tick the box at the bottom to set the executable bit. 
Copy this launcher (.desktop file) to your desktop/panels/docks or wherever you want to place a launcher.

Note: the folder /home/<username>/bin is part of your system path, it will be included in the system path after a log out / log back in if it has just been newly created. So the "Exec=" line can contain just the script name without the complete (absolute) path.

Storing icons in your home folder in a ".icons" folder will allow you to hold custom icons which can be put in the Icon= line by name (include the file extension as well if you use a custom icons folder in your home directory).

I store all my custom launchers (.desktop configuration files) in the folder /home/<my username>/.local/share/applications. The "NoDisplay=true" entry keeps my custom launchers out of any system menus etc. 

I then put a copy of the desktop configuration file on the Desktop or panels/docks etc for launching such custom scripts. It is simple to write a launcher to stop a process just by changing the Exec= line to a "killall command" and a few other of the descriptions/details to suit. Cheers.

---

### Post by RocketPenguin on 2015-02-15
> **yetimon_64 said:**
> I would write up the scripts as nerdtron notes, and then rather than double clicking the script itself set up a desktop configuration file to activate the script.

eg 1. In your /home/<username>/bin folder store the actual script that contains the start command and make it executable, for this example I'll name the first script "servod".

2. Open gedit and put the following in a file

```

[Desktop Entry]
Type=Application
Name=ServoBlaster
Comment=Start the servod script to run ServoBlaster.
Exec=servod
Icon=
Terminal=false
NoDisplay=true
```

3. Save the file /home/<your-username>/.local/share/applications/servoblaster.desktop and set it executable. 
Right click > Properties > Permissions tab, tick the box at the bottom to set the executable bit. 
Copy this launcher (.desktop file) to your desktop/panels/docks or wherever you want to place a launcher.

Note: the folder /home/<username>/bin is part of your system path, it will be included in the system path after a log out / log back in if it has just been newly created. So the "Exec=" line can contain just the script name without the complete (absolute) path.

Storing icons in your home folder in a ".icons" folder will allow you to hold custom icons which can be put in the Icon= line by name (include the file extension as well if you use a custom icons folder in your home directory).

I store all my custom launchers (.desktop configuration files) in the folder /home/<my username>/.local/share/applications. The "NoDisplay=true" entry keeps my custom launchers out of any system menus etc. 

I then put a copy of the desktop configuration file on the Desktop or panels/docks etc for launching such custom scripts. It is simple to write a launcher to stop a process just by changing the Exec= line to a "killall command" and a few other of the descriptions/details to suit. Cheers.
I would prefer scripts... I don't need custom icons, and for the scratchClient, i need to see it in terminal (For errors and such) Same goes with servoblaster.

---

### Post by nerdtron on 2015-02-15
Hmmm. I edited my first post.

Have you tried just writing the script and then Right Click> Run in terminal?

---

### Post by RocketPenguin on 2015-02-15
> **nerdtron said:**
> Hmmm. I edited my first post.

Have you tried just writing the script and then Right Click> Run in terminal?
Which script? All the ones i tried writing never stayed open, nor completed the task (Used things such as xterm -e and so on)

---

### Post by nerdtron on 2015-02-15
> **linux junkie said:**
> Which script? All the ones i tried writing never stayed open, nor completed the task (Used things such as xterm -e and so on)

The script itself (or rather the program itself). Go to the directory of the servod program. Make sure it's executable and the Right click>Open in terminal.

---

### Post by RocketPenguin on 2015-02-17
> **nerdtron said:**
> The script itself (or rather the program itself). Go to the directory of the servod program. Make sure it's executable and the Right click>Open in terminal.
Runs, opens terminal, and closes. May run in background. How would i make a desktop icon? And for the other one?

---

