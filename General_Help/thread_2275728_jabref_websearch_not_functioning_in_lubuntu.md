---
title: "jabref websearch not functioning in lubuntu"
date: 2015-04-28
forum: General Help
---

### Post by sn0m on 2015-04-28
Hi Guys
Jabref dosen't do any online search anymore after the last update.
I am a doctor and jabref is essential to my work, so right now i feel completely handicapped.
this is what i get from command line:
koli@koli-N250P-N145P:~$ jabref 
log4j:WARN No appenders could be found for logger (org.java.plugin.ObjectFactory).
log4j:WARN Please initialize the log4j system properly.
log4j:WARN See [http://logging.apache.org/log4j/1.2/faq.html#noconfig](http://logging.apache.org/log4j/1.2/faq.html#noconfig) for more info.
Found 2 plugin(s):
  - net.sf.jabref.core (jar:file:/usr/share/jabref/JabRef-2.10b2.jar!/plugins/net.sf.jabref.core/plugin.xml)
  - net.sf.jabref.export.misq (jar:file:/usr/share/jabref/JabRef-2.10b2.jar!/plugins/net.sf.jabref.export.misq/plugin.xml)

Could not get key binding for "Open folder"

The websearch can also be started by pressing F5 but when I do that, nothing happens, no even any output in terminal which makes me think this is some sort of policy blocking websearch.
I had a look online and one suggested downgrading java to version 6 from 7 but if I do that, the whole thing dosen't start at all.
Can anyone help me kickstart the websearch again???
Many thanks
Sokol

---

### Post by dragonfly41 on 2015-04-28
Found similar symptoms here .. searched ..

```
log4j:WARN No appenders could be found for logger (org.java.plugin.ObjectFactory).
```

[http://superuser.com/questions/497241/jabref-will-not-start](http://superuser.com/questions/497241/jabref-will-not-start)

Recommendation from above .. Use Oracle's JRE.

---

### Post by vasa1 on 2015-04-28
> **dragonfly41 said:**
> ...
Recommendation from above .. Use Oracle's JRE.
+1
And this was a painless way for me: [http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html](http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html)

---

### Post by sn0m on 2015-04-28
Hi guys, thanks for your help. I am not the most tech-savy out there so bear with me.
I've installed oracles java 8 (thank you vasa1) but still no joy.
This is what I get so far:
koli@koli-N250P-N145P:~$ java -version
java version "1.8.0_45"
Java(TM) SE Runtime Environment (build 1.8.0_45-b14)
Java HotSpot(TM) Server VM (build 25.45-b02, mixed mode)
koli@koli-N250P-N145P:~$ java -jar Downloads/JabRef-2.10.jar 
Found 2 plugin(s):
  - net.sf.jabref.export.misq (jar:file:/home/koli/Downloads/JabRef-2.10.jar!/plugins/net.sf.jabref.export.misq/plugin.xml)
  - net.sf.jabref.core (jar:file:/home/koli/Downloads/JabRef-2.10.jar!/plugins/net.sf.jabref.core/plugin.xml)

Could not get key binding for "Open folder"
koli@koli-N250P-N145P:~$ 

When jabref graphical interface comes on, still no joy with websearch. I also installed oracles java 6 and java 7 run-times and toggled between all three but still couldn't make it work.
Any more guidance/help will be greatly appreciated.
Many thanks
Sokol

---

### Post by sn0m on 2015-04-29
Hi everyone.
I managed to get it working again, or more precisely I sorted out my cockup.
Apparently a new database need to be open or an existing one before one can do websearch!!!!!!
I appreciate and thank all of you who tried to help me out.
Many thanks
Sokol

---

