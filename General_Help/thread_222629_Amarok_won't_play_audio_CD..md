---
title: "Amarok won't play audio CD."
date: 2006-07-25
forum: General Help
---

### Post by GarethMB on 2006-07-25
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
amarok:   BEGIN: void App::fixHyperThreading()
amarok:     Fix not enabled
amarok:   END__: void App::fixHyperThreading() - Took 0.00099s
amarok:   BEGIN: DeviceManager::DeviceManager()
amarok:     BEGIN: Medium* DeviceManager::getDevice(QString)
amarok:       DeviceManager: getDevice called with name argument = init
amarok:       BEGIN: QStringList DeviceManager::getDeviceStringList(bool)
amarok:       END__: QStringList DeviceManager::getDeviceStringList(bool) - Took 0.00081s
amarok:     END__: Medium* DeviceManager::getDevice(QString) - Took 0.0017s
amarok:     DeviceManager:  connectDCOPSignal returned sucessfully!
amarok:   END__: DeviceManager::DeviceManager() - Took 0.0043s
amarok:   BEGIN: EngineBase* EngineController::loadEngine(const QString&)
amarok:     [PluginManager] Plugin trader constraint: [X-KDE-Amarok-framework-version] == 25 and [X-KDE-Amarok-plugintype] == 'engine' and [X-KDE-Amarok-name] != 'void-engine' and [X-KDE-Amarok-rank] > 0
amarok:     [PluginManager] Plugin trader constraint: [X-KDE-Amarok-framework-version] == 25 and [X-KDE-Amarok-plugintype] == 'engine' and [X-KDE-Amarok-name] == 'void-engine' and [X-KDE-Amarok-rank] > 0
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
amarok:     X-KDE-Amarok-framework-version: 25
amarok:
amarok:   END__: EngineBase* EngineController::loadEngine(const QString&) - Took 0.057s
amarok:   BEGIN: void PlaylistWindow::init()
amarok:     BEGIN: CollectionDB::CollectionDB()
amarok:       BEGIN: void CollectionDB::initialize()
amarok:         [ThreadWeaver] Creating pthread key, exit value is 0
amarok:         BEGIN: SqliteConnection::SqliteConnection(const SqliteConfig*)
amarok:         END__: SqliteConnection::SqliteConnection(const SqliteConfig*) - Took 0.0016s
amarok:         [CollectionDB] Podcast tables created and up to date
amarok:       END__: void CollectionDB::initialize() - Took 0.0073s
amarok:       [CollectionDB] INotify not available, using QTimer!
amarok:     END__: CollectionDB::CollectionDB() - Took 0.09s
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
amarok:     BEGIN: Creating browsers. Please report long start times!
amarok:       BEGIN: ContextBrowser
amarok:         [ContextBrowser] Rendering showCurrentTrack()
amarok:       END__: ContextBrowser - Took 0.13s
amarok:       BEGIN: CollectionBrowser
amarok:         [CollectionView::CollectionView(CollectionBrowser*)]
amarok:         BEGIN: void CollectionView::renderView(bool)
amarok:           current browser is not collection, aborting renderView()
amarok:         END__: void CollectionView::renderView(bool) - Took 0.00047s
amarok:       END__: CollectionBrowser - Took 0.018s
amarok:       BEGIN: PlaylistBrowser
amarok:         BEGIN: virtual void ThreadWeaver::Thread::run()
amarok:           BEGIN: virtual bool CurrentTrackJob::doJob()
amarok:             BEGIN: void CurrentTrackJob::showHome()
amarok:               BEGIN: SqliteConnection::SqliteConnection(const SqliteConfig*)
amarok:               END__: SqliteConnection::SqliteConnection(const SqliteConfig*) - Took 0.00056s
amarok:               BEGIN: PlaylistCategory* PlaylistBrowser::loadPodcasts()
amarok:               END__: PlaylistCategory* PlaylistBrowser::loadPodcasts() - Took 0.0027s
amarok:             END__: PlaylistBrowser - Took 0.063s
amarok:             BEGIN: FileBrowser
ScimInputContextPlugin()
amarok:             END__: void CurrentTrackJob::showHome() - Took 0.44s
amarok:           END__: virtual bool CurrentTrackJob::doJob() - Took 0.44s
amarok:         END__: virtual void ThreadWeaver::Thread::run() - Took 0.44s
amarok:       END__: FileBrowser - Took 0.64s
amarok:       [PluginManager] Plugin trader constraint: [X-KDE-Amarok-framework-version] == 25 and [X-KDE-Amarok-plugintype] == 'mediadevice' and [X-KDE-Amarok-rank] > 0
amarok:     END__: Creating browsers. Please report long start times! - Took 0.94s
amarok:   END__: void PlaylistWindow::init() - Took 1.2s
amarok:   BEGIN: UrlLoader
amarok:     BEGIN: UrlLoader::UrlLoader(const KURL::List&, QListViewItem*, bool)
amarok:       [KDE::ProgressBar::ProgressBar(QWidget*, QLabel*)]
amarok:     END__: UrlLoader::UrlLoader(const KURL::List&, QListViewItem*, bool) - Took 0.034s
amarok:     BEGIN: void App::applySettings(bool)
amarok:       BEGIN: virtual void ThreadWeaver::Thread::run()
amarok:       END__: virtual void ThreadWeaver::Thread::run() - Took 0.0049s
amarok:       [Scrobbler] Performing immediate handshake
amarok:       [Scrobbler] Handshake url: [http://post.audioscrobbler.com/?hs=true&p=1.1&c=ark&v=1.4&u=GarethMB](http://post.audioscrobbler.com/?hs=true&p=1.1&c=ark&v=1.4&u=GarethMB)
amarok:       [virtual void BrowserBar::polish()]
amarok:       [void ContextBrowser::tabChanged(QWidget*)]
amarok:       [ContextBrowser] Rendering showCurrentTrack()
amarok:       BEGIN: void CollectionView::renderView(bool)
amarok:         current browser is not collection, aborting renderView()
amarok:       END__: void CollectionView::renderView(bool) - Took 0.00048s
amarok:       [ThreadWeaver] Job aborted: CurrentTrackJob. Jobs pending: 1
amarok:       [ThreadWeaver] Job completed: UrlLoader. Jobs pending: 0
amarok:     END__: UrlLoader - Took 0.24s
amarok:     BEGIN: virtual void ThreadWeaver::Thread::run()
amarok:       BEGIN: virtual bool CurrentTrackJob::doJob()
amarok:         BEGIN: void CurrentTrackJob::showHome()
amarok:           BEGIN: SqliteConnection::SqliteConnection(const SqliteConfig*)
amarok:           END__: SqliteConnection::SqliteConnection(const SqliteConfig*) - Took 0.00056s
amarok:           [virtual KDE::ProgressBar::~ProgressBar()]
amarok:           BEGIN: EngineBase* EngineController::loadEngine()
amarok:             BEGIN: EngineBase* EngineController::loadEngine(const QString&)
amarok:               [PluginManager] Plugin trader constraint: [X-KDE-Amarok-framework-version] == 25 and [X-KDE-Amarok-plugintype] == 'engine' and [X-KDE-Amarok-name] != 'xine-engine' and [X-KDE-Amarok-rank] > 0
amarok:               [PluginManager] Plugin trader constraint: [X-KDE-Amarok-framework-version] == 25 and [X-KDE-Amarok-plugintype] == 'engine' and [X-KDE-Amarok-name] == 'xine-engine' and [X-KDE-Amarok-rank] > 0
amarok:               [PluginManager] Trying to load: libamarok_xine-engine
amarok:               [xine-engine] hello
amarok:
amarok:               PluginManager Service Info:
amarok:               ---------------------------
amarok:               name                          : xine Engine
amarok:               library                       : libamarok_xine-engine
amarok:               desktopEntryPath              : amarok_xine-engine.desktop
amarok:               X-KDE-Amarok-plugintype       : engine
amarok:               X-KDE-Amarok-name             : xine-engine
amarok:               X-KDE-Amarok-authors          : (Max Howell)
amarok:               X-KDE-Amarok-rank             : 255
amarok:               X-KDE-Amarok-version          : 1
amarok:               X-KDE-Amarok-framework-version: 25
amarok:
amarok:               BEGIN: virtual bool XineEngine::init()
amarok:                 [xine-engine] 'Bringing joy to small mexican gerbils, a few weeks at a time.'
amarok:                 [xine-engine] w00t/home/gareth/.kde/share/apps/amarok/xine-config
amarok:               END__: void CurrentTrackJob::showHome() - Took 0.41s
amarok:             END__: virtual bool CurrentTrackJob::doJob() - Took 0.41s
amarok:           END__: virtual void ThreadWeaver::Thread::run() - Took 0.41s
amarok:           [xine-engine] gapless playback enabled.
amarok:         END__: virtual bool XineEngine::init() - Took 0.27s
amarok:       END__: EngineBase* EngineController::loadEngine(const QString&) - Took 0.29s
amarok:     END__: EngineBase* EngineController::loadEngine() - Took 0.29s
amarok:     BEGIN: void CollectionView::renderView(bool)
amarok:       current browser is not collection, aborting renderView()
amarok:     END__: void CollectionView::renderView(bool) - Took 0.00069s
amarok:     [ContextBrowser] Rendering showCurrentTrack()
amarok:   END__: void App::applySettings(bool) - Took 0.68s
amarok:   BEGIN: ScriptManager::ScriptManager(QWidget*, const char*)
amarok:   END__: ScriptManager::ScriptManager(QWidget*, const char*) - Took 0.0033s
gareth@ubuntudapper:~$ amarok: END__: App::App() - Took 2.2s
amarok: [ThreadWeaver] Job aborted: CurrentTrackJob. Jobs pending: 1
amarok: BEGIN: virtual void ThreadWeaver::Thread::run()
amarok:   BEGIN: virtual bool CurrentTrackJob::doJob()
amarok:     BEGIN: void CurrentTrackJob::showHome()
amarok:       BEGIN: SqliteConnection::SqliteConnection(const SqliteConfig*)
amarok:       END__: SqliteConnection::SqliteConnection(const SqliteConfig*) - Took 0.00057s
amarok:       [ScriptManager] Loaded: playlist2html.py
amarok:       [ScriptManager] Loaded: PlaylistServer.py
amarok:       [ScriptManager] Loaded: Lyrc
amarok:       [ScriptManager] Loaded: Default
amarok:       [ScriptManager] Loaded: Impulsive
amarok:       [ScriptManager] Loaded: Web Control
amarok:       [ScriptManager] Auto-running script: Default
amarok:       [ScriptManager] Running script: /usr/share/apps/amarok/scripts/score_default/score_default.rb
amarok:       [ScriptManager] Auto-running script: Lyrc
amarok:       [ScriptManager] Running script: /usr/share/apps/amarok/scripts/lyrics_lyrc/lyrics_lyrc.rb
amarok:       BEGIN: ScanController::ScanController(CollectionDB*, bool, const QStringList&)
amarok:         BEGIN: void ScanController::initIncremental()
amarok:           [Scrobbler] Handshake result parsed: challenge=32EAFC790C2AF4E31CD073F70FA58B2C, submitUrl=http://62.216.251.205:80/protocol_1.1
amarok:           [Scrobbler] Nothing to schedule
amarok:         END__: void ScanController::initIncremental() - Took 0.21s
amarok:       END__: ScanController::ScanController(CollectionDB*, bool, const QStringList&) - Took 0.21s
amarok:       BEGIN: virtual void ThreadWeaver::Thread::run()
amarok:         BEGIN: virtual bool ScanController::doJob()
amarok:           BEGIN: SqliteConnection::SqliteConnection(const SqliteConfig*)
amarok:           END__: SqliteConnection::SqliteConnection(const SqliteConfig*) - Took 0.00068s
amarok:         END__: virtual bool ScanController::doJob() - Took 0.0012s
amarok:         [CollectionDB] JobFinishedEvent from Incremental ScanController received.
amarok:         [ThreadWeaver] Job completed: CollectionScanner. Jobs pending: 0
amarok:         BEGIN: virtual ScanController::~ScanController()
amarok:         END__: virtual ScanController::~ScanController() - Took 0.00042s
amarok:       END__: virtual void ThreadWeaver::Thread::run() - Took 0.007s
amarok:     END__: void CurrentTrackJob::showHome() - Took 0.55s
amarok:   END__: virtual bool CurrentTrackJob::doJob() - Took 0.55s
amarok:   [ThreadWeaver] Job completed: CurrentTrackJob. Jobs pending: 0
amarok: END__: virtual void ThreadWeaver::Thread::run() - Took 0.84s
amarok: BEGIN: Medium* DeviceManager::getDevice(QString)
amarok:   DeviceManager: getDevice called with name argument = dummyjusttorerundecop
amarok:   BEGIN: QStringList DeviceManager::getDeviceStringList(bool)
amarok:   END__: QStringList DeviceManager::getDeviceStringList(bool) - Took 0.0011s
amarok: END__: Medium* DeviceManager::getDevice(QString) - Took 0.0014s
                                             

This is what Amarok outputs when it loads.

When i try and play CD Amarok says:

Cannot read audio CD.

CD's play fine in kaffeine, and KSCD, but they don't have last.fm support so i'd like to fix this. Any suggestions?

---

### Post by GarethMB on 2006-07-25
Fixed. Changed the device to /dev/cdrom and it works now. :D

---

### Post by mahavishnu on 2006-08-06
how could you do that?

---

