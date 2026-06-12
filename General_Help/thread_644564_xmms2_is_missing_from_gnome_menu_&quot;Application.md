---
title: "xmms2 is missing from gnome menu: &quot;Applications -&gt; Sound and Video -&gt; XMMS&quot;"
date: 2007-12-19
forum: General Help
---

### Post by phillipbeynon on 2007-12-19
Issue: I installed xmms2 using the package manager, but xmms2 isn't listed in the gnome menu "Applications -> Sound and Video -> XMMS"

Question: How do I add it?

TS:
*  Followed instructions: [https://help.ubuntu.com/community/XMMS](https://help.ubuntu.com/community/XMMS) All commands to associate files completed without any errors.
*  Attempted to open several types of music files expecting them to be associated with xssf but they are not.
*  Read several posts that seemed relevant but none seem to lead anywhere:
  -  I have no "Applications -> System Tools" or "Applications -> System Tools -> Applications Menu Editor"
  -  I can't find any "smeg".
*  /usr/bin/xmms2 exists.  This is the command line interface.  Where's the GUI?  I should get that on a t-shirt. :)

I'm feeling frustrated.  I can follow documentation and I have, but I'm lost. Your assistance would be greatly appreciated. Thank you.

---

### Post by FuturePilot on 2007-12-19
You might have to refresh the menus.
```
killall gnome-panel
```

Also to get to the Menu Editor right click on "Applications" and go to Edit Menus.

---

### Post by phillipbeynon on 2007-12-19
Thank you very much.  I am now able to find the menu editor and have successfully added a new menu entry; however xmms2 fails to initialize.

Issue:
ERROR: ../src/xmms/ipc.c:881: Couldn't setup IPC listening on 'unix:///tmp/xmms-ipc-phillipbeynon'.
FATAL: ../src/xmms/main.c:476: IPC failed to init!


TS: 

phillipbeynon@ThinkCenter8185-D3U:~$ xmms2
Available commands:
  add - adds a URL to the playlist
  addarg - adds one URL with arguments to the playlist
  addid - adds a Medialib id to the playlist
  insert - inserts one URL at a specific position
  insertid - inserts one Medialib id at a specific position
  radd - adds a directory recursively to the playlist
  clear - clears the playlist
  shuffle - shuffles the playlist
  sort - sort the playlist; use a space delimiter for multiple properties
  remove - removes something from the playlist
  list - lists the playlist
  addpls - Adds the contents of a playlist file to the playlist
  play - starts playback
  stop - stops playback
  toggleplay - toggles playback status between play/pause
  pause - pause playback
  next - play next song
  prev - play previous song
  seek - seek to a specific place in current song
  jump - take a leap in the playlist
  move - move a entry in the playlist
  volume - set volume for a channel
  volume_list - list volume levels for each channel
  mlib - medialib manipulation - type 'xmms2 mlib' for more extensive help
  playlist - playlist manipulation - type 'xmms2 playlist' for more extensive help
  coll - collection manipulation - type 'xmms2 coll' for more extensive help
  browse - browse server file lists
  status - go into status mode
  info - information about current entry
  current - formatted information about the current entry
  config - set a config value
  config_list - list all config values
  plugin_list - list all plugins loaded in the server
  stats - get statistics from server
  quit - make the server quit
  help - print help about a command
phillipbeynon@ThinkCenter8185-D3U:~$ xmms2d
 INFO: ../src/xmms/log.c:36: Initialized logging system :)
ERROR: ../src/xmms/ipc.c:881: Couldn't setup IPC listening on 'unix:///tmp/xmms-ipc-phillipbeynon'.
FATAL: ../src/xmms/main.c:476: IPC failed to init!
phillipbeynon@ThinkCenter8185-D3U:~$ xmms2-launcher
Log output will be stored in /home/phillipbeynon/.cache/xmms2/xmms2d.log
startup failed!
phillipbeynon@ThinkCenter8185-D3U:~$ xmms2-mlib-updater

---

### Post by eben on 2008-02-22
if anyone has this 

you should look at: [http://wiki.xmms2.xmms.se/index.php/FAQ#When_I_start_xmms2d_or_xmms2-launcher_I_get_ERROR:_Couldn.27t_initialize_IPC_socket_or_startup_failed.21]("http://wiki.xmms2.xmms.se/index.php/FAQ#When_I_start_xmms2d_or_xmms2-launcher_I_get_ERROR:_Couldn.27t_initialize_IPC_socket_or_startup_failed.21")

main reason: xmms2d is already running ...

---

### Post by kaivalagi on 2008-03-24
xmms2 is a music daemon, and not a graphical player, install gxmms2 or something else like this to control what it does.

---

### Post by kaivalagi on 2008-03-30
Your best front end for xmms2 in the repo's at present is esperanza in my opinion, install that and see how you get on...

---

