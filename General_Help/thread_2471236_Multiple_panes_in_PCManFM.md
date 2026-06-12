---
title: "Multiple panes in PCManFM"
date: 2022-01-24
forum: General Help
---

### Post by zkab on 2022-01-24
I have Ubuntu 21.10 and PCManFM 1.3.2 and want to open PCManFM with 2 panes each pointing at different subdir.
How can that be done ... have spent a lot of time googling but still no solution.

---

### Post by dragonfly41 on 2022-01-24
I have just looked at PCManFM but I suggest you will find it easier to use a dual pane file manager.
I use Krusader extensively but there is also Double Commander.

Actually you can create two PCManFM windows and position them. I would use xdotool for that.

---

### Post by zkab on 2022-01-24
OK - thanks

---

### Post by schragge on 2022-01-24
Krusader depends on KDE though, while Double Commander has both a GTK2 and a Qt5 version. Worker has no extra dependencies beyond X11, but it will look out of place in a modern DE. 4Pane uses GTK3, but is, well, 4-panel ;). SpaceFM has a GTK2 and a GTK3 build and an easily switchable one-to-four panel layout. Its last release was 2018 though. gentoo is even older (2016) and GTK3.

Here is a table I once did.

**GUI**
[TABLE="width: 600"]
[TR]
[TD]2202[/TD]
[TD]2.50#r1793[/TD]
[TD][File Commander]("http://silk.apana.org.au/fc.html")[/TD]
[TD][Far]("https://www.farmanager.com")-like[/TD]
[/TR]
[TR]
[TD]2202[/TD]
[TD]1.14.0[/TD]
[TD][GNOME Commander]("https://gcmd.github.io")[/TD]
[TD]GTK2[/TD]
[/TR]
[TR]
[TD]2202[/TD]
[TD]1.0.4[/TD]
[TD][Double Commander]("http://doublecmd.sf.net")[/TD]
[TD]Pascal, GTK2|Qt5[/TD]
[/TR]
[TR]
[TD]2201[/TD]
[TD]15.9.15[/TD]
[TD][Cloud Commander]("https://cloudcmd.io")[/TD]
[TD]Node.js[/TD]
[/TR]
[TR]
[TD]2112[/TD]
[TD]4.10.0[/TD]
[TD][Worker]("http://boomerangsworld.de/cms/worker")[/TD]
[TD]X11[/TD]
[/TR]
[TR]
[TD]2105[/TD]
[TD]0.9.7[/TD]
[TD][muCommander]("http://www.mucommander.com")[/TD]
[TD]Java[/TD]
[/TR]
[TR]
[TD]2012[/TD]
[TD]7.0[/TD]
[TD][4Pane]("http://www.4pane.co.uk")[/TD]
[TD]4-pan; GTK3[/TD]
[/TR]
[TR]
[TD]1908[/TD]
[TD]2.7.2[/TD]
[TD][Krusader]("https://krusader.org")[/TD]
[TD]KF5[/TD]
[/TR]
[TR]
[TD]1803[/TD]
[TD]1.0.6[/TD]
[TD][SpaceFM]("http://ignorantguru.github.io/spacefm")[/TD]
[TD]1-to-4-pan; GTK2|3[/TD]
[/TR]
[TR]
[TD]1606[/TD]
[TD]0.20.7[/TD]
[TD][gentoo]("http://gentoo.sf.net")[/TD]
[TD]GTK3[/TD]
[/TR]
[TR]
[TD]1504[/TD]
[TD]0.20.0#0d7375b[/TD]
[TD][WCM Commander]("https://github.com/corporateshark/WCMCommander")[/TD]
[TD][Far]("https://www.farmanager.com")-like; git:2009; abandoned[/TD]
[/TR]
[TR]
[TD]1402[/TD]
[TD]0.9.1#92f616d[/TD]
[TD][EmelFm2]("https://github.com/tom2tom/emelfm2")[/TD]
[TD]GTK2|3; git:1704[/TD]
[/TR]
[TR]
[TD]1306[/TD]
[TD]0.3.7b1[/TD]
[TD][Fire Commander]("https://code.google.com/archive/p/firecommander")[/TD]
[TD][XPI]("https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions/Your_first_WebExtension")[/TD]
[/TR]
[TR]
[TD]0912[/TD]
[TD]0.2.0[/TD]
[TD][PerlFM]("https://metacpan.org/release/PerlFM")[/TD]
[TD]Perl[/TD]
[/TR]
[TR]
[TD]0911[/TD]
[TD]0.6.70[/TD]
[TD][Tux]("http://tuxcmd.sf.net")[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]0907[/TD]
[TD]0.91.5a[/TD]
[TD][X WinCommander]("http://xwc.sf.net")[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]0809[/TD]
[TD]4.1.0[/TD]
[TD][Beesoft Commander]("http://www.beesoft.pl/?id=bsc")[/TD]
[TD]Qt4[/TD]
[/TR]
[TR]
[TD]0511[/TD]
[TD]1.0#051109[/TD]
[TD][Not A Commander]("http://nac.sf.net")[/TD]
[TD]Tcl/Tk[/TD]
[/TR]
[TR]
[TD]0502[/TD]
[TD]0.0.12[/TD]
[TD][foXcommander]("http://foxdesktop.sf.net")[/TD]
[TD][FOX]("http://fox-toolkit.org")[/TD]
[/TR]
[/TABLE]

**TUI**
[TABLE="width: 600"]
[TR]
[TD]2202[/TD]
[TD]4.23[/TD]
[TD][vfu]("http://cade.datamax.bg/vfu")[/TD]
[TD]sid[/TD]
[/TR]
[TR]
[TD]2202[/TD]
[TD]0.17.2[/TD]
[TD][xplr]("https://xplr.dev")[/TD]
[TD]not [OFM]("http://www.softpanorama.org/OFM")[/TD]
[/TR]
[TR]
[TD]2201[/TD]
[TD]3.00.0007[/TD]
[TD][NDN]("http://ndn.muxe.com")[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]2201[/TD]
[TD]1.4[/TD]
[TD][clifm]("https://github.com/leo-arch/clifm")[/TD]
[TD]not [OFM]("http://www.softpanorama.org/OFM")[/TD]
[/TR]
[TR]
[TD]2111[/TD]
[TD]4.4[/TD]
[TD][nnn]("https://github.com/jarun/nnn")[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]2110[/TD]
[TD]r26[/TD]
[TD][lf]("https://github.com/gokcehan/lf")[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]2109[/TD]
[TD]0.12[/TD]
[TD][Vifm]("https://vifm.info")[/TD]
[TD]2-pan vi-keys[/TD]
[/TR]
[TR]
[TD]2108[/TD]
[TD]4.8.27[/TD]
[TD][Midnight Commander]("http://midnight-commander.org")[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]2107[/TD]
[TD]#240d283[/TD]
[TD][Bash Commander]("https://github.com/sergev/bash-commander")[/TD]
[TD]Bash 5.1 + [OFM]("http://www.softpanorama.org/OFM"); BSD[/TD]
[/TR]
[TR]
[TD]2009[/TD]
[TD]2.2[/TD]
[TD][fff]("https://github.com/dylanaraps/fff")[/TD]
[TD]not OFM[/TD]
[/TR]
[TR]
[TD]2009[/TD]
[TD]4.6#p10[/TD]
[TD][CLEX]("http://www.clex.sk")[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]2009[/TD]
[TD]0.24.3[/TD]
[TD][Wal Commander]("http://www.wal-commander.org")[/TD]
[TD][Far]("https://www.farmanager.com")-like[/TD]
[/TR]
[TR]
[TD]2006[/TD]
[TD]1.0.1[/TD]
[TD][Rover]("https://lecram.github.io/p/rover")[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]2001[/TD]
[TD]1.3.5[/TD]
[TD][hunter]("https://github.com/rabite0/hunter")[/TD]
[TD]Rust[/TD]
[/TR]
[TR]
[TD]1912[/TD]
[TD]1.9.3[/TD]
[TD][ranger]("https://ranger.github.io")[/TD]
[TD]miller|OFM-vi|OFM keys; Python[/TD]
[/TR]
[TR]
[TD]1908[/TD]
[TD]#bfe589a[/TD]
[TD][noice]("https://git.2f30.org/noice/log.html")[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]1908[/TD]
[TD]1.0500[/TD]
[TD][vshnu]("http://kinzler.com/me/vshnu")[/TD]
[TD]Perl; BSD[/TD]
[/TR]
[TR]
[TD]1907[/TD]
[TD]3.01j[/TD]
[TD][FDclone]("http://hp.vector.co.jp/authors/VA012337/soft/fd")[/TD]
[TD]not OFM[/TD]
[/TR]
[TR]
[TD]1807[/TD]
[TD]#9f4f145[/TD]
[TD][hund]("https://github.com/miahuoe/hund")[/TD]
[TD]vi-keys[/TD]
[/TR]
[TR]
[TD]1706[/TD]
[TD]3.1#148[/TD]
[TD][Last File Manager]("https://inigo.katxi.org/devel/lfm")[/TD]
[TD]1-/2-pan; Python; hg:2101[/TD]
[/TR]
[TR]
[TD]1404[/TD]
[TD]2.12.3#431[/TD]
[TD][Personal File Manager]("http://p-f-m.sf.net")[/TD]
[TD]1-pan ~vi-keys; Perl; svn:1704; BSD[/TD]
[/TR]
[TR]
[TD]0610[/TD]
[TD]0.52[/TD]
[TD][MCJ]("http://mc-gcj.sf.net")[/TD]
[TD]Java:gcj[/TD]
[/TR]
[/TABLE]

**[XTree]("http://www.xtreefanpage.org") TUI clones**
[TABLE="width: 600"]
[TR]
[TD]2112[/TD]
[TD]3.0.3[/TD]
[TD][UnixTree]("http://www.unixtree.org")[/TD]
[/TR]
[TR]
[TD]2111[/TD]
[TD]2.04[/TD]
[TD][Ytree]("http://www.han.de/~werner/ytree.html")[/TD]
[/TR]
[TR]
[TD]0808[/TD]
[TD]1.3b[/TD]
[TD][linuXtree]("http://www.stahlke.org/dan/lxt")[/TD]
[/TR]
[/TABLE]

---

### Post by uninvolved on 2022-01-24
You can possible just use SpaceFM. I'm not sure if it's exactly what you want, however.

Make it dual pane in the view menu, open the directories you want in each tab, and you're actually all done. That's all you need to do.

When you re-open SpaceFM, it should open the same directories you had open when you closed it.

---

### Post by zkab on 2022-01-25
I tried to install Double Commander from [https://software.opensuse.org//download.html?project=home%3AAlexx2000&package=doublecmd-gtk](https://software.opensuse.org//download.html?project=home%3AAlexx2000&package=doublecmd-gtk) but there was 
only a version for 21.04 and since I have 21.10 I received error ... 'unmet dependencies'
I will test SpaceFM ...

---

### Post by vanadium on 2022-01-25
Open a window of PCManFM and hit Super+Left. Then hit Super+N to create a new window of PCManFM, and hit Super+Right to position it on the right side.

---

### Post by dragonfly41 on 2022-01-25
Although Krusader suggested earlier does come with baggage, the added features outweighs this.
You can add your custom UserActions. For example I can push full filepaths into a server.
Usage is limited only by ingenuity.
You can have an embedded terminal running under the dual panes.

[https://docs.kde.org/trunk5/en/krusader/krusader/krusader-tools.html](https://docs.kde.org/trunk5/en/krusader/krusader/krusader-tools.html)

---

### Post by coley9225 on 2022-01-25
I use PCmanFM in my lubuntu 20.04 install. I get double panes by pressing  <f6>, and a new pane opens on left side of window. Click in a pane to make it active and navigate to where you want to go. I use it a lot for copy/paste or moving files from 1 directory to another. This is persistent, so if you close PCmanFM, and relauch, it will open to dual panes. If you don't want dual panes, simply press <f6> again. Hope this helps.

---

### Post by zkab on 2022-01-25
Nothing happens with <f6> but <f3> gives me a new pane ... but it is not persistent ...

---

### Post by guiverc on 2022-01-25
> **coley9225 said:**
> I use PCmanFM in my lubuntu 20.04 install. I get double panes by pressing  <f6>, and a new pane opens on left side of window. Click in a pane to make it active and navigate to where you want to go. I use it a lot for copy/paste or moving files from 1 directory to another. This is persistent, so if you close PCmanFM, and relauch, it will open to dual panes. If you don't want dual panes, simply press <f6> again. Hope this helps.

Lubuntu 18.10 & later have not offered `pcmanfm` as Lubuntu no longer uses GTK2.

It's possible you're referring to `pcmanfm-qt` which is a modern fork/port of `pcmanfm` that uses Qt5.  It was created by the original author [PCMan]("https://github.com/PCMan"), but is actually a different program, as has changed rather significantly since original fork.

*The original `pcmanfm` (GTK2) was first ported to GTK3 before that port was abandoned (PCMan wrote about it being too heavy leading to LXDE's port to GTK3 being abandoned and instead LXDE devs joining with Razor-Qt team in creating new replacement for LXDE being the LXQt project). This led to the Qt5 version & the modern `pcmanfm-qt` now found in Lubuntu.*

---

### Post by dragonfly41 on 2022-01-25
I have added a twist to this by adding .. into Krusader .. a UserAction which launches pcmanfm-qt at the directory active in Krusader.  This is the command I use:

pcmanfm-qt %aPath%

%aPath% is the active path of selected Krusader panel (of two).

I can add as many UserActions as needed.

Added note:

Here is another example of command.

pcmanfm-qt %lPath% %rPath%

This launches the Krusader left panel and right panel as separate tabs in pcmanfm-qt window.

If there are multiple usages it might be useful to create profiles. Or multiple UseActions under new category File Manager.

---

### Post by coley9225 on 2022-01-26
Guiverc, you are correct, I'm using PCmanFM-qt. I was unaware it was a different program, and apologize if it created unnecessary confusion.

---

### Post by zkab on 2022-01-27
I installed PCManFM-QT with snap ... it works OK with <f6> dual/persistant panes.
The layout look somewhat boring ... how do I install themes?

---

### Post by zkab on 2022-01-27
I installed PCManFM-QT with snap ... it works OK with dual persistent panes.
The layout looks somewhat dull ... are there any themes to add?

---

### Post by zkab on 2022-01-27
pcmanfm-qt --help gives:
Usage: pcmanfm-qt [options] [FILE1, FILE2,...]

but when I launch the command:

pcmanfm-qt /home/forsete/Downloads /home/forsete/Dropbox

it opens pane(left): Downloads,Dropbox and pane(right): Downloads
How can I make PCManFM to open pane(left): Downloads and pane(right): Dropbox

Sorry about my double post above ...

---

### Post by dragonfly41 on 2022-01-27
Toolbar > View > Split View (or F6)

---

