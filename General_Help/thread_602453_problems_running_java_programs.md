---
title: "problems running java programs"
date: 2007-11-04
forum: General Help
---

### Post by popformula on 2007-11-04
I'm running Gutsy x64 on a Macbook C2D. I've got the Sun Java 6 runtime installed, as well as the default gij-4.2.

I've been using "sudo update-alternatives --config java to choose between the different providers.

With gij-4.2 selected, Azureus runs fine but DimSum ([www.mandarintools.com](www.mandarintools.com)) doesn't even start, just giving these errors:

```
joe@ubuntubook:~/Desktop$ java -jar DimSum.jar
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.81)
   at javax.swing.plaf.basic.BasicLookAndFeel.initialize(libgcj.so.81)
   at javax.swing.UIManager.setLookAndFeel(libgcj.so.81)
   at javax.swing.UIManager.<clinit>(libgcj.so.81)
   at java.lang.Class.initializeClass(libgcj.so.81)
   at Annotator.main(Annotator.java:6326)
Caused by: java.lang.UnsatisfiedLinkError: libgtkpeer: libgtkpeer.so: cannot open shared object file: No such file or directory
   at java.lang.Runtime._load(libgcj.so.81)
   at java.lang.Runtime.loadLibrary(libgcj.so.81)
   at java.lang.System.loadLibrary(libgcj.so.81)
   at gnu.java.awt.peer.gtk.GtkToolkit.<clinit>(libgcj.so.81)
   at java.lang.Class.initializeClass(libgcj.so.81)
   at java.lang.Class.forName(libgcj.so.81)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.81)
   ...5 more
```


With Sun Java 6 selected:
Azureus closes as soon as it opens, if run from the launcher. If run by typing "azureus" in the terminal, it stays running for as long as the terminal window is open.

DimSum ([www.mandarintools.com](www.mandarintools.com)) freezes at the splash screen if run from the launcher. Running from the terminal gives a long output about all the fonts it's loading and then this error message:

```
Starting dictionary
Resetting props

(<unknown>:8013): Gtk-WARNING **: Attempting to add a widget with type GtkButton to a GtkComboBoxEntry (need an instance of GtkEntry or of a subclass)

(<unknown>:8013): Gtk-CRITICAL **: gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed
Starting flashcards
Resetting props
```

and then
```

Exception in thread "AWT-XAWT" java.lang.OutOfMemoryError: Java heap space
        at java.util.logging.LogRecord.<clinit>(LogRecord.java:52)
        at java.util.logging.Logger.log(Logger.java:581)
        at sun.awt.X11.XToolkit.processException(XToolkit.java:493)
        at sun.awt.X11.XToolkit.run(XToolkit.java:590)
        at sun.awt.X11.XToolkit.run(XToolkit.java:519)
        at java.lang.Thread.run(Thread.java:619)
Exception in thread "main" java.lang.OutOfMemoryError: Java heap space
        at java.lang.AbstractStringBuilder.<init>(AbstractStringBuilder.java:45)
        at java.lang.StringBuilder.<init>(StringBuilder.java:68)
        at java.awt.Component.addMouseWheelListener(Component.java:5343)
        at javax.swing.plaf.basic.BasicScrollPaneUI.installListeners(BasicScrollPaneUI.java:151)
        at javax.swing.plaf.synth.SynthScrollPaneUI.installListeners(SynthScrollPaneUI.java:93)
        at javax.swing.plaf.basic.BasicScrollPaneUI.installUI(BasicScrollPaneUI.java:187)
        at javax.swing.JComponent.setUI(JComponent.java:673)
        at javax.swing.JScrollPane.setUI(JScrollPane.java:365)
        at javax.swing.JScrollPane.updateUI(JScrollPane.java:378)
        at javax.swing.JScrollPane.<init>(JScrollPane.java:290)
        at javax.swing.plaf.basic.BasicComboPopup.createScroller(BasicComboPopup.java:541)
        at javax.swing.plaf.basic.BasicComboPopup.<init>(BasicComboPopup.java:316)
        at javax.swing.plaf.synth.SynthComboPopup.<init>(SynthComboPopup.java:28)
        at javax.swing.plaf.synth.SynthComboBoxUI.createPopup(SynthComboBoxUI.java:97)
        at javax.swing.plaf.basic.BasicComboBoxUI.installUI(BasicComboBoxUI.java:217)
        at javax.swing.JComponent.setUI(JComponent.java:673)
        at javax.swing.JComboBox.setUI(JComboBox.java:238)
        at javax.swing.JComboBox.updateUI(JComboBox.java:247)
        at javax.swing.JComboBox.init(JComboBox.java:212)
        at javax.swing.JComboBox.<init>(JComboBox.java:164)
        at com.sun.java.swing.plaf.gtk.GTKFileChooserUI.installComponents(GTKFileChooserUI.java:543)
        at javax.swing.plaf.basic.BasicFileChooserUI.installUI(BasicFileChooserUI.java:136)
        at sun.swing.plaf.synth.SynthFileChooserUI.installUI(SynthFileChooserUI.java:122)
        at com.sun.java.swing.plaf.gtk.GTKFileChooserUI.installUI(GTKFileChooserUI.java:464)
        at javax.swing.JComponent.setUI(JComponent.java:673)
        at javax.swing.JFileChooser.updateUI(JFileChooser.java:1762)
        at javax.swing.JFileChooser.setup(JFileChooser.java:360)
        at javax.swing.JFileChooser.<init>(JFileChooser.java:333)
        at javax.swing.JFileChooser.<init>(JFileChooser.java:286)
        at Annotator.<init>(Annotator.java:435)
        at Annotator.main(Annotator.java:6359)
```

DimSum runs fine on OS X and on my Windows XP box... any ideas what the problem is, how to get around it? Is it the x64 architecture?

---

### Post by mali2297 on 2007-11-04
> **popformula said:**
> I'm running Gutsy x64 on a Macbook C2D. I've got the Sun Java 6 runtime installed, as well as the default gij-4.2.

I've been using "sudo update-alternatives --config java to choose between the different providers.

With gij-4.2 selected, Azureus runs fine but DimSum ([www.mandarintools.com](www.mandarintools.com)) doesn't even start, just giving these errors:

```
joe@ubuntubook:~/Desktop$ java -jar DimSum.jar
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.81)
   at javax.swing.plaf.basic.BasicLookAndFeel.initialize(libgcj.so.81)
   at javax.swing.UIManager.setLookAndFeel(libgcj.so.81)
   at javax.swing.UIManager.<clinit>(libgcj.so.81)
   at java.lang.Class.initializeClass(libgcj.so.81)
   at Annotator.main(Annotator.java:6326)
Caused by: java.lang.UnsatisfiedLinkError: libgtkpeer: libgtkpeer.so: cannot open shared object file: No such file or directory
   at java.lang.Runtime._load(libgcj.so.81)
   at java.lang.Runtime.loadLibrary(libgcj.so.81)
   at java.lang.System.loadLibrary(libgcj.so.81)
   at gnu.java.awt.peer.gtk.GtkToolkit.<clinit>(libgcj.so.81)
   at java.lang.Class.initializeClass(libgcj.so.81)
   at java.lang.Class.forName(libgcj.so.81)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.81)
   ...5 more
```

There exists a package called [classpath-gtkpeer]("http://packages.ubuntu.com/gutsy/libs/classpath-gtkpeer"), you could try again after installing that.

> 
With Sun Java 6 selected:
Azureus closes as soon as it opens, if run from the launcher. If run by typing "azureus" in the terminal, it stays running for as long as the terminal window is open.

Type
```

azureus &
disown

```
Then you should be able to close terminal without stopping Azureus. You could also check what command the launcher use and change it.

> 
DimSum ([www.mandarintools.com](www.mandarintools.com)) freezes at the splash screen if run from the launcher. Running from the terminal gives a long output about all the fonts it's loading and then this error message:

```
Starting dictionary
Resetting props

(<unknown>:8013): Gtk-WARNING **: Attempting to add a widget with type GtkButton to a GtkComboBoxEntry (need an instance of GtkEntry or of a subclass)

(<unknown>:8013): Gtk-CRITICAL **: gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed
Starting flashcards
Resetting props
```

and then
```

Exception in thread "AWT-XAWT" java.lang.OutOfMemoryError: Java heap space
        at java.util.logging.LogRecord.<clinit>(LogRecord.java:52)
        at java.util.logging.Logger.log(Logger.java:581)
        at sun.awt.X11.XToolkit.processException(XToolkit.java:493)
        at sun.awt.X11.XToolkit.run(XToolkit.java:590)
        at sun.awt.X11.XToolkit.run(XToolkit.java:519)
        at java.lang.Thread.run(Thread.java:619)
Exception in thread "main" java.lang.OutOfMemoryError: Java heap space
        at java.lang.AbstractStringBuilder.<init>(AbstractStringBuilder.java:45)
        at java.lang.StringBuilder.<init>(StringBuilder.java:68)
        at java.awt.Component.addMouseWheelListener(Component.java:5343)
        at javax.swing.plaf.basic.BasicScrollPaneUI.installListeners(BasicScrollPaneUI.java:151)
        at javax.swing.plaf.synth.SynthScrollPaneUI.installListeners(SynthScrollPaneUI.java:93)
        at javax.swing.plaf.basic.BasicScrollPaneUI.installUI(BasicScrollPaneUI.java:187)
        at javax.swing.JComponent.setUI(JComponent.java:673)
        at javax.swing.JScrollPane.setUI(JScrollPane.java:365)
        at javax.swing.JScrollPane.updateUI(JScrollPane.java:378)
        at javax.swing.JScrollPane.<init>(JScrollPane.java:290)
        at javax.swing.plaf.basic.BasicComboPopup.createScroller(BasicComboPopup.java:541)
        at javax.swing.plaf.basic.BasicComboPopup.<init>(BasicComboPopup.java:316)
        at javax.swing.plaf.synth.SynthComboPopup.<init>(SynthComboPopup.java:28)
        at javax.swing.plaf.synth.SynthComboBoxUI.createPopup(SynthComboBoxUI.java:97)
        at javax.swing.plaf.basic.BasicComboBoxUI.installUI(BasicComboBoxUI.java:217)
        at javax.swing.JComponent.setUI(JComponent.java:673)
        at javax.swing.JComboBox.setUI(JComboBox.java:238)
        at javax.swing.JComboBox.updateUI(JComboBox.java:247)
        at javax.swing.JComboBox.init(JComboBox.java:212)
        at javax.swing.JComboBox.<init>(JComboBox.java:164)
        at com.sun.java.swing.plaf.gtk.GTKFileChooserUI.installComponents(GTKFileChooserUI.java:543)
        at javax.swing.plaf.basic.BasicFileChooserUI.installUI(BasicFileChooserUI.java:136)
        at sun.swing.plaf.synth.SynthFileChooserUI.installUI(SynthFileChooserUI.java:122)
        at com.sun.java.swing.plaf.gtk.GTKFileChooserUI.installUI(GTKFileChooserUI.java:464)
        at javax.swing.JComponent.setUI(JComponent.java:673)
        at javax.swing.JFileChooser.updateUI(JFileChooser.java:1762)
        at javax.swing.JFileChooser.setup(JFileChooser.java:360)
        at javax.swing.JFileChooser.<init>(JFileChooser.java:333)
        at javax.swing.JFileChooser.<init>(JFileChooser.java:286)
        at Annotator.<init>(Annotator.java:435)
        at Annotator.main(Annotator.java:6359)
```

DimSum runs fine on OS X and on my Windows XP box... any ideas what the problem is, how to get around it? Is it the x64 architecture?

I don't know. I suggest you search the [x64 forum]("http://ubuntuforums.org/forumdisplay.php?f=134") on how to get Sun Java to work on that architecture.

---

### Post by kaaredump on 2008-05-30
I get the same error on my ThinkPad T60 running Ubuntu 8.04 and Sun-Java 6.0 (don't think it's a 64bits only problem)

Get the error: 
```
(<unknown>:15695): Gtk-WARNING **: Attempting to add a widget with type GtkButton to a GtkComboBoxEntry (need an instance of GtkEntry or of a subclass)

(<unknown>:15695): Gtk-CRITICAL **: gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed

(<unknown>:15695): Gtk-CRITICAL **: gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(<unknown>:15695): Gtk-CRITICAL **: gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(<unknown>:15695): Gtk-CRITICAL **: gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(<unknown>:15695): Gtk-CRITICAL **: gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed

```
And the "file filter box" dont' get drawn properly! 
The app keeps running, and the error re-occurrs every time i open a JFileChooser!

I wrote the app myself, and have not yet tested it on other platforms.

Ran my app in Sun JDK 5.0 and 6.0.... same errors!
Then i opened it in OpenJDK, and everything worked fine, no errors, and the filechooser was drawn just fine!

---

