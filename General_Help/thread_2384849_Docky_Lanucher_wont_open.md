---
title: "Docky Lanucher wont open"
date: 2018-02-12
forum: General Help
---

### Post by arc- on 2018-02-12
I'm using Xubuntu 16.04 LTS
Docky Lanucher, will not open. I installed it, no problem, then added items to the lanucher, no problem, until I added ( Session Manager ) since that point I can not get to open. I have "removed, purged" and reinstalled it and the problem remains. 
Since, I add "session manager" to the launcher it disappeared. The very second it was added it disappeared. When I try to open it, the screen flashes, like it open somewhere, but I can not find where. I have the same problem as the thread below.
I saw a thread, [https://ubuntuforums.org/showthread.php?t=2358987](https://ubuntuforums.org/showthread.php?t=2358987) 
I tried what was posted and it did not work.
Any ideas on how to get Docky to work? What am I doing wrong? Did I forget something or miss something?
Really need help. Thanks.

---

### Post by again? on 2018-02-12
I believe docky keeps its settings in gconf.
```
sudo apt install gconf-editor
```
In gconf-editor look in the path /apps/docky-2

If you just want a simple dock/launcher try plank, which I use in Xubuntu.

---

### Post by arc- on 2018-02-13
Thanks, I tried gconfig, but could not get it remove the "session manager" I will try again. Also, I will try Plank.
How did you insert that box that said "code" 
 	Code:
 	sudo apt install gconf-editor 
I can not find how to do that, can you explain?

---

### Post by again? on 2018-02-13
You enclose your text like so... 
[noparse] ```
some text
``` [/noparse]

Which will display as... 
```
some text
```

You can write the code boxes manually.
[Basic guide to BB Code]("https://ubuntuforums.org/faq.php?faq=vb3_reading_posting#faq_vb3_basic_bb_code")
[Complete guide to BB Code]("https://ubuntuforums.org/misc.php?do=bbcode")
[SIZE=3]**or**[/SIZE] 
reply in advanced mode where you can highlight text with the left mouse button then hit the "#" icon.
[ATTACH=CONFIG]278511[/ATTACH]

As for docky, I would consider removing.
Docky relies on mono which is an open source implementation of Microsoft&#8217;s .NET Framework.
Mono introduces another layer where errors can occur and from what I've seen the errors occur quite often.

These are the extra  mono packages installed when you install docky.
```
**[COLOR="#006400"]glen@Xubarty:~$[/COLOR] sudo apt install docky**
[sudo] password for glen:         
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  binfmt-support ca-certificates-mono cli-common libdbus-glib2.0-cil libdbus2.0-cil libgconf2.0-cil libgdiplus libgkeyfile1.0-cil libglib2.0-cil libgnome-keyring1.0-cil
  libgtk2.0-cil libmono-accessibility4.0-cil libmono-addins0.2-cil libmono-cairo4.0-cil libmono-corlib4.5-cil libmono-data-tds4.0-cil libmono-i18n-west4.0-cil libmono-i18n4.0-cil
  libmono-ldap4.0-cil libmono-posix4.0-cil libmono-security4.0-cil libmono-sharpzip4.84-cil libmono-sqlite4.0-cil libmono-system-componentmodel-dataannotations4.0-cil
  libmono-system-configuration4.0-cil libmono-system-core4.0-cil libmono-system-data4.0-cil libmono-system-design4.0-cil libmono-system-drawing4.0-cil
  libmono-system-enterpriseservices4.0-cil libmono-system-ldap4.0-cil libmono-system-numerics4.0-cil libmono-system-runtime-serialization-formatters-soap4.0-cil
  libmono-system-runtime-serialization4.0-cil libmono-system-security4.0-cil libmono-system-servicemodel-internals0.0-cil libmono-system-transactions4.0-cil
  libmono-system-web-applicationservices4.0-cil libmono-system-web-services4.0-cil libmono-system-web4.0-cil libmono-system-windows-forms4.0-cil libmono-system-xml-linq4.0-cil
  libmono-system-xml4.0-cil libmono-system4.0-cil libmono-webbrowser4.0-cil libnotify0.4-cil mono-4.0-gac mono-gac mono-runtime mono-runtime-common mono-runtime-sgen
```

You can find a large collection of plank themes [HERE]("https://github.com/LinxGem33/Plank-Themes") with install instructions.
To open plank preferences, ctrl+Rightmouse on plank or via terminal....
```
plank --preferences
```

---

### Post by arc- on 2018-02-14
Thanks again, I just finished the ```
sudo apt purge docky
``` I think its all gone, I catfish'd it, and ```
sudo rm docky
``` sorry for all the codes, I just want to practice. i found them in ```
/usr/share/spp-install/desktop/
``` and in four other ones. 
Thanks for the post, [post]Basic guide to BB Code[/post] [post]Complete guide to BB Code[/post] 
Thanks for all you help.
I can't figure out how to post the BB Code part, that will take practice.

---

### Post by again? on 2018-02-14
> **arc- said:**
> Thanks again, I just finished the ```
sudo apt purge docky
``` I think its all gone, I catfish'd it, and ```
sudo rm docky
``` sorry for all the codes, I just want to practice. i found them in ```
/usr/share/spp-install/desktop/
``` and in four other ones. 
Thanks for the post, [post]Basic guide to BB Code[/post] [post]Complete guide to BB Code[/post] 
Thanks for all you help.
I can't figure out how to post the BB Code part, that will take practice.

The "sudo apt purge *package*" command removes all installed *package* files except user created configs in your home directory,
so it's not necessary to "sudo rm" anything and will only get you into trouble. :cry:

From apt manual page....
```
man apt
```
> 
**install, remove, purge (apt-get(8))**

Performs the requested action on one or more packages specified via regex(7), glob(7) or exact match. The requested action can be overridden for specific packages by append a plus (+) to the package name to install this package or a minus (-) to remove it.
A specific version of a package can be selected for installation by following the package name with an equals (=) and the version of the package to select. Alternatively the version from a specific release can be selected by following the package name with a forward slash (/) and codename (stretch, buster, sid ...) or suite name (stable, testing, unstable). This will also select versions from this release for dependencies of this package if needed to satisfy the request.

Removing a package removes all packaged data, but leaves usually small (modified) user configuration files behind, in case the remove was an accident. Just issuing an installation request for the accidentally removed package will restore its function as before in that case. On the other hand you can get rid of these leftovers by calling purge even on already removed packages. Note that this does not affect any data or configuration stored in your home directory.


---

### Post by arc- on 2018-02-14
Thanks, I will be more careful.

---

### Post by again? on 2018-02-14
> **arc- said:**
> Thanks, I will be more careful.
No harm in exploring/learning.
Backup and be prepared to reinstall.
If you take it apart and can't put it back together... just get a shiny new one. 8-[

---

### Post by arc- on 2018-02-14
there were 3 item, I went into each dir, example ```
cd /usr/share/app-install/desktop/
``` 
[LIST=1]
[*]docky:docky.desktoop 
[*]docky.docky.svg 
[*]docky.png 
[/LIST]
I used the command line ```
sudo rm *each item listed above*
```
Hope I didn't break anything.

---

### Post by again? on 2018-02-14
Explanation [HERE]("https://askubuntu.com/questions/464807/why-so-many-files-in-usr-share-app-install-desktop").

---

### Post by arc- on 2018-02-15
Thanks, that explained that there are just installed for use if needed. I have a lot to learn.

---

