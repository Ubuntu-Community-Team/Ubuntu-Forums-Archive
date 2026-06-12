---
title: "Broken JRE"
date: 2007-02-02
forum: General Help
---

### Post by rgu on 2007-02-02
Hello,

I followed the instructions on installing java here: 
[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/java.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/java.html)

Whenever I go to a site with java in firefox, the browser locks up and needs restarted. When I go to the same site (with java) in epiphany, I get a "Java" page that just sits there (doesn't launch the app).

If anyone knows how to fix this, I'd be grateful for some help! :)

---

### Post by docetes on 2007-02-02
you can try use automatrix to install java.
It does everything for you

hope that helps,
Dave

---

### Post by rgu on 2007-02-02
> **docetes said:**
> you can try use automatrix to install java.
It does everything for you

hope that helps,
Dave

Cool package, it installed - but I get the same result. 

Browse to a page with a java app in it with firefox, and the browser crashes.

---

### Post by docetes on 2007-02-02
Are you using dapper or edgy? 
Maybe try and reinstall firefox 
or try another browser

---

### Post by phossal on 2007-02-02
Firefox will crash if the browser plugin is not properly installed. You might also have problems if you're running on a 64Bit platform.

I've had the most success installing the Java 6 SE JDK directly from SUN using the method laid out in the tutorial (included in my signature). However, the plugin .so which comes with the Java JRE, should still exist on your system if you're using version 5. 

Wherever your JRE is located, inside the folder is a plugin(s) folder. Inside that is the mozilla/firefox java plugin. You need to create a symbolic link to that file in the /usr/lib/firefox/plugin folder. 

Then, after restarting firefox, you should be rid of the problems. 

PM me if you need help.

---

