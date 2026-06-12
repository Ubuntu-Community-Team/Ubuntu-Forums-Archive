---
title: "Help with nautilus-script (SFV-check)"
date: 2005-09-06
forum: General Help
---

### Post by Lapse on 2005-09-06
Hello
I'd like to be able to rightclick an .sfv-file, choose -> Script -> SFV-check or whatever name I'd give it, and a terminal pops up and checks the files.
The problem is that I don't know how to script something like that. All I know is that it's supposed to be placed in *~/.gnome2/nautilus-scripts* folder.

Could someone help me and tell me what to put in the file, so that I don't have to type *cksfv -f filename.sfv* in a terminal every time.

---

### Post by arnieboy on 2005-09-06
[QUOTE=Lapse]Hello
I'd like to be able to rightclick an .sfv-file, choose -> Script -> SFV-check or whatever name I'd give it, and a terminal pops up and checks the files.
The problem is that I don't know how to script something like that. All I know is that it's supposed to be placed in *~/.gnome2/nautilus-scripts* folder.

Could someone help me and tell me what to put in the file, so that I don't have to type *cksfv -f filename.sfv* in a terminal every time.[/QUOTE]
put the following in a file, put it [email]in $HOME/.gnom[/email]e2/nautilus-scripts/ and make it executable:
> cksfv -f $@

---

### Post by Lapse on 2005-09-06
Okay, I created a file named sfv in the directory, with only *cksfv -f $@* in it, and made in executable (sudo chmod +x file ?). 
It does show up in the menu, but it does nothing to an sfv-file. At least not anything I can see. No terminal or anything.

---

### Post by arnieboy on 2005-09-06
[QUOTE=Lapse]Okay, I created a file named sfv in the directory, with only *cksfv -f $@* in it, and made in executable (sudo chmod +x file ?). 
It does show up in the menu, but it does nothing to an sfv-file. At least not anything I can see. No terminal or anything.[/QUOTE]
it does the job but it does not open a terminal.

---

### Post by Lapse on 2005-09-06
Alright, but what does it do if a file is missing or corrupted? 
I can't read it in any terminal, and there's no popup or whatsoever.

---

### Post by pmj on 2005-09-06
[QUOTE=Lapse]Could someone help me and tell me what to put in the file, so that I don't have to type *cksfv -f filename.sfv* in a terminal every time.[/QUOTE]
If you don't mind using a GUI program, try Parano ([http://freshmeat.net/projects/parano/](http://freshmeat.net/projects/parano/) ).

---

### Post by Lapse on 2005-09-06
[QUOTE=pmj]If you don't mind using a GUI program, try Parano ([http://freshmeat.net/projects/parano/](http://freshmeat.net/projects/parano/) ).[/QUOTE]
Thanks, works fine. :)


But if it's possible (ehm, should be) I'd still like to have the terminal pop up and show the information when the files are checked using cksfv. :D

---

### Post by ow50 on 2005-09-07
I'll share my scripts as well. They use cfv. You'll need a gnome-terminal profile called "open" which is configured to keep the terminal window open after all commands have been run.
```
#!/bin/bash

# Check an SFV file searching also for wrongly named files.

directory=$(dirname "$1")
cd "$directory"
gnome-terminal \
	--window-with-profile="open" \
	--working-directory="$directory" \
	--geometry=85x33+310+220 \
	-x cfv -v -s -f "$1"
```
```
#!/bin/bash

# Check an SFV file searching also for wrongly named files and rename all
# wrongly named files.

directory=$(dirname "$1")
cd "$directory"
gnome-terminal \
	--window-with-profile="open" \
	--working-directory="$directory" \
	--geometry=85x33+310+220 \
	-x cfv -v -s -n -f "$1"
```
Since these scripts are used only for SFV files, I prefer not to clutter the nautilus-scripts menu. I have defined a mime-type "text/x-extension-sfv" and wrote desktop files to associate the above scripts with the SFV mime-type. I can post instruction for that if someone is interested.

---

### Post by Lapse on 2005-09-07
Wow, sound good.
Please post those instructions if you don't mind.


Also, I tried with a script just to see if it works. Made the profile open and set it to keep it open after commandos. But When I try it on an sfv file I only get.

```
thesfvfile.sfv : No such file or directory (CF)
0 files, 0 OK, 1 chksum file errors.  0.001 seconds, 0.0K/s

```

It's the same on all of the sfv-files.

---

### Post by ow50 on 2005-09-07
The scripts should apparently use "cd $NAUTILUS_SCRIPT_CURRENT_URI" if used as nautilus scripts. So the **nautilus scripts** would be
```
#!/bin/bash

# Check an SFV file searching also for wrongly named files.

cd $NAUTILUS_SCRIPT_CURRENT_URI
gnome-terminal \
	--window-with-profile="open" \
	--geometry=85x33+310+220 \
	-x cfv -vs -f "$1"
```
```
#!/bin/bash

# Check an SFV file searching also for wrongly named files.

cd $NAUTILUS_SCRIPT_CURRENT_URI
gnome-terminal \
	--window-with-profile="open" \
	--geometry=85x33+310+220 \
	-x cfv -vsn -f "$1"
```

The second option would be **mime-type specific scripts**. Instructions:

1. Add the following to ~/bin or where-ever you keep your scripts.

```
gedit ~/bin/cfv-check
```
Paste:
```
#!/bin/bash

# Check an SFV file searching also for wrongly named files.

directory=$(dirname "$1")
cd "$directory"
gnome-terminal \
	--window-with-profile="open" \
	--working-directory="$directory" \
	--geometry=85x33+310+220 \
	-x cfv -vs -f "$1"
```
```
gedit ~/bin/cfv-check-rename
```
Paste:
```
#!/bin/bash

# Check an SFV file searching also for wrongly named files and rename all
# wrongly named files.

directory=$(dirname "$1")
cd "$directory"
gnome-terminal \
	--window-with-profile="open" \
	--working-directory="$directory" \
	--geometry=85x33+310+220 \
	-x cfv -vsn -f "$1"
```

2. Add a mime-type for SFV files.

```
gedit ~/.local/share/mime/packages/Override.xml
```
Make the file look like (but don't remove entries for other mime-types):
```
<?xml version="1.0" encoding="UTF-8"?>
<mime-info xmlns="http://www.freedesktop.org/standards/shared-mime-info">

<mime-type type="text/x-extension-sfv">
	<comment>SFV checksum</comment>
	<glob pattern="*.sfv"/>
</mime-type>

</mime-info>
```

3. Rebuild mime-type database. The changes should be instant-applied, but if not try logging out and logging back in.

```
update-mime-database ~/.local/share/mime
```

4. Add desktop files.

```
gedit ~/.local/share/applications/cfv-check.desktop
```
Paste replacing the username on the "Exec" line:
```
[Desktop Entry]
Encoding=UTF-8
Name=CFV Check
MimeType=text/x-extension-sfv;
Exec='/home/osmo/bin/cfv-check'
Type=Application
Terminal=false
NoDisplay=true
```

```
gedit ~/.local/share/applications/cfv-check-rename.desktop
```
Paste replacing the username on the "Exec" line:
```
[Desktop Entry]
Encoding=UTF-8
Name=CFV Check and Rename
MimeType=text/x-extension-sfv;
Exec='/home/osmo/bin/cfv-check-rename'
Type=Application
Terminal=false
NoDisplay=true
```

5. Right-click an SFV file. You should see entries "CFV Check" and "CFV Check and Rename".

Let me know if it works. It's a long time since I set this up and it's not very thoroughly tested.

Edit:
Fixed cfv options (-f should be last).

---

### Post by Lapse on 2005-09-07
Thanks for using your time for this. :O

I followed all the steps of the mime-type specific scripts, but it simply doesn't show up.
I've logged out and in and I've even rebooted the computer.

---

### Post by ow50 on 2005-09-07
[QUOTE=Lapse]I followed all the steps of the mime-type specific scripts, but it simply doesn't show up.[/QUOTE]

Did the mime-type get correctly installed? Right-click an SFV file and check if the mime-type is "text/x-extension-sfv".

If no, I'd like to see the output of
```
tree ~/.local/share/mime
```

If yes, you can try:
```
echo "text/x-extension-sfv=cfv-check-rename.desktop;cfv-check.desktop;" >> ~/.local/share/applications/mimeinfo.cache
echo "text/x-extension-sfv=cfv-check.desktop" >> ~/.local/share/applications/defaults.list
```

But probably if the mime-type got correctly installed there's something wrong with the desktop files.

If this seems to get too troublesome, use the nautilus-scripts. They work, right?

---

### Post by Lapse on 2005-09-07
[QUOTE=ow50]Did the mime-type get correctly installed? Right-click an SFV file and check if the mime-type is "text/x-extension-sfv".

If no, I'd like to see the output of
```
tree ~/.local/share/mime
```
[/QUOTE]
Mime-type: application/x-sfv

~/.local/share/mime$
aliases  
globs  
magic  
packages   -> Override.xml  Override.xml~
subclasses  
text   -> x-extension-sfv.xml
XMLnamespaces

[QUOTE=ow50]If this seems to get too troublesome, use the nautilus-scripts. They work, right?[/QUOTE]
Yeah, I tried it and it works fine. :)

---

### Post by ow50 on 2005-09-07
[QUOTE=Lapse]Mime-type: application/x-sfv[/QUOTE]
Ah! Reading above, it seems you installed Parano, which created a mime-type "application/x-sfv" and I tried to get you to create "text/x-extension-sfv". Conflict!

You could change the MimeType in the desktop files to "application/x-sfv" and perhaps remove the "text/x-extension-sfv" mime-type.

The reason why I chose the "text/x-extension-sfv" mime-type myself, is that it gives me text previews of the SFV files. I don't really know any official standards on mime-type naming.

---

