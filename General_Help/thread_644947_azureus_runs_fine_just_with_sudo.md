---
title: "azureus runs fine just with sudo"
date: 2007-12-19
forum: General Help
---

### Post by trazart on 2007-12-19
I get the following errors when i start azureus, they are not critical because I can run it without problems, but I cant close it. I have to kill the process (-9).

There must be something with write privileges because when i run 'sudo azureus'  i get no errors and azureus closes fine.

Can you help me? Thanks

```
$ azureus 
Looking for and picking a preferred Java runtime
Use environment AZUREUS_JAVA to override
Using Java: /usr/lib/jvm/java-7-icedtea/jre/bin/java
19-dic-2007 20:00:01 com.sun.corba.se.impl.ior.IORImpl getProfile
ADVERTENCIA: "IOP00511201: (INV_OBJREF) IOR must have at least one IIOP profile"
org.omg.CORBA.INV_OBJREF:   vmcid: SUN  minor code: 1201  completed: No
        at com.sun.corba.se.impl.logging.IORSystemException.iorMustHaveIiopProfile(IORSystemException.java:473)
        at com.sun.corba.se.impl.logging.IORSystemException.iorMustHaveIiopProfile(IORSystemException.java:495)
        at com.sun.corba.se.impl.ior.IORImpl.getProfile(IORImpl.java:334)
        at com.sun.corba.se.impl.encoding.CDRInputStream_1_0.read_Object(CDRInputStream_1_0.java:787)
        at com.sun.corba.se.impl.encoding.CDRInputStream_1_0.read_Object(CDRInputStream_1_0.java:761)
        at com.sun.corba.se.impl.encoding.CDRInputStream.read_Object(CDRInputStream.java:231)
        at com.sun.corba.se.impl.resolver.INSURLOperationImpl.getIORFromString(INSURLOperationImpl.java:116)
        at com.sun.corba.se.impl.resolver.INSURLOperationImpl.operate(INSURLOperationImpl.java:126)
        at com.sun.corba.se.impl.orb.ORBImpl.string_to_object(ORBImpl.java:838)
        at org.GNOME.Accessibility.AccessUtil.getRegistryObject(AccessUtil.java:143)
        at org.GNOME.Accessibility.JavaBridge.registerApplication(JavaBridge.java:1058)
        at org.GNOME.Accessibility.JavaBridge.<init>(JavaBridge.java:341)
        at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
        at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:57)
        at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
        at java.lang.reflect.Constructor.newInstance(Constructor.java:539)
        at java.lang.Class.newInstance0(Class.java:373)
        at java.lang.Class.newInstance(Class.java:326)
        at java.awt.Toolkit.loadAssistiveTechnologies(Toolkit.java:801)
        at java.awt.Toolkit.getDefaultToolkit(Toolkit.java:889)
        at sun.awt.shell.ShellFolder.<clinit>(ShellFolder.java:199)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Class.java:187)
        at org.gudy.azureus2.ui.swt.ImageRepository.getPathIcon(ImageRepository.java:447)
        at org.gudy.azureus2.ui.swt.ImageRepository.getPathIcon(ImageRepository.java:375)
        at org.gudy.azureus2.ui.swt.views.tableitems.mytorrents.NameItem.refresh(NameItem.java:85)
        at org.gudy.azureus2.ui.swt.views.table.impl.TableColumnImpl.invokeCellRefreshListeners(TableColumnImpl.java:447)
        at org.gudy.azureus2.ui.swt.views.table.impl.TableCellImpl.refresh(TableCellImpl.java:826)
        at org.gudy.azureus2.ui.swt.views.table.impl.TableCellImpl.refresh(TableCellImpl.java:761)
        at org.gudy.azureus2.ui.swt.views.table.impl.TableRowImpl.refresh(TableRowImpl.java:212)
        at org.gudy.azureus2.ui.swt.views.TableView.visibleRowsChanged(TableView.java:3337)
        at org.gudy.azureus2.ui.swt.views.TableView._addDataSourcesToSWT(TableView.java:2058)
        at org.gudy.azureus2.ui.swt.views.TableView.access$2700(TableView.java:101)
        at org.gudy.azureus2.ui.swt.views.TableView$30.runSupport(TableView.java:1903)
        at org.gudy.azureus2.core3.util.AERunnable.run(AERunnable.java:38)
        at org.eclipse.swt.widgets.RunnableLock.run(RunnableLock.java:35)
        at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Synchronizer.java:123)
        at org.eclipse.swt.widgets.Display.runAsyncMessages(Display.java:3157)
        at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:2859)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init>(SWTThread.java:134)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThread.java:68)
        at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.java:105)
        at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:80)
        at org.gudy.azureus2.ui.swt.Main.main(Main.java:180)
DEBUG::Wed Dec 19 20:00:07 CET 2007::org.gudy.azureus2.core3.util.DebugLight::printStackTrace::38:
  java.lang.NullPointerException
        at org.gudy.azureus2.update.CoreUpdateChecker.doUsageStats(CoreUpdateChecker.java:73)
        at org.gudy.azureus2.ui.swt.update.UpdateMonitor$5.runSupport(UpdateMonitor.java:233)
        at org.gudy.azureus2.core3.util.AERunnable.run(AERunnable.java:38)
        at org.gudy.azureus2.core3.util.DelayedEvent$1.perform(DelayedEvent.java:48)
        at org.gudy.azureus2.core3.util.TimerEvent.runSupport(TimerEvent.java:109)
        at org.gudy.azureus2.core3.util.AERunnable.run(AERunnable.java:38)
        at org.gudy.azureus2.core3.util.ThreadPool$threadPoolWorker$1.runSupport(ThreadPool.java:510)
        at org.gudy.azureus2.core3.util.AEThread.run(AEThread.java:69)

```

---

### Post by timseal on 2007-12-19
Not sure why it's only working with root, but obviously you don't want to be doing that.   Try installing sun-java6-jre and see if it works with the official Java runtime.

---

### Post by trazart on 2007-12-19
Different error message but same result, it doesnt close using Exit, I have to kill the process.

Using sudo closes O_o

```
$ azureus
Looking for and picking a preferred Java runtime
Use environment AZUREUS_JAVA to override
Using Java: /usr/lib/jvm/java-6-sun/jre/bin/java
DEBUG::Wed Dec 19 23:19:16 CET 2007::org.gudy.azureus2.core3.util.DebugLight::printStackTrace::38:
  java.lang.NullPointerException
        at org.gudy.azureus2.update.CoreUpdateChecker.doUsageStats(CoreUpdateChecker.java:73)
        at org.gudy.azureus2.ui.swt.update.UpdateMonitor$5.runSupport(UpdateMonitor.java:233)
        at org.gudy.azureus2.core3.util.AERunnable.run(AERunnable.java:38)
        at org.gudy.azureus2.core3.util.DelayedEvent$1.perform(DelayedEvent.java:48)
        at org.gudy.azureus2.core3.util.TimerEvent.runSupport(TimerEvent.java:109)
        at org.gudy.azureus2.core3.util.AERunnable.run(AERunnable.java:38)
        at org.gudy.azureus2.core3.util.ThreadPool$threadPoolWorker$1.runSupport(ThreadPool.java:510)
        at org.gudy.azureus2.core3.util.AEThread.run(AEThread.java:69)

```

Well, actually it's the same error, But i dont think it is the problem when i want to exit.

---

### Post by timseal on 2007-12-19
Are you using azureus-gcj or azureus?
Try downloading directly from azureus.sourceforge.net, extract it somewhere under your home directory, cd into azureus and run it with ./azureus.
do a mv ~/.azureus ~/azureus.old or similar to make sure it's not picking up any rogue settings.

---

### Post by jken146 on 2007-12-19
edit: What was I talking about?  Totally wrong info, sorry.

---

### Post by trazart on 2007-12-20
I have been using azureus (not azureus-gcj).

I have downloaded Azureus3 from the web and I got no errors executing it but when I closed it, the process was still there!!

---

### Post by danwood76 on 2007-12-20
when you close it do you go file then exit? because otherwise it runs in the background and should display an icon in the notification area.

---

### Post by trazart on 2007-12-20
Yeah, I know, File and exit, or right click the icon and exit.

---

### Post by trazart on 2007-12-20
I have been testing this and... if I dont have any file in the queue azureus closes fine, but if there is a file downloading or uploading it wont exit. Even if all of them were removed from the list before exiting.

This is really weird, my downloads are in a FAT32 partition and i have read and write permissions

---

### Post by danwood76 on 2007-12-20
Why are you using FAT32? Such an aweful filesystem. Though I dont think this shouyld effect azureus.

You could try downloading a torrent to an ext3 partition and seeing if it makes any difference.

regards,
Danny

---

### Post by trazart on 2007-12-20
I just did it and no change, i tried to download a file to a folder in my home directory and actually it downloads (as with FAT) but it doesnt close completely. I get no error by the way.


BTW, im using FAT32 because i shared this partition with windows, i will format it as Ext3 soon ;)

---

### Post by danwood76 on 2007-12-20
What version of ubuntu are you running?

---

### Post by trazart on 2007-12-20
Gutsy.

I'm thinking that java may be blocking the files somehow, How can I check if a file is being used?

---

### Post by trazart on 2007-12-21
I solved it installing sun-java version 5 !!

What version of java runtime are you using?

---

