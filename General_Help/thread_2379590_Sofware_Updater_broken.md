---
title: "Sofware Updater broken"
date: 2017-12-07
forum: General Help
---

### Post by flix3 on 2017-12-07
Hello everybody. I'm on Ubuntu 16.04 LTS 64-bit.
My problem is the following:


[LIST]
[*]When I launch "Software Updater" I get: 
[/LIST]
```
An unhandlable error occurred
There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks.
```
[LIST]
[*]This is the output of some commands I've issued: 
[/LIST]
```
me@PC:~$ sudo apt-get clean
me@PC:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
me@PC:~$ sudo apt-get install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
[LIST]
[*]When I type: 
[/LIST]
```
sudo mv /var/lib/apt/lists /var/lib/apt/lists_old
```[INDENT]And then I launch "Software Updater" again I get:
```
Software Updater
Checking for updates...
Waiting for other software managers to quit
```
But of course there's no other software manager to wait for... so I've reverted the mv.
[/INDENT]

Can anybody please help me?
Thank you in advance.

---

### Post by ian-weisser on 2017-12-07
Does the "Unhandlable Error" message include anything else?
Usually it includes the python error traceback.

How long has the current system been installed?

Have you run "sudo apt update"?

---

### Post by flix3 on 2017-12-07
> **ian-weisser said:**
> Does the "Unhandlable Error" message include anything else?
Usually it includes the python error traceback.
Nothing else. Basically as soon as the "Update Manager" is "Loading software list" I see that error message with three buttons: 
[LIST]
[*]"Settings" (that does nothing other than displaying the message "The software on this computer is up to date." without checking for updates). 
[*]"Try again" (that restart the check and repeats the error message). 
[*]"OK" (that has the same effect as "Settings"). 
[/LIST]

> **ian-weisser said:**
> How long has the current system been installed?
Years, and it always worked.
> **ian-weisser said:**
> Have you run "sudo apt update"?
Yes, the command line seems to work well as far as I can see. I get:
```
sudo apt update
Hit:1 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease                     
Hit:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial InRelease                        
Get:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates InRelease [102 kB]       
Get:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports InRelease [102 kB]     
Get:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]      
Hit:6 [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) xenial InRelease         
Fetched 306 kB in 35s (8.676 B/s)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.

```

I should add that if I launch from the "System Settings" "Software and Updates" nothing happens...

---

### Post by slickymaster on 2017-12-07
@flix3:

Please [use code tags]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168"), instead of quote tags, when posting output. Output posted as plain text loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand.

---

### Post by flix3 on 2017-12-07
@slickymaster:

Ok.

---

### Post by flix3 on 2017-12-07
Not sure if this is related or not. Basically if this links is true:  [https://askubuntu.com/questions/812203/what-is-the-package-name-for-software-updates-and-how-to-remove-it](https://askubuntu.com/questions/812203/what-is-the-package-name-for-software-updates-and-how-to-remove-it),  the "Software And Updates" inside "System Settings" is called: software-properties-gtk. Well, I've just tried to run it from terminal. It does not work, but I can get these messages:

```
> software-properties-gtk
/usr/lib/python3/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py:40: PyGIWarning: Gdk was imported without specifying a version first. Use gi.require_version('Gdk', '3.0') before import to ensure that the right version gets loaded.
  from gi.repository import GObject, Gdk, Gtk, Gio, GLib
/usr/lib/python3/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py:40: PyGIWarning: Gtk was imported without specifying a version first. Use gi.require_version('Gtk', '3.0') before import to ensure that the right version gets loaded.
  from gi.repository import GObject, Gdk, Gtk, Gio, GLib
Traceback (most recent call last):
  File "/usr/bin/software-properties-gtk", line 101, in <module>
    app = SoftwarePropertiesGtk(datadir=options.data_dir, options=options, file=file)
  File "/usr/lib/python3/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 98, in __init__
    SoftwareProperties.__init__(self, options=options, datadir=datadir)
  File "/usr/lib/python3/dist-packages/softwareproperties/SoftwareProperties.py", line 114, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python3/dist-packages/softwareproperties/SoftwareProperties.py", line 607, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python3/dist-packages/aptsources/distro.py", line 142, in get_sources
    self.get_mirrors()
  File "/usr/lib/python3/dist-packages/aptsources/distro.py", line 457, in get_mirrors
    self, mirror_template="http://%s.archive.ubuntu.com/ubuntu/")
  File "/usr/lib/python3/dist-packages/aptsources/distro.py", line 166, in get_mirrors
    et = ElementTree(file=fname)
  File "/usr/lib/python3.5/xml/etree/ElementTree.py", line 556, in __init__
    self.parse(file)
  File "/usr/lib/python3.5/xml/etree/ElementTree.py", line 596, in parse
    self._root = parser._parse_whole(source)
xml.etree.ElementTree.ParseError: syntax error: line 1, column 0

```

Any hint ?

---

### Post by shintaomonk on 2017-12-07
Have you tried to run both update and upgrade?

```
sudo apt update && sudo apt upgrade
```

---

### Post by ian-weisser on 2017-12-07
> **flix3 said:**
> 
```
>
  File "/usr/lib/python3/dist-packages/aptsources/distro.py", **line 166**, in get_mirrors
    et = ElementTree(file=fname)
  ...
  File "/usr/lib/python3.5/xml/etree/ElementTree.py", line 596, in parse
    self._root = parser._parse_whole(source)
  xml.etree.ElementTree.ParseError: syntax error: line 1, column 0

```


I think that's the key.

Let's look at those Python lines in /usr/lib/python3/dist-packages/aptsources/distro.py, around line 166:
```

        fname = "/usr/share/xml/iso-codes/iso_3166.xml"
        if os.path.exists(fname):
            et = ElementTree(file=fname)

```
Easy enough: It's trying to parse /usr/share/xml/iso-codes/iso_3166.xml, but encountering a syntax error.
That xml file is corrupt or changed or otherwise not valid xml.

So let's see what package provides that corrupt file:
```
$ dpkg -S /usr/share/xml/iso-codes/iso_3166.xml
**iso-codes**: /usr/share/xml/iso-codes/iso_3166.xml
```

There you are: Try reinstalling the 'iso-codes' package.

```
sudo apt install --reinstall iso-codes
```

---

### Post by flix3 on 2017-12-08
@shintaomonk:
Yes, it works because apt works perfectly on the terminal: it's just a GUI problem, or something like that.

> **ian-weisser said:**
> I think that's the key.
Looking at the code, it's tying to parse /usr/share/xml/iso-codes/iso_3166.xml, but encountering a syntax error- that file is corrupt or changes or otherwise not valid xml.

So let's see what package provides that corrupt file:
```
$ dpkg -S /usr/share/xml/iso-codes/iso_3166.xml
**iso-codes**: /usr/share/xml/iso-codes/iso_3166.xml
```

There you are: Try reinstalling the 'iso-codes' package.

```
sudo apt install --reinstall iso-codes
```

**[SOLVED] **Thank you very much! That fixed both "Software Updater" and "Software and Updates" in a single shot! 
Wow! You know how to track down and solve error logs!

---

