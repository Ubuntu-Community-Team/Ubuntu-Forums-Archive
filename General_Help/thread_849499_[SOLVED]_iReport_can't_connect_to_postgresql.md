---
title: "[SOLVED] iReport can't connect to postgresql"
date: 2008-07-04
forum: General Help
---

### Post by Mateo on 2008-07-04
This is the error I get.  Google isn't much help.  I **do** have the libpg-java package installed.

```


Exception
 

Message:
    java.lang.ClassNotFoundException: org.postgresql.Driver
Level:
    SEVERE
Stack Trace:
    it.businesslogic.ireport.connection.DriverPool.registerDriver(DriverPool.java:155)
    it.businesslogic.ireport.connection.JDBCConnection.getConnection(JDBCConnection.java:90)
    it.businesslogic.ireport.connection.JDBCConnection.test(JDBCConnection.java:404)
    it.businesslogic.ireport.connection.gui.ConnectionDialog.jButtonTestActionPerformed(ConnectionDialog.java:322)
    it.businesslogic.ireport.connection.gui.ConnectionDialog.access$300(ConnectionDialog.java:24)
    it.businesslogic.ireport.connection.gui.ConnectionDialog$4.actionPerformed(ConnectionDialog.java:274)
    javax.swing.AbstractButton.fireActionPerformed(AbstractButton.java:1995)
    javax.swing.AbstractButton$Handler.actionPerformed(AbstractButton.java:2318)
    javax.swing.DefaultButtonModel.fireActionPerformed(DefaultButtonModel.java:387)
    javax.swing.DefaultButtonModel.setPressed(DefaultButtonModel.java:242)
    javax.swing.plaf.basic.BasicButtonListener.mouseReleased(BasicButtonListener.java:236)
    java.awt.Component.processMouseEvent(Component.java:6041)
    javax.swing.JComponent.processMouseEvent(JComponent.java:3265)
    java.awt.Component.processEvent(Component.java:5806)
    java.awt.Container.processEvent(Container.java:2058)
    java.awt.Component.dispatchEventImpl(Component.java:4413)
    java.awt.Container.dispatchEventImpl(Container.java:2116)
    java.awt.Component.dispatchEvent(Component.java:4243)
    java.awt.LightweightDispatcher.retargetMouseEvent(Container.java:4322)
    java.awt.LightweightDispatcher.processMouseEvent(Container.java:3986)
    java.awt.LightweightDispatcher.dispatchEvent(Container.java:3916)
    java.awt.Container.dispatchEventImpl(Container.java:2102)
    java.awt.Window.dispatchEventImpl(Window.java:2440)
    java.awt.Component.dispatchEvent(Component.java:4243)
    java.awt.EventQueue.dispatchEvent(EventQueue.java:599)
    java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:273)
    java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:183)
    java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:177)
    java.awt.Dialog$1.run(Dialog.java:1045)
    java.awt.Dialog$3.run(Dialog.java:1097)
    java.security.AccessController.doPrivileged(Native Method)
    java.awt.Dialog.show(Dialog.java:1095)
    java.awt.Component.show(Component.java:1422)
    java.awt.Component.setVisible(Component.java:1375)
    java.awt.Window.setVisible(Window.java:806)
    java.awt.Dialog.setVisible(Dialog.java:985)
    it.businesslogic.ireport.gui.ConnectionsDialog.jButtonModifyParameterActionPerformed(ConnectionsDialog.java:514)
    it.businesslogic.ireport.gui.ConnectionsDialog.access$300(ConnectionsDialog.java:53)
    it.businesslogic.ireport.gui.ConnectionsDialog$7.actionPerformed(ConnectionsDialog.java:232)
    javax.swing.AbstractButton.fireActionPerformed(AbstractButton.java:1995)
    javax.swing.AbstractButton$Handler.actionPerformed(AbstractButton.java:2318)
    javax.swing.DefaultButtonModel.fireActionPerformed(DefaultButtonModel.java:387)
    javax.swing.DefaultButtonModel.setPressed(DefaultButtonModel.java:242)
    javax.swing.plaf.basic.BasicButtonListener.mouseReleased(BasicButtonListener.java:236)
    java.awt.Component.processMouseEvent(Component.java:6041)
    javax.swing.JComponent.processMouseEvent(JComponent.java:3265)
    java.awt.Component.processEvent(Component.java:5806)
    java.awt.Container.processEvent(Container.java:2058)
    java.awt.Component.dispatchEventImpl(Component.java:4413)
    java.awt.Container.dispatchEventImpl(Container.java:2116)
    java.awt.Component.dispatchEvent(Component.java:4243)
    java.awt.LightweightDispatcher.retargetMouseEvent(Container.java:4322)
    java.awt.LightweightDispatcher.processMouseEvent(Container.java:3986)
    java.awt.LightweightDispatcher.dispatchEvent(Container.java:3916)
    java.awt.Container.dispatchEventImpl(Container.java:2102)
    java.awt.Window.dispatchEventImpl(Window.java:2440)
    java.awt.Component.dispatchEvent(Component.java:4243)
    java.awt.EventQueue.dispatchEvent(EventQueue.java:599)
    java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:273)
    java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:183)
    java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:177)
    java.awt.Dialog$1.run(Dialog.java:1045)
    java.awt.Dialog$3.run(Dialog.java:1097)
    java.security.AccessController.doPrivileged(Native Method)
    java.awt.Dialog.show(Dialog.java:1095)
    java.awt.Component.show(Component.java:1422)
    java.awt.Component.setVisible(Component.java:1375)
    java.awt.Window.setVisible(Window.java:806)
    java.awt.Dialog.setVisible(Dialog.java:985)
    it.businesslogic.ireport.gui.ConnectionsDialog.setVisible(ConnectionsDialog.java:623)
    it.businesslogic.ireport.gui.MainFrame.jMenuItemConnectionsActionPerformed(MainFrame.java:6276)
    it.businesslogic.ireport.gui.MainFrame.access$13800(MainFrame.java:101)
    it.businesslogic.ireport.gui.MainFrame$175.actionPerformed(MainFrame.java:3606)
    javax.swing.AbstractButton.fireActionPerformed(AbstractButton.java:1995)
    javax.swing.AbstractButton$Handler.actionPerformed(AbstractButton.java:2318)
    javax.swing.DefaultButtonModel.fireActionPerformed(DefaultButtonModel.java:387)
    javax.swing.DefaultButtonModel.setPressed(DefaultButtonModel.java:242)
    javax.swing.AbstractButton.doClick(AbstractButton.java:357)
    javax.swing.plaf.basic.BasicMenuItemUI.doClick(BasicMenuItemUI.java:1220)
    javax.swing.plaf.basic.BasicMenuItemUI$Handler.menuDragMouseReleased(BasicMenuItemUI.java:1324)
    javax.swing.JMenuItem.fireMenuDragMouseReleased(JMenuItem.java:568)
    javax.swing.JMenuItem.processMenuDragMouseEvent(JMenuItem.java:465)
    javax.swing.JMenuItem.processMouseEvent(JMenuItem.java:411)
    javax.swing.MenuSelectionManager.processMouseEvent(MenuSelectionManager.java:304)
    javax.swing.plaf.basic.BasicPopupMenuUI$MouseGrabber.eventDispatched(BasicPopupMenuUI.java:807)
    java.awt.Toolkit$SelectiveAWTEventListener.eventDispatched(Toolkit.java:2360)
    java.awt.Toolkit$ToolkitEventMulticaster.eventDispatched(Toolkit.java:2252)
    java.awt.Toolkit.notifyAWTEventListeners(Toolkit.java:2210)
    java.awt.Component.dispatchEventImpl(Component.java:4311)
    java.awt.Container.dispatchEventImpl(Container.java:2116)
    java.awt.Component.dispatchEvent(Component.java:4243)
    java.awt.LightweightDispatcher.retargetMouseEvent(Container.java:4322)
    java.awt.LightweightDispatcher.processMouseEvent(Container.java:3986)
    java.awt.LightweightDispatcher.dispatchEvent(Container.java:3916)
    java.awt.Container.dispatchEventImpl(Container.java:2102)
    java.awt.Window.dispatchEventImpl(Window.java:2440)
    java.awt.Component.dispatchEvent(Component.java:4243)
    java.awt.EventQueue.dispatchEvent(EventQueue.java:599)
    java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:273)
    java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:183)
    java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:173)
    java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:168)
    java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:160)
    java.awt.EventDispatchThread.run(EventDispatchThread.java:121)
```

---

### Post by Mateo on 2008-07-04
figured it out. didn't have my classpath set correctly.

---

