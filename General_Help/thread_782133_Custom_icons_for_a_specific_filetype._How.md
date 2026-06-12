---
title: "Custom icons for a specific filetype. How?"
date: 2008-05-04
forum: General Help
---

### Post by Senesence on 2008-05-04
I guess this is actually a tutorial request of sorts, because everything else I found out there is either outdated or not working with Hardy. 

Ideally, a set of step by step instructions on how to set an arbitrary image (like a .png) as an icon for all files that share a specific extension (.blend in my case).

Also, please keep in mind that certain methods override others (for example local user settings can override default system-wide settings), so due to the fact that I messed around with some previous methods already, I would require a method that overrides all other possible methods for setting a specific filetype icon.

TIA.

PS: The fact that gnome still doesn't provide a tool for this is truly bizarre.

---

### Post by pofigster on 2008-05-04
I'd be interested to see how to do this, too.  I want to get my .R and .py files to look different than regular text files.

---

### Post by Senesence on 2008-05-04
> **pofigster said:**
> I'd be interested to see how to do this, too.  I want to get my .R and .py files to look different than regular text files.

Well, I view code as text anyway, so I don't mind that a .py would be shown as basic text, but for everything else....yea, it's a big problem.

To add on to my previous rant; this is one of those things that should just be included as a feature in a desktop environment. I mean if you give the user the ability to choose with which application a certain filetype will be opened, allowing them to set the icon for the very same filetype should be a given.

Not to say that I'm too lazy to edit various xml files, but doing so just to set an icon for a group of files is just plain wrong.

I like gnome, but really, this is ridiculous.

---

### Post by Senesence on 2008-05-05
Anyone?

---

### Post by rolandixor on 2008-05-05
I've done it a few times, but I'll have to get back to my old Gutsy installation to get the instructions... :S
don't worry, I should get back to you before the week is over (remind me)...

---

### Post by Periswell on 2008-05-05
got it. right click on the object and click properties then click on the picture of its icon on the left hand side of its name and just pick and image from you folders.

hoped this helped

-josh

---

### Post by rolandixor on 2008-05-05
Yups, that's one way to do it. But there is a program I have on the other system that edits MIME types...

---

### Post by Periswell on 2008-05-05
i just find it easier to do that though i am not sure if it changes a single file's icon or all of the type of file's icon.

-josh

---

### Post by Senesence on 2008-05-05
[QUOTE=Periswell]got it. right click on the object and click properties then click on the picture of its icon on the left hand side of its name and just pick and image from you folders.[/QUOTE]

That only changes the icon for that single file, not the entire filetype. It would really be a bother to do that for every file, and every time I create a new one.

As rolandixor implied; mime-types probably need to be modified. But which mime-types, and where? Also, I looked through a few xml files that "describe the mime-type" and nowhere in there do I see a path to an image file ----> It leaves the question: How exactly does the mime-type know about which icon to use?

It's all so annoying, especially because it seems like such a trivial issue, but the way gnome works makes the whole thing overly complicated.

---

### Post by rolandixor on 2008-05-22
I'll see if I can get it soon, sorry for the delays. My brother is using the system I have it on (with XP, not my ubuntu HD)

---

### Post by kzlazy on 2008-05-22
To add something to this thread I must say that when you change the icon of a specific folder by right clicking and then changing the icon of the folder, it is then locked to this new icon.

The result is that if you change the theme, all other folder icons of the desktop change, following the theme change, but the single folder icon you manually reset does not. It also messes up the properties of the folders content.

It might get a little tricky if you change your mind afterwards and want to undo the icon changes.

---

### Post by crossedout on 2008-05-22
It sounds like you want to alter mimetypes.  If you are using an installed theme, you can access the folder with mimetypes via: ctrl+H )to view hidden folders), then navigate to .icons->YourThemeName->Size->mimetypes.

Copy the icon you want to use into that folder, then rename it to reflect the item you are changing (blender in your case).  The real trick is determining the proper name.  Usually you can determine the name by looking through the icon themes that come pre-installed.  /usr/share/icons/ThemeName/mimetypes.

Additonally, mime-editor is a program that might do what you need but it was last updated in '05, so its hard to say if it will still function properly.
Find it here: [http://freshmeat.net/projects/mime-editor/]("http://freshmeat.net/projects/mime-editor/")

-Xout

---

### Post by rolandixor on 2008-06-20
I found the app again.

It's assogiate, and it should work (If I remember correctly)...

---

### Post by AFarris01 on 2008-11-02
I know this thread is a little old, but I'm trying to deal with this issue as well on Hardy, and the assogiate program isn't doing the trick.

I have 4 custom icons i'd like to apply, for .mds & .mdp monodevelop files, .wings files, and .glables files, because for some reason, the programs themselves didn't do it automatically.

I've tried using assogiate to set custom icons for these file types (have to run as root, otherwise no changes will take) and they show up in assogiate as being set, but they don't show up in the nautilus view.

Is there any other way to get the job done here?

---

### Post by rolandixor on 2008-11-02
If you are using a custom icon theme, try using the default one and see what happens. If not try another. Usually each icon theme has some missing icons, so you will see that some file types are blank.

---

### Post by AFarris01 on 2008-11-12
My present icon theme is Dropline Nou...

I've tried switching back to the default 'Human' theme, as well as switching around to a few different themes...none of which did anything different.  

Here's something else i noticed: if i open one of these files in a program, say opening one of the monodevelop files in gedit, the custom icon i set shows up in the top corner for the window 'menu,' but i still see the generic 'gears' looking one when browsing in nautilus

why is that?

---

### Post by AFarris01 on 2008-12-06
i'll bump this thread, cause i'd really like to see this answered definitively.

I still can't get custom icons for a specific file type to show up in the nautilus view.  the list of file types i'd like to do this to is growing, as is my frustration.

I'll also be submitting a Brainstorm idea to fix this issue

---

### Post by rolandixor on 2008-12-08
It's possible to do this manually if you know how to do/modify icon themes, and possibly how to override them. I don't have the time to look at how to do that yet myself lol.

---

