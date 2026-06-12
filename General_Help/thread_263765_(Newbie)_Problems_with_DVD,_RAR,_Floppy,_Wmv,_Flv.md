---
title: "(Newbie) Problems with: DVD, RAR, Floppy, Wmv, Flv"
date: 2006-09-23
forum: General Help
---

### Post by Sabrage on 2006-09-23
Just a few problems I'm hoping someone could help me with:

**DVD**: A DVD with data works just fine, but films on DVD is not working. In Totem it says: "An error occured. Could not read from source." In VLC nothing happens, no picture and no error message. Swedish DVD.

**RAR**: I installed the package for rar but I still can't open rar archives. The archive manager says: "Could not open [file]. Archive type not supported. Which is weird because I installed the rar package?

**FLOPPY**: Can't read/write floppydisks. There are some files showing in the fd directory, but I think maybe it's set up wrong? In Gedit it says "No permission" and in Abdiword it says: "Error importing file".

**WMV**: I'd like to view WMV-files but I get one the sound, no picture. This is the same in both VLC and Totem.

**FLV**: With flashvideo in VLC I get no sound or picture. It just rushes through the file in one second. In Totem it says: "You do not have the encoder". But shouldn't this wotk when I have flash installed? Or do I need a package or plugin or something?

Any help or tips is very much appreciated.

---

### Post by christhemonkey on 2006-09-23
**DVD:**Install libdvdread0
```
sudo apt-get install libdvdread0 
```
If it is encoded you need to install libdvdcss2, but it is not available from ubuntu.

**RAR:**Install unrar.
```
sudo apt-get install unrar 
```

**Floppy:**Not a clue :)

**WMV:**You might need to install gstreamer0.10-pitfdll and possibly the w32codecs package (also unavailable from official ubuntu repos)

**FLV:**Dont know if it is possible to play them outside of Firefox et al.
But for in firefox, you need flash plugin-nonfree:
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by Sabrage on 2006-09-23
thanks christhemonkey

I opened a terminal and typed:> user@user-desktop:~$ sudo apt-get install libdvdread0
Password:
user@user-desktop:~$ sudo apt-get install unrar
user@user-desktop:~$ sudo apt-get install flashplugin-nonfree
user@user-desktop:~$

I think I'm doing something wrong here. I don't think it actually installed anything, because there was no waiting after each command, just immediately back to the prompt. And the files are still not working. :confused: Any ideas?

---

### Post by christhemonkey on 2006-09-24
That doesnt look good...

Can you search for these things in synaptic and install them from there?

If they are not listed you will need to add extra repositories.  See here:
[http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories)

---

### Post by Volfied on 2006-09-25
Are you sure you wrote your password correct? Maybe you wrote it wrong and its taking some time to check it and you just kept writing commands. 

I can't think of anything else there :/

---

### Post by christhemonkey on 2006-09-25
If he had written his password wrong, it would not have gone back to the "user@user-desktop:~$" prompt.


What about trying:
```
sudo apt-get update 
```

---

### Post by Sabrage on 2006-09-25
I'm pretty sure I got the password correct this time, but thanks for reminding me to double-check, Volfied.

christhemonkey, I changed user to my commando-user and installed rar-unfree from synaptic like you said and it worked! Could not get the update command working (same thing happened) but I'm sure I'll figure it out eventually. Thanks so much for your help.

---

