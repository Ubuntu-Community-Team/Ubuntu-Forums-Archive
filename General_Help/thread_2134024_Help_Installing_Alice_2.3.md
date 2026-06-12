---
title: "Help Installing Alice 2.3"
date: 2013-04-09
forum: General Help
---

### Post by Ramo10 on 2013-04-09
Im trying to Install Alice 2.3 but need help.

After I opened the terminal to the directory of where I downloaded the file which is cd ~/Downloads , I followed the step which was to run in the command, **[FONT=Courier New]tar xvfz Alice2.3tar.gz[/FONT]** , but once it begins to extract, i get a message at the end saying, "tar: Exiting with failure status due to previous errors"

At first I tried to extract the file to the desktop and I got an error saying "tar: Alice2.3/Required/jre/man/ja: Cannot create symlink to `ja_JP.eucJP': File exists"
Could that be the problem? :confused:

---

### Post by Ramo10 on 2013-04-10
[COLOR=#000000]Im trying to Install Alice 2.3 but need help.[/COLOR]

[COLOR=#000000]After I opened the terminal to the directory of where I downloaded the file which is cd ~/Downloads , I followed the step which was to run in the command, [/COLOR][B][FONT=Courier New]tar xvfz Alice2.3tar.gz[/FONT] , but once it begins to extract, i get a message at the end saying, "tar: Exiting with failure status due to previous errors"

At first I tried to extract the file to the desktop and I got an error saying "tar: Alice2.3/Required/jre/man/ja: Cannot create symlink to `ja_JP.eucJP': File exists"
Could that be the problem? :confused:[/B]

---

### Post by squakie on 2013-04-10
I know nothing about it, but I went searching to find what you are trying to do.  The only thing I could find was an educational program that teaches programming of some sort, with [this]("http://help.alice.org/w/page/58034183/Download%20Alice%202_3") as the instructions for installation.  If you have been following those instructions, then please highlight and copy the terminal information for each of the steps and paste each back here in a reply.  As it is we need more information.

---

### Post by oldos2er on 2013-04-10
Threads merged. Please don't start more than one thread per question, in accordance with the Code of Conduct: "[COLOR=#000000]Do not cross post, or post the same thing in multiple locations."[/COLOR]

---

### Post by Ramo10 on 2013-04-12
> **squakie said:**
> I know nothing about it, but I went searching to find what you are trying to do.  The only thing I could find was an educational program that teaches programming of some sort, with [this]("http://help.alice.org/w/page/58034183/Download%20Alice%202_3") as the instructions for installation.  If you have been following those instructions, then please highlight and copy the terminal information for each of the steps and paste each back here in a reply.  As it is we need more information.

Ok heres all the terminal information

```
omar@omar-Dell-System-XPS-L322X:~$ cd ~/Downloads
```

```
omar@omar-Dell-System-XPS-L322X:~/Downloads$ tar xvfz Alice2.3.tar.gz
```

After I hit enter It begins to extract as you can see below but then I get the error message at the end.

```
Alice2.2/Required/jython-2.1/lib/alice/__init__.py
Alice2.2/Required/jython-2.1/lib/alice/animations$py.class
Alice2.2/Required/jython-2.1/lib/alice/animations.py
Alice2.2/Required/jython-2.1/lib/alice/constants$py.class
Alice2.2/Required/jython-2.1/lib/alice/constants.py
Alice2.2/Required/jython-2.1/lib/alice/linearalgebra$py.class
Alice2.2/Required/jython-2.1/lib/alice/linearalgebra.py
Alice2.2/Required/jython-2.1/lib/alice/pinchgloves.py
Alice2.2/Required/jython-2.1/lib/jxxload_help/DiscardHelp.java
Alice2.2/Required/jython-2.1/lib/jxxload_help/JavaLoaderFactory.java
Alice2.2/Required/jython-2.1/lib/jxxload_help/Makefile
Alice2.2/Required/jython-2.1/lib/jxxload_help/PackageManager.java
Alice2.2/Required/jython-2.1/lib/jxxload_help/PathVFS.java
Alice2.2/Required/jython-2.1/lib/jxxload_help/PathVFSJavaLoader.java
Alice2.2/Required/jython-2.1/lib/pawt/__init__.py
Alice2.2/Required/jython-2.1/lib/pawt/colors.py
Alice2.2/Required/jython-2.1/lib/pawt/Makefile
Alice2.2/Required/jython-2.1/lib/pawt/swing.py
Alice2.2/Required/jython-2.1/Lib/pawt/__init__.py
Alice2.2/Required/jython-2.1/Lib/pawt/colors.py
Alice2.2/Required/jython-2.1/Lib/pawt/Makefile
Alice2.2/Required/jython-2.1/Lib/pawt/swing.py
Alice2.2/Required/jython-2.1/Lib/alice/__init__.py
Alice2.2/Required/jython-2.1/Lib/alice/animations$py.class
Alice2.2/Required/jython-2.1/Lib/alice/animations.py
Alice2.2/Required/jython-2.1/Lib/alice/constants$py.class
Alice2.2/Required/jython-2.1/Lib/alice/constants.py
Alice2.2/Required/jython-2.1/Lib/alice/linearalgebra$py.class
Alice2.2/Required/jython-2.1/Lib/alice/linearalgebra.py
Alice2.2/Required/jython-2.1/Lib/alice/pinchgloves.py
Alice2.2/Required/jython-2.1/Lib/jxxload_help/DiscardHelp.java
Alice2.2/Required/jython-2.1/Lib/jxxload_help/JavaLoaderFactory.java
Alice2.2/Required/jython-2.1/Lib/jxxload_help/Makefile
Alice2.2/Required/jython-2.1/Lib/jxxload_help/PackageManager.java
Alice2.2/Required/jython-2.1/Lib/jxxload_help/PathVFS.java
Alice2.2/Required/jython-2.1/Lib/jxxload_help/PathVFSJavaLoader.java
Alice2.2/Required/jython-2.1/cachedir/packages/resources$2.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/rt$2.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/jsse$2.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/jce$2.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/charsets$2.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/sunpkcs11$2.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/sunjce_provider$2.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/localedata$2.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/dnsns$2.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/alice$2.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/customizer$2.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/getopt-1.0.7$2.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/javazoom$2.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/jmf$2.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/jogl$2.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/jython$2.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/mediaplayer$2.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/mp3plugin$2.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/multiplayer$2.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/resolver$2.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/vecmath$2.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/xercesImpl$2.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/xml-apis$2.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/xmlParserAPIs$2.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/resources$3.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/rt$3.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/jsse$3.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/jce$3.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/charsets$3.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/rhino$2.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/sunpkcs11$3.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/sunjce_provider$3.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/pulse-java$2.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/localedata$3.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/dnsns$3.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/alice.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/customizer.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/getopt-1.0.7.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/javazoom.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/jmf.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/jogl.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/jython.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/mediaplayer.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/mp3plugin.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/multiplayer.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/resolver.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/vecmath.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/xercesImpl.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/xml-apis.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/xmlParserAPIs.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/resources.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/rt.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/jsse.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/jce.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/charsets.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/rhino.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/sunpkcs11.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/sunjce_provider.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/pulse-java.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/localedata.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/dnsns.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/packages.idx
Alice2.2/Required/jython-2.1/cachedir/packages/alice$1.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/customizer$1.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/getopt-1.0.7$1.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/javazoom$1.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/jmf$1.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/jogl$1.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/jython$1.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/mediaplayer$1.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/mp3plugin$1.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/multiplayer$1.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/resolver$1.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/vecmath$1.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/xercesImpl$1.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/xml-apis$1.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/xmlParserAPIs$1.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/resources$1.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/rt$1.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/jsse$1.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/jce$1.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/charsets$1.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/rhino$1.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/sunpkcs11$1.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/sunjce_provider$1.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/pulse-java$1.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/localedata$1.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/dnsns$1.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/customizer$3.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/getopt-1.0.7$3.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/j3dcore.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/j3dutils.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/javazoom$3.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/jl1.0.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/jmf$3.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/jogl$3.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/jython$3.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/mediaplayer$3.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/mp3plugin$3.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/multiplayer$3.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/resolver$3.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/sound.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/vecmath$3.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/xercesImpl$3.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/xercesSamples.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/xml-apis$3.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/xmlParserAPIs$3.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/resources$4.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/rt$4.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/jsse$4.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/jce$4.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/charsets$4.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/sunpkcs11$4.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/sunjce_provider$4.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/localedata$4.pkc
Alice2.2/Required/jython-2.1/cachedir/packages/dnsns$4.pkc
Alice2.2/Required/lib/linux-i586/libjogl_cg.so
Alice2.2/Required/lib/linux-i586/libjogl_awt.so
Alice2.2/Required/lib/linux-i586/libjogl.so
Alice2.2/Required/lib/linux-i586/libjogl_drihack.so
Alice2.2/Required/resources/common/StandardResources.py
Alice2.2/Required/resources/common/vssver.scc
Alice2.2/Required/resources/common/ResourceTransfer.py
Alice2.2/Required/resources/en/Alice Style.py
Alice2.2/Required/resources/en/Java Style.py
Alice2.2/Required/resources/en/Java Text Style.py
Alice2.2/Required/resources/es/Alice Style.py
Alice2.2/Required/resources/es/Java Style.py
Alice2.2/Required/resources/es/Java Text Style.py
Alice2.2/Required/jre/bin/pack200
Alice2.2/Required/jre/bin/keytool
Alice2.2/Required/jre/bin/unpack200
Alice2.2/Required/jre/bin/java
Alice2.2/Required/jre/bin/orbd
Alice2.2/Required/jre/bin/rmiregistry
Alice2.2/Required/jre/bin/servertool
Alice2.2/Required/jre/bin/rmid
Alice2.2/Required/jre/bin/tnameserv
Alice2.2/Required/jre/bin/policytool
Alice2.2/Required/jre/bin/javaws
Alice2.2/Required/jre/lib/jsse.jar
Alice2.2/Required/jre/lib/jce.jar
Alice2.2/Required/jre/lib/charsets.jar
Alice2.2/Required/jre/lib/classlist
Alice2.2/Required/jre/lib/currency.data
Alice2.2/Required/jre/lib/jvm.hprof.txt
Alice2.2/Required/jre/lib/compilefontconfig.jar
Alice2.2/Required/jre/lib/javazic.jar
Alice2.2/Required/jre/lib/management-agent.jar
Alice2.2/Required/jre/lib/meta-index
Alice2.2/Required/jre/lib/rhino.jar
Alice2.2/Required/jre/lib/tz.properties
Alice2.2/Required/jre/lib/resources.jar
Alice2.2/Required/jre/lib/rt.jar
Alice2.2/Required/jre/lib/jexec
Alice2.2/Required/jre/lib/jar.binfmt
Alice2.2/Required/jre/lib/swing.properties
Alice2.2/Required/jre/lib/logging.properties
Alice2.2/Required/jre/lib/flavormap.properties
Alice2.2/Required/jre/lib/psfontj2d.properties
Alice2.2/Required/jre/lib/sound.properties
Alice2.2/Required/jre/lib/fontconfig.bfc
Alice2.2/Required/jre/lib/accessibility.properties
Alice2.2/Required/jre/lib/calendars.properties
Alice2.2/Required/jre/lib/psfont.properties.ja
Alice2.2/Required/jre/lib/fontconfig.properties
Alice2.2/Required/jre/lib/net.properties
Alice2.2/Required/jre/lib/content-types.properties
Alice2.2/Required/jython-2.1/lib/__future__.py
Alice2.2/Required/jython-2.1/lib/anydbm.py
Alice2.2/Required/jython-2.1/lib/atexit.py
Alice2.2/Required/jython-2.1/lib/base64.py
Alice2.2/Required/jython-2.1/lib/BaseHTTPServer.py
Alice2.2/Required/jython-2.1/lib/bdb.py
Alice2.2/Required/jython-2.1/lib/binhex.py
Alice2.2/Required/jython-2.1/lib/bisect.py
Alice2.2/Required/jython-2.1/lib/calendar.py
Alice2.2/Required/jython-2.1/lib/cgi.py
Alice2.2/Required/jython-2.1/lib/CGIHTTPServer.py
Alice2.2/Required/jython-2.1/lib/cmd.py
Alice2.2/Required/jython-2.1/lib/code.py
Alice2.2/Required/jython-2.1/lib/codecs.py
Alice2.2/Required/jython-2.1/lib/colorsys.py
Alice2.2/Required/jython-2.1/lib/commands.py
Alice2.2/Required/jython-2.1/lib/compileall.py
Alice2.2/Required/jython-2.1/lib/ConfigParser.py
Alice2.2/Required/jython-2.1/lib/Cookie.py
Alice2.2/Required/jython-2.1/lib/copy.py
Alice2.2/Required/jython-2.1/lib/copy_reg.py
Alice2.2/Required/jython-2.1/lib/dbexts.py
Alice2.2/Required/jython-2.1/lib/difflib.py
Alice2.2/Required/jython-2.1/lib/dircache.py
Alice2.2/Required/jython-2.1/lib/doctest.py
Alice2.2/Required/jython-2.1/lib/dospath.py
Alice2.2/Required/jython-2.1/lib/dumbdbm.py
Alice2.2/Required/jython-2.1/lib/fileinput.py
Alice2.2/Required/jython-2.1/lib/fnmatch.py
Alice2.2/Required/jython-2.1/lib/formatter.py
Alice2.2/Required/jython-2.1/lib/fpformat.py
Alice2.2/Required/jython-2.1/lib/ftplib.py
Alice2.2/Required/jython-2.1/lib/getopt.py
Alice2.2/Required/jython-2.1/lib/glob.py
Alice2.2/Required/jython-2.1/lib/gopherlib.py
Alice2.2/Required/jython-2.1/lib/gzip.py
Alice2.2/Required/jython-2.1/lib/htmlentitydefs.py
Alice2.2/Required/jython-2.1/lib/htmllib.py
Alice2.2/Required/jython-2.1/lib/httplib.py
Alice2.2/Required/jython-2.1/lib/imaplib.py
Alice2.2/Required/jython-2.1/lib/imghdr.py
Alice2.2/Required/jython-2.1/lib/isql.py
Alice2.2/Required/jython-2.1/lib/javaos.py
Alice2.2/Required/jython-2.1/lib/javapath.py
Alice2.2/Required/jython-2.1/lib/jreload.py
Alice2.2/Required/jython-2.1/lib/keyword.py
Alice2.2/Required/jython-2.1/lib/linecache.py
Alice2.2/Required/jython-2.1/lib/macpath.py
Alice2.2/Required/jython-2.1/lib/macurl2path.py
Alice2.2/Required/jython-2.1/lib/mailbox.py
Alice2.2/Required/jython-2.1/lib/mailcap.py
Alice2.2/Required/jython-2.1/lib/marshal.py
Alice2.2/Required/jython-2.1/lib/mhlib.py
Alice2.2/Required/jython-2.1/lib/mimetools.py
Alice2.2/Required/jython-2.1/lib/mimetypes.py
Alice2.2/Required/jython-2.1/lib/MimeWriter.py
Alice2.2/Required/jython-2.1/lib/mimify.py
Alice2.2/Required/jython-2.1/lib/multifile.py
Alice2.2/Required/jython-2.1/lib/mutex.py
Alice2.2/Required/jython-2.1/lib/nntplib.py
Alice2.2/Required/jython-2.1/lib/ntpath.py
Alice2.2/Required/jython-2.1/lib/nturl2path.py
Alice2.2/Required/jython-2.1/lib/pdb.py
Alice2.2/Required/jython-2.1/lib/pickle.py
Alice2.2/Required/jython-2.1/lib/pipes.py
Alice2.2/Required/jython-2.1/lib/popen2.py
Alice2.2/Required/jython-2.1/lib/poplib.py
Alice2.2/Required/jython-2.1/lib/posixfile.py
Alice2.2/Required/jython-2.1/lib/posixpath.py
Alice2.2/Required/jython-2.1/lib/pprint.py
Alice2.2/Required/jython-2.1/lib/profile.py
Alice2.2/Required/jython-2.1/lib/pstats.py
Alice2.2/Required/jython-2.1/lib/pyclbr.py
Alice2.2/Required/jython-2.1/lib/Queue.py
Alice2.2/Required/jython-2.1/lib/quopri.py
Alice2.2/Required/jython-2.1/lib/random.py
Alice2.2/Required/jython-2.1/lib/re.py
Alice2.2/Required/jython-2.1/lib/reconvert.py
Alice2.2/Required/jython-2.1/lib/repr.py
Alice2.2/Required/jython-2.1/lib/rfc822.py
Alice2.2/Required/jython-2.1/lib/sched.py
Alice2.2/Required/jython-2.1/lib/sgmllib.py
Alice2.2/Required/jython-2.1/lib/shelve.py
Alice2.2/Required/jython-2.1/lib/shutil.py
Alice2.2/Required/jython-2.1/lib/SimpleHTTPServer.py
Alice2.2/Required/jython-2.1/lib/site.py
Alice2.2/Required/jython-2.1/lib/smtplib.py
Alice2.2/Required/jython-2.1/lib/sndhdr.py
Alice2.2/Required/jython-2.1/lib/socket.py
Alice2.2/Required/jython-2.1/lib/SocketServer.py
Alice2.2/Required/jython-2.1/lib/sre.py
Alice2.2/Required/jython-2.1/lib/sre_compile.py
Alice2.2/Required/jython-2.1/lib/sre_constants.py
Alice2.2/Required/jython-2.1/lib/sre_parse.py
Alice2.2/Required/jython-2.1/lib/stat.py
Alice2.2/Required/jython-2.1/lib/string.py
Alice2.2/Required/jython-2.1/lib/StringIO.py
Alice2.2/Required/jython-2.1/lib/symbol.py
Alice2.2/Required/jython-2.1/lib/telnetlib.py
Alice2.2/Required/jython-2.1/lib/tempfile.py
Alice2.2/Required/jython-2.1/lib/threading.py
Alice2.2/Required/jython-2.1/lib/token.py
Alice2.2/Required/jython-2.1/lib/tokenize.py
Alice2.2/Required/jython-2.1/lib/traceback.py
Alice2.2/Required/jython-2.1/lib/tzparse.py
Alice2.2/Required/jython-2.1/lib/unittest.py
Alice2.2/Required/jython-2.1/lib/urllib.py
Alice2.2/Required/jython-2.1/lib/urlparse.py
Alice2.2/Required/jython-2.1/lib/user.py
Alice2.2/Required/jython-2.1/lib/UserDict.py
Alice2.2/Required/jython-2.1/lib/UserList.py
Alice2.2/Required/jython-2.1/lib/UserString.py
Alice2.2/Required/jython-2.1/lib/warnings.py
Alice2.2/Required/jython-2.1/lib/weakref.py
Alice2.2/Required/jython-2.1/lib/whichdb.py
Alice2.2/Required/jython-2.1/lib/whrandom.py
Alice2.2/Required/jython-2.1/lib/xdrlib.py
Alice2.2/Required/jython-2.1/lib/xmllib.py
Alice2.2/Required/jython-2.1/lib/zipfile.py
Alice2.2/Required/jython-2.1/lib/zlib.py
Alice2.2/Required/jython-2.1/Lib/linecache$py.class
Alice2.2/Required/jython-2.1/Lib/random$py.class
Alice2.2/Required/jython-2.1/Lib/stat$py.class
Alice2.2/Required/jython-2.1/Lib/string$py.class
Alice2.2/Required/jython-2.1/Lib/traceback$py.class
Alice2.2/Required/lib/alice.jar
Alice2.2/Required/sounds/chicken.mp3
Alice2.2/Required/sounds/doorbell.mp3
Alice2.2/Required/sounds/drip.mp3
Alice2.2/Required/sounds/gong.mp3
Alice2.2/Required/sounds/pop.mp3
Alice2.2/Required/sounds/splash.wav
Alice2.2/Required/sounds/thud1.mp3
Alice2.2/Required/sounds/thud2.mp3
Alice2.2/Required/sounds/whoosh1.mp3
Alice2.2/Required/sounds/whoosh2.mp3
Alice2.2/Required/templateWorlds/dirt.a2w
Alice2.2/Required/templateWorlds/grass.a2w
Alice2.2/Required/templateWorlds/sand.a2w
Alice2.2/Required/templateWorlds/snow.a2w
Alice2.2/Required/templateWorlds/space.a2w
Alice2.2/Required/templateWorlds/water.a2w
Alice2.2/Required/textureMap/DirtTexture.png
Alice2.2/Required/textureMap/GrassTexture.png
Alice2.2/Required/textureMap/MoonTexture.png
Alice2.2/Required/textureMap/SandTexture.png
Alice2.2/Required/textureMap/SnowTexture.png
Alice2.2/Required/textureMap/WaterTexture.png
Alice2.2/Required/tutorial/Tutorial1.stl
Alice2.2/Required/tutorial/Tutorial2.stl
Alice2.2/Required/tutorial/Tutorial3.stl
Alice2.2/Required/tutorial/Tutorial4.stl
Alice2.2/Required/tutorial/vssver.scc
Alice2.2/Required/resources/vssver.scc
Alice2.2/Required/tutorialWorlds/IceSkaterWorld.a2w
Alice2.2/Required/tutorialWorlds/naptime.a2w
Alice2.2/Required/tutorialWorlds/penguinChorus1b.a2w
Alice2.2/Required/tutorialWorlds/space.a2w
Alice2.2/Required/jre/THIRD_PARTY_README
Alice2.2/Required/jre/ASSEMBLY_EXCEPTION
Alice2.2/Required/externalLib/getopt-1.0.7.jar
Alice2.2/Required/externalLib/jmf.properties
Alice2.2/Required/externalLib/javazoom.jar
Alice2.2/Required/externalLib/mediaplayer.jar
Alice2.2/Required/externalLib/mp3plugin.jar
Alice2.2/Required/externalLib/vecmath.jar
Alice2.2/Required/externalLib/resolver.jar
Alice2.2/Required/externalLib/xercesImpl.jar
Alice2.2/Required/externalLib/xml-apis.jar
Alice2.2/Required/externalLib/xmlParserAPIs.jar
Alice2.2/Required/externalLib/customizer.jar
Alice2.2/Required/externalLib/jmf.jar
Alice2.2/Required/externalLib/multiplayer.jar
Alice2.2/Required/externalLib/jogl.jar
Alice2.2/Required/externalLib/jython.jar
Alice2.2/Required/exampleWorlds/amusementPark.a2w
Alice2.2/Required/exampleWorlds/flightSimulator.a2w
Alice2.2/Required/exampleWorlds/lakeSkater.a2w
Alice2.2/Required/exampleWorlds/lakeSkaterDemoStart.a2w
Alice2.2/Required/exampleWorlds/LightDemo.a2w
Alice2.2/Required/exampleWorlds/snowLove.a2w
Alice2.2/Required/etc/version.txt
Alice2.2/Required/etc/aliceapplet.jar
Alice2.2/Required/etc/AliceSplash.jpg
Alice2.2/Required/etc/appletTemplate.html
Alice2.2/Required/etc/default.a2w
Alice2.2/Required/etc/default_es.a2w
Alice2.2/Required/jython-2.1/registry
Alice2.2/Required/run-alice
Alice2.2/Required/DISCLAIMER.txt
Alice2.2/Required/jythonLicense.txt
Alice2.2/Required/lgpl.txt
Alice2.2/Required/README.txt
Alice2.2/Required/mp3register
Alice2.2/Required/Alice2.3_LICENSE.pdf
Alice2.2/.dropbox
Alice2.2/Required/gallery/English/High School/Students and Teachers/Prom/
Alice2.2/Required/jre/man/ja/man1/
Alice2.2/Required/jre/man/ja_JP.eucJP/man1/
Alice2.2/Required/jre/lib/images/cursors/
Alice2.2/Required/jre/lib/i386/jli/
Alice2.2/Required/jre/lib/i386/headless/
Alice2.2/Required/jre/lib/i386/client/
Alice2.2/Required/jre/lib/i386/server/
Alice2.2/Required/jre/lib/i386/native_threads/
Alice2.2/Required/jre/lib/i386/cacao/
Alice2.2/Required/jre/lib/i386/jamvm/
Alice2.2/Required/jre/lib/i386/xawt/
Alice2.2/Required/gallery/English/High School/Students and Teachers/
Alice2.2/Required/gallery/English/Hawaii/animals/
Alice2.2/Required/gallery/English/Hawaii/environment/
Alice2.2/Required/gallery/English/Hawaii/People/
Alice2.2/Required/gallery/English/Hawaii/Plants/
Alice2.2/Required/gallery/English/Hawaii/Transportation/
Alice2.2/Required/gallery/English/Environments/Skies/
Alice2.2/Required/gallery/English/Fantasy/Faeries/
Alice2.2/Required/gallery/English/Holidays/Birthday/
Alice2.2/Required/gallery/English/Holidays/Christmas/
Alice2.2/Required/gallery/English/Kitchen/Food/
Alice2.2/Required/gallery/English/People/Urban/
Alice2.2/Required/gallery/English/People/Walking People/
Alice2.2/Required/gallery/English/Animals/Dinosaurs/
Alice2.2/Required/gallery/English/Animals/Bugs/
Alice2.2/Required/jre/man/ja
tar: Alice2.2/Required/jre/man/ja: Cannot create symlink to `ja_JP.eucJP': File exists
Alice2.2/Required/jre/man/ja_JP.eucJP/
Alice2.2/Required/jre/man/man1/
Alice2.2/Required/jre/lib/images/
Alice2.2/Required/jre/lib/cmm/
Alice2.2/Required/jre/lib/ext/
Alice2.2/Required/jre/lib/im/
Alice2.2/Required/jre/lib/i386/
Alice2.2/Required/jre/lib/management/
Alice2.2/Required/jre/lib/security/
Alice2.2/Required/gallery/English/Farm/
Alice2.2/Required/gallery/English/Furniture/
Alice2.2/Required/gallery/English/Pilgrims/
Alice2.2/Required/gallery/English/High School/
Alice2.2/Required/gallery/English/Roads and Signs/
Alice2.2/Required/gallery/English/SciFi/
Alice2.2/Required/gallery/English/Beach/
Alice2.2/Required/gallery/English/Hawaii/
Alice2.2/Required/gallery/English/Buildings/
Alice2.2/Required/gallery/English/Amusement Park/
Alice2.2/Required/gallery/English/City/
Alice2.2/Required/gallery/English/Controls/
Alice2.2/Required/gallery/English/Egypt/
Alice2.2/Required/gallery/English/Environments/
Alice2.2/Required/gallery/English/Fantasy/
Alice2.2/Required/gallery/English/Holidays/
Alice2.2/Required/gallery/English/Japan/
Alice2.2/Required/gallery/English/Kitchen/
Alice2.2/Required/gallery/English/Lights/
Alice2.2/Required/gallery/English/Math/
Alice2.2/Required/gallery/English/Medieval/
Alice2.2/Required/gallery/English/Musical Instruments/
Alice2.2/Required/gallery/English/Nature/
Alice2.2/Required/gallery/English/Objects/
Alice2.2/Required/gallery/English/Ocean/
Alice2.2/Required/gallery/English/Old West/
Alice2.2/Required/gallery/English/Park/
Alice2.2/Required/gallery/English/People/
Alice2.2/Required/gallery/English/Shapes/
Alice2.2/Required/gallery/English/Skate Park/
Alice2.2/Required/gallery/English/Space/
Alice2.2/Required/gallery/English/Special Effects/
Alice2.2/Required/gallery/English/Spooky/
Alice2.2/Required/gallery/English/Sports/
Alice2.2/Required/gallery/English/Vehicles/
Alice2.2/Required/gallery/English/Visualizations/
Alice2.2/Required/gallery/English/Ancients/
Alice2.2/Required/gallery/English/Animals/
Alice2.2/Required/jython-2.1/lib/alice/
Alice2.2/Required/jython-2.1/lib/jxxload_help/
Alice2.2/Required/jython-2.1/lib/pawt/
Alice2.2/Required/jython-2.1/Lib/pawt/
Alice2.2/Required/jython-2.1/Lib/alice/
Alice2.2/Required/jython-2.1/Lib/jxxload_help/
Alice2.2/Required/jython-2.1/cachedir/packages/
Alice2.2/Required/lib/linux-i586/
Alice2.2/Required/resources/common/
Alice2.2/Required/resources/en/
Alice2.2/Required/resources/es/
Alice2.2/Required/jre/bin/
Alice2.2/Required/jre/man/
Alice2.2/Required/jre/lib/
Alice2.2/Required/gallery/English/
Alice2.2/Required/jython-2.1/lib/
Alice2.2/Required/jython-2.1/Lib/
Alice2.2/Required/jython-2.1/cachedir/
Alice2.2/Required/lib/
Alice2.2/Required/sounds/
Alice2.2/Required/templateWorlds/
Alice2.2/Required/textureMap/
Alice2.2/Required/tutorial/
Alice2.2/Required/resources/
Alice2.2/Required/tutorialWorlds/
Alice2.2/Required/jre/
Alice2.2/Required/externalLib/
Alice2.2/Required/exampleWorlds/
Alice2.2/Required/etc/
Alice2.2/Required/gallery/
Alice2.2/Required/jython-2.1/
Alice2.2/Required/
Alice2.2/
**tar: Exiting with failure status due to previous errors**
omar@omar-Dell-System-XPS-L322X:~/Downloads$ 

```

---

### Post by catherinedevlin on 2013-04-12
I'm having precisely the same problem.  I suspect that the Alice project botched the packaging - this is the first version where they've even tried to release for Linux, and notice how the Alice 2.3 file unzips into Alice2.2?

Description:	Ubuntu 12.10
Release:	12.10
Codename:	quantal
64-bit

---

### Post by Ramo10 on 2013-04-14
> **catherinedevlin said:**
> I'm having precisely the same problem.  I suspect that the Alice project botched the packaging - this is the first version where they've even tried to release for Linux, and notice how the Alice 2.3 file unzips into Alice2.2?

Description:    Ubuntu 12.10
Release:    12.10
Codename:    quantal
64-bit

Yea I did notice that. Man i still haven't gotten it to work. This is bs -_-

---

### Post by squakie on 2013-04-16
It thinks a file or link already exists:  tar: Alice2.2/Required/jre/man/ja: Cannot create symlink to `ja_JP.eucJP': File exists
.  However, I also noticed the Alice2.2 notations.  My gut feel is this is an error on behalf of the developers of the package.  You should probably go to their website and ask for help there.

---

