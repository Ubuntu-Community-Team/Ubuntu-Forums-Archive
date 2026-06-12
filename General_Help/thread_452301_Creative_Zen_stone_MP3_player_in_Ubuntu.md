---
title: "Creative Zen stone MP3 player in Ubuntu"
date: 2007-05-23
forum: General Help
---

### Post by ali780 on 2007-05-23
[SIZE="3"]Hello everybody.
I have a Creative Zen Stone MP3 player. I want to know that can I use ubuntu for charging the battery and for transferring songs to it?
Thank you[/SIZE]

---

### Post by fictivetoast on 2007-05-23
You can almost certainly charge the Stone over USB with no problem, even if Ubuntu doesn't know what to do with it.

As for transferring material though, I'm not entirely sure - since the Stone is a new product, it may take a little while for support to pop up, though surely not long.  I've got a Creative Zen Vision M, which transfers via MTP (I'm assuming the Stone likely does too), and I've already got full support in Amarok (including album art), with buggy transfer methods also working in Rhythmbox and Banshee.  And outside of a music player, Gnomad2 can easily take care of direct transfers too.  The sooncoming Songbird has MTP support slated for their next big milestone release too, I believe.

Try installing Gnomad2 and Amorak to see if you'll have any luck.  The versions available in the Feisty repos are already compiled with MTP transfer support, so install without any worry and be ready to go:

sudo apt-get install gnomad2
sudo ap-tget install amorak

Fire up gnomad2 and plug in your stone ; if it works, it'll read the database and let you transfer files with a basic 2-pane navigator style view.

Getting an MTP device up in Amarok takes a few more steps, but is certainly not difficult ; you can try googling Amarok and looking it up on their wiki to see what to do in the Amarok config dialogue.

Best of luck!

---

### Post by nairod on 2007-08-29
Actually, you dont need any software. It works like an external hard drive, just plug it in, drag the files to MUSIC folder and unplug. Simple. :0)

---

### Post by mflayer on 2007-09-10
I've also bought a Zen Stone and tried connecting it to Ubuntu Feisty powered laptop. At first it didn't get recognized. I had to reset the device (using the mini reset button), after that it mounted automatically just like any external USB drive.
FYI, you can use whatever directories you like, no need for the MUSIC folder... there's a button to skip folder and play next -> you can sort music by albums, artist, etc.

---

### Post by coldstatue on 2007-09-10
Does the stone work with playlists, and synchronize with Amarok? What about the Vision M? I'd like an iTunes-like setup, entirely within linux.

Thanks

---

### Post by dayhorse on 2007-10-10
hi. my girlfriend just got a creative zen stone 1gb and i am running ubuntu. So, does anyone know if you can get rhythmbox to recognise the creative zen stone 1gb?
any easy way to get it done?  etc...

thanks.
please excuse the bad punctuation, capitalisation and grammar.

---

### Post by kkkkatie on 2007-10-13
Hey, just been reading the feed because i wanted to know a similar thing - for my zen vision: M, do you have to have both gnomad 2 qamorak, they seem  to always be mentioned together? do they perform different tasks??  Sounds like a thick question but u no

---

### Post by kkkkatie on 2007-10-13
THANX GUYS.  Fianlly managing to shake of hte last shards of need of microsoft!!:KS

---

### Post by jadedjay on 2007-10-20
Ive been using a Creative Vision M with Amarok and MTP for a while and thought that I could connect my Creative Stone in the same manner.  
In fact the Creative stone is simple to connect to your PC but requires a few steps to get working with Amarok.
The main steps are:

1. Plug it in and let it be discovered as a device on the system. (found but not mounted)
    Remember the device path that the system creates for you  /dev/sd??
    For this example lets use /dev/sdh1
    Note: At this stage if you have Amarok running, Amarok may pop up a screen to let you know that it has detected a device.  However if you try to connect to the device Amarok will provide you with a message saying "Cannot to connect to the device".

2. Mount the Stone player rw available to which users (uid) or user group (gid) you want.  I couldnt get this to work from the command line.  
    So I put this into my "/etc/fstab" file.  
   The options I chose where:
    /dev/sdh1 /mnt/stone vfat noatime,auto,users,uid=1000,gid=100,umask=007 0 0
    Note: I have included both uid and gid in my example but you may not need both if you dont desire.

3. Open a terminal and execute
    sudo mount -a 
    to mount your player.

    Note: I got this solution from a similar problem I had with SD cards mounting read only (ro).
    I could never work out how to get this command to work correctly from the command line, as it kept mounting the device with "root" as the owner and the Stone player read only.
    Sometimes its just best to stick to what you know.

4. Go into the Amarok settings -->  Configure Amarok --> Media Devices
    You will see a list of devices including your /dev/sd??.  
    For the plugin option (next to your device) choose : "Generic media player".
    Note: I tried the other plugin options with no success.

5. Click on the cogs next to the plugin options to enter the "Configure device settings"
    Change the Song Location to something like 
    /%artist_%album_%track_%title.%filetype
    Basically you dont want to create subdirectories (subfolders) as I believe the Stone player simply wont find them. So you want to put all files under "/" (your first directory).
    I use the %artist_%album_%track_%title.%filetype format to keep all my files seperated.  But play around with this and see what you like.
    Following the example your resulting  "Example Song Location" should be something like this 
    "/mnt/stone/The One Artist_Some Album_01_Some Title.mp3"
    Click OK to close the window.
    Edit: I later discovered that you can create one level folders under "/" and use the Folder Skip button on your Stone player to change folders.  So you play around with the Song Location setting and create different folders for each album.   

6. Click Apply.   Note: At this stage my Stone player was detected by Amarok and connected without request, this may not happen for everyone.  
   Click Ok to close the window.
   
   If your device has not automatically connected.  
   In the main Amarok window click on the Devices tab.  From the top of the window select Generic Audio Player /dev/sd?? and then click on the connect option.  Now you can transfer your music using Amarok.

7. When your done, disconnect in Amarok.  Then from the desktop, select your player icon and chose "safely remove" or umount via a terminal.
    

Hope all this helps.
 :guitar:

---

### Post by frenchninja112 on 2007-11-18
I have stone but i tried to format it and failed (long story) and now when I connect it I either get an error messages saying cannot read supeblock or nothing pops up and i cant find it in the compeuter file browser but i see it the Device manger. How do I fix this problem?

Now i can see it in the file browser but when i try to mount it i get this error message: "Unable to mount media. There is probably no media in the drive.

---

### Post by jadedjay on 2007-11-29
> **frenchninja112 said:**
> I have stone but i tried to format it and failed (long story) and now when I connect it I either get an error messages saying cannot read supeblock or nothing pops up and i cant find it in the compeuter file browser but i see it the Device manger. How do I fix this problem?

Now i can see it in the file browser but when i try to mount it i get this error message: "Unable to mount media. There is probably no media in the drive.

When you connect your Stone player does it show up under /dev device directory?
Check there first.  If it is then at least the system is finding it as a device.

---

### Post by zero244 on 2008-03-23
Try this...........open a terminal window and copy and paste this.

sudo rmmod ehci_hcd

It will then ask you for your password.
Password:

Then try and mount your player. This goes away on reboot. I made a launcher on my desktop, so I just double click it when I want to mount my mp3 players.
This works with Edgy and Feisty.......I havent tried it with Gutsy yet.
It seems some mp3 players are seen as scsi drives instead of plain ole flash drives.
This command has worked on all my mp3 players that wouldn't mount before.
Good Luck.

---

### Post by lefo on 2008-05-06
Using Hardy 8.04, My ZenStone 1 GB player shows up in Rhythmbox, and I can put music on it by dragging from the music list onto the Stone.  However, I'm only able to copy 256MB of MP3's.  Any way to get a whole gig on there?

TIA

lefo

---

### Post by lefo on 2008-05-06
> **lefo said:**
> Using Hardy 8.04, My ZenStone 1 GB player shows up in Rhythmbox, and I can put music on it by dragging from the music list onto the Stone.  However, I'm only able to copy 256MB of MP3's.  Any way to get a whole gig on there?

TIA

lefo

Okey-Doke!  Scratch this request for help.  I dug down further into the Zen Stone and found the thing keeps it's own trash that was filling up the player. Deleted the trash when I unmounted it, and voila!  Got the rest of my space back, and Rhythmbox is JUST like working in iTunes for tranferring songs.  I love it!

lefo

---

