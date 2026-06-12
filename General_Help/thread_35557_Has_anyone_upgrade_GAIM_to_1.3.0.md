---
title: "Has anyone upgrade GAIM to 1.3.0?"
date: 2005-05-19
forum: General Help
---

### Post by zaxer on 2005-05-19
Hi guys.

Have you updated gaim to its newer version?
Synaptic and backports didnt include it yet..

---

### Post by Zelut on 2005-05-19
[QUOTE=zaxer]Hi guys.

Have you updated gaim to its newer version?
Synaptic and backports didnt include it yet..[/QUOTE]
 You're right, apt-get isn't going to find it yet but I've managed to install it.

I used the autopackage version from the gaim site ([http://gaim.sf.net)](http://gaim.sf.net)).  If you download the .package version, chmod +x (or Properties > Permissions > Executable) and run the file.  It'll download the needed autopackage libs, & install it.  Be sure to uninstall 1.2.1 or whichever version you have now before you install.  (sudo apt-get remove gaim)

Autopackage seems to be cool because it is more of a universal installation program.  It manages to install packages for any distro.

---

### Post by ruben_b on 2005-05-19
whats new in this version of gaim?

---

### Post by Zelut on 2005-05-19
version 1.3.0 (5/10/2005):
	* Removed parts of the font selection dialog that were not respected
	* Fix being invited to a multi user chat on MSN
	* Multiple SILC accounts should work now (Pekka Riikonen)
	* Fix times on jabber chat backlogs
	* Fix gevolution plugin to compile with e-d-s 1.0 or 1.2
	* Fix gevolution plugin to remember buddy name when someone added you
	  and you then add them
	* Formatting in jabber chats works
	* Fix to prevent MSN disconnecting if you change status while connecting
	* Fixes for two remotely exploitable crash bugs.  See
	  [http://gaim.sourceforge.net/security/](http://gaim.sourceforge.net/security/) for more information.

taken from the changelog at [http://gaim.sourceforge.net/ChangeLog](http://gaim.sourceforge.net/ChangeLog)

---

### Post by bored2k on 2005-05-19
I upgraded. A whole lot of nothing new.

---

### Post by Zelut on 2005-05-19
Seems nothing noticeably new in any update.  Just behind the scenes stuff.

---

### Post by zaxer on 2005-05-19
[QUOTE=kuyaedz]Seems nothing noticeably new in any update.  Just behind the scenes stuff.[/QUOTE]
 Hey guys.

Ive updated it too but I got another question?

How can I know where its been installed? I want to add a set of icons and I dont know where to place them...

Thanks!

---

### Post by poofyhairguy on 2005-05-19
Any thread involving backports does not belong in the beginner section. Thanks for your patience as us mods work things out.

---

### Post by bored2k on 2005-05-19
Type
sudo updatedb
After that
locate gaim

It will show where gaim is installed.

If you installed an autopackage with your user account, open the file manager nautilus, view > show hidden. It should be .somewhere.

---

### Post by zaxer on 2005-05-20
[QUOTE=bored2k]Type
sudo updatedb
After that
locate gaim

It will show where gaim is installed.

If you installed an autopackage with your user account, open the file manager nautilus, view > show hidden. It should be .somewhere.[/QUOTE]
 I cant complete this...

I want to add this set of icons [http://www.gnomelook.org/content/show.php?content=22348](http://www.gnomelook.org/content/show.php?content=22348) to the gaim 1.0.3 Ive just installed with autopackage.

I would like to hear of someone who can and helps me...

Thanks..

---

### Post by bored2k on 2005-05-20
[QUOTE=zaxer]I cant complete this...

I want to add this set of icons [http://www.gnomelook.org/content/show.php?content=22348](http://www.gnomelook.org/content/show.php?content=22348) to the gaim 1.0.3 Ive just installed with autopackage.

I would like to hear of someone who can and helps me...

Thanks..[/QUOTE]
 If you installed as a regular user :
```
tar xzf 22348-gaim-iconset-1.1.tar.gz 
cp -rf gaim/ ~/.local/share/pixmaps/
```

If you installed as root:
```
tar xzf 22348-gaim-iconset-1.1.tar.gz 
cp -rf gaim/ /usr/share/pixmaps/
```

---

### Post by fng on 2005-05-21
its now in backports

---

### Post by zaxer on 2005-05-21
[QUOTE=bored2k]If you installed as a regular user :
```
tar xzf 22348-gaim-iconset-1.1.tar.gz 
cp -rf gaim/ ~/.local/share/pixmaps/
```
[/QUOTE]

I tried this and worked.

Thanks bored2k!  :)

---

