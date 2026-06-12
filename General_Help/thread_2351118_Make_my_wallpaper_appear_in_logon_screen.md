---
title: "Make my wallpaper appear in logon screen?"
date: 2017-01-31
forum: General Help
---

### Post by jsc12345 on 2017-01-31
Sooooo, I just installed Ubuntu on my computer and was getting settled in, when I saw that my personalised wallpaper wasn't appearing on the login screen. There were twp weird bits, namely:
[LIST]
[*]I've already tried copying the image to the /usr/share/backgrounds 
[*]There's another user on the computer with a personalised wallpaper and his wallpaper shows on the logon screen.
[/LIST]
&#8203;So what should I do?

---

### Post by howefield on 2017-01-31
Just to clarify, this is the Unity desktop environment that you are using ?

---

### Post by jsc12345 on 2017-01-31
> **howefield said:**
> Just to clarify, this is the Unity desktop environment that you are using ?
Yep

---

### Post by deadflowr on 2017-01-31
You need to enable your Pictures folder to read access for others.
Obviously this means you also need to set your home folder read-access for others, or else setting it read for the Pictures folder and not the directory above it is moot.
Then any picture you set in the Pictures folder as wallpaper will be accessible to the login system.
That is the simplest method.

---

### Post by jsc12345 on 2017-02-01
Oh, okay. I'll try that now.

---

### Post by jsc12345 on 2017-02-01
How do I make my pictures folder accessible?

---

### Post by jsc12345 on 2017-02-02
Bump. Are we allowed to do that here?

---

### Post by wildmanne39 on 2017-02-02
> **jsc12345 said:**
> Bump. Are we allowed to do that here?

Yes once every twelve hours.:)

---

### Post by deadflowr on 2017-02-02
> **jsc12345 said:**
> How do I make my pictures folder accessible?

Navigate to the folder and then highlight it and
right click >> properties >> permissions
set  other as read only,
click on the Change Permissions on enclosed files.
Set those as read only.

---

### Post by jsc12345 on 2017-02-02
Does Access Files count as read-only?

---

### Post by deadflowr on 2017-02-02
> **jsc12345 said:**
> Does Access Files count as read-only?

Yes.
By read-only I meant readable.

Access files will give you readable just fine.

---

### Post by jsc12345 on 2017-02-03
All the settings you described were set that way already, and when I set them, my wallpaper reset to the Unity Wallpaper

---

### Post by deadflowr on 2017-02-03
Check the dconf settings for com.canonical.unity-greeter >> draw-user-backgrounds
Either install dconf-editor (dconf editor in the software center),
or
run this
```
gsettings get com.canonical.unity-greeter draw-user-backgrounds
```
in a terminal.

I'd recommend installing the editor, since it is handy to have around.

The settings in dconf are user-specific, so your settings can differ from other users.
(what your settings are may differ from what others settings are)

I think that's the setting.

---

### Post by jsc12345 on 2017-02-04
When I ran that I got the output "false" does that mean anything?

---

### Post by deadflowr on 2017-02-04
I think the default is true, or should be.
change it either through dconf editor, or
reframe the above command and run it with set, like
```
gsettings set com.canonical.unity-greeter draw-user-backgrounds true
```

---

### Post by jsc12345 on 2017-02-21
I'm bring this back because I have another question. Now, my backgrounds show on the logon screen, but only if they're one of the stock backgrounds. Just after installation, I made my home directory inaccessible to others with "sudo chmod 0700" Is this preventing my wallpaper from appearing on the login screen? And if so, how should I fix it?

---

### Post by deadflowr on 2017-02-21
> I made my home directory inaccessible to others with "sudo chmod 0700" Is this preventing my wallpaper from appearing on the login screen? And if so, how should I fix it?
Yes, and change the home folder back to 755. and set the Pictures folder to 755.
As the wallpaper folder needs to access (see) the Pictures folders images, to be able to use them.
(0700 denies the program that access)

You can always set 700 for all other folders if you want, you could run something like
```
sudo chmod 700 folder1 folder2 folder3
```
against all folder that you do not want others to view.

The options of what to do are yours, of course.

---

