---
title: "Radio Tray - how add stations?"
date: 2014-12-18
forum: General Help
---

### Post by petermartin2 on 2014-12-18
I've installed radiotray and I can get the radiostations to play well in the brorwser but as soon as I add an adress to the application in configure radios I get this message:

Radio Error
>  gstdecodebin2.c(3576):
gst_decode_bin_expose ():/
GstPlayBin2:player/
GstURIDecodeBin:uridecodebin13/
GstDecodeBin2:decodebin214:
no suitable plugins found

I've tried with bbc and several british channels, the method I use is copying the url straight from the browser window and pasting it into configure radios add window. Is this wrong? How should it be done?

Thanks in advance

---

### Post by slickymaster on 2015-01-05
Right click on Radio Tray and select “Configure radios…”, click “Add”, paste the URL into the URL box, and give the stream a name that you will recognize.

---

### Post by kerry_s on 2015-01-05
i use this list, it's huge & makes start up a little slow but worth it.
[http://gnome-look.org/content/show.php/The+Ultimate+List+of+Radio+Stations?content=135497](http://gnome-look.org/content/show.php/The+Ultimate+List+of+Radio+Stations?content=135497)

just grab sections out of the xml you want, don't use whole list.

---

### Post by petermartin2 on 2015-01-08
> **slickymaster said:**
> Right click on Radio Tray and select “Configure radios…”, click “Add”, paste the URL into the URL box, and give the stream a name that you will recognize.
Everytime I try this it seems to happen nothing. I've found an URL online and click add and paste the URL and click save but nothing happens. There's already a list of dirs on installation and I've tried removing them first but nothing happens

> **kerry_s said:**
> i use this list, it's huge & makes start up a little slow but worth it.
[http://gnome-look.org/content/show.php/The+Ultimate+List+of+Radio+Stations?content=135497](http://gnome-look.org/content/show.php/The+Ultimate+List+of+Radio+Stations?content=135497)

just grab sections out of the xml you want, don't use whole list.

I've downloaded this list now but how do I import it into radio tray?

---

### Post by kerry_s on 2015-01-08
use you text editor to view the xml & copy the stations you want to the bookmarks xml.
instructions are on that download page. don't use the whole list its way to long and will be off screen, you won't be able to see the quit button.

don't do this, just go to location and open stock bookmarks.xml, very easy to add to it.
**For Radiotray users, copy the file, 'bookmarks.xml', to ~/.local/share/radiotray.**

---

### Post by HermanAB on 2015-01-08
IMHO Streamtuner2 is much better.

---

### Post by petermartin2 on 2015-01-08
> **kerry_s said:**
> use you text editor to view the xml & copy the stations you want to the bookmarks xml.
instructions are on that download page. don't use the whole list its way to long and will be off screen, you won't be able to see the quit button.

don't do this, just go to location and open stock bookmarks.xml, very easy to add to it.
**For Radiotray users, copy the file, 'bookmarks.xml', to ~/.local/share/radiotray.**

Could you please tell me where I could locate the xml-files? I've tried looking in usr/bin but couldn't find it and can't find a folder called "location"?

---

### Post by buzzingrobot on 2015-01-08
> **petermartin2 said:**
> I've installed radiotray and I can get the radiostations to play well in the brorwser but as soon as I add an adress to the application in configure radios I get this message:

Radio Error


I've tried with bbc and several british channels, the method I use is copying the url straight from the browser window and pasting it into configure radios add window. Is this wrong? How should it be done?



The errors are complaining about missing codecs.  If you haven't already, install 'ubuntu-restricted-extras'.  It will supply codecs that can handle most streams.

I've found various links for BBC streams result in varying success with Radiotray. Some work, some do not.  Streams intended for consumption in the UK -- iPlayer and such -- won't work outside the UK no matter what codecs are installed (BBC blocks non-UK IP addresses for those streams.)

Adding stream URL's via 'Configure Radio's' is correct.  You can, if you want, also edit the raw XML file, but that seems unnecessary to me. (It's ~/.local/share/radiotray/bookmarks.xml. XML files typically open in a browser, so you'd need to explicitiy open it with a text editor.)

As you've likely noticed, some stations may it difficult to find the URL of their actual stream.  They want you to use their site.

---

### Post by petermartin2 on 2015-01-08
> **buzzingrobot said:**
> The errors are complaining about missing codecs.  If you haven't already, install 'ubuntu-restricted-extras'.  It will supply codecs that can handle most streams.

I've found various links for BBC streams result in varying success with Radiotray. Some work, some do not.  Streams intended for consumption in the UK -- iPlayer and such -- won't work outside the UK no matter what codecs are installed (BBC blocks non-UK IP addresses for those streams.)

Adding stream URL's via 'Configure Radio's' is correct.  You can, if you want, also edit the raw XML file, but that seems unnecessary to me. (It's ~/local/share/radiotray/bookmarks.xml. XML files typically open in a browser, so you'd need to explicitiy open it with a text editor.)

As you've likely noticed, some stations may it difficult to find the URL of their actual stream.  They want you to use their site.
Ok, thanks for the information. According to my Ubuntu Software Store the package ubuntu-restricted-extras is already installed. 

I'm still having trouble locating the XML file unfortunately. I've looked in "computer" and "home" folders for share or local maps but can't find them and I've tried the following in terminal:


```
w@w:~$ sudo gedit /local/share/radiotray/bookmarks.xml

(gedit:3167): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
w@w:~$ cd /local/share/radiotray/bookmarks.xml
bash: cd: /local/share/radiotray/bookmarks.xml: No such file or directory
w@w:~$ cd /local/share/radiotray/
bash: cd: /local/share/radiotray/: No such file or directory
w@w:~$ cd local
bash: cd: local: No such file or directory
w@w:~$ cd share
bash: cd: share: No such file or directory
w@w:~$ cd /w/
bash: cd: /w/: No such file or directory
w@w:~$ 
```

edit: w is the name of my home folder if that is what "local" stands for!

---

### Post by buzzingrobot on 2015-01-08
".local" is a hidden folder.  Don't forget the'.' (as  I did above).

Using the "Configure Radios" option adds/removes/edits URL's in bookmarks.xml without the need to deal with XML.

---

### Post by petermartin2 on 2015-01-08
> **buzzingrobot said:**
> ".local" is a hidden folder.  Don't forget the'.' (as  I did above).

Using the "Configure Radios" option adds/removes/edits URL's in bookmarks.xml without the need to deal with XML.

```
w@w:~$ cp -i bookmarks.xml /.local/share/radiotray/
cp: cannot create regular file ‘/.local/share/radiotray/’: No such file or directory
```

However I did manage to locate a bookmarks.xml in /usr/share/radiotray/ and I copied the bookmarks.xml file from the compressed bundle there and checked that it was replaced with the new longer list. It was but still the stations will not appear in radiotray!  Also when I press reload bookmarks there is not one single station!

---

### Post by buzzingrobot on 2015-01-08
> **petermartin2 said:**
> ```
w@w:~$ cp -i bookmarks.xml /.local/share/radiotray/
cp: cannot create regular file ‘/.local/share/radiotray/’: No such file or directory
```

However I did manage to locate a bookmarks.xml in /usr/share/radiotray/ and I copied the bookmarks.xml file from the compressed bundle there and checked that it was replaced with the new longer list. It was but still the stations will not appear in radiotray!  Also when I press reload bookmarks there is not one single station!

Not quite sure I understand what you're trying to do or fix.  When it's run the first time, Radiotray creates, and writes its default configuration files to, ~/.local/share/radiotray. One of those files is bookmarks.xml, which contains the stations Radiotray displays. Out of the box, its well populated.

The '/' before the '.local/....' you entered begins the file path at the '/' directory, where there is no .local. Since you're the folder one level up from .local - your home folder -- omit it.

---

### Post by petermartin2 on 2015-01-08
> **buzzingrobot said:**
> Not quite sure I understand what you're trying to do or fix.  When it's run the first time, Radiotray creates, and writes its default configuration files to, ~/.local/share/radiotray. One of those files is bookmarks.xml, which contains the stations Radiotray displays. Out of the box, its well populated.

The '/' before the '.local/....' you entered begins the file path at the '/' directory, where there is no .local. Since you're the folder one level up from .local - your home folder -- omit it.

ok thanks. that implemented the list. So now I guess I know how to add radiostations I just have to edit the bookmarks file thanks

---

### Post by mc4man on 2015-01-08
As an aside - 
you really should be more careful about using sudo in a terminal & only do so when it's needed & proper.
ex. - while you got the path wrong the intent here was an improper use of sudo on a couple of levels,
> w@w:~$ sudo gedit /local/share/radiotray/bookmarks.xml

radiotray itself appears to be a dead project (2 yrs. since updated) so it probably will have some issues.

---

### Post by buzzingrobot on 2015-01-08
> **mc4man said:**
> As an aside - 
you really should be more careful about using sudo in a terminal & only do so when it's needed & proper.
ex. - while you got the path wrong the intent here was an improper use of sudo on a couple of levels

Yes.  No need to use sudo in your home directory.  Combined with the filepath error, it could easily have resulted in unwittingly editing a file belong to root, with unknown consequences.


> radiotray itself appears to be a dead project (2 yrs. since updated) so it probably will have some issues.

The version in the 14.10 repos works as usual here.  The version available for Fedora 21 does not work at all here, though, generating a rather generic complaint when I execute it in the shell (the kind that generates a million irrelevant Google hits).  It's a python script, and I suspect Fedora's python has left it behind.

Pity, it's a favorite of mine.  if it really has been orphaned, I hope someone adopts it.

---

