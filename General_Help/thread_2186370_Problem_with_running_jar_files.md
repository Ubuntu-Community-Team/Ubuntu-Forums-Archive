---
title: "Problem with running jar files"
date: 2013-11-07
forum: General Help
---

### Post by blake2556 on 2013-11-07
Hi guys,

I don't know if this is the right forum, maybe stackoverflow would be a better choice. So when I run my jar file from console via command java -jar nameOfJar.jar it's working but when I right click on jar and then select open with OpenJDK Java 7 Runtime it will get me this error "The file '/home/user/Downloads/nameOfJar.jar' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.".

Do you know how to fix it? I was googling about it but not succesfully.

Thanks for all help.

---

### Post by blake2556 on 2013-11-07
So this solved my problem sudo chmod +x nameOfJar.jar. Have I to do it with every file or is there some other way?

---

### Post by Morbius1 on 2013-11-07
It's kind of sad really but you have come up against a couple of things that would have been a lot easier to correct a year or so ago. If you want a GUI way to correct this problem:

Install the file manager from XFCE:
```
sudo apt-get install thunar
```
In thunar right click any *.jar file > Open with other application.

In the "use a custom command" window enter:
```
java -jar
```
And make sure "use as default for this kind of file" is selected.

From that point on you should be able to just double click a jar file to launch the java RE from anywhere or in any file manager.

The default mechanism uses something called "cautious launcher" to check to see if a jar file has the executable bit enabled but as you know a jar file is not in itself an executable entity. It's an attempt to protect the user from himself but as you yourself demonstrated the user will always find a way around these impediments.

EDIT: You may never need Thunar again after this but it does come in handy if you want to set other "custom commands" or set defaults for applications as these features have been removed from Gnome.

---

### Post by blake2556 on 2013-11-07
Thank you very much.

---

