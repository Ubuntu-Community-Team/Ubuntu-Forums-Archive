---
title: "Beagle not starting, disk full?"
date: 2007-04-24
forum: General Help
---

### Post by ChillMonkey on 2007-04-24
For some reason beagled won't start on my system, this is a pretty new development. I'm not sure why,  It seems to be a disk space issue(just a guess), but i know i have enough space. curiously Disk Usage Analyzer reports 100% usage, but df shows accurate stats. any help is appreciated.

My System:
ubuntu 7.04(Feisty)
Linux home 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux

disk usage:
monkey@home:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2              28G  435M   28G   2% /
varrun                506M  128K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb            506M  120K  506M   1% /proc/bus/usb
udev                  506M  120K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   33M  473M   7% /lib/modules/2.6.20-15-generic/volatile
/dev/hda1             1.9G   52M  1.7G   3% /boot
/dev/sda1             112G   64G   49G  57% /home
/dev/hda3              45G  1.8G   43G   4% /usr

trying to start beagled gives me this:

monkey@home:~$ beagled --fg --debug
Always: Starting Beagle Daemon (version 0.2.16.3)
Always: Running on Mono 1.2.3.1
Always: Using sqlite version 3
Always: Command Line: /usr/lib/beagle/BeagleDaemon.exe --fg --debug
Debug: Established a connection to the X server
Debug: Loading Beagle.Util.Conf+IndexingConfig from indexing.xml
Debug: Loading Beagle.Util.Conf+DaemonConfig from daemon.xml
Debug: Loading Beagle.Util.Conf+SearchingConfig from searching.xml
Debug: Starting main loop
Debug: Beginning main loop
Debug: Starting messaging server
Debug: Starting QueryDriver
Always: BEAGLE_EXERCISE_THE_DOG is set.
Debug: Found index helper at /usr/lib/beagle/beagled-index-helper
Debug: Found 2 backends in /usr/lib/beagle/Backends/EvolutionBackends.dll
Debug: Starting Inotify FSQ file event backend
Debug: Found 8 backends in /usr/lib/beagle/BeagleDaemonLib.dll
Debug: Reading mapping from filters
Debug: Loading system static indexes.
Debug: Initializing static queryable: /var/cache/beagle/indexes/applications
Debug: Initializing static queryable: /var/cache/beagle/indexes/documentation
Debug: Found 2 system-wide indexes.
Debug: Loading user-configured static indexes.
Debug: Found 0 user-configured static indexes..
Debug: Starting queryables
Debug: Starting backend: 'EvolutionMail'
Debug: Starting backend: 'EvolutionDataServer'
Debug: Starting backend: 'Files'
Debug: Adding root: /home/monkey
Debug: Starting Evolution mail backend
Debug: Starting mail crawl
Debug: Will index mbox /home/monkey/.evolution/mail/local/Inbox
Debug: Mail crawl finished
Debug: Evolution mail driver worker thread done in .02s
Debug: Loaded 75848 records from /home/monkey/.beagle/Indexes/FileSystemIndex/FileAttributesStore.db in 0.765s
Error: Maximum inotify watch limit hit adding watch to /home/monkey.  Try adjusting /proc/sys/fs/inotify/max_user_watches
Debug: Adding root: /usr
Debug: Adding root: /opt
Debug: Adding root: /home
Debug: Done starting FileSystemQueryable
Debug: Starting backend: 'GaimLog'
Debug: Starting backend: 'IndexingService'
Debug: Starting backend: 'Tomboy'
Warn: Exception caught while executing Beagle.Daemon.IndexingServiceQueryable.IndexingServiceQueryable:Void StartWorker()
System.IO.IOException: Attempt to watch /home/monkey/.beagle/ToIndex failed: No space left on device
  at Beagle.Util.Inotify.CreateOrModifyWatch (Beagle.Util.WatchInfo watched) [0x00000] 
  at Beagle.Util.Inotify.Subscribe (System.String path, Beagle.Util.InotifyCallback callback, EventType mask, EventType initial_filter) [0x00000] 
  at Beagle.Util.Inotify.Subscribe (System.String path, Beagle.Util.InotifyCallback callback, EventType mask) [0x00000] 
  at Beagle.Daemon.IndexingServiceQueryable.IndexingServiceQueryable.StartWorker () [0x00000] 
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void ()
  at Beagle.Util.ExceptionHandlingThread.ThreadStarted () [0x00000] 
Warn: Exception caught while executing Beagle.Daemon.TomboyQueryable.TomboyQueryable:Void StartWorker()
System.IO.IOException: Attempt to watch /home/monkey/.tomboy failed: No space left on device
  at Beagle.Util.Inotify.CreateOrModifyWatch (Beagle.Util.WatchInfo watched) [0x00000] 
  at Beagle.Util.Inotify.Subscribe (System.String path, Beagle.Util.InotifyCallback callback, EventType mask, EventType initial_filter) [0x00000] 
  at Beagle.Util.Inotify.Subscribe (System.String path, Beagle.Util.InotifyCallback callback, EventType mask) [0x00000] 
  at Beagle.Daemon.TomboyQueryable.TomboyQueryable.StartWorker () [0x00000] 
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void ()
  at Beagle.Util.ExceptionHandlingThread.ThreadStarted () [0x00000] 
Debug: Starting backend: 'Labyrinth'
Debug: Starting backend: 'Blam'
Debug: Starting backend: 'Liferea'
Debug: Starting backend: 'Akregator'
Debug: Starting backend: 'applications'
Debug: Starting backend: 'documentation'
Debug: Starting Scheduler thread
Debug: Starting Inotify threads
Debug: Opening mbox Inbox
Debug: Inbox: Finished indexing 1 messages
Error: Unhandled exception thrown.  Exiting immediately.
System.IO.IOException: Attempt to watch /home/monkey/.beagle/config failed: No space left on device
at Beagle.Util.Inotify.CreateOrModifyWatch (Beagle.Util.Inotify/WatchInfo) <0x00246>
at Beagle.Util.Inotify.Subscribe (string,Beagle.Util.Inotify/InotifyCallback,Beagle.Util.Inotify/EventType,Beagle.Util.Inotify/EventType) <0x00298>
at Beagle.Util.Inotify.Subscribe (string,Beagle.Util.Inotify/InotifyCallback,Beagle.Util.Inotify/EventType) <0x00012>
at Beagle.Util.Conf.WatchForUpdates () <0x0007f>
at Beagle.Daemon.BeagleDaemon.StartupProcess () <0x00297>
at (wrapper delegate-invoke) System.MulticastDelegate.invoke_bool () <0x00045>
at IdleProxy.Handler () <0x0002a>
at (wrapper native-to-managed) IdleProxy.Handler () <0x00036>
in (unmanaged) 0xb7f49090
at (wrapper managed-to-native) GLib.MainLoop.g_main_loop_run (intptr) <0x00004>
at GLib.MainLoop.Run () <0x0000d>
at Beagle.Daemon.BeagleDaemon.DoMain (string[]) <0x00b46>
at Beagle.Daemon.BeagleDaemon.Main (string[]) <0x00014>

Debug: Server '/home/monkey/.beagle/socket' shut down
Warn: Exception caught while executing Beagle.Daemon.Server:Void Run()
System.NullReferenceException: Object reference not set to an instance of an object
  at System.IO.StreamWriter.LowLevelWrite (System.String s) [0x00000] 
  at System.IO.StreamWriter.Write (System.String value) [0x00000] 
  at System.IO.TextWriter.WriteLine (System.String value) [0x00000] 
  at Beagle.Util.Log.WriteLine (LogLevel level, System.String format, System.Object[] args, System.Exception ex) [0x00000] 
  at Beagle.Util.Log.Debug (System.String message, System.Object[] args) [0x00000] 
  at Beagle.Util.Logger.Debug (System.String message, System.Object[] args) [0x00000] 
  at Beagle.Daemon.Server.Run () [0x00000] 
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void ()
  at Beagle.Util.ExceptionHandlingThread.ThreadStarted () [0x00000] 

Unhandled Exception: System.NullReferenceException: Object reference not set to an instance of an object
  at System.IO.StreamWriter.LowLevelWrite (System.String s) [0x00000] 
  at System.IO.StreamWriter.Write (System.String value) [0x00000] 
  at System.IO.TextWriter.WriteLine (System.String value) [0x00000] 
  at Beagle.Util.Log.WriteLine (LogLevel level, System.String format, System.Object[] args, System.Exception ex) [0x00000] 
  at Beagle.Util.Log.Warn (System.Exception ex, System.String message, System.Object[] args) [0x00000] 
  at Beagle.Util.Logger.Warn (System.Exception ex, System.String message, System.Object[] args) [0x00000] 
  at Beagle.Util.ExceptionHandlingThread.ThreadStarted () [0x00000] 
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void ()

** (/usr/lib/beagle/BeagleDaemon.exe:1900): WARNING **: _wapi_handle_unref: Attempting to unref unused handle 0x20

---

