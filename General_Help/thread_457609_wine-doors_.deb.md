---
title: "wine-doors .deb"
date: 2007-05-28
forum: General Help
---

### Post by MZaza on 2007-05-28
Anyone have got or can build a debian package for the [wine-doors]("http://www.wine-doors.org")?

---

### Post by tyn0r on 2007-06-04
check dep : 

Software Dependencies

    * Wine
    * cabextract, tar, gzip, bzip, unzip
    * python-gnome2-desktop >= 2.16 (python rsvg support, Debian/Ubuntu package, might differ on other systems)
    * python >= 2.4
    * python2.4-cairo >= 1.2.0
    * libcairo2 >= 1.2.4
    * python-libxml2
    * python-glade2


& just this :p

```
 
sudo apt-get install subversion
cd ~
mkdir .wine-doors
cd .wine-doors/
svn co http://www.wine-doors.org/svn/wine-doors/trunk wine-doors
cd wine-doors
python setup.py install
```

and have fun :p ==> App ==> Sys tool ==> Wine-doors

to unistall : 

```
 
cd ~/.wine-doors/wine-doors
python setup.py uninstall
```

---

### Post by MZaza on 2007-06-04
Thanks, that's useful.

---

### Post by YokoZar on 2007-06-04
> **MZaza said:**
> Anyone have got or can build a debian package for the [wine-doors]("http://www.wine-doors.org")?
Hey, I make the Wine packages for Ubuntu.  I'll be looking into building a wine-doors package next week.

So, yes, in time, you'll have an easy to install Wine-doors deb.

---

### Post by MZaza on 2007-06-04
That will be great.

---

### Post by flawedprefect on 2007-06-25
Followed the steps, but at the last step, I get this:

[email]paul@fiesty:~/.wine[/email]-doors$ cd wine-doors
[email]paul@fiesty:~/.wine[/email]-doors/wine-doors$ python setup.py install
Traceback (most recent call last):
  File "setup.py", line 112, in <module>
    from preferences import preferences
  File "./src/preferences.py", line 161, in <module>
    preferences = Preferences()
  File "./src/preferences.py", line 49, in __init__
    self.Save()
  File "./src/preferences.py", line 148, in Save
    f = open( prefsfile, "w" )
IOError: [Errno 13] Permission denied: u'/home/paul/.wine/wine-doors/preferences.xml'
[email]paul@fiesty:~/.wine[/email]-doors/wine-doors$

---

### Post by spottraining on 2007-07-08
Hi

I am getting also errors: All pyhon dependencies are installed.

Error:
```
suvi@lapakas:~/.wine-doors/wine-doors-0.1$ python setup.py installTraceback (most recent call last):
  File "setup.py", line 112, in <module>
    from preferences import preferences
  File "./src/preferences.py", line 161, in <module>
    preferences = Preferences()
  File "./src/preferences.py", line 48, in __init__
    self.Load()
  File "./src/preferences.py", line 128, in Load
    parser.parse( prefsfile )
  File "/usr/lib/python2.5/site-packages/_xmlplus/sax/expatreader.py", line 109, in parse
    xmlreader.IncrementalParser.parse(self, source)
  File "/usr/lib/python2.5/site-packages/_xmlplus/sax/xmlreader.py", line 125, in parse
    self.close()
  File "/usr/lib/python2.5/site-packages/_xmlplus/sax/expatreader.py", line 226, in close
    self.feed("", isFinal = 1)
  File "/usr/lib/python2.5/site-packages/_xmlplus/sax/expatreader.py", line 220, in feed
    self._err_handler.fatalError(exc)
  File "/usr/lib/python2.5/site-packages/_xmlplus/sax/handler.py", line 38, in fatalError
    raise exception
xml.sax._exceptions.SAXParseException: /home/suvi/.wine/wine-doors/preferences.xml:5:0: no element found
suvi@lapakas:~/.wine-doors/wine-doors-0.1$ 

```

EDIT: Solved. I look to setup.py code and I find, that problem was with importing preferences to .wine/wine-doors. I have previously also tested wine-doors and there was already same folder and files. So - after deleting these - everything work fine.

---

### Post by atselby on 2007-07-09
> **tyn0r said:**
> check dep : 

Software Dependencies

    * Wine
    * cabextract, tar, gzip, bzip, unzip
    * python-gnome2-desktop >= 2.16 (python rsvg support, Debian/Ubuntu package, might differ on other systems)
    * python >= 2.4
    * python2.4-cairo >= 1.2.0
    * libcairo2 >= 1.2.4
    * python-libxml2
    * python-glade2


& just this :p

```
 
sudo apt-get install subversion
cd ~
mkdir .wine-doors
cd .wine-doors/
svn co http://www.wine-doors.org/svn/wine-doors/trunk wine-doors
cd wine-doors
python setup.py install
```

and have fun :p ==> App ==> Sys tool ==> Wine-doors

to unistall : 

```
 
cd ~/.wine-doors/wine-doors
python setup.py uninstall
```
Worked perfect, thanks.

---

### Post by acejones on 2007-07-09
```
mike@acejones-nix:~/.wine-doors/wine-doors$ python setup.py install
Compressing and installing pack files
  ** Base Repo
  ** Libraries.Repo
  ** Applications.Repo
  ** Games Repo
Symlinking executable
Creating initial preferences
Checking dependencies
  wine . . .  Found
  cabextract . . .  Found
  tar . . .  Found
  orange . . .  Found
  ps . . .  Found
  pygtk . . .  Found
  pycairo . . .  Found
  rsvg . . .  Found
mike@acejones-nix:~/.wine-doors/wine-doors$ 
```

Nothing is listed under App --> System tools

---

### Post by itsjustarumour on 2007-12-04
> **tyn0r said:**
> check dep : 

Software Dependencies

    * Wine
    * cabextract, tar, gzip, bzip, unzip
    * python-gnome2-desktop >= 2.16 (python rsvg support, Debian/Ubuntu package, might differ on other systems)
    * python >= 2.4
    * python2.4-cairo >= 1.2.0
    * libcairo2 >= 1.2.4
    * python-libxml2
    * python-glade2


& just this :p

```
 
sudo apt-get install subversion
cd ~
mkdir .wine-doors
cd .wine-doors/
svn co http://www.wine-doors.org/svn/wine-doors/trunk wine-doors
cd wine-doors
python setup.py install
```

and have fun :p ==> App ==> Sys tool ==> Wine-doors

to unistall : 

```
 
cd ~/.wine-doors/wine-doors
python setup.py uninstall
```

I checked that all dependencies were present and correct, installed Wine-Doors, ran it from Applications>System Tools>Wine-Doors, and it opened up the box that told me I was running it for the first time. So far so good - I entered my details and ticked  "Yes I have a valid Windows Licence", closed the box... and then when I try and open it again from Applications>System Tools>Wine-Doors nothing happened.  I tried running it from terminal, which gives me:

> ian@COOLERMASTER:~$ wine-doors
Started logging session
Checking wine drive: /home/ian/.wine/




Traceback (most recent call last):
  File "/home/ian/bin/wine-doors", line 104, in <module>
    ui.winedoors = ui.WineDoorsGUI()
  File "/home/ian/.local/share/wine-doors/src/ui.py", line 1004, in __init__
    self.tree = PackTree( self.window['tv_packlist'], self.window )
  File "/home/ian/.local/share/wine-doors/src/ui.py", line 538, in __init__
    self.widget.set_model( self.CreateModel() )
  File "/home/ian/.local/share/wine-doors/src/ui.py", line 898, in CreateModel
    urllib.urlretrieve( pack['icon'], icon_file )
KeyError: 'icon'
ian@COOLERMASTER:~$ 


Any ideas?

---

### Post by itsjustarumour on 2007-12-10
Bump

---

### Post by itsjustarumour on 2007-12-11
Bump.

---

### Post by bodhi.zazen on 2007-12-11
I have played with wine doors in the *past* and it is in development and has always been buggy (I have installed it some 5 times in the past).

I would direct you to their web site : [http://www.wine-doors.org/wordpress/](http://www.wine-doors.org/wordpress/)

And encourage you to file a bug report : [http://www.wine-doors.org/trac/newticket](http://www.wine-doors.org/trac/newticket)

---

### Post by itsjustarumour on 2007-12-11
> **bodhi.zazen said:**
> I have played with wine doors in the *past* and it is in development and has always been buggy (I have installed it some 5 times in the past).

I would direct you to their web site : [http://www.wine-doors.org/wordpress/](http://www.wine-doors.org/wordpress/)

And encourage you to file a bug report : [http://www.wine-doors.org/trac/newticket](http://www.wine-doors.org/trac/newticket)



Hi there bodhi,

Thanks for the links, I'll go have a look...

itsjustarumour

---

