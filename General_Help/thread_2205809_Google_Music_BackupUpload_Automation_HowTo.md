---
title: "Google Music Backup/Upload Automation HowTo"
date: 2014-02-16
forum: General Help
---

### Post by NorthBridge4839 on 2014-02-16
I did something pretty cool with my Google music library. What it does is it takes music either on my Google drive or FTP folder and checks it, uploads anything in it, and (optional) moves all the music to a final storage location. I did this on a ubuntu 13.04 headless server. I'd imagine it would work the same on a desktop environment but I'm not 100% sure.

I added a lot of ################ and capital letters for when you need to put your own username or filepath.

------------------------------------------------------

1.1) Main Sync Programs Needed
--google-musicmanger-beta
--vnc4server
--fluxbox (or some other window manager)

1.2) File sync software
--grive (for google drive sync)
--openssh (for sftp)
--any other server for placing files in on the server in a chosen folder



2) Install (assuming use of google drive sync for now)
```
sudo apt-get install google-musicmanager-beta vnc4server fluxbox grive
```

3) VNC Server setup
run this and it will ask you to setup a password. ```
vnc4server
```

now kill that session so we can configure the vnc server. ```
vnc4server -kill :1
```

edit your ~/.vnc/xstartup (same thing as /home/YOURNAME/.vnc/xstartup) to look like this ```
#!/bin/sh

# Uncomment the following two lines for normal desktop:
 unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc
fluxbox &

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
#x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#x-window-manager &

```

this sets up the vnc server to use fluxbox.

4) Google Music Manager setup
Now you need to log in to the graphical environment and set up your google music manager credentials.

start the graphical environment. If you're on the desktop and you already have a graphical interface then skip this command. If you are using a ubuntu server, you'll need to start the x server using
```
startx
```

If you're doing this from another computer then start the server using
```
vnc4server
```
and use a VNC client to connect to it on port 5901. If you are connecting remotely then you'll need to either use SSH tunneling and connect to the newly setup VNC server by starting the vnc server using
and then SSH tunneling to the server and connecting to 127.0.0.1 on port 5901. The TightVNC client allows SSH tunneling within the program if VNC over an SSH tunnel is necessary. The TightVNC client settings if using SSH tunneling should be...
Remote Host: 127.0.0.1
Port: 5901
Check the "Use SSH Tunneling" box
SSH Server: YOUR_IP_HERE
SSH port: 22
SSH User: YOUR_USERNAME_HERE

Now you need to start the music manager application. Open a terminal in the graphical environment and type ```
google-musicmanager
```

This should bring up or start the music manager minimized. Log in with your credentials and add the folder you want to upload music from. If your music is going to be stored in a google drive then come back to this step and add the folder later after your google drive is synced.

5) Setting up Google Drive with grive
Create a folder you wish to store your google drive contents in.
```
mkdir ~/google_drive
```

and change into it
```
cd ~/google_drive
```

now you need to authenticate grive to access and sync your files to your computer
```
grive -a
```

this will generate a URL that you need to put into your web browser which will then give you a conformation code. Copy this confirmation code into the grive prompt. This will then authenticate grive and you can sync your files

To sync your files...
-cd into the directory (VERY IMPORTANT because the folder that you created for this holds the authentication to allow you to not need to use grive -a every time.)
-run grive
```
grive
```

Now at this point don't forget to go back and add whatever google drive folder you're using for music to the watched folders in the music manager if you are using google drive for music.

So... at this point... you have a lightweight, remotely-accessible desktop to run the google music manager and a way to get your files from the cloud for the music manager to see and upload to your google music collection. Let's automate this shall we?



6) Automation
So the first step is to create a script that will start all of this stuff and get your computer ready to start syncing and uploading. type
```
nano ~/.grive
```
and copy all of this into it
```
#!/bin/bash

vnc4server

echo "wait for fluxbox"

while [ -z "$(ps -Al | grep fluxbox)" ]; do
        sleep 1
done

echo "fluxbox started"

export XAUTHORITY=/home/YOUR_USERNAME/.Xauthority ######################
export DISPLAY=':1'


echo "starting manager"

/opt/google/musicmanager/google-musicmanager

echo "manager opened"

cd ~/google_drive
while true; do grive;
 chmod -R 755 "/home/YOUR_USERNAME/google_drive/MUSIC_FOLDER_NAME"; ##################
 sleep 300;

```

Press control o, ENTER, control x to save and exit

Now we need to be able to execute this script. Make it executable by using
```
chmod 755 ~/.grive
```

What this does is start the vnc server which will then automatically start fluxbox because of the script we wrote earlier. It then waits for fluxbox to start and once it does, it tells music manager where to open, tells music manager to open, and then goes into a never ending loop of checking and syncing your google drive folder ever 5 minutes (sleep 300 means stop for 300 seconds). Sleep can be changed to whatever you want but remember it's in seconds.

Now if you run this, you should see "wait for fluxbox" then "fluxbox started" then "starting manager" then "manager opened" and a sync occur. Test this with
```
~/.grive
```

If all goes well then press control c to kill the script.

Last step is to automate starting the script that starts everything (linuxception, we must go deeper...)

Add a line to your /etc/rc.local by using nano
```
sudo nano /etc/rc.local
```

it should look like this when you're done
```
 #!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

su YOUR_USERNAME -c '/home/YOUR_USERNAME/.grive &'  ###################

exit 0

```







AND THAT SHOULD BE IT! You should now have your rc.local script call your ~/.grive which will start your vnc server and fluxbox, create musicmanager on that fluxbox instance, and then enter an infinite loop to keep syncing your google drive.

Restart your computer and everything should now start automatically. Try uploading a music file to your google drive music folder and within 5 minutes it should pop up in your google music library!




7) Automatic Deletion/Backup/Truecrypt
If you want to save space on your google drive by deleting it off your google drive once it's synced to google music, you can change the while loop at the end of ~/.grive using nano

WARNING!!! - THIS WILL MOVE EVERYTHING IN YOUR GOOGLE DRIVE MUSIC FOLDER TO THE TRASH. It will copy everything to your local music folder and then sync the deletion to your google drive. You can restore your music the google drive if you need to though.

```
nano ~/.grive
```

and have it look like this
```
while true; do grive;
 chmod -R 755 "/home/YOUR_USERNAME/google_music/PATH_TO_MUSIC";  ###################

 sleep 300;

 echo "cp and rm";
 cp -R "/home/YOUR_USERNAME/google_drive/PATH_TO_MUSIC" /PATH/TO/YOUR/MUSIC/FOLDER; ###############
 rm -R "/home/YOUR_USERNAME/google_drive/PATH_TO_MUSIC/"*;  ####################
 echo "done";

 done

```

Or if you use truecrypt, move it to your folder on your truecrypt drive but only do so if your truecrypt drive is mounted. For instance if your drive gets mounted to /media/truecrypt1

```
while true; do grive;
 chmod -R 755 "/home/YOUR_USERNAME/google_music/PATH_TO_MUSIC";  ###################

 sleep 300;

 if  [ "$(df | grep truecrypt1)" ]; then
 echo "cp and rm";
 cp -R "/home/YOUR_USERNAME/google_drive/PATH_TO_MUSIC" /media/truecrypt1/MUSIC_FOLDER; ###############
 rm -R "/home/YOUR_USERNAME/google_drive/PATH_TO_MUSIC/"*;  ####################
 echo "done";
fi
 done

```

This works because it will bring your files onto your computer, give computer 300 seconds to find and upload the file to google music (assuming you have music manager watching google_drive/. You can also just have it watch your local storage folder such as /PATH/TO/YOUR/MUSIC/FOLDER or /media/truecrypt1/MUSIC_FOLDER), copies it to wherever you want, and then removes the original, and syncs the deletion to your google drive.



It can be used in multiple ways. My favorite idea is that if you ever get legally obtained music files on your phone but want those same files in your google music cloud, you can use folder sync or the google drive app or whatever to put that file on your google drive, have your computer watching it, download it, upload it with music manager to the google music cloud, and then delete it off your drive. Now that same file is available everywhere including the phone you just uploaded it from.


Lastly, you can use any other method of file transfer into a watched folder for music upload. If you're uploading from a phone, FolderSync supports everything from Google Drive to SFTP.


Hope this was helpful! Comment with any questions!.

---

