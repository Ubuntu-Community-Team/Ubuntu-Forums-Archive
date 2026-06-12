---
title: "Java Plugin for Opera?"
date: 2005-04-27
forum: General Help
---

### Post by rockett15 on 2005-04-27
I have sun-j2re1.5 installed and Opera 8, however java is still showing as not installed in Opera. It works in firefox and I even tried creating a symbolic link from the plugin file to /usr/lib/opera/plugins and still no luck.

Anyone know how to get it to work?

---

### Post by defkewl on 2005-04-27
Did you install opera first or the other way around?

---

### Post by alx23 on 2005-04-27
This is what I had to do to get it working:

[list=1]
[*]Open Tools->Preferences
[*]Choose the 'Advanced' tab, and the 'Content' item off this tab.
[*]Check the 'Enable Java' box, then press the 'Java Options' button
[*]Enter/browse to the correct path for Java - on my machine it's /usr/lib/sun-j2sdk1.5.0/jre/lib/i386
[*]Press the 'Validate Java path' button to ensure the path works
[*]OK out of preferences and restart Opera.
[/list] 

If Tools->Advanced->Java console brings up the console, you're in business.

---

### Post by rockett15 on 2005-04-28
\\:D/  Thanks :) if only i'd known it was that easy :P

---

### Post by Woocash on 2005-05-18
I've got java installed exactly as in ubuntuguide and opera installed from ubuntu deb package. Succesfuly configured for Opera as shown before.

I'm observing a little problem that when I have an applet loaded and i'm entering characters from keyboard into applet window -- I cannot write anything in any other opera tab... I cannot even edit url of the page on wich the applet is located.
When I close the tab with java applet -- everything is back to work.

Have you observed sth like this ?

---

### Post by WSmart on 2008-01-21
/usr/lib/jvm/java-7-icedtea/jre/lib/i386

Great Post alx23!  That was as refreshing as a cup of iced tea.  Speaking of which, my directory path was a little different, but not much.

---

### Post by TheExplorer on 2008-01-21
Well, everything seems to be fine with Opera under Ubuntu including Java. But there is only one thing that annoys me and that is flash. Actually, there is no flash version for Opera, only for Mozilla and they offer to make a symbolic link into Opera plugins. Having done this I still get a crash log in /var/crash. It points to a faulty Opera plugin wrapper. It doesn't affect my browsing and I see flash animations though. Just wondering why there is a crash log? :)

---

