---
title: "Azureus &quot;Not A File&quot; Error in Gutsy 64 w/ Backports"
date: 2008-01-10
forum: General Help
---

### Post by gschoppe on 2008-01-10
To bring anyone who may be confused about the issue, I'm referring to a known Azureus bug where  torrent files cannot open in Azureus by double-clicking them... instead of opening, you get a[COLOR="Red"] "Not A File"[/COLOR] error dialog.  This same issue appears when choosing "open file" in firefox on a torrent link as a "file not found, check browser cache size" error.

according to the filed bug listing, the latest version of azureus available in [COLOR="Red"]gutsy backports[/COLOR] fixed this issue... however, after upgrading to gutsy and snagging that copy, the bug is [COLOR="Red"]NOT FIXED![/COLOR]

I need some feedback. [COLOR="Red"] Is this a 64 issue?[/COLOR]  Is there a known fix?  Did I do something wrong?

This issue is KILLING me!  I need to be able to snag torrents with a third-party app and load them in Azureus, but this Bug is totally inscrutable... I assume it has to do with parsing filenames and paths... but at that point I get lost.


HELP, PLEASE?

---

### Post by gschoppe on 2008-01-11
Just to add more info on my specific system, my package is [COLOR="Red"]2.5.0.4-1ubuntu3~gutsy1[/COLOR] from the backports repository... i updated from the original repository version.  I have several Java varieties available.. normally I use java-6-sun, but I also tried icedtea7, as that's what the newest Azureus was compiled with...  The same error appears on both, and icedtea7 breaks Torrent Episode Downloader... Now I'm back to Java-6-sun.  

here's my Update-Alternatives output:
```

gschoppe@Hippocampus:~$ sudo update-alternatives --config java

There are 5 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/lib/jvm/java-6-sun/jre/bin/java
          2    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
          3    /usr/bin/gij-4.2
          4    /usr/bin/gij-4.1
*+        5    /usr/lib/jvm/java-7-icedtea/jre/bin/java

```


ERROR DETAILS:

If I click a torrent link in Firefox and choose open in Azureus, Azureus does nothing... no error, no loading of the torrent.

If, on the firefox downloads page (ctrl-y in firefox), I choose "open", I get the following error:
```

Error
Failed to access torrent file 'file:///
tmp/torrent.name.torrent'. Ensure 
sufficient temporary file space 
available 
(check browser cache usage)

```

followed by:
```

Open Error
 'file:///tmp/torrent.name.torrent'
could not be opened:
Not a File

```

If I save the file, and double click it to open, I get the second error only...

why does lauchpad say this is fixed... would purging and reinstalling Azureus help?

---

### Post by gschoppe on 2008-01-11
Update:

Complete removal (via synaptic) and reinstall had no effect on bug, however, my settings seem to have been preserved over the reinstall. (i.e. i didn't have to change ports and AZWebUI was still installed)

Could this still be the right track?  is this a configuration issue?

---

### Post by gschoppe on 2008-01-12
I tried reinstalling it after a complete removal, and letting it use icedtea7... after my first error log, azureus would open, then immediately close, with the following terminal output:

```

gschoppe@Hippocampus:~$ azureus
Looking for and picking a preferred Java runtime
Use environment AZUREUS_JAVA to override
Using Java: /usr/lib/jvm/java-7-icedtea/jre/bin/java
should load blocklist from: http://www.bluetack.co.uk/config/spconfig.txt
Retrieving data from: http://www.bluetack.co.uk/config/splist.zip
Analysing /home/gschoppe/.azureus/hs_err_pid22851.log
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002b9d2b3dbe11, pid=22949, tid=1074792784
#
# Java VM: IcedTea 64-Bit Server VM (1.7.0-b21 mixed mode linux-amd64)
# Problematic frame:
# V  [libjvm.so+0x5c9e11]
#
# An error report file with more information is saved as:
# /home/gschoppe/.azureus/hs_err_pid22949.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
Aborted (core dumped)

```

I know this was an issue with earlier versions, but I'd been told that both of these issues were fixed in backports... apparently only for 32bit users.

GRRRR... When will 64bit get good support?

---

