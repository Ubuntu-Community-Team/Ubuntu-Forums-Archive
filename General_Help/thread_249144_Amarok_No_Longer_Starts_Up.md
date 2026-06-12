---
title: "Amarok No Longer Starts Up"
date: 2006-09-02
forum: General Help
---

### Post by AlphaMack on 2006-09-02
I have been using Amarok 1.4.2 beautifully for the longest time until recently.  I have no idea what has happened but it will no longer start up.  Under Kubuntu it shows as starting up but disappears after 30s.  Under Ubuntu it never starts up but appears in the System Monitor chewing up CPU cycles.  The splash screen doesn't appear at all.

What I have done to no avail:
-Reinstalled
-Tried launching it in a test account (failed obviously)
-Deleted configuration files in my /home/username/.kde/...

Any ideas?

---

### Post by patwack on 2006-09-02
mine started doing what you describe a few days ago, but it eventually popped up about 5 minutes later after using the cpu at almost 100% for that time, i was assuming it was some sort of database problem, have you tried using mysql instead of sqlite if you aren't already?

---

### Post by David Corrales on 2006-09-02
Have you tried starting it from the console? You get more info that way. It could be a lock file somewhere around for example.

---

### Post by jleems86 on 2006-09-02
I have asimilar problem.  i run ubuntu dapper and amarok won't start no matter what.  the splash screen shows up, disappears and nothing happens.  i tried running it from console and the [rocess ended after it produced the following
```
:~$ amarok
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
amarok: BEGIN: App::App()
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
amarok: BEGIN: void App::fixHyperThreading()
amarok:     Workaround not enabled
amarok: END__: void App::fixHyperThreading() - Took 0.0004s
amarok: END__: App::App() - Took 0.73s
amarok: BEGIN: void App::continueInit()
amarok: BEGIN: EngineBase* EngineController::loadEngine(const QString&)
amarok:     [PluginManager] Plugin trader constraint: [X-KDE-Amarok-framework-version] == 26 and [X-KDE-Amarok-plugintype] == 'engine' and [X-KDE-Amarok-name] != 'void-engine' and [X-KDE-Amarok-rank] > 0
amarok:     [PluginManager] Plugin trader constraint: [X-KDE-Amarok-framework-version] == 26 and [X-KDE-Amarok-plugintype] == 'engine' and [X-KDE-Amarok-name] == 'void-engine' and [X-KDE-Amarok-rank] > 0
amarok:     [PluginManager] Trying to load: libamarok_void-engine_plugin
amarok:
amarok:     PluginManager Service Info:
amarok:     ---------------------------
amarok:     name                          : <no engine>
amarok:     library                       : libamarok_void-engine_plugin
amarok:     desktopEntryPath              : amarok_void-engine_plugin.desktop
amarok:     X-KDE-Amarok-plugintype       : engine
amarok:     X-KDE-Amarok-name             : void-engine
amarok:     X-KDE-Amarok-authors          : (Max Howell,Mark Kretschmann)
amarok:     X-KDE-Amarok-rank             : 1
amarok:     X-KDE-Amarok-version          : 1
amarok:     X-KDE-Amarok-framework-version: 26
amarok:
amarok: END__: EngineBase* EngineController::loadEngine(const QString&) - Took 0.0092s
amarok: BEGIN: CollectionDB::CollectionDB()
amarok: BEGIN: void CollectionDB::initialize()
amarok:       [ThreadWeaver] Creating pthread key, exit value is 0
amarok: BEGIN: SqliteConnection::SqliteConnection(const SqliteConfig*)
amarok: END__: SqliteConnection::SqliteConnection(const SqliteConfig*) - Took 0.00085s
amarok:       [CollectionDB] Updating DEVICES table
amarok: END__: void CollectionDB::initialize() - Took 0.03s
amarok:     [CollectionDB] INotify not available, using QTimer!
amarok: END__: CollectionDB::CollectionDB() - Took 0.061s
amarok: BEGIN: void CollectionDB::checkDatabase()
amarok:     [CollectionDB] Beginning database update
amarok:     [CollectionDB] Different database stats version detected! Stats table will be updated or rebuilt.
amarok:     [CollectionDB] [ERROR!] Database statistics version too new for this version of Amarok. Quitting...
amarok: BEGIN: virtual CollectionDB::~CollectionDB()
amarok:       [CollectionDB] Running VACUUM
amarok: END__: virtual CollectionDB::~CollectionDB() - Took 0.098s
amarok:     [virtual EngineController::~EngineController()]

```
Any help would be much appreciated

---

### Post by AlphaMack on 2006-09-02
Could it be related to sqlite?

```
:~$ amarok
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
amarok: BEGIN: App::App()
amarok: BEGIN: void App::fixHyperThreading()
amarok:     Workaround not enabled
amarok: END__: void App::fixHyperThreading() - Took 0.0022s
amarok: END__: App::App() - Took 0.06s
amarok: BEGIN: void App::continueInit()
amarok: BEGIN: EngineBase* EngineController::loadEngine(const QString&)
amarok:     [PluginManager] Plugin trader constraint: [X-KDE-Amarok-framework-version] == 26 and [X-KDE-Amarok-plugintype] == 'engine' and [X-KDE-Amarok-name] != 'void-engine' and [X-KDE-Amarok-rank] > 0
amarok:     [PluginManager] Plugin trader constraint: [X-KDE-Amarok-framework-version] == 26 and [X-KDE-Amarok-plugintype] == 'engine' and [X-KDE-Amarok-name] == 'void-engine' and [X-KDE-Amarok-rank] > 0
amarok:     [PluginManager] Trying to load: libamarok_void-engine_plugin
amarok:
amarok:     PluginManager Service Info:
amarok:     ---------------------------
amarok:     name                          : <no engine>
amarok:     library                       : libamarok_void-engine_plugin
amarok:     desktopEntryPath              : amarok_void-engine_plugin.desktop
amarok:     X-KDE-Amarok-plugintype       : engine
amarok:     X-KDE-Amarok-name             : void-engine
amarok:     X-KDE-Amarok-authors          : (Max Howell,Mark Kretschmann)
amarok:     X-KDE-Amarok-rank             : 1
amarok:     X-KDE-Amarok-version          : 1
amarok:     X-KDE-Amarok-framework-version: 26
amarok:
amarok: END__: EngineBase* EngineController::loadEngine(const QString&) - Took 0.16s
amarok: BEGIN: CollectionDB::CollectionDB()
amarok: BEGIN: void CollectionDB::initialize()
amarok:       [ThreadWeaver] Creating pthread key, exit value is 0
amarok: BEGIN: SqliteConnection::SqliteConnection(const SqliteConfig*)
amarok:         [CollectionDB] [WARNING!] Database versions incompatible. Removing and rebuilding database.
amarok: END__: SqliteConnection::SqliteConnection(const SqliteConfig*) - Took 0.0046s
amarok:       [CollectionDB] [ERROR!] [virtual QStringList SqliteConnection::query(const QString&)]  sqlite3_compile error:
amarok:       [CollectionDB] [ERROR!] no such table: tags
amarok:       [CollectionDB] [ERROR!] on query: SELECT COUNT( url ) FROM tags LIMIT 1 OFFSET 0;
amarok:       [CollectionDB] [ERROR!] [virtual QStringList SqliteConnection::query(const QString&)]  sqlite3_compile error:
amarok:       [CollectionDB] [ERROR!] no such table: tags
amarok:       [CollectionDB] [ERROR!] on query: SELECT COUNT( url ) FROM tags LIMIT 1 OFFSET 0;
amarok:       [CollectionDB] [ERROR!] [virtual QStringList SqliteConnection::query(const QString&)]  sqlite3_compile error:
amarok:       [CollectionDB] [ERROR!] no such table: tags
amarok:       [CollectionDB] [ERROR!] on query: SELECT COUNT( url ) FROM tags LIMIT 1 OFFSET 0;
amarok:       [CollectionDB] [ERROR!] [virtual QStringList SqliteConnection::query(const QString&)]  sqlite3_compile error:
amarok:       [CollectionDB] [ERROR!] no such table: tags
amarok:       [CollectionDB] [ERROR!] on query: SELECT COUNT( url ) FROM tags LIMIT 1 OFFSET 0;
amarok:       [CollectionDB] [ERROR!] [virtual QStringList SqliteConnection::query(const QString&)]  sqlite3_compile error:
amarok:       [CollectionDB] [ERROR!] no such table: tags
amarok:       [CollectionDB] [ERROR!] on query: SELECT COUNT( url ) FROM tags LIMIT 1 OFFSET 0;
amarok:       [CollectionDB] [ERROR!] [virtual QStringList SqliteConnection::query(const QString&)]  sqlite3_compile error:
amarok:       [CollectionDB] [ERROR!] no such table: tags
amarok:       [CollectionDB] [ERROR!] on query: SELECT COUNT( url ) FROM tags LIMIT 1 OFFSET 0;
amarok:       [CollectionDB] [ERROR!] [virtual QStringList SqliteConnection::query(const QString&)]  sqlite3_compile error:
amarok:       [CollectionDB] [ERROR!] no such table: tags
amarok:       [CollectionDB] [ERROR!] on query: SELECT COUNT( url ) FROM tags LIMIT 1 OFFSET 0;
amarok:       [CollectionDB] [ERROR!] [virtual QStringList SqliteConnection::query(const QString&)]  sqlite3_compile error:
amarok:       [CollectionDB] [ERROR!] no such table: tags
amarok:       [CollectionDB] [ERROR!] on query: SELECT COUNT( url ) FROM tags LIMIT 1 OFFSET 0;
amarok:       [CollectionDB] [ERROR!] [virtual QStringList SqliteConnection::query(const QString&)]  sqlite3_compile error:
amarok:       [CollectionDB] [ERROR!] no such table: tags
amarok:       [CollectionDB] [ERROR!] on query: SELECT COUNT( url ) FROM tags LIMIT 1 OFFSET 0;
amarok:       [CollectionDB] [ERROR!] [virtual QStringList SqliteConnection::query(const QString&)]  sqlite3_compile error:
amarok:       [CollectionDB] [ERROR!] no such table: tags
amarok:       [CollectionDB] [ERROR!] on query: SELECT COUNT( url ) FROM tags LIMIT 1 OFFSET 0;

```

And it kept repeating the same lines over and over until I killed it.

---

### Post by David Corrales on 2006-09-02
It's most probably a problem with the sqlite backend. Probably an update killed it or it's functioning badly. Try to purge those packages (select Complete removal in synaptic, that will delete it's configuration files) and reinstall them.

---

### Post by jleems86 on 2006-09-02
tried purging libsqlite0 and libsqlite3-0 and reinstalled them.  amarok still didn't start and ended completely.  i think this might have somthing to do with the error that it spit out
```
amarok:     [CollectionDB] [ERROR!] Database statistics version too new for this version of Amarok. Quitting...

```

---

### Post by jleems86 on 2006-09-02
just fixed mine, hope this helps everyone
found the fix from [HTML]http://amarok.kde.org/forum/index.php?topic=12828.msg14555[/HTML]
> If you've ever downgraded from 1.4.2_beta (or 1.4.2)  back to 1.4.anything, then tried to upgrade again, sorry. your database is broken.
You'll need to drop and recreate your mysql amarok db (see mysql man page for details).
Note: this goes for sqlite as well - you'll need to delete your ~/.kde/share/apps/amarok/collection.db to fix the problem.

nearest i can tell, this delets your statistics and collection database so all your song ratings and rankings will be gone unfortunately.  at least you still have your songs though

---

### Post by AlphaMack on 2006-09-03
^ Still doesn't work after doing that.

---

### Post by AlphaMack on 2006-09-04
Decided to reinstall Ubuntu/Kubuntu from scratch using Ubuntu 6.06-1 alt. CD.  Amarok still doesn't work and I'm beginning to suspect it's something in /home although I tried removing configs from the paths aforementioned in this thread.

---

### Post by AlphaMack on 2006-09-04
Downgraded to 1.3.9 and everything works.  Seems to be a conflict with 1.4.2.  Unfortunately, I still can't pin it down. :?

---

### Post by AlphaMack on 2006-09-05
Last post in this thread.  I'm currently running Amarok 1.4.1 as 1.4.2 still breaks for me.

I believe that my problem in the OP had to do with the upgrade to 1.4.2 now that I think about it.

So if you guys have the same issue, what I suggest doing is adding the repo below:

```
wget http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg
sudo apt-key add kubuntu-packages-jriddell-key.gpg

deb http://kubuntu.org/packages/amarok-141 dapper main
```

and perform the downgrade from 1.4.2.

---

### Post by orb9220 on 2006-09-05
Wierd since 1.4.2 works for me. Had no problems with it. Installed by:

wget [http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg](http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg)

sudo -s

apt-key add kubuntu-packages-jriddell-key.gpg

echo "deb [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) dapper main" >> /etc/apt/sources.list

apt-get update

apt-get install amarok amarok-engines

may get error for the jriddell-key.gpg line but otherwise it installed fine.

The only bug I read about if people installed the 1.4.2 beta wolf? something and then tried to downgrade or upgrade that it broke amarok.

---

### Post by snoudly on 2006-10-06
I got the same problem too. 
Looks like the new version of amaroK doesn't recognise an old mysql-database.
Solved it by **dropping all the tables in the amarok-db**, so it's totally empty.

If you really like your statistics you could try to rename your db and then transfer the datas back again, after amarok has built a new db. A bit puzzly, I think...

---

### Post by spyrakos on 2006-10-11
I've been having the same problem since upgrading to 1.4.3. Amarok started up once, everything seemed fine. Then on reboot, it wouldn't start anymore. Strange thing here is that it boots, starts as an tray icon, but hangs when told to restore to window mode. 

I tried regrading back to 1.3.9: that worked, but even if it scanned my collection it wouldn't show up. Going back to 1.4.3 had the same effect as before, it worked the first time then nothing. After deleting the amarok-db (sqlite) in ./kde/share/apps/amarok, it started up normally but only for once as before. So I thought that it might be the database's fault, and switched to mysql. I set it up accordingly to Amarok's HowTo and seemed to work fine (faster too :)). On the "quit-and-restart" test though, the problem was back, but this time Amarok would start in tray icon mode, then on right click-->restore it crashes displaying a popup saying 

"couldn't launch the mail client 
KDEInit could not launch Kmail
Could not find 'kmail' executable" :-? 

Any ideas???

Here's the terminal output in case it helps
```
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokap p.
amarok: BEGIN: App::App()
amarok: BEGIN: void App::fixHyperThreading()
amarok:     Workaround not enabled
amarok: END__: void App::fixHyperThreading() - Took 0.00046s
amarok: END__: App::App() - Took 0.0045s
amarok: BEGIN: void App::continueInit()
amarok: BEGIN: EngineBase* EngineController::loadEngine(const QString&)
amarok:     [PluginManager] Plugin trader constraint: [X-KDE-Amarok-framework-ve rsion] == 27 and [X-KDE-Amarok-plugintype] == 'engine' and [X-KDE-Amarok-name] ! = 'void-engine' and [X-KDE-Amarok-rank] > 0
amarok:     [PluginManager] Plugin trader constraint: [X-KDE-Amarok-framework-ve rsion] == 27 and [X-KDE-Amarok-plugintype] == 'engine' and [X-KDE-Amarok-name] = = 'void-engine' and [X-KDE-Amarok-rank] > 0
amarok:     [PluginManager] Trying to load: libamarok_void-engine_plugin
amarok:
amarok:     PluginManager Service Info:
amarok:     ---------------------------
amarok:     name                          : <no engine>
amarok:     library                       : libamarok_void-engine_plugin
amarok:     desktopEntryPath              : amarok_void-engine_plugin.desktop
amarok:     X-KDE-Amarok-plugintype       : engine
amarok:     X-KDE-Amarok-name             : void-engine
amarok:     X-KDE-Amarok-authors          : (Max Howell,Mark Kretschmann)
amarok:     X-KDE-Amarok-rank             : 1
amarok:     X-KDE-Amarok-version          : 1
amarok:     X-KDE-Amarok-framework-version: 27
amarok:
amarok: END__: EngineBase* EngineController::loadEngine(const QString&) - Took 0 .0089s
amarok: BEGIN: CollectionDB::CollectionDB()
amarok: BEGIN: void CollectionDB::initialize()
amarok:       [ThreadWeaver] Creating pthread key, exit value is 0
amarok: BEGIN: MySqlConnection::MySqlConnection(const MySqlConfig*)
amarok:         [CollectionDB] [MySqlConnection::MySqlConnection(const MySqlConf ig*)]
amarok:         [CollectionDB] Connection Charset is now: latin1
amarok: END__: MySqlConnection::MySqlConnection(const MySqlConfig*) - Took 0.007 4s
amarok: END__: void CollectionDB::initialize() - Took 0.01s
amarok:     [Scrobbler] Couldn't open file: /home/spyros/.kde/share/apps/amarok/ submit.xml
amarok:     [CollectionDB] INotify not available, using QTimer!
amarok: END__: CollectionDB::CollectionDB() - Took 0.016s
amarok: BEGIN: void CollectionDB::checkDatabase()
amarok:     [CollectionDB] INotify not available, using QTimer!
amarok: END__: void CollectionDB::checkDatabase() - Took 0.063s
amarok: BEGIN: MediaDeviceManager::MediaDeviceManager()
amarok: BEGIN: DeviceManager::DeviceManager()
amarok:       During DeviceManager init, error during DCOP call
amarok: BEGIN: Medium* DeviceManager::getDevice(QString)
amarok:         DeviceManager: getDevice called with name argument = init
amarok: BEGIN: QStringList DeviceManager::getDeviceStringList()
amarok:           Error during DCOP call
amarok: END__: QStringList DeviceManager::getDeviceStringList() - Took 0.00032s
amarok: END__: Medium* DeviceManager::getDevice(QString) - Took 0.0005s
amarok:       DeviceManager:  connectDCOPSignal returned successfully!
amarok: END__: DeviceManager::DeviceManager() - Took 0.0017s
amarok: BEGIN: QStringList DeviceManager::getDeviceStringList()
amarok:       Error during DCOP call
amarok: END__: QStringList DeviceManager::getDeviceStringList() - Took 0.0003s
amarok:     DeviceManager didn't return any devices, we are probably running on a non-KDE system. Trying to reinit media devices later
amarok: END__: MediaDeviceManager::MediaDeviceManager() - Took 0.0025s
amarok: BEGIN: void PlaylistWindow::init()
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
amarok: BEGIN: void MountPointManager::init()
amarok:       [PluginManager] Plugin trader constraint: [X-KDE-Amarok-framework- version] == 27 and [X-KDE-Amarok-plugintype] == 'device' and [X-KDE-Amarok-rank]  > 0
amarok:       [MountPointManager] Received [3] device plugin offers
amarok:       [PluginManager] Trying to load: libamarok_massstorage-device
amarok:
amarok:       PluginManager Service Info:
amarok:       ---------------------------
amarok:       name                          : Mass Storage Device
amarok:       library                       : libamarok_massstorage-device
amarok:       desktopEntryPath              : amarok_massstorage-device.desktop
amarok:       X-KDE-Amarok-plugintype       : device
amarok:       X-KDE-Amarok-name             : massstorage-device
amarok:       X-KDE-Amarok-authors          : (Maximilian Kossick)
amarok:       X-KDE-Amarok-rank             : 100
amarok:       X-KDE-Amarok-version          : 1
amarok:       X-KDE-Amarok-framework-version: 27
amarok:
amarok:       [PluginManager] Trying to load: libamarok_smb-device
amarok:
amarok:       PluginManager Service Info:
amarok:       ---------------------------
amarok:       name                          : SMB Device
amarok:       library                       : libamarok_smb-device
amarok:       desktopEntryPath              : amarok_smb-device.desktop
amarok:       X-KDE-Amarok-plugintype       : device
amarok:       X-KDE-Amarok-name             : smb-device
amarok:       X-KDE-Amarok-authors          : (Maximilian Kossick)
amarok:       X-KDE-Amarok-rank             : 100
amarok:       X-KDE-Amarok-version          : 1
amarok:       X-KDE-Amarok-framework-version: 27
amarok:
amarok:       [PluginManager] Trying to load: libamarok_nfs-device
amarok:
amarok:       PluginManager Service Info:
amarok:       ---------------------------
amarok:       name                          : NFS Device
amarok:       library                       : libamarok_nfs-device
amarok:       desktopEntryPath              : amarok_nfs-device.desktop
amarok:       X-KDE-Amarok-plugintype       : device
amarok:       X-KDE-Amarok-name             : nfs-device
amarok:       X-KDE-Amarok-authors          : (Maximilian Kossick)
amarok:       X-KDE-Amarok-rank             : 100
amarok:       X-KDE-Amarok-version          : 1
amarok:       X-KDE-Amarok-framework-version: 27
amarok:
amarok: BEGIN: QStringList DeviceManager::getDeviceStringList()
amarok:         Error during DCOP call
amarok: END__: QStringList DeviceManager::getDeviceStringList() - Took 0.00043s
amarok: END__: void MountPointManager::init() - Took 0.013s
amarok:     [Moodbar] Resetting moodbar:
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for Play listWindow/PlaylistWindow
amarok: BEGIN: Creating browsers. Please report long start times!
amarok: BEGIN: ContextBrowser
amarok: END__: ContextBrowser - Took 0.1s
amarok: BEGIN: CollectionBrowser
amarok: BEGIN: virtual void ThreadWeaver::Thread::run()
amarok: BEGIN: MySqlConnection::MySqlConnection(const MySqlConfig*)
amarok:             [CollectionDB] [MySqlConnection::MySqlConnection(const MySql Config*)]
amarok:             [CollectionDB] Connection Charset is now: latin1
amarok: END__: MySqlConnection::MySqlConnection(const MySqlConfig*) - Took 0.000 93s
amarok:           [CollectionView::CollectionView(CollectionBrowser*)]
amarok:           current browser is not collection, aborting renderView()
amarok: END__: CollectionBrowser - Took 0.18s
amarok: BEGIN: PlaylistBrowser
amarok: BEGIN: PlaylistCategory* PlaylistBrowser::loadPodcasts()
amarok: END__: PlaylistCategory* PlaylistBrowser::loadPodcasts() - Took 0.002s
amarok: END__: PlaylistBrowser - Took 0.053s
amarok: BEGIN: FileBrowser
amarok: END__: virtual void ThreadWeaver::Thread::run() - Took 0.43s
amarok: END__: FileBrowser - Took 0.37s
amarok:       [PluginManager] Plugin trader constraint: [X-KDE-Amarok-framework- version] == 27 and [X-KDE-Amarok-plugintype] == 'mediadevice' and [X-KDE-Amarok- rank] > 0
amarok: BEGIN: MediaBrowser
amarok: END__: MediaBrowser - Took 0.0077s
amarok: END__: Creating browsers. Please report long start times! - Took 0.84s
amarok: END__: void PlaylistWindow::init() - Took 1.1s
amarok:   | Stamp: 1
amarok: BEGIN: void App::applySettings(bool)
QPainter::begin: Cannot paint null pixmap
amarok:     [Moodbar] Resetting moodbar:
amarok:     [Scrobbler] Performing immediate handshake
amarok:     [Scrobbler] Handshake url: [http://post.audioscrobbler.com/?hs=true&p](http://post.audioscrobbler.com/?hs=true&p) =1.1&c=ark&v=1.4&u=spyrakos
amarok:     [CollectionDB] Database engine settings changed: recreating DbConnec tions
amarok: BEGIN: void CollectionDB::initialize()
amarok: BEGIN: MySqlConnection::MySqlConnection(const MySqlConfig*)
amarok:         [CollectionDB] [MySqlConnection::MySqlConnection(const MySqlConf ig*)]
amarok:         [CollectionDB] Connection Charset is now: latin1
amarok: END__: MySqlConnection::MySqlConnection(const MySqlConfig*) - Took 0.000 96s
amarok: END__: void CollectionDB::initialize() - Took 0.0033s
amarok:     current browser is not collection, aborting renderView()
amarok: BEGIN: EngineBase* EngineController::loadEngine()
amarok: BEGIN: EngineBase* EngineController::loadEngine(const QString&)
amarok:         [PluginManager] Plugin trader constraint: [X-KDE-Amarok-framewor k-version] == 27 and [X-KDE-Amarok-plugintype] == 'engine' and [X-KDE-Amarok-nam e] != 'xine-engine' and [X-KDE-Amarok-rank] > 0
amarok:         [PluginManager] Plugin trader constraint: [X-KDE-Amarok-framewor k-version] == 27 and [X-KDE-Amarok-plugintype] == 'engine' and [X-KDE-Amarok-nam e] == 'xine-engine' and [X-KDE-Amarok-rank] > 0
amarok:         [PluginManager] Trying to load: libamarok_xine-engine
amarok:         [xine-engine] hello
amarok:
amarok:         PluginManager Service Info:
amarok:         ---------------------------
amarok:         name                          : xine Engine
amarok:         library                       : libamarok_xine-engine
amarok:         desktopEntryPath              : amarok_xine-engine.desktop
amarok:         X-KDE-Amarok-plugintype       : engine
amarok:         X-KDE-Amarok-name             : xine-engine
amarok:         X-KDE-Amarok-authors          : (Max Howell)
amarok:         X-KDE-Amarok-rank             : 255
amarok:         X-KDE-Amarok-version          : 1
amarok:         X-KDE-Amarok-framework-version: 27
amarok:
amarok: BEGIN: virtual bool XineEngine::init()
amarok:           [xine-engine] 'Bringing joy to small mexican gerbils, a few we eks at a time.'
amarok:           [xine-engine] w00t/home/spyros/.kde/share/apps/amarok/xine-con fig
amarok:           [xine-engine] gapless playback enabled.
amarok: END__: virtual bool XineEngine::init() - Took 0.28s
amarok: END__: EngineBase* EngineController::loadEngine(const QString&) - Took 0 .36s
amarok: END__: EngineBase* EngineController::loadEngine() - Took 0.36s
amarok:     current browser is not collection, aborting renderView()
amarok: END__: void App::applySettings(bool) - Took 0.44s
amarok:   | Stamp: 2
amarok: BEGIN: ScriptManager::ScriptManager(QWidget*, const char*)
amarok: END__: ScriptManager::ScriptManager(QWidget*, const char*) - Took 0.0037 s
amarok:   | Stamp: 3
amarok:   [Moodbar] Resetting moodbar:
spyros@spyros-laptop:~$ amarok: END__: void App::continueInit() - Took 2s
amarok: [ThreadWeaver] Job aborted: CurrentTrackJob. Jobs pending: 2
amarok: [ThreadWeaver] Job aborted: CurrentTrackJob. Jobs pending: 1
amarok: [ScriptManager] Loaded: playlist2html.py
amarok: [ScriptManager] Loaded: PlaylistServer.py
amarok: [ScriptManager] Loaded: Lyrc
amarok: [ScriptManager] Loaded: Default
amarok: [ScriptManager] Loaded: Impulsive
amarok: BEGIN: virtual void ThreadWeaver::Thread::run()
amarok: BEGIN: MySqlConnection::MySqlConnection(const MySqlConfig*)
amarok:     [CollectionDB] [MySqlConnection::MySqlConnection(const MySqlConfig*) ]
amarok:     [CollectionDB] Connection Charset is now: latin1
amarok: END__: MySqlConnection::MySqlConnection(const MySqlConfig*) - Took 0.000 94s
amarok: BEGIN: virtual void ThreadWeaver::Thread::run()
amarok: BEGIN: virtual bool StatisticsUpdateJob::doJob()
amarok: BEGIN: MySqlConnection::MySqlConnection(const MySqlConfig*)
amarok:         [CollectionDB] [MySqlConnection::MySqlConnection(const MySqlConf ig*)]
amarok:         [CollectionDB] Connection Charset is now: latin1
amarok: END__: MySqlConnection::MySqlConnection(const MySqlConfig*) - Took 0.000 9s
amarok:       [MountPointManager] Trying to update 0 statistics rows
amarok: END__: virtual bool StatisticsUpdateJob::doJob() - Took 0.0013s
amarok: END__: virtual void ThreadWeaver::Thread::run() - Took 0.0015s
amarok:   [ScriptManager] Loaded: Web Control
amarok:   [ScriptManager] Auto-running script: Default
amarok:   [ScriptManager] Running script: /usr/share/apps/amarok/scripts/score_d efault/score_default.rb
amarok:   [ScriptManager] Auto-running script: Lyrc
amarok:   [ScriptManager] Running script: /usr/share/apps/amarok/scripts/lyrics_ lyrc/lyrics_lyrc.rb
amarok:   [ThreadWeaver] Job completed: StatisticsUpdateJob. Jobs pending: 0
amarok: END__: virtual void ThreadWeaver::Thread::run() - Took 0.5s
amarok: [ThreadWeaver] Job completed: CurrentTrackJob. Jobs pending: 0
amarok: [Scrobbler] Handshake result parsed: challenge=20B4242C71D997BFC2EE4360E ACB5E28, submitUrl=http://62.216.251.205:80/protocol_1.1
amarok: [Scrobbler] Nothing to schedule
amarok: BEGIN: QStringList DeviceManager::getDeviceStringList()
amarok:   Error during DCOP call
amarok: END__: QStringList DeviceManager::getDeviceStringList() - Took 0.00078s
```

---

### Post by Warm.Beer on 2007-04-24
I had the same issue.  Try removing any .mp4 video files from your collection before starting Amarok.  Fixed mine straight away, it mustn't have liked Battlestar Galactica :)

---

