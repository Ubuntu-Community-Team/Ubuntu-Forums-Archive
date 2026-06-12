---
title: "Where is Sun Java for Edgy?"
date: 2006-10-26
forum: General Help
---

### Post by Laterix on 2006-10-26
I can't find Sun Java from Edgy repositories? I have enabled universe, multiverse and back-ports. Are there still official packages for it?

---

### Post by beerfan on 2006-10-26
I don't know about Edgy specifically but the easiest way I could find to install sun java in Dapper was in the "Add/Remove" menu option and check the "commercial applications" box and then search for it. You might look there.

---

### Post by Laterix on 2006-10-26
> **beerfan said:**
> I don't know about Edgy specifically but the easiest way I could find to install sun java in Dapper was in the "Add/Remove" menu option and check the "commercial applications" box and then search for it. You might look there.

Thanks for the tip. It displays Runtime environment and plugin, but I would need JDK, because I'm writting some Java software. Maybe repository mirrors aren't fully synchronized yet.

---

### Post by jocko on 2006-10-26
> **Laterix said:**
> Thanks for the tip. It displays Runtime environment and plugin, but I would need JDK, because I'm writting some Java software. Maybe repository mirrors aren't fully synchronized yet.

There's a package named sun-java5-jdk in multiverse. Could that be it?

---

### Post by jdunn on 2006-10-26
I followed this:
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)
I only need Sun JRE and I can't get it to work on Firefox 2.0.  It doesn't show up in about:plugins.  It seems to work in Konqueror

*Update*
Never Mind.  I figured it out.  Install Sun Java and the java-browser-plugin from the repositories.  Makes sure that the plugin-package created a symlink in your '/usr/lib/firefox/plugins' directory called 'libjavaplugin.so -> /etc/alternatives/firefox-javaplugin.so'.  

If you are using Sun Java, the symlink leads to another symlink as follows:  
firefox-javaplugin.so -> /usr/lib/jvm/java-1.5.0-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so

Its a little convoluted.  In any case, do not copy the plugin directly to your 'usr/lib/firefox/plugins/' directory.

---

### Post by Laterix on 2006-10-27
Yep, Problem solved. I changed my default repository mirrors to new ones.

---

