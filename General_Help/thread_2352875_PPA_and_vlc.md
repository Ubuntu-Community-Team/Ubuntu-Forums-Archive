---
title: "PPA and vlc"
date: 2017-02-16
forum: General Help
---

### Post by anon_private on 2017-02-16
I would like to use a PPA to keep vlc up to date.

The only PPA that I can find is for ubuntu ver 15 and 16

I use kubuntu ver 14.04

I believe that kubuntu will be fine because it is essentially ubuntu, but I am concerned because I am using version 14.04, and wonder if it will be compatible. I do not want to break my system.

Advice please.

---

### Post by &amp;KyT$0P# on 2017-02-16
I use this one - [https://launchpad.net/~marian.kadanka/+archive/ubuntu/vlc]("https://launchpad.net/~marian.kadanka/+archive/ubuntu/vlc")

---

### Post by #&amp;thj^% on 2017-02-16
There is also this one:
[https://launchpad.net/~n-muench/+archive/ubuntu/vlc](https://launchpad.net/~n-muench/+archive/ubuntu/vlc)
I have no experience with either PPA

---

### Post by SeijiSensei on 2017-02-16
I use Doug McMahon's PPA for 14.04: [https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media)

You might consider trying SMPlayer with mpv as the player engine.  It's in his PPA as well.  It's the only player I've used for years now.

---

### Post by deadflowr on 2017-02-16
What kernel are you using?
I ask because snaps are now available on 14.04,
but they require the 4.4 kernel series to be installed.

*(To install the snap package on 14.04,simply run:
```
sudo apt install snapd
```
then reboot and to install the vlc snap (daily) run
```
sudo snap install vlc
```
what's more, snaps are transactional and set to update automatically.
so you can both let it update without intervention and revert the package if the update is bad/buggy/borked.)

**sorry for the infomercial.
 
but again as asked, if you need the 3.13 kernel series, ignore.

---

### Post by anon_private on 2017-02-17
> **halogen2 said:**
> I use this one - [https://launchpad.net/~marian.kadanka/+archive/ubuntu/vlc](https://launchpad.net/~marian.kadanka/+archive/ubuntu/vlc)

Of the selection, I like the look of this one.

Couple of related questions. I have been wondering about PPA's and the programmes themselves. Why use a PPA, why not just download and install the latest software, in this case vlc?

> **1fallen said:**
> There is also this one:
[https://launchpad.net/~n-muench/+archive/ubuntu/vlc](https://launchpad.net/~n-muench/+archive/ubuntu/vlc)
I have no experience with either PPA


I am a little concerned regarding the number of failed builds with this PPA

> **SeijiSensei said:**
> I use Doug McMahon's PPA for 14.04: [https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media)

You might consider trying SMPlayer with mpv as the player engine.  It's in his PPA as well.  It's the only player I've used for years now.

This PPA has some cautions.

Out of interest, if someone un-installs the software, say, vlc, should one also un-install the PPA. I expect so

> **deadflowr said:**
> What kernel are you using?
I ask because snaps are now available on 14.04,
but they require the 4.4 kernel series to be installed.

*(To install the snap package on 14.04,simply run:
```
sudo apt install snapd
```
then reboot and to install the vlc snap (daily) run
```
sudo snap install vlc
```
what's more, snaps are transactional and set to update automatically.
so you can both let it update without intervention and revert the package if the update is bad/buggy/borked.)

**sorry for the infomercial.
 
but again as asked, if you need the 3.13 kernel series, ignore.

I have a kernel within the 4.4 series, but I have never heard of snaps. Looking into it, it looks a 'step too far' at the moment.

Best wishes

---

### Post by SeijiSensei on 2017-02-17
> **anon_private said:**
> This PPA has some cautions.

Out of interest, if someone un-installs the software, say, vlc, should one also un-install the PPA. I expect so

If you don't want any of the other packages in the PPA, then yes you can remove it.  However leaving it in your sources won't affect anything either.

---

### Post by &amp;KyT$0P# on 2017-02-17
> **anon_private said:**
> Of the selection, I like the look of this one.
Glad to help. :KS

> Couple of related questions. I have been wondering about PPA's and the programmes themselves. Why use a PPA, why not just download and install the latest software, in this case vlc?
Because, most often, the "Linux" download of the latest software is only a source tarball.  You're left to compile it yourself.  And usually they don't offer the option to build a .deb package, so you're also left to install with [FONT=Courier New]sudo make install[/FONT].

Problems with that are,
 A) finding the build dependencies isn't always easy;
 B) compiling can be very time-consuming, and you can't do other things with the machine while it's compiling;
 C) if you ever decide to upgrade or remove the software, uninstalling what you have might be non-trivial.

... and for people like me, repeating all that on every *buntu machine I admin or help support?  I rather take the easier, faster, and more portable route. :cool:

---

### Post by anon_private on 2017-02-17
> **halogen2 said:**
> Glad to help. :KS


Because, most often, the "Linux" download of the latest software is only a source tarball.  You're left to compile it yourself.  And usually they don't offer the option to build a .deb package, so you're also left to install with [FONT=Courier New]sudo make install[/FONT].

Problems with that are,
 A) finding the build dependencies isn't always easy;
 B) compiling can be very time-consuming, and you can't do other things with the machine while it's compiling;
 C) if you ever decide to upgrade or remove the software, uninstalling what you have might be non-trivial.

... and for people like me, repeating all that on every *buntu machine I admin or help support?  I rather take the easier, faster, and more portable route. :cool:

Is that also true for those of us who use kubuntu and the muon repository?

---

### Post by SeijiSensei on 2017-02-17
Kubuntu uses the same repositories as all other Ubuntu flavors.  Muon just happens to be KDE's client.

---

### Post by &amp;KyT$0P# on 2017-02-17
> **anon_private said:**
> Is that also true for those of us who use kubuntu 
Yes.  "*buntu" is my shorthand way of writing "Ubuntu and all flavors of Ubuntu".

> and the muon repository? 
What's the muon repository?  Are you referring to the software available through Muon package manager?

* oops, collided posting with SeijiSensei.  never mind about this last part.

---

### Post by SeijiSensei on 2017-02-17
Kubuntu uses the same repositories as all other Ubuntu flavors.  Muon just happens to be KDE's client.

> **halogen2 said:**
> Problems with that are,
 A) finding the build dependencies isn't always easy;
Running "sudo apt-get build-dep vlc" should download all the dependencies you need.  You need to install the build-essential package as well, of course, to get the compiler and associated files.

> B) compiling can be very time-consuming, and you can't do other things with the machine while it's compiling;

I've compiled software from source many times.  I can always continue to use the machine.  You can always use "renice" to force the compiler to use fewer resources, though I haven't had to do that myself.

> C) if you ever decide to upgrade or remove the software, uninstalling what you have might be non-trivial.
Most well-behaved programs install to /usr/local/[bin|sbin]/ with perhaps some other files in /usr/local/etc or /usr/local/lib.  If you delete the program from /usr/local/bin, it's gone.   In some cases the program installs to /usr/local/something/.  For instance, PostgreSQL puts everything under /usr/local/pgsql/.

---

### Post by &amp;KyT$0P# on 2017-02-17
> **SeijiSensei said:**
> I've compiled software from source many times.  I can always continue to use the machine.
I use higher-end laptops, where that really isn't reasonable unless the compiling is done in a VM.  Don't know about desktops and servers, which would have more resources available.

I've also read stuff that says you will likely mess up the compiler/linker if you do other things while compiling.  Is that not actually true?

---

### Post by SeijiSensei on 2017-02-17
> **halogen2 said:**
> I've also read stuff that says you will likely mess up the compiler/linker if you do other things while compiling.  Is that not actually true?
Not in my experience, and I've probably run at least fifty compilations in my lifetime, mostly for server-side programs like Postgres, BIND, Squid, and a few others.  In all those cases the server continues to truck along while the compilation takes place.

---

### Post by &amp;KyT$0P# on 2017-02-17
> **SeijiSensei said:**
> Not in my experience, and I've probably run at least fifty compilations in my lifetime, mostly for server-side programs like Postgres, BIND, Squid, and a few others.  In all those cases the server continues to truck along while the compilation takes place.
Good to know.  Thanks :KS

---

### Post by anon_private on 2017-02-18
> **halogen2 said:**
> I use this one - [https://launchpad.net/~marian.kadanka/+archive/ubuntu/vlc](https://launchpad.net/~marian.kadanka/+archive/ubuntu/vlc)

I have now installed the PPA.

Can I check my observations against yours.

The player appears black by default with white lettering.

I note that in Help:About there is no information regaridng authors, licence, or credits. The links are present, but no information. This has surprised me.

In addition, there appears to be no reference to the version of vlc. This again has surprised me.

Other points.

I doubt if the colour scheme of vlc can be changed without changing the desktop parameters.

Suppose the user decides to update their version of kubuntu from 14.04 to a higher version, would one delete the PPA'a and re-install the appropriate archives?

Best wishes

---

### Post by &amp;KyT$0P# on 2017-02-18
> **anon_private said:**
> The player appears black by default with white lettering.
Nope.  I'm guessing it did a poor job of grabbing the Qt 4 style.  [This guide]("https://forums.informaction.com/viewtopic.php?f=18&t=21842") should get it usable.

> I note that in Help:About there is no information regaridng authors, licence, or credits. The links are present, but no information. This has surprised me.
Yeah, I see the same.

> In addition, there appears to be no reference to the version of vlc.
Mine says "2.2.2 Weatherwax" in large font.  I would suspect if you fix the color scheme this will become visible.

> Suppose the user decides to update their version of kubuntu from 14.04 to a higher version, would one delete the PPA'a and re-install the appropriate archives?
You can use [FONT=Courier New]ppa-purge[/FONT], which mostly automates that procedure.  Although personally I'm planning on the clean install route.

---

### Post by anon_private on 2017-02-19
> **halogen2 said:**
> Nope.  I'm guessing it did a poor job of grabbing the Qt 4 style.  [This guide]("https://forums.informaction.com/viewtopic.php?f=18&t=21842") should get it usable.


Yeah, I see the same.


Mine says "2.2.2 Weatherwax" in large font.  I would suspect if you fix the color scheme this will become visible.


You can use [FONT=Courier New]ppa-purge[/FONT], which mostly automates that procedure.  Although personally I'm planning on the clean install route.



'Nope.  I'm guessing it did a poor job of grabbing the Qt 4 style.  [This guide]("https://forums.informaction.com/viewtopic.php?f=18&t=21842") should get it usable'

I don't really understand the page

I am wondering if it best to remove vlc and add another PPA.

The player works alright

I am using QT 4.8.6. Whatever that means

I could always leave it

---

### Post by &amp;KyT$0P# on 2017-02-19
> **anon_private said:**
> 'Nope.  I'm guessing it did a poor job of grabbing the Qt 4 style.  [This guide]("https://forums.informaction.com/viewtopic.php?f=18&t=21842") should get it usable'

I don't really understand the page
What part of it is unclear?  I know the user who posted it and might be able to get them to clarify.


1) Run in Terminal -
```
sudo add-apt-repository ppa:hda-me/qt5ct
sudo apt-get update && sudo apt-get install qt5ct
```

2) Add this line on the end of [FONT=Courier New]~/.profile[/FONT]
```
export QT_QPA_PLATFORMTHEME="qt5ct"
```
Log out and log back in for the change to take effect.

3) Open qt5ct (Qt 5 Settings) and set it up how you want.

4) You're done, enjoy VLC media player. :)

---

### Post by anon_private on 2017-02-19
I am unfamiliar with the field, and feel uncomfortable initiating commands when I am uncertain.

Can you post the image of vlc. It might be that the appearance is as it should be

---

### Post by &amp;KyT$0P# on 2017-02-19
> **anon_private said:**
> Can you post the image of vlc. 
[ATTACH=CONFIG]273798[/ATTACH]

---

### Post by anon_private on 2017-02-20
Mine looks like this
and below


[ATTACH=CONFIG]273807[/ATTACH]

[ATTACH=CONFIG]273808[/ATTACH]



Thank you for merging the posts, I had difficulty in uploading

---

### Post by &amp;KyT$0P# on 2017-02-20
I assume you've installed qt5ct per above.  When you run qt5ct, does it give you a dialog with the Qt 5 settings, or an alert box indicating a problem?

If you're seeing the Qt 5 settings, select Fusion theme and (for now) the default color scheme.  Click Apply and then OK.  Now how does VLC look if you open a Terminal and run this? -
```
export QT_STYLE_OVERRIDE=
export QT_QPA_PLATFORMTHEME=qt5ct
vlc
```

---

### Post by anon_private on 2017-02-20
I have not installed anything.

My images might be al-right. You have not commented on them.

I have downloaded a skin, but there is no skin folder. I assume that I will need to make this manually.

---

### Post by &amp;KyT$0P# on 2017-02-20
> **anon_private said:**
> I have not installed anything.
If you would like to change the colors of that VLC media player, please install qt5ct as above.

If you prefer your VLC with the white-on-black/white-on-grey color scheme, please let us know.

> My images might be al-right. You have not commented on them.
Well, everything about the look of the Qt 5 stuff strikes me as odd.  Like I said, Qt 5 is doing a poor job of grabbing some other style.

> I have downloaded a skin, b
I don't know anything about skins, sorry.

---

### Post by anon_private on 2017-02-21
> **halogen2 said:**
> If you would like to change the colors of that VLC media player, please install qt5ct as above.

If you prefer your VLC with the white-on-black/white-on-grey color scheme, please let us know.


Well, everything about the look of the Qt 5 stuff strikes me as odd.  Like I said, Qt 5 is doing a poor job of grabbing some other style.


I don't know anything about skins, sorry.

I have now installed qt5ct.

I am running Fusion with the default palette.

If I want a custom palette it looks like I need to define a file and create one.

vlc is black and white but is a lot better than before.

I also see the version of vlc and all the information regarding credits, licence, and authors.

Am I right in assuming that I have installed qt5ct, the configuration tool for qt5 that I have installed?

I wonder why it wasn't installed as default.

I have the kde interface in kubuntu, does the configuration tool conflict in any way with kde?

Ps. No error messages

---

### Post by &amp;KyT$0P# on 2017-02-21
> **anon_private said:**
> vlc is black and white but is a lot better than before.

I also see the version of vlc and all the information regarding credits, licence, and authors.

Am I right in assuming that I have installed qt5ct, the configuration tool for qt5 that I have installed?
You've certainly installed it, but the question is how much is it doing...and how much should it be doing.  And I don't know.  I don't use Kubuntu.

If you tell me which KDE widget theme, KDE color scheme, & GTK theme(s) you're using, I'd be happy to test it.

> I wonder why it wasn't installed as default.
Because qt5ct is not in the standard repositories.

---

### Post by anon_private on 2017-02-21
'If I want a custom palette it looks like I will need to define a file and create one.'

Do you agree?

Widget style Oxygen;
Colours: 'Current' - that's all it says!;
GTK: Oxygen-gtk.

In addition, I made many of my own icons, hence no style.

I get the impression that qt5ct is working (from vlc behaviour). I have not noticed any effects on other utilities. However, it is only a configuration tool.

Ps. What is 'Fusion'

---

### Post by &amp;KyT$0P# on 2017-02-21
Looks like, without qt5ct, it's using the KDE colorscheme with the Fusion Qt 5 style.  With qt5ct, everything works same as in Lubuntu.

> **anon_private said:**
> 'If I want a custom palette it looks like I will need to define a file and create one.'

Do you agree?
Yep.

> Ps. What is 'Fusion'
It's just the name of the default Qt 5 style.

---

### Post by anon_private on 2017-02-22
> **halogen2 said:**
> Looks like, without qt5ct, it's using the KDE colorscheme with the Fusion Qt 5 style.  With qt5ct, everything works same as in Lubuntu.


Yep.


It's just the name of the default Qt 5 style.

Do you know how I can create a pallet?

---

### Post by &amp;KyT$0P# on 2017-02-22
In qt5ct, for Appearance > Palette, select "Custom".  On the far right of the line starting with "Color Scheme" is a button with 3 dots and a triangle.  Click that, then click "Create".

Make sure your newly-created color scheme is selected in the dropdown, then click that 3-dots button again.  This time select "Edit".

You should now be able to change the colors graphically.

Do note that the color you've last clicked will be shown as the highlight color.  You actually did change the color how you wanted, just click another color to see that. :)

---

### Post by anon_private on 2017-02-22
I managed to get that far a little earlier.

But I find that I can only control some of the colours through changing the style, rather than the palate colours. The palate seems to have no effect

I am wondering if kde may be incompatible with qt5?

---

### Post by &amp;KyT$0P# on 2017-02-22
Kubuntu 14.04 KDE uses Qt 4, which is separate from Qt 5.

Specifically which color changes in qt5ct appear to have no effect?  How are you determining that they're not working?

---

### Post by anon_private on 2017-02-23
If I am using kde and qt 4, and vlc with qt 5. It means that both qt 4 and 5 are operating on my system. Is this normal? Since I only installed qt5ct, then qt 5 must have been already installed on my machine, so it probably is normal. Am I correct? I wonder why I do not have qt4ct?


I edit the palette, which I have called palettte1.
 I then see all the options and the Active, Inactive a Disabled panes.. I select the colour and click OK. Regardless of the colour, I get a blue colour in say the Active pane. The other panes also give their own colours irrespective of my selections.

---

### Post by &amp;KyT$0P# on 2017-02-23
> **anon_private said:**
> If I am using kde and qt 4, and vlc with qt 5. It means that both qt 4 and 5 are operating on my system. Is this normal? Since I only installed qt5ct, then qt 5 must have been already installed on my machine, so it probably is normal. Am I correct?
Yes it's normal, and yes I think you're correct.

> I wonder why I do not have qt4ct?
You do, in a sense.  In KDE, that functionality is part of the system settings.  For non-KDE systems, there is the [FONT=Courier New]qt4-qtconfig[/FONT] package.

> I edit the palette, which I have called palettte1.
I then see all the options and the Active, Inactive a Disabled panes.. I select the colour and click OK. Regardless of the colour, I get a blue colour in say the Active pane. The other panes also give their own colours irrespective of my selections. 
This sounds like you're doing everything right.  Just that you're getting confused by the blue highlighting I mentioned above.

If it is actually picking random colors instead of what you selected, I'm not seeing that and have no idea what to suggest, sorry.

---

### Post by anon_private on 2017-02-25
Update

I am beginning to get the hang of the qt5 settings.

The correct colours are appearing.

Now it is a question of creating a colour scheme that looks nice. So far, my scheme looks awful.

If I note that none of my utility colour scheme are changing, I will assume that qt4 or kde is controlling these schemes.

vlc may be a qt5 enabled application.

Best wishes

P.S. Which aspect conrols the colour of the top panel (VLC media player); and the drop down menu texts. In my scheme some appear white, some black

---

### Post by &amp;KyT$0P# on 2017-02-25
> **anon_private said:**
> P.S. Which aspect conrols the colour of the top panel (VLC media player); 
That would be "Window".  Unless you mean the window's titlebar - that's controlled by KDE.

> the drop down menu texts
That would be "Normal text".

> In my scheme some appear white, some black 
The difference is because some menu items are disabled.  Those pick up the "Disabled" color, while the rest pick up the "Active" color.

---

### Post by anon_private on 2017-02-26
Normal Text: Active (black), Inactive (black), Disabled (grey)
Observed in the dropdown menu: black or white

Window: Active (blue), Inactive (white), Disabled (white). Top panel with the title vlc media player is grey. Is that the panel control by kde colours?

---

### Post by &amp;KyT$0P# on 2017-02-26
> **anon_private said:**
> Normal Text: Active (black), Inactive (black), Disabled (grey)
Observed in the dropdown menu: black or white
It might help to know which menu items are showing up white, and the circumstances when that happens.  For example, if you're playing an audio file, is one of the white menu items Video > Video Track?

> Window: Active (blue), Inactive (white), Disabled (white). Top panel with the title vlc media player is grey. Is that the panel control by kde colours? 
Right, that part doesn't belong to VLC.  I think it is controlled by KDE's window manager settings.

---

### Post by anon_private on 2017-02-26
> **halogen2 said:**
> It might help to know which menu items are showing up white, and the circumstances when that happens.  For example, if you're playing an audio file, is one of the white menu items Video > Video Track?


Right, that part doesn't belong to VLC.  I think it is controlled by KDE's window manager settings.


I will give an example, nothing is loaded in vlc

Under media, the dropdown menu lettering  is all black.

Under playback, all dropdown menu items are white, except, jump to specific time; play; previous; and next which are black

---

### Post by &amp;KyT$0P# on 2017-02-27
> **anon_private said:**
> I will give an example, nothing is loaded in vlc

Under media, the dropdown menu lettering  is all black.

Under playback, all dropdown menu items are white, except, jump to specific time; play; previous; and next which are black
Yep, the white ones are the disabled menu items.

Looks like the disabled menu items text is controlled by two colors - both "Normal text" disabled, and "Bright" disabled.

---

### Post by anon_private on 2017-02-27
> **halogen2 said:**
> Yep, the white ones are the disabled menu items.

Looks like the disabled menu items text is controlled by two colors - both "Normal text" disabled, and "Bright" disabled.

Thank you.

You have been very helpful in this matter.

Much appreciated.

---

### Post by &amp;KyT$0P# on 2017-02-27
You're welcome! :KS

---

