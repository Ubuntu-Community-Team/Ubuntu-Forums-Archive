---
title: "Thunar in Unity/14.04 - no icons in menus?"
date: 2016-01-02
forum: General Help
---

### Post by seanos on 2016-01-02
I installed Thunar a while back because Nautilus has just become too stupid and although I like Nemo it is a little slow and seems to lock up from time to time, much like Nautilus. I didn’t use it much straight away as I wanted to give Nemo a decent try, but now that I’ve been using it a while I realised there are no icons appearing in Thunar’s menus. I’ve seen screenshots of the menus *with* icons and you can choose an icon for a custom action but of course they never appear for me either.

Any ideas how I could fix this (apart from moving to Xfce)?

Ubuntu 14.04
Thunar 1.6.3 (latest available for 14.04)

---

### Post by Dreamer Fithp Apprentice on 2016-01-02
Do you mean the menus from the menu bar?
Maybe you could show a screenshot?

For the sidepane there is Edit, Preferences, Side Pane tab, check "show icons".

If you mean the menu bar menus, or any of the context menus, I'd be delighted to know how to turn them off myself, so I'll watch with interest because I'd like to have your problem.

---

### Post by seanos on 2016-01-02
Yes, I mean the regular menus (File, etc) and the context menus. Icons are really useful to me for quickly identifying a choice, especially with custom actions.

I would post a screenshot, but it&#8217;s actually really hard to take a screenshot of a menu as activating the built in utility hides the menu.

All the other icons (files, locations, folder, devices, etc.) are fine.

---

### Post by Dreamer Fithp Apprentice on 2016-01-03
I don't know what screenshot utility you use, but for gnome-screenshot, you just use the command:
gnome-screenshot -i
and you get a gui that will let you set how many seconds delay you want to get set. Other screenshot utilities probably have a similar function. To find out, you can try
man whatever-your-program-is-named
in a terminal.

Alternately you can type this in a terminal:
sleep 10 && whatever-screenshot-command-you-use

Then press enter and get set for the screenshot 10 seconds later.

But, that said, I THINK you described it clearly enough, so I doubt I'll be able to help, but screenshots might help somebody who can, and they remove a possibility of misunderstanding. If nothing else, at least I've bumped your thread.

I suppose it is possible thunar may be looking or icons that aren't installed. It's crude, but you could try installing all the icon packages in the repo, and if it works, unistall them one by one until it breaks again, reinstall that one and then uninstall the extras. I'm sure there is a better way but that might work.

---

### Post by Frogs Hair on 2016-01-03
In Unity and Gnome Nautilus handles the desktop. Thunar native to XFCE doesn’t function this way so it will not work the same way.

---

### Post by Dreamer Fithp Apprentice on 2016-01-03
> **Frogs Hair said:**
> In Unity and Gnome Nautilus handles the desktop.
I can't see a connection between that and  the question. I don't even use a "desktop" - my root window is bare. I don't use unity and only a handful of gnome programs, but my thunar DOES have icons.

> **Frogs Hair said:**
> IThunar native to XFCE doesn’t function this way so it will not work the same way.That seems a bit circular.

And Thunar WILL handle a desktop if you set it up to. But I think the icon issue is totally separate.  And thunar CAN have icons in the menus, because mine does. So the answer isn't "It doesn't do that because it doesn't do that". Clearly it is something specific missing in OP's installation or configuration. I looked in Synaptic, which is a wonderful tool, searched for "thunar" in the name and description, sorted by installation status and looked at the ones I have.  The package

thunar-data

is described thus:

"Provides thunar documentation, icons and translations"

So hold off on what I suggested earlier for a last resort and try```
sudo apt-get install thunar-data
```and if it doesn't work right off the bat try rebooting.

---

### Post by seanos on 2016-01-04
Why is there no delete message option?

Thanks for your replies DFApprentice. Not solutions, but thanks for trying.

Frogs Hair, thanks for responding, but your reply bears no relation to  what I’ve described. I’m not trying to use thunar to manage the desktop.

*thunar-data* is part of installing the *thunar* package so it’s already installed.

The fact that I can select icons for Custom Actions and have them display in the *dialog box*, but not appear in the *context menu*  suggests that this has nothing to do with missing icons or missing  components. I’m guessing this is something to do with an assumption  about the desktop environment, but I don’t understand enough about the  various components involved to say what in particular.

I also don’t see icons in the *Open With*  menu. I’d assume Thunar would get those from the same place as Nautilus  or Nemo - ultimately the .desktop files for those apps. Perhaps it’s  something to do with Thunar not understanding how Gnome caches them? On  the other hand, folder icons, etc *are* displayed correctly in the left pane and change when I change the Gnome theme.
[B][SIZE=4]
Screenshots[/SIZE][/B]

[ATTACH=CONFIG]266527[/ATTACH][ATTACH=CONFIG]266529[/ATTACH][ATTACH=CONFIG]266530[/ATTACH]

**[SIZE=4]How it should look (according to docs.xfce.org)[/SIZE]**

[ATTACH=CONFIG]266531[/ATTACH][ATTACH=CONFIG]266528[/ATTACH]

---

### Post by Dreamer Fithp Apprentice on 2016-01-04
Good job on the screenies.  Anybody that wanders into your thread should understand the problem clearly now without doubt. I tried purging thunar-data, hoping maybe that would reproduce your issue, but it took thunar with it. I may take a closer look at the options of apt-get later and try that again later. It doesn't sound like it should be essential. But anyway, you have it, so other than the unlikely possibility it is corrupt, it isn't the problem.

> **seanos said:**
> The fact that I can select icons for Custom Actions and have them display in the *dialog box*, but not appear in the *context menu*  suggests that this has nothing to do with missing icons That seems totally sound and convincing to me.> **seanos said:**
>  or missing  components.Depending on your definition of "component", that might be a little broad.> **seanos said:**
> I&#8217;m guessing this is something to do with an assumption   about the desktop environment I suspect you are headed in the right direction there.

> **seanos said:**
> I&#8217;d assume Thunar would get those from the same place as Nautilus  or Nemo - ultimately the .desktop files for those apps.Not "ultimately". Typically there is a line in those files that specifies the filename (NOT the path, just the basename) of the image to be used, but not the image itself, nor where to find it. Your theme engine takes that information and the name of your theme and figures out where to look for the actual image. Which brings me to the point. the problem might lie in either the theme or the theme engine.

What application do you use for theming?
What theme do you have selected?
What theme engines do you have installed?

I have

gtk2-engines-xfce
gtk3-engines-xfce
gtk2-engines
gtk2-engines-pixbuff
gtk2-engines-cleanice

My theme I rolled myself, so that won't help you. I can tell you that you must have the right engine installed for the theme you select. You'd think that would be taken care of by the package software as a dependency but for some reason it ain't necessarily so.

---

### Post by seanos on 2016-01-04
The currently installed GTK theme is Zukimac and the Icon theme is Vertex-icons.

I&#8217;m not sure exactly what you mean by what application but I use Unity Tweak Tool to change themes and I also have Gnome Tweak Tool installed.

The engines I have installed...

gtk2-engines
gtk2-engines-murrine
gtk2-engines-pixbuff

gtk3-engines-unico

The appropriate icons appear in the left pane when changing themes, but the lack of icons in menus is the same in all themes.

---

### Post by Frogs Hair on 2016-01-04
Desktop handling entails drawing/displaying some  of visual elements and functional elements of the desktop. That's all I was trying to point out.

---

### Post by Dreamer Fithp Apprentice on 2016-01-04
I'm running low on ideas and starting to scrape up the long shots.  I don't think it is the gtk2-engines-xfce & gtk3-engines-xfce packages you need because I just purged them and rebooted and it didn't change my thunar menus. Still, you could try those. You didn't get either Zukimac or the Vertex-icons from the regular repo, did you? Still, you imply you've tried several themes without affecting the problem and presumably at least SOME of those were commonly used themes from the repo, right? Have you tried changing icon themes as well?

Maybe try downloading an xfce iso of the same release number and booting it to find out what the standard theme engine, theme, and icon theme are, and try using those, if only to find out if it works. Or you could try purging everything to do with thunar, manually deleting any thunar files in ~/ or ~/.config. Remember to look for folders and files, hidden and not hidden, capital and lower case. You'd think "purge" would do that, but it doesn't always seem to. Then reinstall, using the "--install-suggests" option.

Have you looked to see if any other programs you have have a similar issue?

---

### Post by seanos on 2016-01-12
I&#8217;ve tried downloading what looks like the default icon theme for Xubuntu 14.04.2 (elementary-xfce) from Launchpad but that didn&#8217;t help or give me any clues. I might try a reinstall, but I&#8217;m not too hopeful. Since it&#8217;s not the latest version (only latest in the repos for 14.04) and it&#8217;s focus isn&#8217;t Unity I&#8217;m reluctant to bother them with a bug report. If a few months I&#8217;ll move on to 16.04.1 and no doubt have other complaints.  8)

I can&#8217;t remember what distro you were using, but I am interested to see if anyone else using it in Unity has the same problem. **Edit:** or doesn&#8217;t.

---

