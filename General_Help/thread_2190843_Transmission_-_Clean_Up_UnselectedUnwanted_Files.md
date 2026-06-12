---
title: "Transmission - Clean Up Unselected/Unwanted Files"
date: 2013-11-29
forum: General Help
---

### Post by andre.allen.m on 2013-11-29
One thing that has always annoyed me about Ubuntu is that the default torrent program Transmission keeps incomplete files you do not select even after the torrent has finished. (Renames them .part)

I understand that this may make sense as a developer but it's not what the end user wants.

Transmission is an excellent piece of software so I wanted to get around this and continue using it.

I simply created a script to run after the file has finished downloading (using Transmission's built in "run script" feature) that deletes ".part" files and empty folders.

Simply open Transmissions preferences, select the "Downloading" tab, under "Save Location" select a folder named "Complete Transmission" in your users home/Downloads directory.

Check "Keep incomplete torrents in:" and select a folder named "Incomplete Transmission" in your users /home/Downloads folder.

Then check "Call script when torrent is completed:" and select file named "Transmission.sh" you have placed in your users home/Downloads/Transmission Script folder.

The script should contain the following.

[B]find /home/username/Downloads/"Complete Transmission" -iname "*.part" -delete; find /home/username/Downloads/"Complete Transmission" -type d -empty -delete
[/B]
That can be done by simply creating an empty file, adding the text via a text editor, putting .sh as it's filename extension and checking "Allow this file to run as a program" in the file properties.

[IMG]http://i.imgur.com/CgPqCrR.png[/IMG]    [IMG]http://i.imgur.com/jwnsCUO.png[/IMG]    [IMG]http://i.imgur.com/KNoucSp.png[/IMG]

---

