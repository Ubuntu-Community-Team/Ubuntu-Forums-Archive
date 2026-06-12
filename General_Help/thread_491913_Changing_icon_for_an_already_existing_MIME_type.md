---
title: "Changing icon for an already existing MIME type?"
date: 2007-07-04
forum: General Help
---

### Post by Senesence on 2007-07-04
The file extension in question is .blend (Blender 3D application). MIME type is set to "application/x-blender".

Where exactly do I put my icon .png, so that it would associate with the mime type? And are there any other commands that I have to run in order for the changes to take effect?

I tried a few things already - like naming my icon "gnome-mime-application-x-blender" and placing it in all the icon folders, 48x48 and so on - but it just won't work.

So if anyone could give me specific instructions on how I can make this work - please do so. Thanks.

---

### Post by Brucevdk on 2007-07-04
I thought I'd try and find out what "The Right Way (TM)" to do this is but failed miserably and ended up quite frustrated. However, perhaps the information I found can help you more than it helped me. I haven't actually tried them out because they all admit that it isn't the ideal way to be doing things, but it's very likely they do work.

First lets start of with some GNOME mime type related documentation, it's interesting but there's not much in there about associating icons with mime types (notice the warning).
[LIST]
[*][GNOME 2.14 Desktop System Administration Guide: MIME types]("http://www.gnome.org/learn/admin-guide/latest/mimetypes-modifying.html#mimetypes-addmodify")
[/LIST]
> 
You should never directly modify the source XML files that are installed to the <MIME>/packages directory by applications. Instead, modify the Overrides.xml file. This file has precedence over all other source XML files installed into the same packages directory. If you are an application author, then this rule does not apply. You should create a new source XML file and place it in the proper <MIME>/packages directory (your Makefile will take care of this, of course).


Here's some other helpful information, the first one from the Ubuntu forums is the most likely solution. Also the last one would most likely work as well but seems to be for usage in combination with custom icon themes.
[LIST]
[*][Ubuntu Forums - Changing mimetype icon sets?]("http://ubuntuforums.org/showpost.php?p=551423&postcount=5")
[*][Mandriva Users: Easy Icon Association In Gnome? [solved] - MandrivaUsers.org]("http://mandrivausers.org/index.php?showtopic=38906&st=0&p=293764&#entry293764")
[*][Ubuntu Forums - HOWTO: Change icon for specific file types in Gnome - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=302549")
[/LIST]

Good luck and please post the "solution" here if you manage to work it out.

---

### Post by Senesence on 2007-07-04
The only thing that I couldn't " test run" was that Mandriva link - I mean he doesn't specify the directories he worked with.

Everything else, I tried, with no results.

How can something as trivial as icon replacement be so overly complicated? You'd think they would just have a simple option in the file properties to do this.

It's all so counter-intuitive.

---

### Post by Brucevdk on 2007-07-05
By accident stumbled upon [the following article]("http://www.ces.clemson.edu/linux/fc4_desktop.shtml") which does seem to contain seem useful information, again I haven't tried it out personally (though I might later). The relevant sections are *Mime Type Editing* and *Icon Association*.

---

### Post by Senesence on 2007-07-05
> **Brucevdk said:**
> By accident stumbled upon [the following article]("http://www.ces.clemson.edu/linux/fc4_desktop.shtml") which does seem to contain seem useful information, again I haven't tried it out personally (though I might later). The relevant sections are *Mime Type Editing* and *Icon Association*.

That didn't work out either.

I don't know exactly how the mimetype-icon association works here. I mean the mimetype is "application/x-blender", so where does the icon go, and what should it be named? (I assume the name is the method by which the mimetype determines the icon to use)

I tried putting "gnome-mime-application-x-blender.png" in the icon folder they list in all those examples you linked to, but I still get nothing.

I hear that doing this with KDE is as simple as a few mousecliks - but I'm not sure. I would just like to get this working with regular ubuntu, instead of switching to Kubuntu just because of something like this.

---

### Post by Brucevdk on 2007-07-05
> **Senesence said:**
> I don't know exactly how the mimetype-icon association works here. I mean the mimetype is "application/x-blender", so where does the icon go, and what should it be named? (I assume the name is the method by which the mimetype determines the icon to use)

That seems correct to me, anyways it seems sorta (and I have to emphasize sorta) to work for me (I combined it with some of the previous guides). Here's the procedure (non-system wide) I followed:
```

mkdir ~/.local/share/mime ~/.local/share/mime/packages
cat > ~/.local/share/mime/packages/Overrides.xml << EOT
<?xml version='1.0' encoding='utf-8'?>
<mime-info xmlns="http://www.freedesktop.org/standards/shared-mime-info">
    <mime-type type="application/maple">
      <comment xml:lang="en">Maple Worksheet</comment>
      <glob pattern="*.mws"/>
    </mime-type>
</mime-info>
EOT
update-mime-database ~/.local/share/mime/

mkdir ~/.icons ~/.icons/gnome ~/.icons/gnome/48x48 ~/.icons/gnome/48x48/mimetypes
cp /usr/share/icons/gnome/48x48/mimetypes/ooffice-extension.png ~/.icons/gnome/48x48/mimetypes/gnome-mime-application-maple.png
gtk-update-icon-cache ~/.icons/gnome/ --ignore-theme-index

```

I tried it with a plain ASCII text file (gave it the .mws extension) which showed up fine though it would show the live preview on the desktop and when selecting a file making the icon sort off useless. Actually it doesn't matter what kind of file, the icon keeps resetting itself on selection.

I think I'm going to look into theming next, because they successfully modify icons.

> **Senesence said:**
> I hear that doing this with KDE is as simple as a few mousecliks - but I'm not sure. I would just like to get this working with regular ubuntu, instead of switching to Kubuntu just because of something like this.

Actually, turns out it is. In Konqueror all you have to do is *Select a file -> Edit -> Edit File Type -> Select an icon -> Apply -> F5 (Refresh)*. To try, you don't have to install the whole distro, just install the kubuntu-desktop package (or even just Konqueror).

---

### Post by Senesence on 2007-07-06
I did everything you did - except in the Overrides.xml I specified "application/blender" and pattern "*.blend", and so in turn the icon was also named "gnome-mime-application-blender.png".

Those changes shouldn't cause any problems, right?

---

### Post by Brucevdk on 2007-07-06
> **Senesence said:**
> I did everything you did - except in the Overrides.xml I specified "application/blender" and pattern "*.blend", and so in turn the icon was also named "gnome-mime-application-blender.png".

Those changes shouldn't cause any problems, right?

It won't cause any problems that I know of (plus these changes aren't system wide), whether it'll work any better than in my case that's the question.

---

