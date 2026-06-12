---
title: "Subsonic Java Problem"
date: 2008-03-24
forum: General Help
---

### Post by djh82uk on 2008-03-24
Hiya all

Im trying to get subsonic working, it works but I just cannot update any cover art for the albums, I get 2 different error messages in the log.

[2008-03-25 02:36:53,174] WARN CoverArtController - Failed to create thumbnail for /home/djh/samba/music/Sonics, the [1966] Boom/folder.jpg
java.lang.NoClassDefFoundError
	at com.sun.imageio.plugins.jpeg.JPEGImageReaderSpi.createReaderInstance(JPEGImageReaderSpi.java:89)
	at javax.imageio.spi.ImageReaderSpi.createReaderInstance(ImageReaderSpi.java:296)
	at javax.imageio.ImageIO$ImageReaderIterator.next(ImageIO.java:488)
	at javax.imageio.ImageIO$ImageReaderIterator.next(ImageIO.java:472)
	at javax.imageio.ImageIO.read(ImageIO.java:1397)
	at javax.imageio.ImageIO.read(ImageIO.java:1322)
	




I also get this error:



[2008-03-25 02:36:52,983] WARN CoverArtController - Failed to create thumbnail for /home/djh/samba/music/Robyn - Robyn (2007)/folder.jpg
java.lang.UnsatisfiedLinkError: /usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre/lib/i386/libawt.so: Can't load IA 32-bit .so on a IA 32-bit platform
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1668)
	at java.lang.Runtime.loadLibrary0(Runtime.java:822)


Ive shortened them a bit as the log is huge, it's just the same old stuff again.

Cany anyone help?

It was working fine, then It stopped working so I had to remove subsonic and re-install (removed /var/subsonic and put a new subsonic.war in webapps)

DJH

---

### Post by djh82uk on 2008-03-25
Anyone?  Im really stuck with this :(

DJH

---

### Post by phidia on 2008-03-25
Maybe there will be more ideas and help at the [subsonic forum]("http://www.activeobjects.no/subsonic/forum/").
Hope that helps.

---

### Post by djh82uk on 2008-03-25
yeh, no replies there either :(

DJH

---

