---
title: "Running gphoto2 in terminal"
date: 2007-08-06
forum: General Help
---

### Post by tinkietruck on 2007-08-06
I am running gphoto2 in the terminal.  I have been trying to upload pictures to Ubuntu.  I am using a Canon Powershot A410.  I can't get this far below, but I don't know what the next command is to upload the pictures to the computer.  Any help would be greatly appreciated.

tinkietruck@tinkietruck:~$ [COLOR="Red"]sudo gphoto2[/COLOR]
Password:
Usage: gphoto2 [-?] [-?|--help] [--usage] [--debug] [--quiet]                  
        [--force-overwrite] [-v|--version] [--list-cameras] [--list-ports]
        [--stdout] [--stdout-size] [--auto-detect] [--port=path]
        [--speed=speed] [--camera=model] [--filename=filename]
        [--usbid=usbid] [-a|--abilities] [-f|--folder folder] [-R|--recurse]
        [--no-recurse] [--new] [-l|--list-folders] [-L|--list-files]
        [-m|--mkdir STRING] [-r|--rmdir STRING] [-n|--num-files]
        [-p|--get-file STRING] [-P|--get-all-files] [-t|--get-thumbnail STRING]
        [-T|--get-all-thumbnails] [--get-metadata=STRING]
        [--get-all-metadata=STRING] [--upload-metadata=STRING]
        [--get-raw-data=STRING] [--get-all-raw-data]
        [--get-audio-data=STRING] [--get-all-audio-data]
        [-d|--delete-file STRING] [-D|--delete-all-files]
        [-u|--upload-file STRING] [--config] [--list-config]
        [--get-config=STRING] [--set-config=STRING] [--wait-event]
        [--capture-preview] [-F|--frames count] [-I|--interval seconds]
        [--capture-image] [--capture-movie] [--capture-sound]
        [--show-exif=STRING] [--show-info=STRING] [--summary] [--manual]
        [--about] [--shell]
tinkietruck@tinkietruck:~$ [COLOR="Red"]sudo gphoto2 --list-files[/COLOR]
There is no file in folder '/'.                                                
There is no file in folder '/store_00010001'.
There is no file in folder '/store_00010001/DCIM'.
There are 27 files in folder '/store_00010001/DCIM/100CANON'.
#1     IMG_0001.JPG                 1219 KB 2048x1536 image/jpeg
#2     IMG_0002.JPG                 1345 KB 2048x1536 image/jpeg
#3     IMG_0003.JPG                 1826 KB 2048x1536 image/jpeg
tinkietruck@tinkietruck:~$[COLOR="Red"] mkdir 2007-08-02a[/COLOR]
tinkietruck@tinkietruck:~$ [COLOR="Red"]sudo gphoto2 --get-all-files[/COLOR]
Downloading 'IMG_0001.JPG' from folder '/store_00010001/DCIM/100CANON'...      
File IMG_0001.JPG exists. Overwrite? [y|n] n                                   
Specify new filename? [y|n] n
Downloading 'IMG_0002.JPG' from folder '/store_00010001/DCIM/100CANON'...
File IMG_0002.JPG exists. Overwrite? [y|n] n                                   
Specify new filename? [y|n] n
Downloading 'IMG_0003.JPG' from folder '/store_00010001/DCIM/100CANON'...
Saving file as IMG_0003.JPG                                                    
tinkietruck@tinkietruck:~$ [COLOR="Red"]cd /home/tinkietruck/2007-08-02a[/COLOR]
tinkietruck@tinkietruck:~/[COLOR="Red"]2007-08-02a$ [/COLOR]

What's my next command to upload pictures to folder specified?  Thanks.

Brandy

---

