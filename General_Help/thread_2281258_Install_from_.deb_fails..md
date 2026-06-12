---
title: "Install from .deb fails."
date: 2015-06-05
forum: General Help
---

### Post by WacoJohn on 2015-06-05
Ths objective is to install catweasel to Lubuntu 32-bit, current version.  Obtained icecat_31.2.0-1+7.0trisquel2_i386.deb and saved to desktop.  Opened it with GDebi and get the following:

[ATTACH=CONFIG]262455[/ATTACH]

and your help is appreciated in advance.

---

### Post by kerry_s on 2015-06-05
[https://wiki.ubuntu.com/IceCat](https://wiki.ubuntu.com/IceCat)

---

### Post by WacoJohn on 2015-06-05
> **kerry_s said:**
> [https://wiki.ubuntu.com/IceCat](https://wiki.ubuntu.com/IceCat)

Thank you.  That is exactly what I have been following.  His method #1 fails:

> **Gnuzilla Team Repository (Recommended)**

[COLOR=#333333][FONT=Ubuntu Beta]IceCat is available in a repository created by the Gnuzilla Team. By adding this repository, you will be able to install IceCat through any package manager of your choice, and will automatically stay up to date with the latest upgrades from the Gnuzillla Team.[/FONT][/COLOR]
**Quick Method (9.10 Karmic and later)**

[COLOR=#333333][FONT=Ubuntu Beta]If you are using a version of Ubuntu which is 9.10 Karmic or later, you can add the IceCat repository with one command. The following command will add the Gnuzilla Team's repository, update your package lists, and then install the IceCat browser all in one go:[/FONT][/COLOR]
[COLOR=#333333]sudo add-apt-repository ppa:gnuzilla-team/ppa && sudo apt-get update && sudo apt-get install icecat -y[/COLOR]

The command fails.  My research into **that** failure, says that item is not available.

Hence, I went to downloading the .deb from [http://archive.trisquel.info/trisquel/pool/main/i/icecat/](http://archive.trisquel.info/trisquel/pool/main/i/icecat/)  ... put it on my desktop, and tried to install it with Gdebi which errors.  I will go back through it all ... I guess, .. and see if I can find out what is wrong.

Anyone have a clue, .. please let me know.

Thank you again.

EDIT:

Guess it's good and messed up now.  Tried a Gdebi install from command line:

```
wacojohn@ubuntuCOMPAQ:~/Desktop$ sudo gdebi-gtk icecat_31.2.0-1+7.0trisquel2_i386.deb
[sudo] password for wacojohn: 

(gdebi-gtk:3666): Gtk-CRITICAL **: gtk_label_set_text: assertion 'GTK_IS_LABEL (label)' failed

(gdebi-gtk:3666): Gtk-CRITICAL **: gtk_label_set_text: assertion 'GTK_IS_LABEL (label)' failed
^CTraceback (most recent call last):
  File "/usr/lib/python3/dist-packages/apt/debfile.py", line 87, in filelist
    self._debfile.data.go(lambda item, data: files.append(item.name))
SystemError: E:read, still have 23552 to read but none left

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/bin/gdebi-gtk", line 79, in <module>
    app = GDebiGtk(datadir=data,options=options,file=afile)
  File "/usr/share/gdebi/GDebi/GDebiGtk.py", line 151, in __init__
    self.open(file)
  File "/usr/share/gdebi/GDebi/GDebiGtk.py", line 312, in open
    for name in self._deb.filelist:
  File "/usr/lib/python3/dist-packages/apt/debfile.py", line 87, in filelist
    self._debfile.data.go(lambda item, data: files.append(item.name))
KeyboardInterrupt
wacojohn@ubuntuCOMPAQ:~/Desktop$ sudo gdebi-gtk icecat_31.2.0-1+7.0trisquel2_i386.deb


```

Maybe someone knows how to install this deb file.

---

### Post by ian-weisser on 2015-06-05
The error means that both firefox and iceweasel depend upon the package 'hunspell-en-us'...
...but on different versions of that package.

A or B. Not both.
You must uninstall the Ubuntu version of Firefox OR find a compatible version of iceweasel

Incompatible dependencies are a common problem when using .debs off the dirty,dirty internet. That's why distros like Debian and Ubuntu provide entire repositories of tested, compatible software...except, of course, for 'iceweasel.'

---

### Post by WacoJohn on 2015-06-05
> **ian-weisser said:**
> The error means that both firefox and iceweasel depend upon the package 'hunspell-en-us'...
...but on different versions of that package.

A or B. Not both.
You must uninstall the Ubuntu version of Firefox OR find a compatible version of iceweasel

Incompatible dependencies are a common problem when using .debs off the dirty,dirty internet. That's why distros like Debian and Ubuntu provide entire repositories of tested, compatible software...except, of course, for 'iceweasel.'

Thank you, Mr. W. for an excellent reply and explanation.  I have been running IceWeasel on a Raspberry PI II, Debian Wheezy, for quite some time and like it.

I have another thread about an Epiphany browser problem on Lubuntu, and I don't want to uninstalL FF until that is fixed ... if ever.  Based on your great info, I guess I will forgo IceCat for now.  I am going to assume I have done no damage to the Lubuntu installation with this IceCat fiasco.  Let me know if you disagree, .... and thank you again.

---

