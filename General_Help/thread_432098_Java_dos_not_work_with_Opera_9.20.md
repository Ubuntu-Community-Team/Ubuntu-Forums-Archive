---
title: "Java dos not work with Opera 9.20"
date: 2007-05-03
forum: General Help
---

### Post by guliver on 2007-05-03
After upgrading to 7.04 and Opera 9.20 Java does not work no more.

When I click F12 in opera and click Enable Java it does not enable Java...


??????

Before upgrade it was working nice.

---

### Post by kerry_s on 2007-05-03
Did you check your java path. I'm using sun-6> /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/

---

### Post by guliver on 2007-05-03
When I try to validate that path it report it as incorrect.

---

### Post by kerry_s on 2007-05-03
What java you have?

---

### Post by guliver on 2007-05-03
This is command that I used to install Java:

```
sudo apt-get install flashplugin-nonfree sun-java6-plugin sun-java6-jre


```

---

### Post by kerry_s on 2007-05-03
I heard java-6 is broken in feisty, use synaptic search sun uninstall all the 6 and try the 5.

---

### Post by kpkeerthi on 2007-05-03
[This]("http://www.opera.com/linux/docs/plugins/install/#java") worked for me. I use jre5 though.

---

### Post by guliver on 2007-05-04
Thanks, Java 6 is working and this is proper Java path on my system:

```
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/
```

---

