---
title: "How can I sort the Icons on the Desktop?"
date: 2008-05-26
forum: General Help
---

### Post by rakan_dr on 2008-05-26
Hi boys,
how can I sort the Icons on the desktop on Ubuntu like Windows? i.e. In windows: right click -> Arrange icons by->-name
                                                  -size
                                                  -type
....etc

so how can i do it in Ubuntu, does anybody know???
I hate the style that Ubuntu use to arrange icons.
When I click "Clean Up by Name" it puts the mounted disks first, then the folders and then the applications icons.

I want to make them like windows: Apps then documents.

What are your styles guys in sorting???

---

### Post by rakan_dr on 2008-05-27
Hello!!!!!!!!!

---

### Post by forestpixie on 2008-05-27
You could just move them where you want them to be and leave them - maybe use keep aligned.

There aren't the same option as there are in windows.

As far as me personally - I don't have anything on the desktop at all - hate having the drives all over the screen.

---

### Post by rakan_dr on 2008-05-27
But common this is very silly thing! Such a powerful operating system like Ubuntu must have like this feature "Sorting icons by...".

That's my opinion...

---

### Post by forestpixie on 2008-05-27
Well it might well have, but I don't know it, my opinion is that it's not needed - but I can see where you are coming from  :)

---

### Post by wootah on 2008-05-27
I don't think GNOME has that kind of option. They are _***really***_ minimalistic.

---

### Post by forestpixie on 2008-05-27
I've got wallpaper though :)

Good point though I'll have a look in kubuntu later

---

### Post by rakan_dr on 2008-05-27
hehehhe oky man.

---

### Post by forestpixie on 2008-05-27
I'll boot into kubuntu later and see if it's there if you want - there are a lot more 'things, bells and whistles' there, see if you can do it there.

But afaik you'll need to move them where you want and line them up.

---

### Post by ibuclaw on 2008-05-27
It is possible, yes. That is true.

But the files that hold the Desktop Icon Placements in GNOME are in cryptic xml files.

Your personal icons are stored here:
```
~/.nautilus/metafiles/file:%252F%252F%252Fhome%252F**YOURNAME**%252FDesktop.xml

```YOURNAME is the name of your user account.

And your Device icons are stored here:
```
~/.nautilus/metafiles/x-nautilus-desktop:%252F%252F%252F.xml
```

To quote mine:
[PHP]
<directory>
<file name="Audio%20Drive.volume" timestamp="1211816982" icon_position="64,102"/>
<file name="82.3%20GB%20Media.volume" timestamp="1211557892" icon_position="64,22"/>
<file name="DVD%20Disc.volume" timestamp="1211584555" icon_position="64,102"/>
<file name="Computer" timestamp="1211816980" icon_position="64,22"/>
<file name="Home" timestamp="1211816974" icon_position="142,22"/>
<file name="Trash" timestamp="1211597020" icon_position="1156,862"/>
<file name="Audio%20Disc.volume" timestamp="1211908224" icon_position="64,202"/>
</directory>
[/PHP]

Possible, yes.
But it would require:
A) Knowing how big your desktop screen is and...
B) Figuring out how to precisely map out the locations of the "icon_position" numbers while noting
C) The size of the Icons.

Is someone going to make it?
I wouldn't hold my breathe for it...

Regards
Iain

---

### Post by wootah on 2008-05-28
> **tinivole said:**
> It is possible, yes. That is true.

But the files that hold the Desktop Icon Placements in GNOME are in cryptic xml files.

Your personal icons are stored here:
```
~/.nautilus/metafiles/file:%252F%252F%252Fhome%252F**YOURNAME**%252FDesktop.xml

```YOURNAME is the name of your user account.

And your Device icons are stored here:
```
~/.nautilus/metafiles/x-nautilus-desktop:%252F%252F%252F.xml
```To quote mine:
[php]
<directory>
<file name="Audio%20Drive.volume" timestamp="1211816982" icon_position="64,102"/>
<file name="82.3%20GB%20Media.volume" timestamp="1211557892" icon_position="64,22"/>
<file name="DVD%20Disc.volume" timestamp="1211584555" icon_position="64,102"/>
<file name="Computer" timestamp="1211816980" icon_position="64,22"/>
<file name="Home" timestamp="1211816974" icon_position="142,22"/>
<file name="Trash" timestamp="1211597020" icon_position="1156,862"/>
<file name="Audio%20Disc.volume" timestamp="1211908224" icon_position="64,202"/>
</directory>
[/php]Possible, yes.
But it would require:
A) Knowing how big your desktop screen is and...
B) Figuring out how to precisely map out the locations of the "icon_position" numbers while noting
C) The size of the Icons.

Is someone going to make it?
I wouldn't hold my breathe for it...

Regards
Iain

I took a look at the directory and wow. That is really ridiculous. I have entries of stuff that has been LONG gone.

I hope it is easier to do in KDE :(

---

### Post by forestpixie on 2008-05-28
As promised - I booted kubuntu and yes in there you can do the same as in win.

Although I wouldn't use kubuntu just for that :)

---

### Post by rakan_dr on 2008-05-29
Thanks man for your effort, but I want to ask 
why Ubuntu is more popular than Kubuntu???
i.e. why GNOME is more popular than KDE??? Is there anything wrong with KDE??? or is it difficult or somthing???

---

### Post by wootah on 2008-05-29
Personal preference I suppose. GNOME and KDE are basically constantly competing. In the large scheme of things, I don't think either is necessarily more popular than the other. I think Ubuntu decided to choose GNOME as their desktop environment instead of KDE because GNOME is very minimalistic and keeps configuration very simple (ie: program options). KDE is somewhat the other direction, where everything is configurable.

Of course with GNOME, if you really want to, you can change a lot about it--but you most likely won't find a checkbox or radio button available for what you want to change :)

---

### Post by forestpixie on 2008-05-29
> **rakan_dr said:**
> Thanks man for your effort, but I want to ask 
why Ubuntu is more popular than Kubuntu???
i.e. why GNOME is more popular than KDE??? Is there anything wrong with KDE??? or is it difficult or somthing???

You are welcome - glad to have helped, now as far as gnome and kde go...

Ubuntu is more popular to me - others not necessarily so - this is the Recurring Discussion forum [http://ubuntuforums.org/forumdisplay.php?f=302](http://ubuntuforums.org/forumdisplay.php?f=302)

You will find answers and non-answers to that question and others of a similar nature :D

I've only been here for 1 year myself and I've seen many of those and also which torrent client, is firefox better than opera - or are others better than them - are we all going mad in handcart :biggrin:

---

