---
title: "Java is not working anymore after Firefox 2.0 was installed"
date: 2006-10-26
forum: General Help
---

### Post by Marcos.Rufino on 2006-10-26
I've just installed Firefox 2.0 but I can't figure out how to make the java plugin works. I still has Firefox 1.5 and java works well within it but not with the new Firefox.

The method I used to install Firefox 2.0 was to copy the untared folder to /opt/ and then execute the firefox file. This method is nice to me because I don't need to uninstall Firefox 1.5, which is necessary for some applications to work properly in Ubuntu.

Anyone know how can I enable java in Firefox 2.0? I already tried to create a symbolic link with java inside the ~/mozilla/plugins and the /opt/firefox folders but it doesn't work. (with the command "ln -s /usr/java/jre1.5.0/plugin/i386/ns7/libjavaplugin_oji.so .")

Thanks.

---

### Post by orbital on 2006-10-31
I now have the same exact problem. Is there any way to get it fixed?

---

### Post by orsula on 2006-10-31
Try to install automatix2 and use it for (among other goodies..) to install the Sun Java 1.5 JRE . It seemed to have helped me. Before I did that, firefox 2 crashed unless I had the 'enable javascript' box NOT checked. When it was checked it crashed. This installation is ,so far working. 
Automatix2 is also great for a host of other things..([www.getautomatix.com](www.getautomatix.com))

---

### Post by traneHead on 2006-10-31
I couldn't get it working either, but then i did the following:
* Exit ff
* $ sudo rm /usr/lib/firefox/plugins/libjava*
* $ sudo ln -s /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins/
* start ff

Check your users plugin directory also and remove any javaplugins there (/home/xxx/.mozilla/plugins) if any.
You can verify if it's working at [http://java.com/sv/download/installed.jsp?detect=jre](http://java.com/sv/download/installed.jsp?detect=jre)

---

### Post by Marcos.Rufino on 2006-10-31
> **traneHead said:**
> I couldn't get it working either, but then i did the following:
* Exit ff
* $ sudo rm /usr/lib/firefox/plugins/libjava*
* $ sudo ln -s /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins/
* start ff


Thank you traneHead. I'd followed your steps and they solved my problem.

---

