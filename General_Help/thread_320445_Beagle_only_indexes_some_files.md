---
title: "Beagle only indexes some files?"
date: 2006-12-17
forum: General Help
---

### Post by johann_p on 2006-12-17
Well, I installed Beagle and wanted it to index my home directory.

Unfortunately, beagle seems to index just a small fraction of files: when I did a few testing queries, a lot of files simply do not show up although I *know* they contain the query term. I mostly checked PDF  and PS files, because those are of most interest to me and I have a large number stored on my disk. 

Is there a way to find out which files have been processed or to check whether a specific file has been indexed? 

Are there alternatives to beagle that would actually work?

---

### Post by Neobuntu on 2006-12-17
I think you can select all or part of your files for speed and your choice.

---

### Post by johann_p on 2006-12-17
Well, I ran the demon in the foreground with command 
```

beagled --fg --debug --indexing-test-mode 

```There were several exceptions, a message that re-occurred 100s of times:

```

Debug: *** Add '<homedir>' '.fonts.cache-1.NEW' (file)
Debug: *** Move '<homedir>' '.fonts.cache-1.NEW' -> '<homedir>' '.fonts.cache-1' (file)
Debug: *** Remove '<homedir>' '.fonts.cache-1.LCK' (file)
Debug: Could not resolve unique id of '.fonts.cache-1.LCK' in '<homedir>' for removal, it is probably already gone

```where <homedir> is the path to my home directory. 

Finally the whole thing crashed:
```

Error: Unhandled exception thrown.  Exiting immediately.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.NullReferenceException: Object reference not set to an instance of an object
  at Lucene.Net.Index.TermBuffer.Set (Lucene.Net.Index.Term term) [0x00000]
  at Lucene.Net.Index.SegmentTermEnum.ScanTo (Lucene.Net.Index.Term term) [0x00000]
  at Lucene.Net.Index.TermInfosReader.ScanEnum (Lucene.Net.Index.Term term) [0x00000]
  at Lucene.Net.Index.TermInfosReader.Get (Lucene.Net.Index.Term term) [0x00000]
  at Lucene.Net.Index.SegmentReader.DocFreq (Lucene.Net.Index.Term t) [0x00000]
  at Lucene.Net.Search.IndexSearcher.DocFreq (Lucene.Net.Index.Term term) [0x00000]
  at Lucene.Net.Search.Similarity.Idf (Lucene.Net.Index.Term term, Lucene.Net.Search.Searcher searcher) [0x00000]
  at Lucene.Net.Search.TermQuery+TermWeight..ctor (Lucene.Net.Search.TermQuery enclosingInstance, Lucene.Net.Search.Searcher searcher) [0x00000]
  at Lucene.Net.Search.TermQuery.CreateWeight (Lucene.Net.Search.Searcher searcher) [0x00000]
  at Lucene.Net.Search.Query.Weight (Lucene.Net.Search.Searcher searcher) [0x00000]
  at Lucene.Net.Search.IndexSearcher.Search (Lucene.Net.Search.Query query, Lucene.Net.Search.Filter filter, Lucene.Net.Search.HitCollector results) [0x00000]
  at Lucene.Net.Search.Searcher.Search (Lucene.Net.Search.Query query, Lucene.Net.Search.HitCollector results) [0x00000]
  at Lucene.Net.Search.QueryFilter.Bits (Lucene.Net.Index.IndexReader reader) [0x00000]
  at Lucene.Net.Search.IndexSearcher.Search (Weight weight, Lucene.Net.Search.Filter filter, Int32 nDocs) [0x00000]
  at Lucene.Net.Search.Hits.GetMoreDocs (Int32 min) [0x00000]
  at Lucene.Net.Search.Hits..ctor (Lucene.Net.Search.Searcher s, Lucene.Net.Search.Query q, Lucene.Net.Search.Filter f) [0x00000]
  at Lucene.Net.Search.Searcher.Search (Lucene.Net.Search.Query query, Lucene.Net.Search.Filter filter) [0x00000]
  at Beagle.Daemon.ThunderbirdQueryable.LuceneAccess.GetStoredUriStrings (System.String server, System.String file) [0x00000]
  at Beagle.Daemon.ThunderbirdQueryable.ThunderbirdIndexableGenerator..ctor (Beagle.Daemon.ThunderbirdQueryable.ThunderbirdIndexer indexer, Beagle.Util.Account account, System.String db_file) [0x00000]
  at Beagle.Daemon.ThunderbirdQueryable.MailIndexableGenerator..ctor (Beagle.Daemon.ThunderbirdQueryable.ThunderbirdIndexer indexer, Beagle.Util.Account account, System.String mork_file) [0x00000]
  at <0x00000> <unknown method>
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[])
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00040] in /build/buildd/mono-1.1.17.1/mcs/class/corlib/System.Reflection/MonoMethod.cs:362 --- End of inner exception stack trace ---

at System.Reflection.MonoCMethod.Invoke (object,System.Reflection.BindingFlags,System.Reflection.Binder,object[],System.Globalization.CultureInfo) [0x00065] in /build/buildd/mono-1.1.17.1/mcs/class/corlib/System.Reflection/MonoMethod.cs:368
at System.Reflection.MonoCMethod.Invoke (System.Reflection.BindingFlags,System.Reflection.Binder,object[],System.Globalization.CultureInfo) [0x00000] in /build/buildd/mono-1.1.17.1/mcs/class/corlib/System.Reflection/MonoMethod.cs:373
at System.Activator.CreateInstance (System.Type,System.Reflection.BindingFlags,System.Reflection.Binder,object[],System.Globalization.CultureInfo,object[]) [0x00123] in /build/buildd/mono-1.1.17.1/mcs/class/corlib/System/Activator.cs:230
at System.Activator.CreateInstance (System.Type,object[],object[]) [0x00000] in /build/buildd/mono-1.1.17.1/mcs/class/corlib/System/Activator.cs:171
at System.Activator.CreateInstance (System.Type,object[]) [0x00000] in /build/buildd/mono-1.1.17.1/mcs/class/corlib/System/Activator.cs:166
at Beagle.Daemon.ThunderbirdQueryable.ThunderbirdIndexer.IndexFile (string) <0x00147>
at Beagle.Daemon.ThunderbirdQueryable.ThunderbirdIndexer.OnInotifyEvent (Beagle.Util.Inotify/Watch,string,string,string,Beagle.Util.Inotify/EventType) <0x00447>
at (wrapper delegate-invoke) System.MulticastDelegate.invoke_void_Inotify/Watch_string_string_string_Inotify/EventType (Beagle.Util.Inotify/Watch,string,string,string,Beagle.Util.Inotify/EventType) <0x00053>
at Beagle.Daemon.ThunderbirdQueryable.ThunderbirdInotify.OnInotifyEvent (Beagle.Daemon.ThunderbirdQueryable.ThunderbirdInotify/Event) <0x00026>
at Beagle.Daemon.ThunderbirdQueryable.ThunderbirdInotify.Process () <0x00231>
at (wrapper delegate-invoke) System.MulticastDelegate.invoke_bool () <0x00037>
at TimeoutProxy.Handler () <0x0002a>
at (wrapper native-to-managed) TimeoutProxy.Handler () <0x00036>
in (unmanaged) 0xb7ebedd5
at (wrapper managed-to-native) GLib.MainLoop.g_main_loop_run (intptr) <0x00004>
at GLib.MainLoop.Run () <0x0000d>
at Beagle.Daemon.BeagleDaemon.DoMain (string[]) <0x00ab3>
at Beagle.Daemon.BeagleDaemon.Main (string[]) <0x00014>


Unhandled Exception: System.NullReferenceException: Object reference not set to an instance of an object
  at System.IO.StreamWriter.LowLevelWrite (System.String s) [0x0000e] in /build/buildd/mono-1.1.17.1/mcs/class/corlib/System.IO/StreamWriter.cs:263
  at System.IO.StreamWriter.Write (System.String value) [0x0001c] in /build/buildd/mono-1.1.17.1/mcs/class/corlib/System.IO/StreamWriter.cs:311
  at System.IO.UnexceptionalStreamWriter.Write (System.String value) [0x00000] in /build/buildd/mono-1.1.17.1/mcs/class/corlib/System.IO/UnexceptionalStreamWriter.cs:123
  at System.IO.TextWriter.Write (System.Object value) [0x00006] in /build/buildd/mono-1.1.17.1/mcs/class/corlib/System.IO/TextWriter.cs:154
  at System.IO.SynchronizedWriter.Write (System.Object value) [0x00008] in /build/buildd/mono-1.1.17.1/mcs/class/corlib/System.IO/TextWriter.cs:427
  at Beagle.Util.Log.WriteLine (LogLevel level, System.String format, System.Object[] args, System.Exception ex) [0x00000]
  at Beagle.Util.Log.Warn (System.Exception ex, System.String message, System.Object[] args) [0x00000]
  at Beagle.Util.Logger.Warn (System.Exception ex, System.String message, System.Object[] args) [0x00000]
  at Beagle.Util.ExceptionHandlingThread.ThreadStarted () [0x00000]
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void ()
Debug: The daemon appears to have gone away.

```

Looks quite unusable :(

---

### Post by johann_p on 2006-12-17
Well, I told beagle to not index my home directory and specified two directories explicitly which for some reason did not keep beagle to still index my Konqueror cache (!), then the thunderbird files, which were not part of the what I wanted to be indexed.

This application is absolutely unusable. :(

---

### Post by laidback on 2006-12-17
I have to agree. Tried it myself several times without positive results. The Ubuntu team at the London Linux Exhibition indicated that it wasn't stable....'work in progress' is the quote. I wouldn't like to rely upon it. Nice idea though. But it could be that I'm just a newbie!

Kindest regards
Laidback

---

### Post by hanzomon4 on 2006-12-17
I got it to work it just takes a long time to index and sends cpu usage up to the heavens. This thread  should help you out  [HowTo: Install and Use Beagle Easily ]("http://www.ubuntuforums.org/showthread.php?t=78810&highlight=beagle")

---

### Post by ciscosurfer on 2006-12-17
> **hanzomon4 said:**
> I got it to work it just takes a long time to index and sends cpu usage up to the heavens. This thread  should help you out  [HowTo: Install and Use Beagle Easily ]("http://www.ubuntuforums.org/showthread.php?t=78810&highlight=beagle")Agreed.

One thing to do, if you haven't already, that will allow Beagle to index your files immediately upon session startup, is to place **beagled **into your startup sessions: System > Preferences > Sessions > Startup Programs | Add :D

---

