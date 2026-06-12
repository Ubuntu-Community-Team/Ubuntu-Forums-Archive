---
title: "Installing RSSowl on Dapper"
date: 2008-01-02
forum: General Help
---

### Post by y-lee on 2008-01-02
I tried to install RSSowl by following the directions at [Ubuntu Guide]("http://ubuntuguide.org/wiki/Dapper#How_to_install_RSS.2FRDF.2FAtom_Newsreader_.28RSSOwl.29")

I have Java(TM) Plug-in 1.5.0_13-b05 already installed in firefox.

Yet when i run RSSowl all I get is a splash screen and then it dies. Running it in the terminal gives:

```
Exception in thread "main" org.eclipse.swt.SWTException: i/o error (java.util.zip.ZipException: Deflated stream ends early.)
   at org.eclipse.swt.SWT.error(SWT.java:2942)
   at org.eclipse.swt.SWT.error(SWT.java:2866)
   at org.eclipse.swt.internal.image.GIFFileFormat.readID(GIFFileFormat.java:138)
   at org.eclipse.swt.internal.image.GIFFileFormat.getExtensions(GIFFileFormat.java:150)
   at org.eclipse.swt.internal.image.GIFFileFormat.loadFromByteStream(GIFFileFormat.java:124)
   at org.eclipse.swt.internal.image.FileFormat.loadFromStream(FileFormat.java:47)
   at org.eclipse.swt.internal.image.FileFormat.load(FileFormat.java:75)
   at org.eclipse.swt.graphics.ImageLoader.load(ImageLoader.java:126)
   at org.eclipse.swt.graphics.ImageDataLoader.load(ImageDataLoader.java:18)
   at org.eclipse.swt.graphics.ImageData.<init>(ImageData.java:327)
   at org.eclipse.swt.graphics.Image.<init>(Image.java:490)
   at net.sourceforge.rssowl.util.shop.PaintShop.loadImage(Unknown Source)
   at net.sourceforge.rssowl.util.shop.PaintShop.loadImage(Unknown Source)
   at net.sourceforge.rssowl.util.shop.PaintShop.initIcons(Unknown Source)
   at net.sourceforge.rssowl.controller.GUI.startUp(Unknown Source)
   at net.sourceforge.rssowl.controller.GUI.<init>(Unknown Source)
   at net.sourceforge.rssowl.controller.RSSOwlLoader.<init>(Unknown Source)
   at net.sourceforge.rssowl.controller.RSSOwlLoader.main(Unknown Source)
Caused by: java.util.zip.ZipException: Deflated stream ends early.
   at java.util.zip.InflaterInputStream.fill(libgcj.so.7)
   at java.util.zip.InflaterInputStream.read(libgcj.so.7)
   at java.util.zip.InflaterInputStream.read(libgcj.so.7)
   at java.io.FilterInputStream.read(libgcj.so.7)
   at java.util.jar.JarFile$EntryInputStream.read(libgcj.so.7)
   at org.eclipse.swt.internal.image.LEDataInputStream.read(LEDataInputStream.java:76)
   at org.eclipse.swt.internal.image.GIFFileFormat.readID(GIFFileFormat.java:134)
   ...15 more
```

I'm not sure what i need to do or what that means. Any help would be greatly appreciated.

---

### Post by dimbulb1024 on 2008-01-02
I'm not running dapper, but what I did was just download RSSOwl and then extracted it to a folder in my Home folder. I already had java installed so all I did was click on the RSSOwl excutable in the folder and it ran fine.
One thing that jumps out to me is my Java is a JRE install and not a Pluig-in install in Firefox. I needed the JRE for another program I run, so maybe that might be your issue.

---

### Post by y-lee on 2008-01-02
Nah I have Java installed. 

 I think this is my problem (from a Install.txt in the RSS owl directory):
 >  	The SWT library that is added to the RSSOwl project needs GTK 2 to run. Make sure that the *.so files are 	on your java.libary.path or any other path that java.exe may access.

i have libgtk installed but don't know anything about paths or setting checking or changing them.  The following *.so files are found in the directory i created for RSSowl (**/opt/rssowl_linux_1_1_3_bin**): ```
libswt-atk-gtk-3138.so    libswt-gtk-3138.so          libswt-pi-gtk-3138.so   libswt-gnome-gtk-3138.so  libswt-mozilla-gtk-3138.so 
```

---

### Post by y-lee on 2008-01-02
Also **dimbulb1024** I tried what you did and all i got was the same sort of errors. (ie download RSSOwl and then extracted it to a folder in my Home folder and click on the RSSOwl excutable in the folder)

---

### Post by dimbulb1024 on 2008-01-02
I tried :(

---

### Post by y-lee on 2008-01-03
Thanks for trying Dude.

---

