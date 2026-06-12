---
title: "How do I install GDM themes?"
date: 2008-05-07
forum: General Help
---

### Post by Extol on 2008-05-07
Hello! I searched the forums for how to install a new GDM theme and only found some vaguely related topics. I just installed Ubuntu 8.04 and would like to use this one as my loging screen.
 [http://www.gnome-look.org/content/show.php/Guild+Wars+Norn+GDM+Theme?content=68888]("http://www.gnome-look.org/content/show.php/Guild+Wars+Norn+GDM+Theme?content=68888")

It's the first time I try this.

PD: I thought this was the most appropriated forum. If I messed up, my bad.

Edit: I also have a widescreen monitor running at 1680x1050 Do I need to chose a widescreen theme or will it change to fit the screen?

---

### Post by chris4585 on 2008-05-07
Its quite easy to install a GDM theme, go to system > admin > login window *type password* then over to Local tab, and hit add, and add the archive file

---

### Post by Extol on 2008-05-07
Nice! I thought you had to use synaptics or something like that. And will the gdm theme work on a wide screen too? Will it automatically stretch to fit the window?

---

### Post by chris4585 on 2008-05-07
> **Extol said:**
> Nice! I thought you had to use synaptics or something like that. And will the gdm theme work on a wide screen too? Will it automatically stretch to fit the window?

I have a 22" wide screen monitor, and I do not have to do anything extra, just works usually

---

### Post by Extol on 2008-05-07
Ok Nice. I am having a problem. It says it cannot open the folder /usr something (great description, I know). But I think I read somewhere else in the forum that there's a command to fix that. I'll search it, but if you know and can post it before I find it, please do so. It's good to have i on this same topic for future forum searches.

Edit: I think this is it:

[http://ubuntuforums.org/showthread.php?t=515850&highlight=install+gdm+themes](http://ubuntuforums.org/showthread.php?t=515850&highlight=install+gdm+themes)

> Can't open file /usr/share/gdm/themes/Human/Human.xml
I think my message is the same but with "norn" at the end of it because that's the name of the theme. Can anyone actually tell me if this will fix the problem?

Edit2: Ok, here's the problem description exactly as it appears in the logging screen:

> Failed to open file '/usr/share/gdm/theme/Norn Guild Wars 1.0/icon-session-active.png':
No such file or directory

---

### Post by chris4585 on 2008-05-07
> **Extol said:**
> Ok Nice. I am having a problem. It says it cannot open the folder /usr something (great description, I know). But I think I read somewhere else in the forum that there's a command to fix that. I'll search it, but if you know and can post it before I find it, please do so. It's good to have i on this same topic for future forum searches.

Edit: I think this is it:

[http://ubuntuforums.org/showthread.php?t=515850&highlight=install+gdm+themes](http://ubuntuforums.org/showthread.php?t=515850&highlight=install+gdm+themes)


I think my message is the same but with "norn" at the end of it because that's the name of the theme. Can anyone actually tell me if this will fix the problem?

Edit2: Ok, here's the problem description exactly as it appears in the logging screen:


Hrm, do other themes work for you? If they do then it might just be that theme then.  That's the only thing I can think of...

But check that folder to see if there's actually anything there, when you install a GDM theme what it does is just extract the files from the tar.gz or tar.bz2 to /usr/share/gdm/themes/

also make sure in the local tab, that you have "Theme selected only" and have the correct theme selected, sometimes that can be tricky.

---

### Post by Extol on 2008-05-07
I looked in the forum it said and it doesn't have the icon-session-active.png file the message says. Everything else is there. I suppose the creator of the GDM theme left it out. I'll ask him. And thanks for all the help, man.

---

### Post by chris4585 on 2008-05-08
> **Extol said:**
> I looked in the forum it said and it doesn't have the icon-session-active.png file the message says. Everything else is there. I suppose the creator of the GDM theme left it out. I'll ask him. And thanks for all the help, man.

You're welcome, =)

---

