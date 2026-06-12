---
title: "Recommend Media player (Graphical and CLI controls)"
date: 2016-06-24
forum: General Help
---

### Post by CaptainMark on 2016-06-24
I'm in the market for a new media player, I'm still using Banshee even though it hasn't seen an update since 2014.

I need a GUI based media player but one that also has full control from the terminal to allow it to be fully scripted upon login without popping up a GUI every time.
I like a simple Genre/Album/Artist type layout like itunes used to look like about 10 years ago before they started adding nonsense stuff to it.

And if you're wondering why I don't just stick with Banshee it's because it's a buggy mess and I've had enough of it's faffing.

So, any recommendations?


Regards
Mark

---

### Post by uRock on 2016-06-24
VLC can be run via GUI or CLI. I started using it after installing ubuntu 16.04 and watching as Rhythmbox loaded the same two songs several thousand times.

---

### Post by Bucky Ball on 2016-06-24
I've never needed more than VLC or Audacious, but Clementine may be worth looking at. It's in the repos I think.

---

### Post by linuxyogi on 2016-06-25
You can try mpv. It can be used using the command line and Smplayer as gui frontend.

---

### Post by pqwoerituytrueiwoq on 2016-06-25
i use gmusicbrowser
i dont ask much out of a music player (start silent, autoplay, and only show up in the notification area)
when i dont need a gui i use mpd and mpc
```
**~$ gmusicbrowser --help**
gmusicbrowser v1.1.13 (c)2005-2014 Quentin Sculo
options :
-nocheck: don't check for updated/deleted songs on startup
-noscan    : don't scan folders for songs on startup
-demo    : don't save settings/tags on exit
-ro    : prevent modifying/renaming/deleting song files
-rotags    : prevent modifying tags of music files
-play    : start playing on startup
-gst    : use gstreamer
-nogst  : do not use gstreamer
-server    : send playing song to connected icecast clent
-port N : listen for connection on port N in icecast server mode
-verbose: print some info, like the file being played
-debug    : print lots of mostly useless informations, implies -verbose
-backtrace : print a backtrace for every warning
-nodbus    : do not provide DBus services
-dbus-id KEY : append .KEY to the DBus service id used by gmusicbrowser (org.gmusicbrowser)
-nofifo : do not create/use named pipe
-F FIFO, -fifo FILE    : use FIFO as named pipe to receive commands (instead of 'gmusicbrowser.fifo' in default folder)
-C FILE, -cfg FILE    : use FILE as configuration file (instead of 'gmbrc' in default folder),
              if FILE is a folder, sets the default folder to FILE.
-l NAME, -layout NAME    : Use layout NAME for player window
+plugin NAME        : Enable plugin NAME
-plugin NAME        : Disable plugin NAME
-noplugins        : Disable all plugins
-searchpath FOLDER    : Additional FOLDER to look for plugins and layouts
-use-gnome-session     : Use gnome libraries to save tags/settings on session logout
-workspace N        : move initial window to workspace N (requires Gnome2::Wnck)
-gzip            : force not compressing gmbrc
+gzip            : force compressing gmbrc with gzip
+xz            : force compressing gmbrc with xz

-cmd CMD        : add CMD to the list of commands to execute
-ifnotrunning MODE    : change behavior when no running gmusicbrowser instance is found
    MODE can be one of :
    * normal (default)    : launch a new instance and execute commands
    * nocmd            : launch a new instance but discard commands
    * abort            : do nothing
-nolaunch        : same as : -ifnotrunning abort
Running instances of gmusicbrowser are detected via the fifo or via DBus.
To run more than one instance, use a unique fifo and a unique DBus-id, or deactivate them.

Options to change what is done with files/folders passed as arguments (done in running gmusicbrowser if there is one) :
-playlist        : Set them as playlist (default)
-enqueue        : Enqueue them
-addplaylist        : Add them to the playlist
-insertplaylist        : Insert them in the playlist after current song
-add            : Add them to the library

-tagedit FOLDER_OR_FILE ... : Edittag mode
-listplugin    : list the available plugins and exit
-listcmd    : list the available fifo commands and exit
-listlayout    : list the available layouts and exit
**~$ gmusicbrowser -listcmd**
Name "GMB::DBus::bus" used only once: possible typo at /usr/bin/gmusicbrowser line 394.
Available commands (for fifo or layouts) :
AddFilesToPlaylist          : Add a list of files/folders to the playlist  (argument : url-encoded list of files/folders)
AddToLibrary                : Add files/folders to library  (argument : url-encoded list of files/folders)
Browser                     : Open Browser 
ChangeDisplay               : Change Display  (argument : Display (:1 or host:0 for example))
ClearPlayFilter             : Clear playlist filter 
ClearPlaylist               : Clear playlist 
ClearQueue                  : Clear queue 
CloseWindow                 : Close Window 
DecVolume                   : Decrease Volume 
DeleteSelected              : Delete Selected Songs 
EditSelectedSongsProperties : Edit selected song properties 
EnqueueAction               : Enqueue Action  (argument : Queue mode)
EnqueueAlbum                : Enqueue Songs from Current Album 
EnqueueArtist               : Enqueue Songs from Current Artist 
EnqueueFiles                : Enqueue a list of files/folders  (argument : url-encoded list of files/folders)
EnqueueSelected             : Enqueue Selected Songs 
Forward                     : Forward  (argument : Number of seconds)
GoToCurrentSong             : Select current song 
Hide                        : Hide 
IncVolume                   : Increase Volume 
InsertFilesInPlaylist       : Insert a list of files/folders at the start of the playlist  (argument : url-encoded list of files/folders)
MenuPlayFilter              : Popup playlist filter menu 
MenuPlayOrder               : Popup playlist order menu 
MenuQueue                   : Popup queue menu 
NextAlbum                   : Next Album 
NextArtist                  : Next Artist 
NextSong                    : Next Song 
NextSongInPlaylist          : Next Song In Playlist 
OpenContext                 : Open Context window 
OpenCustom                  : Open Custom window  (argument : Name of layout)
OpenFiles                   : Play a list of files  (argument : url-encoded list of files)
OpenPref                    : Open Preference window 
OpenQueue                   : Open Queue window 
OpenSearch                  : Open Search window 
OpenSongProp                : Edit Current Song Properties 
Pause                       : Pause 
Play                        : Play 
PlayListed                  : Play listed songs 
PlayPause                   : Play/Pause 
PopupCustom                 : Popup Custom window  (argument : Name of layout)
PopupTrayTip                : Popup Traytip  (argument : Number of milliseconds)
PrevSong                    : Previous Song 
PrevSongInPlaylist          : Previous Song In Playlist 
QueueInsertSelected         : Insert Selected Songs at the top of the queue 
Quit                        : Quit 
ReloadLayouts               : Re-load layouts 
Rewind                      : Rewind  (argument : Number of seconds)
RunPerlCode                 : Run perl code  (argument : perl code)
RunShellCmd                 : Run shell command  (argument : Shell command)
RunShellCmdOnSelected       : Run shell command on selected songs  (argument : Shell command)
RunSysCmd                   : Run system command  (argument : System command)
RunSysCmdOnSelected         : Run system command on selected songs  (argument : System command)
Save                        : Save Tags/Options 
Seek                        : Seek  (argument : Number of seconds)
SetFocusOn                  : Set focus on a layout widget  (argument : Widget name)
SetNextAction               : Set action when song ends  (argument : Action)
SetPlayerLayout             : Set player window layout  (argument : Name of layout)
SetSongLabel                : Add a label to the current song  (argument : Label)
SetSongRating               : Set Current Song Rating  (argument : Rating between 0 and 100, or empty for default)
Show                        : Show 
ShowHide                    : Show/Hide 
ShowHideWidget              : Show/Hide layout widget(s)  (argument : |-separated list of widget names)
Stop                        : Stop 
TogAlbumLock                : Toggle Album Lock 
TogArtistLock               : Toggle Artist Lock 
TogMute                     : Mute/Unmute 
TogSongLock                 : Toggle Song Lock 
ToggleFullscreen            : Toggle fullscreen mode 
ToggleFullscreenLayout      : Toggle the fullscreen layout 
ToggleRandom                : Toggle between Random/Shuffle and Ordered 
ToggleSongLabel             : Toggle a label of the current song  (argument : Label)
UnsetSongLabel              : Remove a label from the current song  (argument : Label)
```

---

