---
title: "Trash can - desktop icon"
date: 2019-10-05
forum: General Help
---

### Post by kesetyan on 2019-10-05
Hi,

I am running Ubuntu 18.04 (fully updated) with the gnome desktop.  I'm still a bit of a novice with Ubuntu but I've managed to carry out a few changes to the look of the desktop environment including using personal icons for my desktop contents.  I've used my own icons by right clicking an item, choosing 'Properties' from the menu, clicking on the icon in the properties window and navigating to and selecting my choice of icon.  

This has all worked smoothly bar one minor issue with the trash can/rubbish bin icon. I was able to change the icon but i cannot get the dual icon effect whereby the trash can icon varies according to whether the bin is empty or not.  I do have both 'empty' and 'not empty' icons in my personal icon file but just can't see how to employ them.  

While this is not a major concern, I would be interested to know if there is a not too complicated means of resolving this situation or failing that, a way to return to the original two icons (I'm not sure where they are stored or indeed where the trash can desktop file is stored should I need to edit a line or two.

Thanks.

---

### Post by CatKiller on 2019-10-05
> **kesetyan said:**
> I was able to change the icon but i cannot get the dual icon effect whereby the trash can icon varies according to whether the bin is empty or not.  I do have both 'empty' and 'not empty' icons in my personal icon file but just can't see how to employ them.  
That behaviour is controlled by the icon theme: there is one icon for when it's empty and another one for when it's full. You've replaced that with your own single fixed icon. I'm typing from my phone, so I can't check the filename, but you should be able to find it easily enough. Having the files called the right thing and in the right place will make it work, once you clear your custom icon. Potentially after logging out and logging back in; I can't remember for sure. 

You can create a new icon theme in your Home folder with the icons that you're interested in, and set it to "inherit" those icons that you haven't included from another theme.

---

### Post by kesetyan on 2019-10-06
Hi CatKiller,

Thanks for your reply.  My icon theme for the moment is 'Oxygen'. I'm presuming the desktop icons are 48x48 pixels so I've searched Oxygen icon folders for that size to find the icons.  I'm not sure about the next stage as all I've been able to do so far is replace my icon with an Oxygen fixed icon - I've a bit more to learn here so, if and when you get time, a little more instruction would be appreciated please.  If I sort out beforehand, I'll let you know.  You've given me a start so I might crack it.  Thanks.

---

### Post by dragonfly41 on 2019-10-06
To keep your Ubuntu house in order I recommend installing [Stacer]("https://github.com/oguzhaninan/Stacer").
For Trash cleaning select System Cleaner from Stacer applet drop down menu in top bar.
But Stacer has many other uses.

---

### Post by CatKiller on 2019-10-06
> **kesetyan said:**
> Hi CatKiller,

Thanks for your reply.  My icon theme for the moment is 'Oxygen'. I'm presuming the desktop icons are 48x48 pixels so I've searched Oxygen icon folders for that size to find the icons.  I'm not sure about the next stage as all I've been able to do so far is replace my icon with an Oxygen fixed icon - I've a bit more to learn here so, if and when you get time, a little more instruction would be appreciated please.  If I sort out beforehand, I'll let you know.  You've given me a start so I might crack it.  Thanks.

Icon themes don't have just one icon, they have several, and the theme engine picks the closest size to what's requested. Which icon file to use for a given task is determined by its name (without any extension); for the recycle bin icon I believe it's *user-trash* and *user-trash-full*. There's [a specification](https://standards.freedesktop.org/icon-theme-spec/icon-theme-spec-latest.html) but each desktop environment still has its own quirks. The housekeeping of which directory structure to search through for each icon is done with text files. The theme itself is checked, followed by the theme listed as *inherited*, followed by the ones *that* theme inherits, all the way back to hicolor, until a match is found. You should be able to work out your two-icon theme just by poking at the themes you have already. You can put as many or as few as you need.

---

### Post by kesetyan on 2019-10-06
Hi Catkiller and dragonfly41,

Thanks for your replies.

Dragonfly41:  Stacer certainly looks useful and the screenshot images I saw on the website look very clear and well set out - I will certainly give it a go.

CatKiller: as a relative newby in Ubuntu, I am closer to the bottom of the learning curve.  I don't fully understand the 'housekeeping' bit in your post nor do I understand what is actually checking the themes.  My understanding of file and directory structure is very much based on the Windows environment although I have also done a fair bit with Puppy Linux systems where I was able to create and utilize my own icon themes and edit .desktop files to change application icons and such like.  Ubuntu seems to be a different ball game so please be patient with me If I am slow to grasp exactly what you are saying.  I can navigate to usr/share/icons and then navigate the various themes (with 'Oxygen' being the pertinent one in my case) but I can't see how to get back to the stage before I made my personal  trash can icon the fixed icon for the trash can so that I get an 'Oxygen' empty bin and full bin operating.  Once I get back to that stage, I will probably need more guidance if I am to substitute my pair of icons to work correctly with the trash can (the inheritance bit is a bit confusing for me as I am not sure how or where to set up my icons with those terms).  

I certainly appreciate your help but don't wish to take up too much of your valuable time.  If you can spare a bit for further help, I will bey very grateful but, as this is not that crucial in terms that my system is working well in all other respects, I will understand if you'd rather leave me to my own devices and let me learn the hard way.

Cheers.

---

### Post by CatKiller on 2019-10-06
> **kesetyan said:**
> CatKiller: as a relative newby in Ubuntu, I am closer to the bottom of the learning curve.  I don't fully understand the 'housekeeping' bit in your post nor do I understand what is actually checking the themes. 

The bottom directory of each icon theme has a text file in it that has things like the name of the theme, maybe a description, and inheritance of other themes. That file is what's used in the theme selection interfaces to pick the theme that you want. 

>  My understanding of file and directory structure is very much based on the Windows environment although I have also done a fair bit with Puppy Linux systems where I was able to create and utilize my own icon themes and edit .desktop files to change application icons and such like.  Ubuntu seems to be a different ball game so please be patient with me If I am slow to grasp exactly what you are saying.  I can navigate to usr/share/icons and then navigate the various themes (with 'Oxygen' being the pertinent one in my case) 

System-wide themes are stored at /usr/share/icons, and per-user themes go in ~/.icons. A user theme can inherit a system theme (and most will). 

>  but I can't see how to get back to the stage before I made my personal  trash can icon the fixed icon for the trash can so that I get an 'Oxygen' empty bin and full bin operating.   

There's probably a reset-to-default button in the place where you changed it (I don't use Gnome) and mechanically it probably created a .desktop file somewhere. 

>  Once I get back to that stage, I will probably need more guidance if I am to substitute my pair of icons to work correctly with the trash can (the inheritance bit is a bit confusing for me as I am not sure how or where to set up my icons with those terms).  


There are probably lots of articles about creating an icon theme. I couldn't recommend a particular one, since it's not something I've done. I've just poked around looking at the files to see how it all works.

It's only because you're after that functionality of automatically changing the icon that using the theme is the way to go. In other cases, just using a static icon is perfectly fine.

---

### Post by kesetyan on 2019-10-07
Hi CatKiller,

Thanks for your time and patience.  You've given me lots to be getting on with so I will now endeavour to see what I can find out.  I've found and opened the text files in relevant icon themes noting the line 'Inherits=hicolor' in 'Oxygen' for example and seeing that the application icons on the system are the 'HiColor' 'Apps icons.  I'm feeling more confident now to explore without causing system damage and, if I can't resolve the trash can icon issue, there's no harm done as I am quite happy with the static icon.

Cheers and thanks again.

---

### Post by CatKiller on 2019-10-07
I'm glad to hear you're getting some confidence with it.

The inheritance functionality is really useful: firstly it means that you don't need to create every icon yourself when you're doing a theme, but it also means that you can choose another icon set that complements your icons rather than one that doesn't: if your icons are really cartoony you wouldn't want some other icons to be all photo-realistic, and vice versa. By choosing which themes your theme inherits, you get to decide that. All icon themes implicitly inherit hicolor, so that's where icons provided by external applications go but, if your theme has its own icon for that application, that will be used in preference.

For the bare minimum to achieve what you're after, you just need to create a theme in ~/.icons, which you can call whatever you like, that has the two trash icon sets - one for full, and one for empty - that inherits the icon theme you're otherwise using - Oxygen, in this case.

There's no reason to stop there, if you don't want to. You can have your own complete theme with as many icons as you like, of whatever style you like. Have a play. 

Good luck, and have fun!

---

### Post by kesetyan on 2019-10-07
Thanks CatKiller (you don't sound like someone capable of harming our feline friends).  Thanks for all your advice.  I'll see what I can do but take my time.  Cheers and best regards.

---

