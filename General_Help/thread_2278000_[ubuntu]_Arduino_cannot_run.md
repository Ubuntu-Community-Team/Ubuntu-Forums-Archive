---
title: "[ubuntu] Arduino cannot run"
date: 2015-05-13
forum: General Help
---

### Post by Tran_Phuc_Sang on 2015-05-13
In the past, when i tried to install Arduino, the terminal shown I held broken packages then I installed it with aptitude and I succeed. However, It cannot start running. When I clicked on the Arduino's icon in launch bar, it response nothing.
I have removed and re-installed it but the result is the same.

This is the result when I run it in the terminal
> ~$ arduino
Exception in thread "AWT-EventQueue-0" java.awt.HeadlessException
    at java.awt.GraphicsEnvironment.checkHeadless(GraphicsEnvironment.java:207)
    at java.awt.Window.<init>(Window.java:535)
    at java.awt.Frame.<init>(Frame.java:420)
    at java.awt.Frame.<init>(Frame.java:385)
    at javax.swing.JFrame.<init>(JFrame.java:174)
    at arduinopc.<init>(arduinopc.java:35)
    at arduinopc$3.run(arduinopc.java:85)
    at java.awt.event.InvocationEvent.dispatch(InvocationEvent.java:251)
    at java.awt.EventQueue.dispatchEventImpl(EventQueue.java:733)
    at java.awt.EventQueue.access$200(EventQueue.java:103)
    at java.awt.EventQueue$3.run(EventQueue.java:694)
    at java.awt.EventQueue$3.run(EventQueue.java:692)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.security.ProtectionDomain$1.doIntersectionPrivilege(ProtectionDomain.java:76)
    at java.awt.EventQueue.dispatchEvent(EventQueue.java:703)
    at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:242)
    at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:161)
    at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:150)
    at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:146)
    at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:138)
    at java.awt.EventDispatchThread.run(EventDispatchThread.java:91)
Exception in thread "main" java.lang.ExceptionInInitializerError
    at processing.app.Preferences.save(Preferences.java:735)
    at processing.app.Preferences.init(Preferences.java:249)
    at processing.app.Base.main(Base.java:117)
Caused by: java.awt.HeadlessException
    at sun.awt.HeadlessToolkit.getMenuShortcutKeyMask(HeadlessToolkit.java:234)
    at processing.core.PApplet.<clinit>(Unknown Source)
    ... 3 more


Please help me, this thing pissed me off a lot :((

---

