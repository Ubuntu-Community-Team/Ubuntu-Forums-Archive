---
title: "Beagle Search seems to be running, but it's not working"
date: 2006-09-16
forum: General Help
---

### Post by diamond on 2006-09-16
A while ago I disabled inotify (by putting the "noinotify" argument after the kernel in menu.lst) and beagled (using the "disable" button in "Startup Programs" under "Sessions") because of memory leak issues.

I have since upgraded to the 2.6.17.11 kernel (I'm running Dapper, but upgraded the kernel manually) and decided to give Beagle a try again in case the memory issues might have been resolved. So I removed the "inotify" argument from the kernel call, and re-enabled beagled in Startup Programs. After rebooting, I check to see if beagle is running, and it seems to be:

```

$ ps -e | grep beagle
 5137 ?        00:00:01 beagled
 6376 ?        00:00:01 beagled-helper
$

```

However, if I use the deskbar to do a Beagle search for a file that I know is in my home directory, I get "No results were found".

Looking at my "Search & Indexing" settings, I see that "Start search & indexing services automatically" is enabled, and so is "Index my home directory" (I don't have any other directories added for indexing right now). Looking in ~/.beagle/Indexes, I see that the FileSystemIndex directory is about 122M in size and hasn't been updated since 8/02 (which I think is about the time I first turned Beagle off).

When I look in the .beagle/Log directory, there's a file called "2006-09-16-10-34-12-Beagle", last modified about two hours ago (the last time I booted up), and it has the following contents:

```

060916 1034129943 01493 Beagle DEBUG: Starting Beagle Daemon (version 0.2.6)
060916 1034130541 01493 Beagle DEBUG: Running on Mono 1.1.13.6
060916 1034130551 01493 Beagle DEBUG: Command Line: /usr/lib/beagle/BeagleDaemon.exe --bg
060916 1034130815 01493 Beagle  WARN: Extended attributes are not supported on this filesystem.  Performance will suffer as a result.
060916 1034131266 01493 Beagle DEBUG: Established a connection to the X server
060916 1034131298 01493 Beagle DEBUG: Starting main loop
060916 1034131423 01493 Beagle DEBUG: Starting messaging server
060916 1034133691 01493 Beagle DEBUG: Starting QueryDriver
060916 1034133934 01493 Beagle DEBUG: Loading Beagle.Util.Conf+IndexingConfig from indexing.xml
060916 1034140310 01493 Beagle DEBUG: Loading Beagle.Util.Conf+DaemonConfig from daemon.xml
060916 1034140683 01493 Beagle DEBUG: Loading Beagle.Util.Conf+SearchingConfig from searching.xml
060916 1034140954 01493 Beagle DEBUG: Loading Beagle.Util.Conf+NetworkingConfig from networking.xml
060916 1034140980 01493 Beagle DEBUG: Loading Beagle.Util.Conf+WebServicesConfig from webservices.xml
060916 1034141043 01493 Beagle DEBUG: '/usr/lib/beagle/Backends' is not a directory: Nothing loaded from here
060916 1034144335 01493 Beagle DEBUG: Found index helper at /usr/lib/beagle/beagled-index-helper
060916 1034144647 01493 Beagle DEBUG: KMail folders not found. Will keep trying 
060916 1034144781 01493 Beagle DEBUG: Starting Inotify Backend
060916 1034246077 01493 Beagle ERROR: Caught exception while instantiating Files backend
060916 1034246111 01493 Beagle ERROR EX: System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.IO.IOException: Lock obain timed out: /home/<user>/.beagle/Indexes/FileSystemIndex/Locks/lucene-7bdc53acf7a0347d0eaaa9a25e52240a-commit.lock -- pid  -- process exists
060916 1034246111 01493 Beagle ERROR EX: in [0x0010e] (at /build/buildd/beagle-0.2.6/beagled/Lucene.Net/Store/Lock.cs:91) Lucene.Net.Store.Lock:Obtain (Int64 lockWaitTimeout)
060916 1034246111 01493 Beagle ERROR EX: in [0x0000e] (at /build/buildd/beagle-0.2.6/beagled/Lucene.Net/Store/Lock.cs:144) Lucene.Net.Store.Lock+With:Run ()
060916 1034246111 01493 Beagle ERROR EX: in [0x0001f] (at /build/buildd/beagle-0.2.6/beagled/Lucene.Net/Index/IndexReader.cs:205) Lucene.Net.Index.IndexReader:Open (Lucene.Net.Store.Directory directory, Boolean closeDirectory)
060916 1034246111 01493 Beagle ERROR EX: in [0x00002] (at /build/buildd/beagle-0.2.6/beagled/Lucene.Net/Index/IndexReader.cs:197) Lucene.Net.Index.IndexReader:Open (Lucene.Net.Store.Directory directory)
060916 1034246111 01493 Beagle ERROR EX: in [0x0002c] (at /build/buildd/beagle-0.2.6/beagled/LuceneCommon.cs:1452) Beagle.Daemon.LuceneCommon:GetReader (Lucene.Net.Store.Directory directory)
060916 1034246111 01493 Beagle ERROR EX: in [0x00001] (at /build/buildd/beagle-0.2.6/beagled/LuceneCommon.cs:1437) Beagle.Daemon.LuceneCommon:GetSearcher (Lucene.Net.Store.Directory directory)
060916 1034246111 01493 Beagle ERROR EX: in [0x00023] (at /build/buildd/beagle-0.2.6/beagled/FileSystemQueryable/LuceneNameResolver.cs:234) Beagle.Daemon.FileSystemQueryable.LuceneNameResolver:GetAllDirectoryNameInfo ()
060916 1034246111 01493 Beagle ERROR EX: in [0x00006] (at /build/buildd/beagle-0.2.6/beagled/FileSystemQueryable/FileSystemQueryable.cs:296) Beagle.Daemon.FileSystemQueryable.FileSystemQueryable:PreloadDirectoryNameInfo ()
060916 1034246111 01493 Beagle ERROR EX: in [0x000f5] (at /build/buildd/beagle-0.2.6/beagled/FileSystemQueryable/FileSystemQueryable.cs:111) Beagle.Daemon.FileSystemQueryable.FileSystemQueryable:.ctor ()
060916 1034246111 01493 Beagle ERROR EX: in <0x00000> <unknown method>
060916 1034246111 01493 Beagle ERROR EX: in (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[])
060916 1034246111 01493 Beagle ERROR EX: in <0x0008d> System.Reflection.MonoCMethod:Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)--- End of inner exception stack trace ---
060916 1034246111 01493 Beagle ERROR EX: 
060916 1034246111 01493 Beagle ERROR EX: in <0x0010e> System.Reflection.MonoCMethod:Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
060916 1034246111 01493 Beagle ERROR EX: in <0x0001c> System.Reflection.MonoCMethod:Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
060916 1034246111 01493 Beagle ERROR EX: in <0x00035> System.Reflection.ConstructorInfo:Invoke (System.Object[] parameters)
060916 1034246111 01493 Beagle ERROR EX: in <0x00105> System.Activator:CreateInstance (System.Type type, Boolean nonPublic)
060916 1034246111 01493 Beagle ERROR EX: in <0x0000c> System.Activator:CreateInstance (System.Type type)
060916 1034246111 01493 Beagle ERROR EX: in [0x000e3] (at /build/buildd/beagle-0.2.6/beagled/QueryDriver.cs:176) Beagle.Daemon.QueryDriver:ScanAssembly (System.Reflection.Assembly assembly)
060916 1034249007 01493 Beagle DEBUG: Found 9 backends in /usr/lib/beagle/BeagleDaemonLib.dll
060916 1034249027 01493 Beagle DEBUG: Reading mapping from filters
060916 1034250395 01493 Beagle DEBUG: Loading system static indexes.
060916 1034250655 01493 Beagle DEBUG: Initializing static queryable: /var/cache/beagle/indexes/applications
060916 1034250680 01493 Beagle DEBUG: Initializing static queryable: /var/cache/beagle/indexes/documentation
060916 1034250682 01493 Beagle DEBUG: Found 2 system-wide indexes.
060916 1034250705 01493 Beagle DEBUG: Loading user-configured static indexes.
060916 1034250707 01493 Beagle DEBUG: Found 0 user-configured static indexes..
060916 1034250708 01493 Beagle DEBUG: Waiting 60 seconds before starting queryables
060916 1034250714 01493 Beagle DEBUG: Starting Scheduler thread
060916 1034250731 01493 Beagle DEBUG: Starting Inotify threads
060916 1034251001 01493 Beagle DEBUG: Daemon initialization finished after 11.97s
060916 1035250725 01493 Beagle DEBUG: Starting queryables
060916 1035250729 01493 Beagle DEBUG: Starting backend: 'KMail'
060916 1035250739 01493 Beagle DEBUG: Starting backend: 'GaimLog'
060916 1035250764 01493 Beagle DEBUG: Starting KMail backend
060916 1035250776 01493 Beagle DEBUG: KMail directories (local mail) /home/<user>/.kde/share/apps/kmail/dimap not found, will repoll.
060916 1035250781 01493 Beagle DEBUG: Starting backend: 'IndexingService'
060916 1035250806 01493 Beagle DEBUG: Scanning for files in the IndexingService directory...
060916 1035251014 01493 Beagle DEBUG: Indexed 0 Indexing Service items in .02s
060916 1035251018 01493 Beagle DEBUG: Starting backend: 'Tomboy'
060916 1035251025 01493 Beagle DEBUG: Starting backend: 'Blam'
060916 1035251062 01493 Beagle DEBUG: Starting backend: 'Liferea'
060916 1035251085 01493 Beagle DEBUG: Starting backend: 'Akregator'
060916 1035251093 01493 Beagle DEBUG: Starting backend: 'KonquerorHistory'
060916 1035251130 01493 Beagle DEBUG: Starting backend: 'Kopete'
060916 1035251146 01493 Beagle DEBUG: Starting backend: 'applications'
060916 1035251147 01493 Beagle DEBUG: Starting backend: 'documentation'
060916 1044145814 01493 Beagle DEBUG: Caught ResponseMessageException: Connection refused
060916 1044145820 01493 Beagle DEBUG: InnerException is SocketException -- we probably need to launch a helper
060916 1044145839 01493 Beagle DEBUG: Launching helper process
060916 1044145921 01493 Beagle DEBUG: IndexHelper PID is 2418
060916 1044155947 01493 Beagle DEBUG: Found IndexHelper (2418) in 1.00s
060916 1231482697 01493 Beagle DEBUG: Parsed query 'test' as text_query
060916 1232280737 01493 Beagle DEBUG: Loading Beagle.Util.Conf+IndexingConfig from indexing.xml
060916 1232280777 01493 Beagle DEBUG: Loading Beagle.Util.Conf+DaemonConfig from daemon.xml
060916 1232280808 01493 Beagle DEBUG: Loading Beagle.Util.Conf+SearchingConfig from searching.xml
060916 1232280847 01493 Beagle DEBUG: Loading Beagle.Util.Conf+NetworkingConfig from networking.xml
060916 1232280863 01493 Beagle DEBUG: Loading Beagle.Util.Conf+WebServicesConfig from webservices.xml
060916 1232326304 01493 Beagle DEBUG: Parsed query 'Test' as text_query
060916 1232391915 01493 Beagle DEBUG: Parsed query '*Test*' as text_query
060916 1234240613 01493 Beagle DEBUG: Lost our connection to the X server!  Trying to shut down gracefully
060916 1234240658 01493 Beagle DEBUG: CancelIfBlocking Beagle.Daemon.ConnectionHandler
060916 1234240693 01493 Beagle DEBUG: Bailing out of HandleConnection -- shutdown requested
060916 1234481092 01493 Beagle DEBUG: Handling signal 15 (SIGTERM)
060916 1234481095 01493 Beagle DEBUG: Shutdown already in progress.

```

Any ideas what might be wrong here?

---

### Post by diamond on 2006-09-16
Heh. Never mind. Sometimes talking about a problem is all you need to do to resolve it.

Apparently I had a lock file in /.beagle/Indexes/FileSystemIndex/Locks/ (it says so right there in the log file I posted). I deleted that and rebooted, and now it seems to be working quite well.

---

