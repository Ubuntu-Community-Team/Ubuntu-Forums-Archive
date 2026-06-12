---
title: "Azureus: &quot;An unhandled Error occured in the GUI.&quot;"
date: 2007-11-11
forum: General Help
---

### Post by leev on 2007-11-11
**Update:** It looks like the problem was resolved temporarily.
The plugins section in the options menu was usable and the column setup window was no longer blank.

I thought it was fixed, but it wasn't. The problem came back when I restarted Azureus. :(

==========================================

Azureus keeps reporting the following error every time I click on the "Plugins" option in the menu.

```
[alert] Alert:3:An unhandled Error occured in the GUI. Consecutive faults may occur -
DEBUG::Sun Nov 11 04:50:46 GMT 2007::org.gudy.azureus2.ui.swt.mainwindow.SWTThread::<init>::170:
  java.lang.ArrayIndexOutOfBoundsException: -1
        at java.util.Arrays$ArrayList.get(Arrays.java:3381)
        at org.gudy.azureus2.ui.swt.views.configsections.ConfigSectionPlugins$8.handleEvent(ConfigSectionPlugins.java:509)
        at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:66)
        at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1101)
        at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1125)
        at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1110)
        at org.eclipse.swt.widgets.Table.checkData(Table.java:273)
        at org.eclipse.swt.widgets.Table.cellDataProc(Table.java:210)
        at org.eclipse.swt.widgets.Display.cellDataProc(Display.java:698)
        at org.eclipse.swt.internal.gtk.OS._gtk_list_store_append(Native Method)
        at org.eclipse.swt.internal.gtk.OS.gtk_list_store_append(OS.java:5458)
        at org.eclipse.swt.widgets.Table.setItemCount(Table.java:2940)
        at org.gudy.azureus2.ui.swt.views.configsections.ConfigSectionPlugins.configSectionCreate(ConfigSectionPlugins.java:555)
        at org.gudy.azureus2.ui.swt.views.ConfigView.ensureSectionBuilt(ConfigView.java:590)
        at org.gudy.azureus2.ui.swt.views.ConfigView.showSection(ConfigView.java:551)
        at org.gudy.azureus2.ui.swt.views.ConfigView.access$000(ConfigView.java:58)
        at org.gudy.azureus2.ui.swt.views.ConfigView$4.widgetSelected(ConfigView.java:252)
        at org.eclipse.swt.widgets.TypedListener.handleEvent(TypedListener.java:227)
        at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:66)
        at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1101)
        at org.eclipse.swt.widgets.Display.runDeferredEvents(Display.java:3319)
        at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:2971)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init>(SWTThread.java:156)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThread.java:68)
        at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.java:102)
        at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:80)
        at org.gudy.azureus2.ui.swt.Main.main(Main.java:203)


(SWT:15443): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width 250 and height -1

```

I've tried to fix it, but nothing seems to work.
Here's what didn't work:
1. Reinstalling from the repos.
2. Installing 3.0.3.4 and 3.0.3.5-B11 from the official Azureus website.
3. Deleting ~/.azureus
4. Reinstalling Java
5. Installing azureus-gcj
6. Replacing swt.jar with a newer version from the Eclipse website.
 
This problem started after I installed Gusty; I was using Edgy before this and everything was working perfectly. 

Most everything else in Azureus works fine. Well, except for when I click "column setup." The column setup window opens, but contains no text. I'll post a screenshot if requested.
I searched for a solution on the forums and also searched using Google with no luck. 

Additional information:
Using Java from the repositories.
java version "1.6.0_03"

---

### Post by leev on 2007-11-11
OK, I installed the version from GetDeb to see if it gives me the same error. (Yes, I know it's the same as the version on the Azureus website.) And of course, it gave me the same error. Any version I try will give me this error. So it is obviously my system, right? 

Is anyone else having this problem too? It'd be nice to get this fixed or at least figure out why this is happening in the first place.

---

