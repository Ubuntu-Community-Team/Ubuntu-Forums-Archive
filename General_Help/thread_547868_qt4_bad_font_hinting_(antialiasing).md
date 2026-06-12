---
title: "qt4 bad font hinting (antialiasing)"
date: 2007-09-10
forum: General Help
---

### Post by MustNotSleep on 2007-09-10
this happened to me recently, after i hosed my last Feisty setup, that strangely i've never had a problem with in the past.. the first thing i do when installing a new system is performing [this](http://ubuntuforums.org/showthread.php?t=235526) procedure to make my Gtk fonts look smooth as eggs.. but Qt4 is a whole 'nother issue...

i noticed the problem first with OpenOffice (2.2.0).. the menus, although somewhat antialiased, still look crappy compared to Gtk's.. but then i saw that it's not just OO, but every app that used Qt4 widgets, and i tend to use a few of them: KeepassX, SMPlayer, etc..

i attach two screenshots so you can see the difference between the way Qt4 looks (qtconfig, OO, KeepassX and SMPlayer) and Gtk (Totem, Gedit)..

i've been a few days with this thing and so far have made 0 progress.. i have tried making a custom ~/fonts.conf file, running fc-cache and emptying my /tmp.. restarting, of course.. nothing...

any ideas? i'm sure i'm not the only one with this.. i have found numerous threads on the intertubes, but no actual solution.. Trolltech has [some weird excuse](http://trolltech.com/developer/knowledgebase/662/), cleaning their hands of the matter..

btw, strangely enough, qt3 doesn't suffer from this problem.. running qtconfig-qt3 shows perfectly antialiased fonts..

any suggesion is greatly appreciated.. TIA!

---

### Post by MustNotSleep on 2007-09-14
nobody knows where i can fix this?

i keep expanding my Qt usage (recently started using QtOctave) and the fonts are really irking me...

anyone?

---

### Post by MustNotSleep on 2007-09-17
still an unresolved issue.. help!

---

### Post by MustNotSleep on 2007-09-21
hasn't anyone bumped into this issue other than me?

i really don't know where else to ask for help.. please, guys..

---

### Post by MustNotSleep on 2007-09-26
ok this is really getting amusing by now...

:confused:

---

### Post by MustNotSleep on 2007-10-01
still trying to get some help here...

:popcorn:

---

### Post by rvm4000 on 2007-10-03
I did the following:

KDE menu: System Settings->Appareance->Fonts. Click on Configure button for "Use anti-aliasing for fonts". 

On "Hinting style" choose "Medium" (everything except "Full" gives better fonts).

Result:

Before:
[[IMG]http://img514.imageshack.us/img514/4397/fonts1uk6.th.png[/IMG]](http://img514.imageshack.us/my.php?image=fonts1uk6.png)

Now:
[[IMG]http://img128.imageshack.us/img128/5713/fonts2wb3.th.png[/IMG]](http://img128.imageshack.us/my.php?image=fonts2wb3.png)

And qtconfig:
[[IMG]http://img130.imageshack.us/img130/641/fonts3sd7.th.png[/IMG]](http://img130.imageshack.us/my.php?image=fonts3sd7.png)

---

### Post by MustNotSleep on 2007-10-03
> **rvm4000 said:**
> I did the following:

KDE menu: System Settings->Appareance->Fonts. Click on Configure button for "Use anti-aliasing for fonts". 

On "Hinting style" choose "Medium" (everything except "Full" gives better fonts).

Result:

Before:
[[IMG]http://img514.imageshack.us/img514/4397/fonts1uk6.th.png[/IMG]](http://img514.imageshack.us/my.php?image=fonts1uk6.png)

Now:
[[IMG]http://img128.imageshack.us/img128/5713/fonts2wb3.th.png[/IMG]](http://img128.imageshack.us/my.php?image=fonts2wb3.png)

And qtconfig:
[[IMG]http://img130.imageshack.us/img130/641/fonts3sd7.th.png[/IMG]](http://img130.imageshack.us/my.php?image=fonts3sd7.png)
thanks for your help!

that would be great and all, but i'm using Gnome and have no access to KDE's control panel (and have no desire to install kdebase).

unless there's a way of installing *just* the font configuration utility (i thought qtconfig served that purpose)?

---

### Post by rvm4000 on 2007-10-04
I don't have gnome installed but maybe there's an option for that in its control panel.
I saw in the KDE control panel options to change fonts for gnome apps.

---

### Post by MustNotSleep on 2007-10-21
> **rvm4000 said:**
> I don't have gnome installed but maybe there's an option for that in its control panel.
I saw in the KDE control panel options to change fonts for gnome apps.
nope.

i updated to Gutsy the other day hoping this issue would be resolved, and it's still the same.

**please, someone here must know the solution..**

thanks in advance!

---

### Post by rainwoodman on 2007-12-19
I found a solution. make sure your ~/.fonts.conf have one line simlilar to this.

```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>

    <match target="font">
        <edit name="rgba" mode="assign">
            <const>rgb</const>
        </edit>
    </match>
</fontconfig>
```

QT, Openoffice(and other fontconfig programs which are not part of gtk) doesn't respect your gtk's font settings(which seems only to modify information in xrdb). However, since they ara raw fontconfig clients, they will proceed ~/.fonts.conf. then all we need is to make sure the ~/.fonts.conf is compatible same as your gtk settings. I think someone should submit a bug for QT and Openoffice. They should respect Xrdb settings, at least when running on X11.


> **MustNotSleep said:**
> this happened to me recently, after i hosed my last Feisty setup, that strangely i've never had a problem with in the past.. the first thing i do when installing a new system is performing [this](http://ubuntuforums.org/showthread.php?t=235526) procedure to make my Gtk fonts look smooth as eggs.. but Qt4 is a whole 'nother issue...

i noticed the problem first with OpenOffice (2.2.0).. the menus, although somewhat antialiased, still look crappy compared to Gtk's.. but then i saw that it's not just OO, but every app that used Qt4 widgets, and i tend to use a few of them: KeepassX, SMPlayer, etc..

i attach two screenshots so you can see the difference between the way Qt4 looks (qtconfig, OO, KeepassX and SMPlayer) and Gtk (Totem, Gedit)..

i've been a few days with this thing and so far have made 0 progress.. i have tried making a custom ~/fonts.conf file, running fc-cache and emptying my /tmp.. restarting, of course.. nothing...

any ideas? i'm sure i'm not the only one with this.. i have found numerous threads on the intertubes, but no actual solution.. Trolltech has [some weird excuse](http://trolltech.com/developer/knowledgebase/662/), cleaning their hands of the matter..

btw, strangely enough, qt3 doesn't suffer from this problem.. running qtconfig-qt3 shows perfectly antialiased fonts..

any suggesion is greatly appreciated.. TIA!

---

### Post by MustNotSleep on 2007-12-19
> **rainwoodman said:**
> I found a solution. make sure your ~/.fonts.conf have one line simlilar to this.

```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>

    <match target="font">
        <edit name="rgba" mode="assign">
            <const>rgb</const>
        </edit>
    </match>
</fontconfig>
```

QT, Openoffice(and other fontconfig programs which are not part of gtk) doesn't respect your gtk's font settings(which seems only to modify information in xrdb). However, since they ara raw fontconfig clients, they will proceed ~/.fonts.conf. then all we need is to make sure the ~/.fonts.conf is compatible same as your gtk settings. I think someone should submit a bug for QT and Openoffice. They should respect Xrdb settings, at least when running on X11.
that solved it for you? it had no effect on my machine.

it's been months now and this issue is still unresolved. frankly, i'm appalled by the lack of support from Trolltech and the lack of interest of the Ubuntu community to get this fixed.. we've gone a long way to make Linux a big player in the desktop market, but it's small things like this that add up to a shaky user experience..

sorry for the soapbox, but this, and other small unrelated issues with my system (like it woke up one morning with the wrong voltage and decided it won't boot without spewing fsck and swap errors.. wtf), is really irking me.. to fix this i'm considering the "format/reinstall" route i've grown accustomed to with Windows, and which Unix users have always made a huge deal about..

thanks for the help though rainwoodman..

---

### Post by rainwoodman on 2007-12-22
That works for QT4 for me. However after carefully examining, it turns out to be not helpful at OOo.

Just try put something wrong (e.g. a mismatch tag) in ~/.fonts.conf and start qtconfig-qt4 from a terminal,
If qt4 respect your ~/.fonts.conf ,then it will complain something is wrong with the file.
If it doesn't, check in your /etc/fonts/fonts.conf and /etc/fonts/conf.d whether 

```
  <include ignore_missing="yes">~/.fonts.conf</include> 
```

exsits.

If you are sure qt4 respect ~/.fonts.conf, 
perhaps you also need to add some lines about hinting in your ~/.fonts.conf to make hinting completely work.

```
    <match target="font"> 
        <edit name="rgba" mode="assign"> 
            <const>rgb</const> 
        </edit> 
        <edit name="hinting" mode="assign">
            <boolean>true</boolean>
        </edit>
        <edit name="hintstyle" mode="assign">
            <const>hintfull</const> <!--or what ever you prefer-->
        </edit>
    </match> 


```

If this also doesn't work, your should check whether your entire /etc/fonts/ directory is messed up, if you ever made tweaks in that directory.

I am using a different distribution(Fedora) so it is also possible that my workaround won't work for you since there should be some differences in system-wide configurations.

---

### Post by 1comment on 2007-12-27
I had the same problem. And adding the .fonts.conf to your home directory does work.
I tested it. One small change, instead of 'boolean' it needed to be 'bool'. After I placed it in home, Qt3 and Qt4 look the same.OpenOffice looked better too. Using ubuntu btw. 

Heres a screenshot, application on top is qtconfig-qt4,  the one below is qtconfig-qt3.


[IMG]http://img168.imageshack.us/img168/1509/screenshotmm7.png[/IMG]


Heres how the fonts.conf file looks. And indeed use the trick described earlier , make a error in the fonts.conf and load qtconfig-qt3 or qt4 and see if it complains about it. If it complains you know its being looked at. But it should work.

<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>

    <match target="font">
        <edit name="rgba" mode="assign">
            <const>rgb</const>
        </edit>
    </match>

    <match target="font">
        <edit name="rgba" mode="assign">
            <const>rgb</const>
        </edit>
        <edit name="hinting" mode="assign">
            <bool>true</bool>
        </edit>
        <edit name="hintstyle" mode="assign">
            <const>hintfull</const>
        </edit>
    </match>

</fontconfig>

---

### Post by MustNotSleep on 2007-12-28
> **1comment said:**
> I had the same problem. And adding the .fonts.conf to your home directory does work.
I tested it. One small change, instead of 'boolean' it needed to be 'bool'. After I placed it in home, Qt3 and Qt4 look the same.OpenOffice looked better too. Using ubuntu btw. 

Heres a screenshot, application on top is qtconfig-qt4,  the one below is qtconfig-qt3.


[IMG]http://img168.imageshack.us/img168/1509/screenshotmm7.png[/IMG]


Heres how the fonts.conf file looks. And indeed use the trick described earlier , make a error in the fonts.conf and load qtconfig-qt3 or qt4 and see if it complains about it. If it complains you know its being looked at. But it should work.

<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>

    <match target="font">
        <edit name="rgba" mode="assign">
            <const>rgb</const>
        </edit>
    </match>

    <match target="font">
        <edit name="rgba" mode="assign">
            <const>rgb</const>
        </edit>
        <edit name="hinting" mode="assign">
            <bool>true</bool>
        </edit>
        <edit name="hintstyle" mode="assign">
            <const>hintfull</const>
        </edit>
    </match>

</fontconfig>
yeah, still nothing. with your config, the only change i see is that the Monospace / Bitstream Vera Sans Mono font looks different (in a bad way) in my terminal. however, OpenOffice and all other QT programs look the same as before.

here are some screenshots:

[[IMG]http://img262.imageshack.us/img262/9116/fontsconfpl4.th.png[/IMG]](http://img262.imageshack.us/my.php?image=fontsconfpl4.png)
this is the normal setup after rebooting. .fonts.conf configured as per 1comment's suggestions. you can see qt4 fonts are still looking ugly. also check the gnome-terminal font.. that doesn't look at all like the Gnome Monospace / Bitstream Vera Sans Mono, and instead has some funny Courier-esque aliasing going on. actually, working with this font gets on my nerves *MORE* than having all QT apps with poor font hinting.

[[IMG]http://img80.imageshack.us/img80/577/fontsconferrorbq4.th.png[/IMG]](http://img80.imageshack.us/my.php?image=fontsconferrorbq4.png)
just to prove the point that QT *is* picking up my .fonts.conf file. also note the gedit instance and see how smoothly anti-aliased the menus and document fonts are.. *THAT'S* the way i want QT to look..

[[IMG]http://img403.imageshack.us/img403/8725/withoutfontsconfnz5.th.png[/IMG]](http://img403.imageshack.us/my.php?image=withoutfontsconfnz5.png)
finally, for reference, after i move the .fonts.conf file and restart the terminal, i'm back with smooth Monospace / Bitstream Vera Sans Mono rendering, and qt4 looks exactly the same.

i'm really not sure you guys are having the same problem as me, because so far nothing has worked for me. i'm really tempted to forget the whole thing, format and reinstall Gutsy from scratch. maybe i'll have better luck next time, eh?

---

### Post by 0x656b694d on 2008-01-16
[http://nikolai.prokoschenko.de/archives/164](http://nikolai.prokoschenko.de/archives/164)

enjoy! :)

---

### Post by MustNotSleep on 2008-01-16
> **0x656b694d said:**
> [http://nikolai.prokoschenko.de/archives/164](http://nikolai.prokoschenko.de/archives/164)

enjoy! :)
well crap.

even though i'm on Gutsy, i uninstalled the font package and restarted, hoping for the best.

it's still the same. :mad:

i guess this is one thing that'll miraculously get resolved once i reinstall Ubuntu from scratch...

thanks for your help though!

---

### Post by hghn on 2008-01-17
> **0x656b694d said:**
> [http://nikolai.prokoschenko.de/archives/164](http://nikolai.prokoschenko.de/archives/164)

enjoy! :)

Hi,

found this thread through google. the other methods do not work in my xubuntu, but this method works. Thank you guys.

and good luck to MustNotSleep!

---

### Post by MustNotSleep on 2008-01-17
> **hghn said:**
> Hi,

found this thread through google. the other methods do not work in my xubuntu, but this method works. Thank you guys.

and good luck to MustNotSleep!
thanks!

according to the QT bug report, any font with AA turned off will screw the AA for the rest of the fonts.. so i'm guessing there's another font i currently have installed with the setting off.. theoretically, couldn't i search for the offending string in /etc/fonts/conf.d/ and locate the bad setting, change it, or remove the font?

i tried looking for 'hinting' and 'alias' and didn't find anything useful..

---

### Post by guano on 2008-02-05
> **0x656b694d said:**
> [http://nikolai.prokoschenko.de/archives/164](http://nikolai.prokoschenko.de/archives/164)

enjoy! :)

Many thanks for that.

---

### Post by marciano on 2008-02-12
Still nothing here (Gutsy) :(:confused:

---

### Post by bilu on 2008-02-19
Just found out that activating subpixel rendering (either RGB ou vRGB) automatically forces full hinting on QT4. I don't know if this has been reported to Trolltech or not.

EDIT: Seems it wasn't reported [http://trolltech.com/developer/task-tracker/index_html?searchstr=subpixel+hinting&method=advsearch&bugs=on&sugs=on](http://trolltech.com/developer/task-tracker/index_html?searchstr=subpixel+hinting&method=advsearch&bugs=on&sugs=on)

Without subpixel rendering you can change between slight, medium and full hinting just fine, but everything feels blurry if you're not using either full hinting OR subpixel rendering.

Full hinting is too aggressive, it "chews" on most fonts, and very few look good.
Subpixel with full hinting on QT3 looks too colored. 

Despite my favorite being Slight Hinting + RGB Subpixel, I ended up using Full Hinting without Subpixel rendering, because is the only setting that looks uniform across QT3, QT4, GTK2 and OpenOffice  :neutral:

Tahoma seems to be the most readable font that survives full hinting and it's smaller than Deja Vu or Bitstream, I can have more text on screen and it's still readable. I'm using Consolas from Vista as my monospace font for the same reason.

EDIT2: A screenshot to show Tahoma w/ Full Hinting + no Subpixel in QT3, QT4, GTK2 and OpenOffice.

With Slight Hinting + RGB Subpixel, most look great. Candara from Vista is one of the most gorgeous fonts I've ever used.


Bruno

---

### Post by bilu on 2008-04-15
Filed a bug on the qt4 subpixel issue :

[https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/217729](https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/217729)

---

### Post by arang on 2008-05-23
i know many suffer cos of this and noone really cares so i'm bumping this with the hope that someone knows how to fix this super ugly bug that's been plaguing Ubuntu for more than 3 releases!!! i do too have the problem with qt4 in SMplayer and others , it looks so horrible, i also tried to uninstall that ming font BUT it didnt help, also the link to the information is broken and u cant read it  , please someone help, things might have changed in Hardy, devs! anyone!

---

### Post by bilu on 2008-05-23
The best I got so far was with autohinting enabled, have you tried it?

Bruno

---

### Post by arang on 2008-05-23
> **bilu said:**
> The best I got so far was with autohinting enabled, have you tried it?

Bruno

hi bruno, could u clarify about what u mean? cos i've tried the conf files in here , result nothing, i tried removing that ming font and nothing, there might be some other font poisoning the whole fonts for qt4 but i cant find it, so any ideas??? in any case please tell me what u mean exactly.

---

