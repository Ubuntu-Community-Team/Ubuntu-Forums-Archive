---
title: "How to change default &quot;open file&quot; location away from &quot;recently used&quot;?"
date: 2013-07-07
forum: General Help
---

### Post by TLangas on 2013-07-07
[FONT=verdana]This has been bothering me ever since I started using Ubuntu.
When ever I go to open a file the file chooser dialog that appears usually defaults to the 'recently used' filter. I'm sure someone finds this useful, but not once in the last 3 years have I every found this window useful.

Is there a way to change this to default to $HOME or even /?

I found an older page explaining that it is possible to temporarily change the 'last-folder-uri' by using dconf-editor.  As dconf-editor is not installed by default in Xubuntu, I was wondering if there is a more reliable solution.[/FONT]
[http://askubuntu.com/questions/63202/can-i-stop-apps-from-selecting-recently-used-by-default-in-file-chooser-dialog](http://askubuntu.com/questions/63202/can-i-stop-apps-from-selecting-recently-used-by-default-in-file-chooser-dialog)

---

### Post by ajgreeny on 2013-07-07
Just like the xubuntu 12.04 save dialog, which instead of using the folder that the particular app used last time, often but not always, reverts to the recently used folder that anything was saved to.

It is so annoying and not in the least useful to me!

---

### Post by Toz on 2013-07-07
After some intensive googling and brief testing, the following seems to make it default to the home directory (Xubuntu 13.04). Edit the file **$HOME/.config/gtk-2.0/gtkfilechooser.ini** and change:
> StartupMode=recent
...to:
```
StartupMode=cwd
```

I'd be interesting in hearing whether this works for others. As for GTK version, I've got 2.24.17:
> $ apt-cache policy libgtk2.0-0
libgtk2.0-0:
  Installed: 2.24.17-0ubuntu2
  Candidate: 2.24.17-0ubuntu2
  Version table:
 *** 2.24.17-0ubuntu2 0
        500 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) raring/main amd64 Packages
        100 /var/lib/dpkg/status

Note: might only work with gtk2 apps.

---

### Post by TLangas on 2013-07-07
Thanks you Toz.
This works wonderfully for most apps.

I'm also running the same gtk2 version.

I'll keep testing programs as i go and see what programs still use the 'recently used' filter.
So far only gedit.

---

### Post by Merrattic on 2013-07-08
Hmmmm......I don't have folder ~/.config/**gtk-2.0 **and consequently no~/.config/**gtk-2.0/gtkfilechooser.ini **file. Just create it with that single entry ?

---

### Post by Toz on 2013-07-08
Which version of Xubuntu are you using. On 13.04, its created automatically as soon as I File->Open on gtk-compliant app. Perhaps [this bug]("https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/1000712") is relevant for you?

Try creating one. The contents of the file are as such:
```
[Filechooser Settings]
LastFolderUri=file:///usr/share/pixmaps
LocationMode=path-bar
ShowHidden=false
ShowSizeColumn=true
GeometryX=306
GeometryY=106
GeometryWidth=792
GeometryHeight=585
SortColumn=name
SortOrder=ascending
StartupMode=recent

```

Be wary of the geometry settings, I believe they set the size of the dialog box.

Now thats interesting. cat'ing the file now, I see that its returned to "StartupMode=recent". Something set it back.

---

### Post by Merrattic on 2013-07-08
I am on 12.04 LTS up to date.

Tried creating folder and file with just StartupMode=cwd in it, re-logged in, but no change.

---

### Post by pqwoerituytrueiwoq on 2013-07-08
> **Merrattic said:**
> I am on 12.04 LTS up to date.

Tried creating folder and file with just StartupMode=cwd in it, re-logged in, but no change.try adding the xfce 4.10 and 4.12 PPAs
```
sudo add-apt-repository ppa:xubuntu-dev/xfce-4.10
sudo add-apt-repository ppa:xubuntu-dev/xfce-4.12
sudo apt-get update
sudo apt-get dist-upgrade
``` 
you will get quite a few upgrades and fixes for xfce stuff (tab file browsing in thunar for example)

---

### Post by Toz on 2013-07-08
[Here]("https://bugzilla.gnome.org/show_bug.cgi?id=658280") is some history.

---

### Post by Merrattic on 2013-07-09
OK, thanks Toz. I am sticking with 12.04 LTS repos for now, will have to await 14.04 ;)

---

### Post by ajgreeny on 2013-07-09
Using the xubuntu 4.10 ppa does not remove this behaviour, I'm afraid, as both the open and the save dialog default to "recently used".

Most annoying, to my way of thinking!

---

### Post by tareqjhe1 on 2013-07-09
Thank you toz.I am too feel this problem many days .

---

### Post by ShadowVegan on 2013-08-01
> **Toz said:**
> After some intensive googling and brief testing, the following seems to make it default to the home directory (Xubuntu 13.04). Edit the file **$HOME/.config/gtk-2.0/gtkfilechooser.ini** and change:  ...to: ```
StartupMode=cwd
```  I'd be interesting in hearing whether this works for others. As for GTK version, I've got 2.24.17:   Note: might only work with gtk2 apps.  This worked for me in Lubuntu 13.04. Thanks.

---

### Post by VMC on 2013-08-01
This is topic is for [xubuntu], for ubuntu I found [this]("https://alexcabal.com/disabling-gnomes-recently-used-file-list-the-better-way/") site.

edit: I haven't tried to create the aforementioned folder, just yet.

---

