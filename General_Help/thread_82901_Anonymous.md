---
title: "Anonymous"
date: 2005-10-27
forum: General Help
---

### Post by Nomearod on 2005-10-27
Hi.

I'm using Ubuntu Breezy and I would like to know who can I surf anonymous. I think that I need to use a proxy, if so, how can I do it? I installed a program called Tor, but don't know how to start it... In the Aplication menu, it does not appear...

Thanks for the help people.

---

### Post by mykey on 2005-10-27
check out [JAP]("http://anon.inf.tu-dresden.de/index_en.html")

---

### Post by Nomearod on 2005-10-28
[QUOTE=mykey]check out [JAP]("http://anon.inf.tu-dresden.de/index_en.html")[/QUOTE]

[http://www.infoanarchy.org/story/2003/8/21/18286/7468](http://www.infoanarchy.org/story/2003/8/21/18286/7468)

As you can read in this site, Jap isn't very "anonymous":( 

Anyone can help?

---

### Post by mykey on 2005-10-28
look at the date of the post it's of Fri Aug 22nd, 2003 - there has been a court case on one of the top german courts meanwhile which confirmed the right for anonymity and was a major blow for the crime-busters - since then it has been extended and is supposed to run the network as originally intended in the near future (check their site) .. more universities are joining .. I would not know of a better system right now but feel free to introduce one to me.

---

### Post by Juda$ on 2005-11-08
JAP is a great program I use it for Windows all the time but I am having trouble in ubuntu (Breezy Badger).  I have Java version 1.4.2 and I have follwed the instructions on the JAP homepage   [http://anon.inf.tu-dresden.de/others/download_en.html](http://anon.inf.tu-dresden.de/others/download_en.html)

when I go to run jap from a terminal  as my self or using sudo   this messge comes up 


:~/JAP$ java -jar JAP.jar
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit() (/usr/lib/libgcj.so.6.0.0)
   at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment() (/usr/lib/libgcj.so.6.0.0)
   at java.awt.Window.Window(java.awt.Window, java.awt.GraphicsConfiguration) (/usr/lib/libgcj.so.6.0.0)
   at java.awt.Window.Window(java.awt.Frame) (/usr/lib/libgcj.so.6.0.0)
   at jap.JAPSplash.JAPSplash(java.awt.Frame) (Unknown Source)
   at JAP.startJAP() (Unknown Source)
   at JAP.main(java.lang.String[]) (Unknown Source)
   at gnu.java.lang.MainThread.call_main() (/usr/lib/libgcj.so.6.0.0)
   at gnu.java.lang.MainThread.run() (/usr/lib/libgcj.so.6.0.0)
Caused by: java.lang.ClassNotFoundException: gnu.java.awt.peer.gtk.GtkToolkit not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:JAP.jar,file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String, boolean) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.forName(java.lang.String, boolean, java.lang.ClassLoader) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.forName(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.awt.Toolkit.getDefaultToolkit() (/usr/lib/libgcj.so.6.0.0)
   ...8 more

I do not understand this and I am fairly new to Linux / Ubuntu if I can get this to work it will speed my move away from windows   

thankyou for any suggestions.

---

### Post by stimpack on 2005-11-23
Ive just install tor too, I guess youve figured it out, that it runs automatically, default socks port is 9050. 
/etc/tor/torrc is the config file to change port etc..

Pretty neat, fooled grc.com

---

