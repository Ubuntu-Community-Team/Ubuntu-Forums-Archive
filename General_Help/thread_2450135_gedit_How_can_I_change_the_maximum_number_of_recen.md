---
title: "gedit: How can I change the maximum number of recent files listed?"
date: 2020-09-08
forum: General Help
---

### Post by Paddy Landau on 2020-09-08
A long time ago, gedit had an option to change the number of recent files listed.

Later, that option was removed (why?), but we could at least change it through Dconf Editor or the command line:
```
gsettings set org.gnome.gedit.preferences.ui max-recents 30
```

Having just moved up to Ubuntu 20.04, I note that the new gedit (version 3.36.2) doesn't even have [FONT=lucida console]max-recents[/FONT]. I tried to add [FONT=lucida console]max-recents[/FONT] to the folder, but I couldn't find out how to do so! (There must be a way, but my googling skills are obviously lacking.)

How can I increase the number of recent files in gedit?

---

### Post by dragonfly41 on 2020-09-08
Search found this ..
[https://stackoverflow.com/questions/4051215/increase-number-recently-opened-file-list-in-gedit-gnome](https://stackoverflow.com/questions/4051215/increase-number-recently-opened-file-list-in-gedit-gnome)

read the very last comment. Re: [FONT=monospace][COLOR=#000000]gedit - Version 3.36.2[/COLOR]
[/FONT]
Perhaps time to choose a different light editor?

---

### Post by Paddy Landau on 2020-09-08
> **dragonfly41 said:**
> Search found this ..
Oh dear, thanks. I think that I'll raise a bug for this with gedit, if I can find out how to.
> **dragonfly41 said:**
> Perhaps time to choose a different light editor?
Well, if there's an editor that does what gedit does, because gedit has some truly helpful features. Do you have a recommendation? It doesn't need to be a light editor.

---

### Post by dragonfly41 on 2020-09-08
Oh dear, I should not have stuck my head above the parapet.

My personal choice these days is [CherryTree]("http://CherryTree"). An interesting feature is the option to embed codeboxes in nodes.
Note that CherryTree is in transition and there is a stable version which runs on 18.04 and a newer version gtk3 which runs on 20.04.
I am in transition between 18.04 and 20.04 right now.

But to match the very rich choice of plugins offered by gedit I also use [Atom]("http://atom.io").  Not exactly a light weight.

Much depends on what you require it do do. I tend to use toolchains and Geany also is used.

[P.S.} Found the Gedit bug reporter here ..

[https://bugs.launchpad.net/ubuntu/+source/gedit](https://bugs.launchpad.net/ubuntu/+source/gedit)

---

### Post by Paddy Landau on 2020-09-08
> **dragonfly41 said:**
> Oh dear, I should not have stuck my head above the parapet.
Uh, yes, you should have! You don't know how many people with a similar problem will find your ideas helpful. Thanks for your contributions.

I'll have a look at CherryTree and Atom, and at the bug area, thank you.

---

### Post by Paddy Landau on 2020-09-08
Update:

I've raised a [bug requesting]("https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/1894878") that the option be reinstated.

If this affects you, please mark the bug accordingly (log in, and select the green writing near the top).

---

### Post by Yellow Pasque on 2020-09-09
As I posted in your Launchpad bug, the request to reinstate the max-recents option has already been dismissed (by the developer that removed the option). [https://gitlab.gnome.org/GNOME/gedit/-/issues/315](https://gitlab.gnome.org/GNOME/gedit/-/issues/315)

But, if you like the older style of gedit, you can try pluma. It offers the max-recents setting with dconf-editor (/org/mate/pluma).

---

### Post by Paddy Landau on 2020-09-09
> **Yellow Pasque said:**
> As I posted in your Launchpad bug, the request to reinstate the max-recents option has already been dismissed (by the developer that removed the option). [https://gitlab.gnome.org/GNOME/gedit/-/issues/315](https://gitlab.gnome.org/GNOME/gedit/-/issues/315)

But, if you like the older style of gedit, you can try pluma. It offers the max-recents setting with dconf-editor (/org/mate/pluma).
Thanks. I saw that report just today. I've [resubmitted a request]("https://gitlab.gnome.org/GNOME/gedit/-/issues/357"), because that report was specifically about max-recents in dconf. This is really about the functionality.

I vaguely know Pluma, so I'll have a look at it. Thanks for the suggestion!

---

### Post by dragonfly41 on 2020-09-10
You can either wait for some movement from the Gedit developers .. or follow a proactive plan. 

This scenario explains how to include Gedit in a toolchain with Krusader to achieve what you require. I have done this with other editors: Atom, VSCode and other applications. Basically I use Krusader as my &#8220;control hub&#8221; integrating with multiple tools.

We install Krusader through command or Synaptic.

sudo apt-get update
sudo apt-get install krusader

There are many tutorials and documents around explaining how to apply Krusader.

Each of the twin panels can have multiple tabs.

Right click on tab name at bottom of panel and here we can manage tabs for each panel.

 A workflow convention might be to regard left panel as &#8220;source&#8221; and right panel as &#8220;destination&#8221;. We can then use the tabs at bottom of Krusader to perform actions F2 to F10. **Note:** These actions apply to the **selected (highlighted)** panel and it is easy to make a mistake and highlight the wrong panel.
 
 Now to integrate Krusader and Gedit we navigate to Toolbar > Settings > Configure Krusader.
 
 There are many settings which can be customised but we open General > Viewer/Editor and in 
 the Editor field set: gedit
 
 This allows any file selected through Krusader front end to open in Gedit. It might be necessary to restart Krusader for some config settings to have effect.
 
 Now Gedit has a limit of 10 recent files.  But Krusader has a larger limit.  Krusader keeps a list of &#8220;Popular URLs&#8221; 
 
 see Krusader > Toolbar > Go > Popular URLs
 
 and this is a list of folders containing recently opened files.
 
 When a Popular URL is selected this launches in the Active Panel in Krusader and in turn files can be selected and opened in Gedit where they will appear in Gedit recently opened files (pushing down the stack).
 
 
 This is a basic example of using Krusader and Gedit in  a toolchain.  There are other integration tricks to follow such as writing custom Useractions in Krusader to take the Krusader filepath and pass to other external tools or scripts through command line. 
 
 One tip is that the list of PopularURLs is held here:
 
 $HOME/.kde/share/config/krusaderrc
 
 and I have experimented by writing a custom list into that file then restarting Krusader for the changes to take effect. In principle this might be used in a custom Useraction to choose profiles of Popular URLs, so the integration options are limitless.
 
 But we will pause here.
 
 To conclude we use Krusader as the front end and Gedit as the backend editor.
 The downside is that Krusader does install with a lot of KDE baggage.

**[P.S. added note]**
Any file selected can either be launched [F4] in external Gedit or viewed [F3] by internal editor.

[https://docs.kde.org/trunk5/en/extragear-utils/krusader/krviewer.html](https://docs.kde.org/trunk5/en/extragear-utils/krusader/krviewer.html)

---

### Post by Paddy Landau on 2020-09-10
> **dragonfly41 said:**
> This scenario explains how to include Gedit in a toolchain with Krusader to achieve what you require…
This seems clever! I'll have to experiment with this to see how well it works for me.

Thank you for the idea!

---

### Post by dragonfly41 on 2020-09-10
Further tip for consideration.
If you have many files scattered throughout your file system you can use Krusader to right click on each file
and choose Link Handling. then you can choose symlink type using a different name to the file and move each created symlink into a link folder in the opposite twin panel, Then you can launch a batch of symlinked files in Gedit by selecting symlinks instead pf the original scattered files.
I use this technique in pushing multiple files to Atom editor. I have created a Useraction for this purpose using command
atom -a %aCurrent%
I'm sure that this might be modified for Gedit.

---

### Post by Keith_Helms on 2021-01-16
It seems like every LTS release has "improved" some feature out of Gedit that I used.  Menus (gone), a quit option (only way now is to click the X on the toolbar) and now being able to adjust the size of the recent document list.

---

