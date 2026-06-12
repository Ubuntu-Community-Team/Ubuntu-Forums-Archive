---
title: "Beagle &quot;search service not running&quot;"
date: 2008-03-11
forum: General Help
---

### Post by ticopelp on 2008-03-11
For the love of pete, how I do I get my computer to keep beagled running? Every time I close the Beagle search window it seems to shut down beagled... so whenever I open up the search window, and enter a query, it says "search service not running" and I have to click the button... wait... wait some more, and then finally my query gets searched for. It didn't used to be like this... so annoying. 

I have beagle-search --icon and beagled --bg in my sessions and activated... what am I doing wrong? 

Thanks for any help.

---

### Post by dbera on 2008-03-11
I would suggest this
- do a beagle-shutdown to make sure beagled is not running
- from a terminal start beagled as "beagled --fg"
- start beagle-search however you want
- now if you close beagle-search, the beagled terminal will have some output saying what happened (as you stated, beagled is not supposed to die with beagle-search)

---

### Post by ticopelp on 2008-03-12
> **dbera said:**
> I would suggest this
- do a beagle-shutdown to make sure beagled is not running
- from a terminal start beagled as "beagled --fg"
- start beagle-search however you want
- now if you close beagle-search, the beagled terminal will have some output saying what happened (as you stated, beagled is not supposed to die with beagle-search)

Thanks for the reply. I did as you suggested, walked away from the computer for a few minutes and got this: 

```
Unhandled Exception: System.NotSupportedException: Stream does not support writing
  at System.IO.FileStream.Write (System.Byte[] src, Int32 src_offset, Int32 count) [0x00000] 
  at System.IO.StreamWriter.FlushBytes () [0x00000] 
  at System.IO.StreamWriter.Flush () [0x00000] 
  at System.IO.StreamWriter.Write (System.String value) [0x00000] 
  at System.IO.CStreamWriter.Write (System.String val) [0x00000] 
  at System.IO.TextWriter.Write (System.Object value) [0x00000] 
  at Beagle.Util.Log.WriteLine (LogLevel level, System.String format, System.Object[] args, System.Exception ex) [0x00000] 
  at Beagle.Util.Log.Debug (System.String message, System.Object[] args) [0x00000] 
  at Beagle.Util.Logger.Debug (System.String message, System.Object[] args) [0x00000] 
  at Beagle.Util.ExceptionHandlingThread.ThreadStarted () [0x00000] 
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void ()
Debug: The daemon appears to have gone away.
Debug: Shutting down helper.
Always: Shutdown requested
Debug: (1) Waiting for 1 worker...
Debug: waiting for server '/home/ticopelp/.beagle/socket-helper'
Debug: Server '/home/ticopelp/.beagle/socket-helper' shut down
Debug: All workers have finished.  Exiting main loop.
Debug: Joining thread 1 of 1: EHT 04159 [04155 IndexHelper] Beagle.IndexHelper.IndexHelperTool:MemoryAndIdleMonitorWorker
ticopelp@frontier:~$ Always: Index helper process shut down cleanly.

```

---

### Post by dbera on 2008-03-12
Those are the lines when the shutdown was already started. There should be some more information on why was the shutdown started. Can you get lines from even before that ... say last 50 lines or so.

---

