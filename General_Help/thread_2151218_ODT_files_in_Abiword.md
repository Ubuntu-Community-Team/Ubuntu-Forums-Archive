---
title: "ODT files in Abiword"
date: 2013-06-03
forum: General Help
---

### Post by Xpinguin on 2013-06-03
Abiword 2.9.2

I'm trying to work with .odt files (open document text).  Many sources
mention opening odt files in Abiword, sometimes mentioning plugins.

On my system, Xubuntu 12.04 64-bit, in the "Open File" or "Save File As"
 dialogs the field named "Open file as type:" does not iclude .odt as a
 file type.  Also Abiword crashed when I tried to open an .odt file.

So far all software I have installed on my system were from Canonical
or Partners via the "Ubuntu Sofware Center", and since I'm a newbie to
Linux I'm trying to stay close to Canonical to minimize problems.  Now
the problem is that on [[http://www.abisource.com/]](http://www.abisource.com/]) they say:

    - latest stable release version: 2.8.6
    - latest development release version: 2.9.4

Xubuntu (Ubuntu Sofware Center) has installed version 2.9.2 on my
system.  It is installed by default when installing the O/S.

On [[http://www.abisource.com/download/plugins.phtml]:](http://www.abisource.com/download/plugins.phtml]:)
AbiWord Plugins
Note that plugins are not shipped separately anymore, but are shipped
 in the main AbiWord installer that is available on our download page.
 Plugins can be selected during the installation of AbiWord.

Can I fix my problem by using Canonical (main, universe, or Partners)
repositories, or should I uninstall the version currently installed
and install the "latest stable release" via the Abiword web site ?

The "Plugin Matrix" at [[http://www.abisource.com/wiki/PluginMatrix]](http://www.abisource.com/wiki/PluginMatrix])
does not mention the ODT format, nor ODF.


Thanks in advance.

---

### Post by snowpine on 2013-06-03
I recommend to simply install LibreOffice writer from the Software Center. It's superior to Abiword in just about every way. (I say this as a professional writer and editor.) Then you will have native support for .odt, problem solved. :)

---

### Post by gifford on 2013-06-03
Would agree with the above...install Libreoffice.
It is in ongoing development and has regular updates.

---

### Post by Charlotte18 on 2013-06-03
Make sure that you have the abiword-common, abiword-dgb, and libabiword-2.9 packages installed in xubuntu.

---

### Post by Xpinguin on 2013-06-05
Hi,

 Charlotte18, I have all three already, if when you wrote "abiword-dgb" you
meant "abiword-dbg" (debugging symbols).  Am I right in assuming that I
should periodically go through the Abiword web site to get updates ?  I'm
asking because I noticed that in the Ubuntu Sofware Center Abiword,
 along with many other apps, says "Canonical does not provide updates
for [app name]...".

I'm a bit surprised about this since Abiword is the pre-installed default
word processor in Xubuntu.

Thanks for helping out.

---

### Post by Xpinguin on 2013-06-05
Thank you snopine & gifford.  I will try a bit more to get Abiword to work before I switch
to Libreoffice.  I've worked a lot with OpenOffice, especially Writer.  If I can install only
the word processor I'll try it when I give up with Abiword.

---

### Post by Charlotte18 on 2013-06-05
I'm using lubuntu (not xubuntu), and Abiword can read and save odt files.  I just checked under Tools > Plugins, and I see that my Abiword has a plugin called OpenDocument Filter, Version 2.9.2. This came pre-installed in lubunut.  

I believe you have a package in the xubuntu repositories called abiword-plugins. Install that. If you do not see abiword-plugins, look for a package called abiword-plugins-odffilter or something like that.  

This will get it working.

> **Xpinguin said:**
> Hi,

 Charlotte18, I have all three already, if when you wrote "abiword-dgb" you
meant "abiword-dbg" (debugging symbols).  Am I right in assuming that I
should periodically go through the Abiword web site to get updates ?  I'm
asking because I noticed that in the Ubuntu Sofware Center Abiword,
 along with many other apps, says "Canonical does not provide updates
for [app name]...".

I'm a bit surprised about this since Abiword is the pre-installed default
word processor in Xubuntu.

Thanks for helping out.

---

### Post by Xpinguin on 2013-06-05
In the Ubuntu Software Center, which by the way I find a pain to work with because it won't sort
by name like it's supposed to (but that's for another thread), the only package shown when I
 search for "Abiword" is the main Abiword package, and when I click the "More Info" button I get
 info that doesn't make sense to me:

1) It says "This package includes many of the available import/export plugins allowing Abiword
    to interact with ODT, WordPerfect, and other formats".  Obviously it is not the case for me.

2) In the "Add-ons" section of the same page, it shows two plugins: one about Grammar
    checking, and the other called "Equation editor".  Nothing resembling "OpenDocument Filter",
    "odffilter", or "ODT".  These two plugin/add-ons packages are not shown when I do a search
    using Ubuntu Software Center, so I conclude that they only come bundled with the main
    Abiword package.

I will go to the Abiword web site with my confusion and see what I can do from there.

I'll post here with the results.

Thanks again.

---

### Post by snowpine on 2013-06-05
There are several alternatives to Ubuntu Software Center:

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Charlotte18 on 2013-06-05
Try to install abiword-plugins via the terminal. Open the terminal and type:

sudo apt-get install abiword-plugins

---

### Post by Xpinguin on 2013-06-05
Yes, I've looked at that already.  I think I will ty using Synaptic and see.

Thanks again.

> **snowpine said:**
> There are several alternatives to Ubuntu Software Center:

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Xpinguin on 2013-06-05
> **Charlotte18 said:**
> Try to install abiword-plugins via the terminal. Open the terminal and type:

sudo apt-get install abiword-plugins

I tried that and the result was: "E: Unable to locate package abiword-plugins".

I went back for the third time to the _Abiword web site_ and they say:

> Note that plugins are not shipped separately anymore, but are
shipped in the main AbiWord installer that is available on our [download page]("http://www.abisource.com/download/").
 Plugins can be selected during the installation of AbiWord.

On the download page, the Linux section says:
> AbiWord is usually available from your Linux distribution repository.
Ubuntu users should go [here]("http://abisource.com/wiki/Install_on_Ubuntu").


So I think my best bet is to uninstall version 2.9.2 and install the last stable
version (2.8.6) with the .deb file from the Abiword site.  After that, if I can't
read or save odt format files I will give up and install the LibreOffice word
processor.

Thanks again.

---

### Post by Charlotte18 on 2013-06-05
Well, I have 2.9.2 in lubuntu, and the plugin is for odt is installed by default and working. For the sake of curiosity and to help others, I'd like to see your xubuntu Abiword working as mine does. What do you see when you go to Tools > Plugins in Abiword?

---

### Post by Xpinguin on 2013-06-05
It's empty !

There's the "Install new plugin" button, that when clicked on asks me
for a file/directory.  There are apparently no plugins installed.

---

### Post by Dennis N on 2013-06-05
There were problems with Abiword 2.92 that was included with the 12.04 releases in Apr 2012: 

[http://ubuntuforums.org/showthread.php?t=2004848](http://ubuntuforums.org/showthread.php?t=2004848)

Since then, there is an newer version of Abiword 2.92 that has fixes. But that did not come until 12.10.

I agree with those who suggest Libre Office. You do not need to install all parts of Libre Office - you could install Libre Office Writer.

---

### Post by Charlotte18 on 2013-06-05
Check the following folder:

/usr/lib/i386-linux-gnu/abiword-2.9/plugins

In this folder, I have files called opendocument.so and openwriter.so

Do you have those?

---

### Post by Xpinguin on 2013-06-05
Yes I have them in  /usr/lib/x86_64-linux-gnu/abiword-2.9/plugins.

The more I work on this, the more confused I get.

I'm new to Linux... just in case it's not obvious already.

---

### Post by Charlotte18 on 2013-06-05
In Abiword, do you see the Opendocument plugin when you go to Tools > Plugins?

---

### Post by Xpinguin on 2013-06-05
Like I said in #14 of this thread all I get is a way to select a file (install new plugin button).

The "Active Plugins" field is empty.

Clicking on Help in that windows points to the wrong directory to open a local help file
with Firefox: /usr/share/abiword-2.9/help/en-US/interface/dialogplugins.html.  A search
for "dialogplugins" in /usr/ comes up empty.  I guess that's for another thread, or maybe
not.  I don't know.

---

### Post by Charlotte18 on 2013-06-06
If you can select a file with the install new plugin button, why not try to install the opendocument.so and openwriter.so plugins from their location in /usr/lib/i386-linux-gnu/abiword-2.9/plugins?

Also, I'm curious about something. Is your abiword 2.9 a fresh install, or is your abiword 2.9 a install that has been upgraded from a previously installed version?

---

### Post by kurt18947 on 2013-06-06
I've installed LibreOffice on the Xubuntu installs I've done.  Abiword was chosen because it's 'lighter' than LibreOffice.  I've used LibreOfffice' ppa to install ver. 4.0.x using the procedure here:

[http://www.webupd8.org/2013/03/install-libreoffice-40-in-ubuntu-1204.html](http://www.webupd8.org/2013/03/install-libreoffice-40-in-ubuntu-1204.html)

Not being real comfortable with terminal is not an impediment; copy/paste works just fine on webupd8.  Open a terminal in the first account you created when installing, that account will have sudo privileges by default.  Copy the two lines  from webupd8 into the terminal.  This is the repository for the stable version of LibreOffice.  There's another for 'bleeding-edge' versions. 

```

sudo add-apt-repository ppa:libreoffice/libreoffice-4-0

```
and press 'enter' to agree to install the repository.  Then update your repositories. 

```

sudo apt-get update

```

LibreOffice 4 should be there. You can install just the parts you want if you wish.

I recall the Abiword people were not thrilled that 'in-development' 2.9.x was included rather than the stable 2.8.x

---

### Post by Xpinguin on 2013-06-06
Thanks kurt18947,

I'll use the info, later.  I'm still trying to get Abiword to work correctly and to help others
figure out what's going on.

If I was one of those people who worked on Abiword, I would be displeased also.
Canonical make Abiword look bad.  It's not Abiword's fault.  Canonical picked the
version.  I guess since were're in an Open Source environment anyone can use
a developpment version of any application or library once it has been released.
Canonical must have had a good reason to pick 2.9.2, I guess.

---

### Post by Xpinguin on 2013-06-06
> **Charlotte18 said:**
> If you can select a file with the install new plugin button, why not try to install the opendocument.so and openwriter.so plugins from their location in /usr/lib/i386-linux-gnu/abiword-2.9/plugins?

Because up until now I did not know what type of file it was asking for.  I don't want to mix
things up, like user specific config with system wide config, session config, etc. before
I know my way around a bit more.

Is what you suggest the standard way, file type, directory to install applications plugins ?

Maybe I'm trying too hard to stay kosher.

> **Charlotte18 said:**
> Also, I'm curious about something. Is your abiword 2.9 a fresh install, or is your abiword 2.9 a install that has been upgraded from a previously installed version?

Abiword 2.9.2 is part of my fresh install of Xubuntu:
6 PACKAGES:  abiword, abiword-common, ttf-punjabi-fonts, abiword-plugin-grammar,
             abiword-plugin-mathview, libabiword-2.9

ttf-punjabi-fonts version:  0.5.11ubuntu1

the five other ones:         2.9.2+svn20120213

All 6 packages were installed with my installation of Xubuntu.

Software Center shows no updates for Abiword since the original installation.

I don't know if some updates have been done outside of the Software Center,
for example when I did "apt-get update" and "apt-get upgrade" a few times.
There is probably a way with apt-get to find out what IT has done so far, but
for lack of time I can't research that right now.

My system is setup to notify me immediately when updates are available, and
so far I have installed them all each time.

---

### Post by Xpinguin on 2013-06-06
-

---

### Post by Xpinguin on 2013-06-06
Sorry, didn't find how to delete one of my posts.

---

### Post by Xpinguin on 2013-06-06
Adding "opendocument.so" and "openwriter.so" via Tools -> Plugins did not work.
Whatever happens, after closing and restarting Abiword the plugins are not there.
I can save a file in .odt format immediately after installing the plugin's .so file but
when I open that file its content is gibberish.  Anyway the plugin(s) won't stick.
Rebooting or re-logging doesn't change anything.

I'm getting close to switching to LibreOffice Writer.

Thanks for trying to help.

---

### Post by Charlotte18 on 2013-06-06
In Abiword, when you go to Edit > Preferences and click the General tab, is "Automatically load all plugins found" checked?  If not, check it.

If so, then open the terminal and type the following commands separately:

sudo chmod ugo+rwx /usr/lib/i386-linux-gnu/abiword-2.9/plugins/

Then:

sudo chmod ugo+rwx /usr/lib/i386-linux-gnu/abiword-2.9/plugins/*

---

### Post by cincinnatus13 on 2013-06-06
You could search for that missing plugins package in the terminal- apt-cache search abiword-* or just plain abiword

I agree with the others though that Libreoffice is the best bet. I don't think it's all that heavy and it is just a better product overall. I understand Abiword's purpose but it has its caveats.

---

### Post by cincinnatus13 on 2013-06-06
You could search for that missing plugins package in the terminal- ```
apt-cache search abiword-*
``` or just plain abiword

I agree with the others though that Libreoffice is the best bet. I don't think it's all that heavy and it is just a better product overall. I understand Abiword's purpose but it has its caveats.

---

### Post by Xpinguin on 2013-06-06
> **cincinnatus13 said:**
> You could search for that missing plugins package in the terminal- apt-cache search abiword-* or just plain abiword

I agree with the others though that Libreoffice is the best bet. I don't think it's all that heavy and it is just a better product overall. I understand Abiword's purpose but it has its caveats.

[SIZE=3][FONT=courier new][SIZE=2]username@machine:~$ apt-cache search abiword[/SIZE]
[FONT=system]DISPLAYS:[/FONT]
[SIZE=2]libenchant-voikko - Voikko spell-checker libenchant plugin
abiword - efficient, featureful word processor with collaboration
abiword-common - efficient, featureful word processor with collaboration -- common files
abiword-dbg - debugging symbols for abiword word processor
abiword-plugin-grammar - grammar checking plugin for AbiWord
abiword-plugin-mathview - equation editor plugin for AbiWord
libabiword-2.9 - efficient, featureful word processor with collaboration -- shared library
libabiword-2.9-dev - efficient, featureful word processor with collaboration -- development files
libgtkmathview-bin - rendering engine for MathML documents
libgtkmathview-dev - rendering engine for MathML documents
libgtkmathview0c2a - rendering engine for MathML documents
pubtal - Template driven web site builder for small sites
python-abiword - Python AbiWidget and TableWidget wrappers
tea - text editor with syntax highlighting & UTF support[/SIZE][/FONT][/SIZE][SIZE=2]
[/SIZE]
Nothing related to Open Document Text, OpenOffice Writer, ODF, or
anything of the sort.

Now I would understand Microsoft not wanting to implement ODT,
but Abiword/Ubuntu/Canonical ?  I'm surprised, again.  Life is full
of surprises, not always as good as chocolates though.  ODT is
the native OpenOffice Writer file format. Am I the only person who
 switched from OpenOffice (XP) to Xubuntu or any other distro
which includes Abiword as default word processor ?

Thanks for the suggestion, and sorry for the ranting.

---

### Post by Xpinguin on 2013-06-06
> **Charlotte18 said:**
> In Abiword, when you go to Edit > Preferences and click the General tab, is "Automatically load all plugins found" checked?  If not, check it.

IT LOOKS LIKE A SUCCESS !

I really have to go now but I was able to open a previously created test
document and this time it was't gibberish but the correct content.

Unfortunately I can't remember if the option in question was checked
initially.  If it was, and I unchecked it, then you may insult me all you
want.  I'll agree with you wholehartedly.

Thank you very much Charlotte18, and the others for your patience.

There are still a few hickups with Abiword but the main thing for me
is apparently solved.

---

### Post by Charlotte18 on 2013-06-06
Too simple. I wish I'd thought of that three days ago.

---

