---
title: "Chromium and Java?"
date: 2015-01-15
forum: General Help
---

### Post by d4m1r on 2015-01-15
Hello, I am having a problem getting the vanilla Java JDK working under Chromium....When I go to about;plugins, there are no java related plugins :(

I have successfully completed the below instructions but still nothing comes up in about;plugins;

```
Chromium checks the mozilla plugins directory for the java plugin, so do:

     Code:
     ls -l ~/.mozilla/plugins/libnpjp2.so 
If it's not found, do:

     Code:
     mkdir ~/.mozilla/plugins
sudo updatedb
locate libnpjp2.so
cd ~/.mozilla/plugins
ln -s /full/path/to/libnpjp2.so 
(substitute the full path of course)

Restart chromium and go to url about: plugins (no spaces)

which will show you all your installed plugins, including your java hopefully.
```


Whenever you try to access any Java related content under Chromium, it just says "This plugin is not supported". I have the latest Chromium, latest Java, and running Ubuntu 12.04 LTS x64. Java works perfectly fine under the latest Firefox (on the same machine) but I want to get it working for Chromium as well...

---

### Post by Holger_Gehrke on 2015-01-15
> **d4m1r said:**
> I have the latest Chromium, latest Java, and running Ubuntu 12.04 LTS x64. Java works perfectly fine under the latest Firefox (on the same machine) but I want to get it working for Chromium as well...

The Java Plugin uses the old Netscape Plugin architecture. Google has dropped support for that type of plugin in version 34 in early 2014. You need a Java Plugin that uses the new 'Pepper' plugin architecture or you can try to find an old Chromium, which would be a) hard to find and b) a potential security problem.

---

### Post by ajgreeny on 2015-01-15
Presumably Chrome has the pepper java plugin by default, in the same way that it has the pepperflash plugin?

Is it possible to get the pepper java into chromium in the same way that we can get the pepperflash plugin?

---

### Post by Yellow Pasque on 2015-01-15
> Presumably Chrome has the pepper java plugin by default, in the same way that it has the pepperflash plugin?
There's no such thing as "pepper java." The icedtea Java plugin has not been ported to use the Pepper/PPAPI: [http://icedtea.classpath.org/bugzilla/show_bug.cgi?id=1791](http://icedtea.classpath.org/bugzilla/show_bug.cgi?id=1791)
I haven't seen any official response from Oracle on whether they plan to port the proprietary Java plugin to PPAPI, but I wouldn't hold my breath.

---

### Post by d4m1r on 2015-01-16
> **Holger_Gehrke said:**
> The Java Plugin uses the old Netscape Plugin architecture. Google has dropped support for that type of plugin in version 34 in early 2014. You need a Java Plugin that uses the new 'Pepper' plugin architecture or you can try to find an old Chromium, which would be a) hard to find and b) a potential security problem.

Huh? So it worked under my older version of Chromium because it still supported NPAPI but this latest version of Chromium ([COLOR=#303942][FONT=Ubuntu]Version 37.0.2062.120 Ubuntu 12.04 (281580) (64-bit))[/FONT][/COLOR] does not?

My java under Chromium has not been working for several months actually now that I think of it so very possible that it was not working for me under Chromium v35, v36, and now v37....

I definitely don't want to use an old Chromium version but who has so far released a new Java plugin for Chromium using the new "Pepper" plugin architecture? I like the official Java JDK because I referenced a single install for Firefox and Chromium :( I hope in the near future Oracle simply releases a new update for their Java JDK that has PPAPI support for Chromium and other browsers...

---

### Post by Yellow Pasque on 2015-01-16
> **d4m1r said:**
> who has so far released a new Java plugin for Chromium using the new "Pepper" plugin architecture?

No one that I know of. From what I gather, it's not a trivial task because of the security/sandboxing limitations of PPAPI.

---

### Post by d4m1r on 2015-02-08
> **Temüjin said:**
> No one that I know of. From what I gather, it's not a trivial task because of the security/sandboxing limitations of PPAPI.

Hmmm....So is there anyway to get any Java client working under Ubuntu with Chromium? :-?

---

### Post by efflandt on 2015-02-08
Not sure how Chromium corresponds with Google Chrome versions, but this is word from [https://java.com/en/download/faq/chrome.xml](https://java.com/en/download/faq/chrome.xml)

---

### Post by Yellow Pasque on 2015-02-08
> **d4m1r said:**
> Hmmm....So is there anyway to get any Java client working under Ubuntu with Chromium?

No.

---

### Post by d4m1r on 2015-02-08
> **Temüjin said:**
> No.

Wow, that is crazy....Thankfully it isn't my preferred browser anyway but that means it is **impossible** for Chrome/Chromium users under Linux to run Java applets....That sounds like 1995, not 2015 :?

Anyway, for anyone else interested, taken from that article;

```

Chrome and Linux
 Starting with Chrome version 35, NPAPI (Netscape Plug-in API) support  was removed for the Linux platform. For more information, see [Chrome and NPAPI]("http://blog.chromium.org/2013/09/saying-goodbye-to-our-old-friend-npapi.html") (blog.chromium.org).  
 Firefox is now the recommended browser for Java on Linux.

 		 			 				
```

---

