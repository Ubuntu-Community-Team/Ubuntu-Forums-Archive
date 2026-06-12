---
title: "Beagle indexing takes sooo long"
date: 2005-03-21
forum: General Help
---

### Post by Shambler on 2005-03-21
I ran Beagle with "beagled --fg --debug" and after about 2 hours i saw this:

DEBUG: Helper Size: VmRSS=15,3 MB, size=1,12, 3,0%
DEBUG: Helper Size: VmRSS=15,3 MB, size=1,12, 3,0%
DEBUG: Helper Size: VmRSS=15,3 MB, size=1,12, 3,0%
DEBUG: Helper Size: VmRSS=15,3 MB, size=1,12, 3,0%
DEBUG: Helper Size: VmRSS=15,3 MB, size=1,12, 3,0%
DEBUG: Helper Size: VmRSS=15,3 MB, size=1,12, 3,0%
DEBUG: Helper Size: VmRSS=15,3 MB, size=1,12, 3,0%
DEBUG: Helper Size: VmRSS=15,3 MB, size=1,12, 3,0%
DEBUG: Helper Size: VmRSS=15,3 MB, size=1,12, 3,0%
DEBUG: Helper Size: VmRSS=15,3 MB, size=1,12, 3,0%
DEBUG: Helper Size: VmRSS=15,3 MB, size=1,12, 3,0%
DEBUG: Helper Size: VmRSS=15,3 MB, size=1,12, 3,1%
DEBUG: Helper Size: VmRSS=15,3 MB, size=1,12, 3,1%

Well, you know, i got two 120 gb files full + my normal root partition, but is that normal? Calculating that would take Beagle a few days to index everything. And BEST ist still, who wonders, not returning any search results...

---

### Post by Shambler on 2005-03-21
Btw, is it really indexing, when it says this in debug mode?

---

### Post by Shambler on 2005-03-22
Btw, I got some exceptions, but can't understand, what they're all about:
```

shambler@shambler:~/.beagle/Log $ beagled --fg --debug
INFO: Starting Beagle Daemon (version 0.0.7)
DEBUG: Command Line: /usr/local/lib/beagle/BeagleDaemon.exe --debug --fg
DEBUG: Initializing D-BUS
DEBUG: Acquiring com.novell.Beagle D-BUS service
DEBUG: Found index helper at /usr/local/lib/beagle/beagled-index-helper
DEBUG: Launching helper process!
DEBUG: D-BUS registered obj=Beagle.IndexHelper.RemoteIndexerImpl path=/com/novell/BeagleIndexHelper/Factory owner=(none)
DEBUG: Helper Size: VmRSS=13,8 MB, size=1,00, 0,0%
DEBUG: Connecting to com.novell.BeagleIndexHelper
DEBUG: Initializing RemoteControl
DEBUG: D-BUS registered obj=Beagle.Daemon.RemoteControlImpl path=/com/novell/Beagle/RemoteControl owner=(none)
DEBUG: D-BUS registered obj=Beagle.Daemon.FactoryImpl path=/com/novell/Beagle/Factory owner=(none)
DEBUG: Starting QueryDriver
DEBUG: Purging /home/shambler/.beagle/FileSystemIndex
DEBUG: Helper Size: VmRSS=14,1 MB, size=1,03, 0,6%
ERROR: Caught exception while instantiating Files backend
ERROR: System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.IO.IOException: Lock obtain timed out: Lock@/home/shambler/.beagle/FileSystemIndex/Locks/lucene-ba8ae9673922b63b56937de1e929c440-write.lock
in [0x0003b] (at /home/shambler/cvs/beagle/beagled/Lucene.Net/Store/Lock.cs:75) Lucene.Net.Store.Lock:Obtain (long)
in [0x00089] (at /home/shambler/cvs/beagle/beagled/Lucene.Net/Index/IndexWriter.cs:299) Lucene.Net.Index.IndexWriter:.ctor (Lucene.Net.Store.Directory,Lucene.Net.Analysis.Analyzer,bool,bool)
in [0x00005] (at /home/shambler/cvs/beagle/beagled/Lucene.Net/Index/IndexWriter.cs:286) Lucene.Net.Index.IndexWriter:.ctor (Lucene.Net.Store.Directory,Lucene.Net.Analysis.Analyzer,bool)
in [0x00249] (at /home/shambler/cvs/beagle/beagled/LuceneDriver.cs:209) Beagle.Daemon.LuceneDriver:Setup (string)
in [0x0004b] (at /home/shambler/cvs/beagle/beagled/LuceneDriver.cs:90) Beagle.Daemon.LuceneDriver:.ctor (string)
in [0x00038] (at /home/shambler/cvs/beagle/beagled/LuceneQueryable.cs:95) Beagle.Daemon.LuceneQueryable:.ctor (string)
in [0x00006] (at /home/shambler/cvs/beagle/beagled/FileSystemQueryable/FileSystemQueryable.cs:53) Beagle.Daemon.FileSystemQueryable.FileSystemQueryable:.ctor ()in (unmanaged) (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[])
in <0x00004> (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[])
in [0x00033] (at /build/buildd/mcs-1.0.5/class/corlib/System.Reflection/MonoMethod.cs:280) System.Reflection.MonoCMethod:Invoke (object,System.Reflection.BindingFlags,System.Reflection.Binder,object[],System.Globalization.CultureInfo)
--- End of inner exception stack trace ---

in [0x00052] (at /build/buildd/mcs-1.0.5/class/corlib/System.Reflection/MonoMethod.cs:284) System.Reflection.MonoCMethod:Invoke (object,System.Reflection.BindingFlags,System.Reflection.Binder,object[],System.Globalization.CultureInfo)
in [0x00007] (at /build/buildd/mcs-1.0.5/class/corlib/System.Reflection/MonoMethod.cs:289) System.Reflection.MonoCMethod:Invoke (System.Reflection.BindingFlags,System.Reflection.Binder,object[],System.Globalization.CultureInfo)
in [0x00017] (at /build/buildd/mcs-1.0.5/class/corlib/System.Reflection/ConstructorInfo.cs:62) System.Reflection.ConstructorInfo:Invoke (object[])
in [0x00074] (at /build/buildd/mcs-1.0.5/class/corlib/System/Activator.cs:262) System.Activator:CreateInstance (System.Type,bool)
in [0x00002] (at /build/buildd/mcs-1.0.5/class/corlib/System/Activator.cs:151) System.Activator:CreateInstance (System.Type)
in [0x000a6] (at /home/shambler/cvs/beagle/beagled/QueryDriver.cs:123) Beagle.Daemon.QueryDriver:ScanAssembly (System.Reflection.Assembly)

DEBUG: Purging /home/shambler/.beagle/GaimLogIndex
DEBUG: Helper Size: VmRSS=14,1 MB, size=1,03, 0,7%
ERROR: Caught exception while instantiating IMLog backend
ERROR: System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.IO.IOException: Lock obtain timed out: Lock@/home/shambler/.beagle/GaimLogIndex/Locks/lucene-004bc5915e3885273be02f47bb1809e3-write.lock
in [0x0003b] (at /home/shambler/cvs/beagle/beagled/Lucene.Net/Store/Lock.cs:75) Lucene.Net.Store.Lock:Obtain (long)
in [0x00089] (at /home/shambler/cvs/beagle/beagled/Lucene.Net/Index/IndexWriter.cs:299) Lucene.Net.Index.IndexWriter:.ctor (Lucene.Net.Store.Directory,Lucene.Net.Analysis.Analyzer,bool,bool)
in [0x00005] (at /home/shambler/cvs/beagle/beagled/Lucene.Net/Index/IndexWriter.cs:286) Lucene.Net.Index.IndexWriter:.ctor (Lucene.Net.Store.Directory,Lucene.Net.Analysis.Analyzer,bool)
in [0x00249] (at /home/shambler/cvs/beagle/beagled/LuceneDriver.cs:209) Beagle.Daemon.LuceneDriver:Setup (string)
in [0x0004b] (at /home/shambler/cvs/beagle/beagled/LuceneDriver.cs:90) Beagle.Daemon.LuceneDriver:.ctor (string)
in [0x00038] (at /home/shambler/cvs/beagle/beagled/LuceneQueryable.cs:95) Beagle.Daemon.LuceneQueryable:.ctor (string)
in [0x00019] (at /home/shambler/cvs/beagle/beagled/GaimLogQueryable/GaimLogQueryable.cs:53) Beagle.Daemon.GaimLogQueryable.GaimLogQueryable:.ctor ()
in (unmanaged) (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[])
in <0x00004> (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[])
in [0x00033] (at /build/buildd/mcs-1.0.5/class/corlib/System.Reflection/MonoMethod.cs:280) System.Reflection.MonoCMethod:Invoke (object,System.Reflection.BindingFlags,System.Reflection.Binder,object[],System.Globalization.CultureInfo)
--- End of inner exception stack trace ---

in [0x00052] (at /build/buildd/mcs-1.0.5/class/corlib/System.Reflection/MonoMethod.cs:284) System.Reflection.MonoCMethod:Invoke (object,System.Reflection.BindingFlags,System.Reflection.Binder,object[],System.Globalization.CultureInfo)
in [0x00007] (at /build/buildd/mcs-1.0.5/class/corlib/System.Reflection/MonoMethod.cs:289) System.Reflection.MonoCMethod:Invoke (System.Reflection.BindingFlags,System.Reflection.Binder,object[],System.Globalization.CultureInfo)
in [0x00017] (at /build/buildd/mcs-1.0.5/class/corlib/System.Reflection/ConstructorInfo.cs:62) System.Reflection.ConstructorInfo:Invoke (object[])
in [0x00074] (at /build/buildd/mcs-1.0.5/class/corlib/System/Activator.cs:262) System.Activator:CreateInstance (System.Type,bool)
in [0x00002] (at /build/buildd/mcs-1.0.5/class/corlib/System/Activator.cs:151) System.Activator:CreateInstance (System.Type)
in [0x000a6] (at /home/shambler/cvs/beagle/beagled/QueryDriver.cs:123) Beagle.Daemon.QueryDriver:ScanAssembly (System.Reflection.Assembly)

DEBUG: Purging /home/shambler/.beagle/BlamIndex
ERROR: Caught exception while instantiating Blam backend
ERROR: System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.IO.IOException: Lock obtain timed out: Lock@/home/shambler/.beagle/BlamIndex/Locks/lucene-8ab49f5176f89ea7c564c8f2f522f48b-write.lock
in [0x0003b] (at /home/shambler/cvs/beagle/beagled/Lucene.Net/Store/Lock.cs:75) Lucene.Net.Store.Lock:Obtain (long)
in [0x00089] (at /home/shambler/cvs/beagle/beagled/Lucene.Net/Index/IndexWriter.cs:299) Lucene.Net.Index.IndexWriter:.ctor (Lucene.Net.Store.Directory,Lucene.Net.Analysis.Analyzer,bool,bool)
in [0x00005] (at /home/shambler/cvs/beagle/beagled/Lucene.Net/Index/IndexWriter.cs:286) Lucene.Net.Index.IndexWriter:.ctor (Lucene.Net.Store.Directory,Lucene.Net.Analysis.Analyzer,bool)
in [0x00249] (at /home/shambler/cvs/beagle/beagled/LuceneDriver.cs:209) Beagle.Daemon.LuceneDriver:Setup (string)
in [0x0004b] (at /home/shambler/cvs/beagle/beagled/LuceneDriver.cs:90) Beagle.Daemon.LuceneDriver:.ctor (string)
in [0x00038] (at /home/shambler/cvs/beagle/beagled/LuceneQueryable.cs:95) Beagle.Daemon.LuceneQueryable:.ctor (string)
in [0x0000d] (at /home/shambler/cvs/beagle/beagled/BlamQueryable/BlamQueryable.cs:51) Beagle.Daemon.BlamQueryable.BlamQueryable:.ctor ()
in (unmanaged) (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[])
in <0x00004> (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[])
in [0x00033] (at /build/buildd/mcs-1.0.5/class/corlib/System.Reflection/MonoMethod.cs:280) System.Reflection.MonoCMethod:Invoke (object,System.Reflection.BindingFlags,System.Reflection.Binder,object[],System.Globalization.CultureInfo)
--- End of inner exception stack trace ---

in [0x00052] (at /build/buildd/mcs-1.0.5/class/corlib/System.Reflection/MonoMethod.cs:284) System.Reflection.MonoCMethod:Invoke (object,System.Reflection.BindingFlags,System.Reflection.Binder,object[],System.Globalization.CultureInfo)
in [0x00007] (at /build/buildd/mcs-1.0.5/class/corlib/System.Reflection/MonoMethod.cs:289) System.Reflection.MonoCMethod:Invoke (System.Reflection.BindingFlags,System.Reflection.Binder,object[],System.Globalization.CultureInfo)
in [0x00017] (at /build/buildd/mcs-1.0.5/class/corlib/System.Reflection/ConstructorInfo.cs:62) System.Reflection.ConstructorInfo:Invoke (object[])
in [0x00074] (at /build/buildd/mcs-1.0.5/class/corlib/System/Activator.cs:262) System.Activator:CreateInstance (System.Type,bool)
in [0x00002] (at /build/buildd/mcs-1.0.5/class/corlib/System/Activator.cs:151) System.Activator:CreateInstance (System.Type)
in [0x000a6] (at /home/shambler/cvs/beagle/beagled/QueryDriver.cs:123) Beagle.Daemon.QueryDriver:ScanAssembly (System.Reflection.Assembly)

DEBUG: Purging /home/shambler/.beagle/LifereaIndex
ERROR: Caught exception while instantiating Liferea backend
ERROR: System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.IO.IOException: Lock obtain timed out: Lock@/home/shambler/.beagle/LifereaIndex/Locks/lucene-95d06098c01629365defe86e544201f5-write.lock
in [0x0003b] (at /home/shambler/cvs/beagle/beagled/Lucene.Net/Store/Lock.cs:75) Lucene.Net.Store.Lock:Obtain (long)
in [0x00089] (at /home/shambler/cvs/beagle/beagled/Lucene.Net/Index/IndexWriter.cs:299) Lucene.Net.Index.IndexWriter:.ctor (Lucene.Net.Store.Directory,Lucene.Net.Analysis.Analyzer,bool,bool)
in [0x00005] (at /home/shambler/cvs/beagle/beagled/Lucene.Net/Index/IndexWriter.cs:286) Lucene.Net.Index.IndexWriter:.ctor (Lucene.Net.Store.Directory,Lucene.Net.Analysis.Analyzer,bool)
in [0x00249] (at /home/shambler/cvs/beagle/beagled/LuceneDriver.cs:209) Beagle.Daemon.LuceneDriver:Setup (string)
in [0x0004b] (at /home/shambler/cvs/beagle/beagled/LuceneDriver.cs:90) Beagle.Daemon.LuceneDriver:.ctor (string)
in [0x00038] (at /home/shambler/cvs/beagle/beagled/LuceneQueryable.cs:95) Beagle.Daemon.LuceneQueryable:.ctor (string)
in [0x0000d] (at /home/shambler/cvs/beagle/beagled/LifereaQueryable/LifereaQueryable.cs:49) Beagle.Daemon.LifereaQueryable.LifereaQueryable:.ctor ()
in (unmanaged) (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[])
in <0x00004> (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[])
in [0x00033] (at /build/buildd/mcs-1.0.5/class/corlib/System.Reflection/MonoMethod.cs:280) System.Reflection.MonoCMethod:Invoke (object,System.Reflection.BindingFlags,System.Reflection.Binder,object[],System.Globalization.CultureInfo)
--- End of inner exception stack trace ---

in [0x00052] (at /build/buildd/mcs-1.0.5/class/corlib/System.Reflection/MonoMethod.cs:284) System.Reflection.MonoCMethod:Invoke (object,System.Reflection.BindingFlags,System.Reflection.Binder,object[],System.Globalization.CultureInfo)
in [0x00007] (at /build/buildd/mcs-1.0.5/class/corlib/System.Reflection/MonoMethod.cs:289) System.Reflection.MonoCMethod:Invoke (System.Reflection.BindingFlags,System.Reflection.Binder,object[],System.Globalization.CultureInfo)
in [0x00017] (at /build/buildd/mcs-1.0.5/class/corlib/System.Reflection/ConstructorInfo.cs:62) System.Reflection.ConstructorInfo:Invoke (object[])
in [0x00074] (at /build/buildd/mcs-1.0.5/class/corlib/System/Activator.cs:262) System.Activator:CreateInstance (System.Type,bool)
in [0x00002] (at /build/buildd/mcs-1.0.5/class/corlib/System/Activator.cs:151) System.Activator:CreateInstance (System.Type)
in [0x000a6] (at /home/shambler/cvs/beagle/beagled/QueryDriver.cs:123) Beagle.Daemon.QueryDriver:ScanAssembly (System.Reflection.Assembly)

DEBUG: Purging /home/shambler/.beagle/MailIndex
ERROR: Caught exception while instantiating Mail backend
ERROR: System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.IO.IOException: Lock obtain timed out: Lock@/home/shambler/.beagle/MailIndex/Locks/lucene-cb98f1440156a98e3dd769fcf4a1b547-write.lock
in [0x0003b] (at /home/shambler/cvs/beagle/beagled/Lucene.Net/Store/Lock.cs:75) Lucene.Net.Store.Lock:Obtain (long)
in [0x00089] (at /home/shambler/cvs/beagle/beagled/Lucene.Net/Index/IndexWriter.cs:299) Lucene.Net.Index.IndexWriter:.ctor (Lucene.Net.Store.Directory,Lucene.Net.Analysis.Analyzer,bool,bool)
in [0x00005] (at /home/shambler/cvs/beagle/beagled/Lucene.Net/Index/IndexWriter.cs:286) Lucene.Net.Index.IndexWriter:.ctor (Lucene.Net.Store.Directory,Lucene.Net.Analysis.Analyzer,bool)
in [0x00249] (at /home/shambler/cvs/beagle/beagled/LuceneDriver.cs:209) Beagle.Daemon.LuceneDriver:Setup (string)
in [0x0004b] (at /home/shambler/cvs/beagle/beagled/LuceneDriver.cs:90) Beagle.Daemon.LuceneDriver:.ctor (string)
in [0x00038] (at /home/shambler/cvs/beagle/beagled/LuceneQueryable.cs:95) Beagle.Daemon.LuceneQueryable:.ctor (string)
in [0x00036] (at /home/shambler/cvs/beagle/beagled/EvolutionMailDriver/EvolutionMailDriver.cs:56) Beagle.Daemon.EvolutionMailDriver.EvolutionMailQueryable:.ctor ()
in (unmanaged) (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[])
in <0x00004> (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[])
in [0x00033] (at /build/buildd/mcs-1.0.5/class/corlib/System.Reflection/MonoMethod.cs:280) System.Reflection.MonoCMethod:Invoke (object,System.Reflection.BindingFlags,System.Reflection.Binder,object[],System.Globalization.CultureInfo)
--- End of inner exception stack trace ---

in [0x00052] (at /build/buildd/mcs-1.0.5/class/corlib/System.Reflection/MonoMethod.cs:284) System.Reflection.MonoCMethod:Invoke (object,System.Reflection.BindingFlags,System.Reflection.Binder,object[],System.Globalization.CultureInfo)
in [0x00007] (at /build/buildd/mcs-1.0.5/class/corlib/System.Reflection/MonoMethod.cs:289) System.Reflection.MonoCMethod:Invoke (System.Reflection.BindingFlags,System.Reflection.Binder,object[],System.Globalization.CultureInfo)
in [0x00017] (at /build/buildd/mcs-1.0.5/class/corlib/System.Reflection/ConstructorInfo.cs:62) System.Reflection.ConstructorInfo:Invoke (object[])
in [0x00074] (at /build/buildd/mcs-1.0.5/class/corlib/System/Activator.cs:262) System.Activator:CreateInstance (System.Type,bool)
in [0x00002] (at /build/buildd/mcs-1.0.5/class/corlib/System/Activator.cs:151) System.Activator:CreateInstance (System.Type)
in [0x000a6] (at /home/shambler/cvs/beagle/beagled/QueryDriver.cs:123) Beagle.Daemon.QueryDriver:ScanAssembly (System.Reflection.Assembly)

DEBUG: Purging /home/shambler/.beagle/WebHistoryIndex
ERROR: Caught exception while instantiating WebHistory backend
ERROR: System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.IO.IOException: Lock obtain timed out: Lock@/home/shambler/.beagle/WebHistoryIndex/Locks/lucene-ef1a02e249c718eee9b24fc33d128ea5-write.lock
in [0x0003b] (at /home/shambler/cvs/beagle/beagled/Lucene.Net/Store/Lock.cs:75) Lucene.Net.Store.Lock:Obtain (long)
in [0x00089] (at /home/shambler/cvs/beagle/beagled/Lucene.Net/Index/IndexWriter.cs:299) Lucene.Net.Index.IndexWriter:.ctor (Lucene.Net.Store.Directory,Lucene.Net.Analysis.Analyzer,bool,bool)
in [0x00005] (at /home/shambler/cvs/beagle/beagled/Lucene.Net/Index/IndexWriter.cs:286) Lucene.Net.Index.IndexWriter:.ctor (Lucene.Net.Store.Directory,Lucene.Net.Analysis.Analyzer,bool)
in [0x00249] (at /home/shambler/cvs/beagle/beagled/LuceneDriver.cs:209) Beagle.Daemon.LuceneDriver:Setup (string)
in [0x0004b] (at /home/shambler/cvs/beagle/beagled/LuceneDriver.cs:90) Beagle.Daemon.LuceneDriver:.ctor (string)
in [0x00038] (at /home/shambler/cvs/beagle/beagled/LuceneQueryable.cs:95) Beagle.Daemon.LuceneQueryable:.ctor (string)
in [0x00006] (at /home/shambler/cvs/beagle/beagled/WebHistoryQueryable/WebHistoryQueryable.cs:58) Beagle.Daemon.WebHistoryQueryable.WebHistoryQueryable:.ctor ()in (unmanaged) (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[])
in <0x00004> (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[])
in [0x00033] (at /build/buildd/mcs-1.0.5/class/corlib/System.Reflection/MonoMethod.cs:280) System.Reflection.MonoCMethod:Invoke (object,System.Reflection.BindingFlags,System.Reflection.Binder,object[],System.Globalization.CultureInfo)
--- End of inner exception stack trace ---

in [0x00052] (at /build/buildd/mcs-1.0.5/class/corlib/System.Reflection/MonoMethod.cs:284) System.Reflection.MonoCMethod:Invoke (object,System.Reflection.BindingFlags,System.Reflection.Binder,object[],System.Globalization.CultureInfo)
in [0x00007] (at /build/buildd/mcs-1.0.5/class/corlib/System.Reflection/MonoMethod.cs:289) System.Reflection.MonoCMethod:Invoke (System.Reflection.BindingFlags,System.Reflection.Binder,object[],System.Globalization.CultureInfo)
in [0x00017] (at /build/buildd/mcs-1.0.5/class/corlib/System.Reflection/ConstructorInfo.cs:62) System.Reflection.ConstructorInfo:Invoke (object[])
in [0x00074] (at /build/buildd/mcs-1.0.5/class/corlib/System/Activator.cs:262) System.Activator:CreateInstance (System.Type,bool)
in [0x00002] (at /build/buildd/mcs-1.0.5/class/corlib/System/Activator.cs:151) System.Activator:CreateInstance (System.Type)
in [0x000a6] (at /home/shambler/cvs/beagle/beagled/QueryDriver.cs:123) Beagle.Daemon.QueryDriver:ScanAssembly (System.Reflection.Assembly)

DEBUG: Purging /home/shambler/.beagle/LauncherIndex
ERROR: Caught exception while instantiating Launcher backend
ERROR: System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.IO.IOException: Lock obtain timed out: Lock@/home/shambler/.beagle/LauncherIndex/Locks/lucene-fc6b0870475ab5efece94b2a2c017df9-write.lock
in [0x0003b] (at /home/shambler/cvs/beagle/beagled/Lucene.Net/Store/Lock.cs:75) Lucene.Net.Store.Lock:Obtain (long)
in [0x00089] (at /home/shambler/cvs/beagle/beagled/Lucene.Net/Index/IndexWriter.cs:299) Lucene.Net.Index.IndexWriter:.ctor (Lucene.Net.Store.Directory,Lucene.Net.Analysis.Analyzer,bool,bool)
in [0x00005] (at /home/shambler/cvs/beagle/beagled/Lucene.Net/Index/IndexWriter.cs:286) Lucene.Net.Index.IndexWriter:.ctor (Lucene.Net.Store.Directory,Lucene.Net.Analysis.Analyzer,bool)
in [0x00249] (at /home/shambler/cvs/beagle/beagled/LuceneDriver.cs:209) Beagle.Daemon.LuceneDriver:Setup (string)
in [0x0004b] (at /home/shambler/cvs/beagle/beagled/LuceneDriver.cs:90) Beagle.Daemon.LuceneDriver:.ctor (string)
in [0x00038] (at /home/shambler/cvs/beagle/beagled/LuceneQueryable.cs:95) Beagle.Daemon.LuceneQueryable:.ctor (string)
in [0x00018] (at /home/shambler/cvs/beagle/beagled/LauncherQueryable/LauncherQueryable.cs:52) Beagle.Daemon.LauncherQueryable.LauncherQueryable:.ctor ()
in (unmanaged) (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[])
in <0x00004> (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[])
in [0x00033] (at /build/buildd/mcs-1.0.5/class/corlib/System.Reflection/MonoMethod.cs:280) System.Reflection.MonoCMethod:Invoke (object,System.Reflection.BindingFlags,System.Reflection.Binder,object[],System.Globalization.CultureInfo)
--- End of inner exception stack trace ---

in [0x00052] (at /build/buildd/mcs-1.0.5/class/corlib/System.Reflection/MonoMethod.cs:284) System.Reflection.MonoCMethod:Invoke (object,System.Reflection.BindingFlags,System.Reflection.Binder,object[],System.Globalization.CultureInfo)
in [0x00007] (at /build/buildd/mcs-1.0.5/class/corlib/System.Reflection/MonoMethod.cs:289) System.Reflection.MonoCMethod:Invoke (System.Reflection.BindingFlags,System.Reflection.Binder,object[],System.Globalization.CultureInfo)
in [0x00017] (at /build/buildd/mcs-1.0.5/class/corlib/System.Reflection/ConstructorInfo.cs:62) System.Reflection.ConstructorInfo:Invoke (object[])
in [0x00074] (at /build/buildd/mcs-1.0.5/class/corlib/System/Activator.cs:262) System.Activator:CreateInstance (System.Type,bool)
in [0x00002] (at /build/buildd/mcs-1.0.5/class/corlib/System/Activator.cs:151) System.Activator:CreateInstance (System.Type)
in [0x000a6] (at /home/shambler/cvs/beagle/beagled/QueryDriver.cs:123) Beagle.Daemon.QueryDriver:ScanAssembly (System.Reflection.Assembly)

DEBUG: Purging /home/shambler/.beagle/TomboyIndex
ERROR: Caught exception while instantiating Tomboy backend
ERROR: System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.IO.IOException: Lock obtain timed out: Lock@/home/shambler/.beagle/TomboyIndex/Locks/lucene-af23e906bcd7aedf406b04ca37052d0e-write.lock
in [0x0003b] (at /home/shambler/cvs/beagle/beagled/Lucene.Net/Store/Lock.cs:75) Lucene.Net.Store.Lock:Obtain (long)
in [0x00089] (at /home/shambler/cvs/beagle/beagled/Lucene.Net/Index/IndexWriter.cs:299) Lucene.Net.Index.IndexWriter:.ctor (Lucene.Net.Store.Directory,Lucene.Net.Analysis.Analyzer,bool,bool)
in [0x00005] (at /home/shambler/cvs/beagle/beagled/Lucene.Net/Index/IndexWriter.cs:286) Lucene.Net.Index.IndexWriter:.ctor (Lucene.Net.Store.Directory,Lucene.Net.Analysis.Analyzer,bool)
in [0x00249] (at /home/shambler/cvs/beagle/beagled/LuceneDriver.cs:209) Beagle.Daemon.LuceneDriver:Setup (string)
in [0x0004b] (at /home/shambler/cvs/beagle/beagled/LuceneDriver.cs:90) Beagle.Daemon.LuceneDriver:.ctor (string)
in [0x00038] (at /home/shambler/cvs/beagle/beagled/LuceneQueryable.cs:95) Beagle.Daemon.LuceneQueryable:.ctor (string)
in [0x00014] (at /home/shambler/cvs/beagle/beagled/TomboyQueryable/TomboyQueryable.cs:48) Beagle.Daemon.TomboyQueryable.TomboyQueryable:.ctor ()
in (unmanaged) (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[])
in <0x00004> (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[])
in [0x00033] (at /build/buildd/mcs-1.0.5/class/corlib/System.Reflection/MonoMethod.cs:280) System.Reflection.MonoCMethod:Invoke (object,System.Reflection.BindingFlags,System.Reflection.Binder,object[],System.Globalization.CultureInfo)
--- End of inner exception stack trace ---

in [0x00052] (at /build/buildd/mcs-1.0.5/class/corlib/System.Reflection/MonoMethod.cs:284) System.Reflection.MonoCMethod:Invoke (object,System.Reflection.BindingFlags,System.Reflection.Binder,object[],System.Globalization.CultureInfo)
in [0x00007] (at /build/buildd/mcs-1.0.5/class/corlib/System.Reflection/MonoMethod.cs:289) System.Reflection.MonoCMethod:Invoke (System.Reflection.BindingFlags,System.Reflection.Binder,object[],System.Globalization.CultureInfo)
in [0x00017] (at /build/buildd/mcs-1.0.5/class/corlib/System.Reflection/ConstructorInfo.cs:62) System.Reflection.ConstructorInfo:Invoke (object[])
in [0x00074] (at /build/buildd/mcs-1.0.5/class/corlib/System/Activator.cs:262) System.Activator:CreateInstance (System.Type,bool)
in [0x00002] (at /build/buildd/mcs-1.0.5/class/corlib/System/Activator.cs:151) System.Activator:CreateInstance (System.Type)
in [0x000a6] (at /home/shambler/cvs/beagle/beagled/QueryDriver.cs:123) Beagle.Daemon.QueryDriver:ScanAssembly (System.Reflection.Assembly)

DEBUG: Found 2 types in BeagleDaemonLib, Version=1.4.3.3, Culture=neutral, PublicKeyToken=null
DEBUG: Starting Scheduler thread
DEBUG: Starting Inotify threads
DEBUG: Ready to accept requests after 8,52s
DEBUG: Starting main loop
DEBUG: OnNameOwnerChanged: com.novell.BeagleIndexHelper '' ':1.6'
DEBUG: Helper Size: VmRSS=14,1 MB, size=1,03, 0,7%
DEBUG: Helper Size: VmRSS=14,2 MB, size=1,03, 0,7%

```

---

### Post by valfader on 2005-03-22
hummm I would guess that it is not indexing it, atleast not everything, a  IOException can never be good ;(
Its it eating all you memory aswell? It did for me last time I tryed it.
You can allways test to put some .noindex files in all the folder trees that you dont want to be indexed. That may speed it things.

---

### Post by Bo Rosén on 2005-03-22
It seems 0.0.7 is just indexing my mail, anyone else have better luck?

**edit:**
I enabled inotify in the kernel. I added .noindex files to a couple of directories which seemed to make the fileindexer give up (containing files with invalid encoding) and moved .gaim/logs to .gaim/logs-old and added a .noindex there as well.

I can now search files and mail, I don't get the error I got earlier for the gaim backend (but haven't chatted with anyone yet so don't know if it works - but xchat doesn't seem to work).
I don't get any media files indexed, but I'm not sure if that is enabled in 0.0.7 or not and the addressbook backend is disabled.

So, fairly succesful on the whole.

---

### Post by Shambler on 2005-03-23
In this thread there's the same problem described with the cvs version: [http://www.ubuntuforums.org/showthread.php?t=21424](http://www.ubuntuforums.org/showthread.php?t=21424)

I managed to get 0.0.7 running, BUT:
The files of my /dev/hda get indexed very well, but not those of my data hard drives /dev/sda and /dev/sdb. But I have added the "user_xattr" attribute for both in /etc/fstab  :confused:

---

### Post by Bo Rosén on 2005-03-23
> **Shambler]In this thread there's the same problem described with the cvs version: [http://www.ubuntuforums.org/showthread.php?t=21424](http://www.ubuntuforums.org/showthread.php?t=21424)
[/quote]
Which I started  said:**
> 
The files of my /dev/hda get indexed very well, but not those of my data hard drives /dev/sda and /dev/sdb. But I have added the "user_xattr" attribute for both in /etc/fstab  :confused:

Yes, I have my music on a separate drive, soft linked from my home directory but it doesn't get indexed either. It has the correct permissions (as far as I can tell), and I added  user_xattr just like you, but no show.
I also noticed that I don't get web pages in my searches (and I ever searched for "beagle" and that **really** should have got me a few hits...
chat logs work though.

---

### Post by Knome_fan on 2005-03-24
beagle-0.0.8 has been released but throws the same exception.

However, according to a post on dev mailing list it is a now problem caused by a bug in mono-1.0.5:
[http://mail.gnome.org/archives/dashboard-hackers/2005-March/msg00111.html](http://mail.gnome.org/archives/dashboard-hackers/2005-March/msg00111.html)

Upgrading to 1.1.4 should fix the problem, however I'm asking myself where to find unstable mono packages for debian.
Any clues?

---

### Post by Shambler on 2005-03-24
@Bo: This might help: [http://www.beaglewiki.org/index.php/Beagle%20FAQ](http://www.beaglewiki.org/index.php/Beagle%20FAQ)

---

### Post by Bo Rosén on 2005-03-28
[QUOTE=Shambler]@Bo: This might help: [http://www.beaglewiki.org/index.php/Beagle%20FAQ](http://www.beaglewiki.org/index.php/Beagle%20FAQ)[/QUOTE]

Thanks, I'd missed that one. I'll try 0.0.8 as well (0.0.7 worked fairly well).

---

