---
title: "cursor installation"
date: 2008-06-06
forum: General Help
---

### Post by Armed Nuke on 2008-06-06
i'm new to ubuntu and i recently downloaded a cursor theme. i extracted it but i don't know how to install it. i read somewhere that i should put it in the usr/shared/icons directory but it won't let me because i'm "not the owner of the file" and i don't have permission.

---

### Post by Gourgi on 2008-06-06
try using nautilus as superuser
```
sudo nautilus
```

---

### Post by sayakb on 2008-06-06
Just take the tarball and drag and drop it open the System->Preferences->Appearance window. Or you might extract and place it in the /home/username/.icons folder.

---

### Post by Armed Nuke on 2008-06-06
when i keyed in sudo nautilus i got this output

tyler@Playroom:~$ sudo nautilus
[sudo] password for tyler: 
Initializing nautilus-share extension
seahorse nautilus module initialized
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:5943): WARNING **: Unable to add monitor: Operation not supported


and i don't have a .icons folder under my username to place it in. i could make one but i don't know how to tell linux to look there. i'm sorry i'm sounding like a complete idiot. i'm super new to linux.

---

### Post by Gourgi on 2008-06-06
ok forget my previous post, use LinuxIsInnovation's above your's instead.
Details:
From Desktop go to **Places** (upper left corner), clik to **Home**.
So far so good, then hit **Ctrl+H** or go **View** --> **Show Hidden files**.
Why are we doing this? Just because in linux the hidden files start with **[COLOR="Red"].[/COLOR]** (dot)
(also basic user's settings are stored in hidden files)
Ok now let's find the .icons folder or if it is not there, just **create it** (right click, create folder, folder's name = **.icons**).
the go inside .icons folder and paste your extracted folder in there ( or if your theme is a tar. archive just ectract it there)


feel free to post backup if you find any problem or else 
go **System** --> **Preferences** --> **Appearance** , at first pop up Tab click **customize**, go to **Pointer** tab and use pointer/cursor

enjoy your theme :popcorn:

you can use this theme to test
[http://www.gnome-look.org/CONTENT/content-files/61037-entis_cursors_x11_others.tgz](http://www.gnome-look.org/CONTENT/content-files/61037-entis_cursors_x11_others.tgz)
it installs just fine for me (tested now)

---

### Post by Armed Nuke on 2008-06-06
thank you very much :) my cursors are now up and running. couldn't have done it without your help :)

---

### Post by Gourgi on 2008-06-06
no problem , 
now you can add your section about installing icons and themes in 
> The Great Desktop Effects FAQ of 2008 here [http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)

i'm sure your instructions will be better than mine ;)

---

### Post by idodialog on 2008-09-12
Why so difficult?

[LIST=1]
[*]Download your cursors (or any theme or controls, colors borders or icons - and cursors are called pointers for some unknown reason) to the desktop.
[*]Don´t unpackage. 
[*]Go System>Preference>Appearance
[*]_[COLOR="Red"]Drag and Drop[/COLOR]_ the package into the Appearance Preference Screen.
[*]A dialog will inform you that the package was properly installed and offer to activate your cursor (or whatever).
[/LIST]

Done.
(If you choose not to activate go from the Theme window to ¨Customize¨ and choose what you wish to customize).

---

### Post by WarTor on 2008-10-10
THanks mate, very helpful!

---

### Post by rafamundez on 2008-12-01
> **idodialog said:**
> Why so difficult?

[LIST=1]
[*]Download your cursors (or any theme or controls, colors borders or icons - and cursors are called pointers for some unknown reason) to the desktop.
[*]Don´t unpackage. 
[*]Go System>Preference>Appearance
[*]_[COLOR="Red"]Drag and Drop[/COLOR]_ the package into the Appearance Preference Screen.
[*]A dialog will inform you that the package was properly installed and offer to activate your cursor (or whatever).
[/LIST]

Done.
(If you choose not to activate go from the Theme window to ¨Customize¨ and choose what you wish to customize).
Because in 8.10, that doesnt work...at all actually.  Neither does extracting it anywhere.  Nor that gcursor thing either.  I'm stuck.

---

