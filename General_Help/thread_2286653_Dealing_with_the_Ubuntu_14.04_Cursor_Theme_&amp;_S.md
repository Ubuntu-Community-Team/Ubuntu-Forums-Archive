---
title: "Dealing with the Ubuntu 14.04 Cursor Theme &amp; Size Matter Entirely"
date: 2015-07-13
forum: General Help
---

### Post by oldefoxx on 2015-07-13
I posted on this subject before, but it was an effort to get others to put in their bits of the puzzle.  None did, and the thread was eventually removed.

I wanted answers though, so I kept at it.  And I documented my way along as I went.  Now I am here to summarize the steps need (which may be enough for a lot of you), and if that is not quite enough, I am attaching three documents.  The brief one just deals with the above steps.  The second explains these steps in some detail, but you get to the same end.  The third is a more detail-oriented journal of finding my way to that end.  I borrowed a lot from other posts on the subject, off this forum and from other sources, and cut out all personal references as to whom said or did what.  This was not to slight anybody, but to just try and get to the core of the matter.  Rather  than dealing with each command separately, why not copy-paste the code to a text file and make it executable by doing a "chmod  +x* filename* after you save it?

**# STEPS TO KEEPING YOUR UBUNTU SOFTWARE UP TO DATE:**
```
sudo apt-get -qq update
sudo apt-get -qq -y dist-upgrade
sudo apt-get -qq -y autoremove
/usr/bin/update-manager
```

**# STEPS TO CHANGE THE MOUSE CURSOR SHAPE, COLOR, AND SIZE:**
```

dir /usr/share/icons/*/cursor.theme | awk -F/ '{print $(NF-1)}'                 # So you can see your cursor choices
CURSOR=DMZ-Black-Large; SCALE=2                                                # Or other cursor of choice and size (1 - 2.65)                                                
gsettings set org.gnome.desktop.interface cursor-theme "$CURSOR"
gsettings set com.canonical.Unity.Interface cursor-scale-factor $SCALE
gsettings set  org.gnome.desktop.interface.cursor-size 48                    # Or 24, 32, or 64gsettings set  org.gnome.desktop.interface
sudo update-alternatives --config x-cursor-theme                                  # pick the same font as you entered in CURSOR

```You have just one line to modify in order to select any cursor or any size.  That is the CURSOR= ; SCALE= line.
The cursor choices are most of the folder names that you find in /usr/share/icons/  there.

**# SETTINGS RELATED TO SIZE OF THINGS ON SCREEN:**
```

gsettings set org.gnome.desktop.interface.scaling-factor 0                    # adjust scale to follow monitor resolution size
gsettings set  org.gnome.desktop.interface.text-scaling-factor 1.2         # increase File Manager Display Magnification
gsettings set  org.gnome.desktop.interface.document-font-name 'sans 14'  # Bigger text in document viewer
gsettings set org.gnome.desktop.interface..font-name 'ubuntu 12'         # Change Gtk+ and Toolbar font and size
gsettings set org.gnome.desktop.interface.monospace-font-name 'ubuntu 12'  # Font & size in terminal windows
```
**# SETTINGS SPECIFIC TO THE GEDIT TEXT EDITOR:**
```

gsettings set org.gedit.preferences.editor.editor-font 'Monospace 12'    # Default gedit editor font & size
gsettings set org.gedit.preferences.editor.use-default-font true              # use above font instead on native gedit font
gsettings set org.gedit.preferences.editor.tab-size 4                              # Monospace needs fewer spaces for tabs
gsettings set org.gedit.preferences.editor.insert-spaces true                 # whether to use spaces instead of tabs or not
gsettings set org.gedit.preferences.editor.highlight-current-line true      # color current line or not
gsettings set org.gedit.preferences.editor.display-line-numbers false    # make true if you want to go to a line later

```
Obviously there are many settings related to Ubuntu's applications, and gsettings handles a lot of them.  To find out everything that is possible, use "**gsettings list-recursively | less**".  Or, to see what a key is used for, do the following:```
sudo apt-get install dconf-tools
dconf-editor
```
In the dconf-editor, you have access to all the keys and can change the values associated with each key.  To know what the key is tied to, just click on it.  dconf-editor then provides a brief summation of what that key is used for.  Using dconf-editor is easy if you remember two rules:  (1) If an arrow is shown by a term in the left pane, click on the arrow, not the term.  The arrow is a toggle that opens to show you an expanded view.  (2)  If no arrow, click on the term.  Thr keys under it will then appear in the right pane, where you can change them.

Changes made in dconf-editor or done using gsettings are immediate.  With gsettings, you can use the argument "get" in place of "set" to see the current settings for any key.

---

### Post by CantankRus on 2015-07-13
> **oldefoxx said:**
> I posted on this subject before, but it was an effort to get others to put in their bits of the puzzle.  None did, and the thread was eventually removed.

I wanted answers though, so I kept at it.  And I documented my way along as I went.  Now I am here to summarize the steps need (which may be enough for a lot of you), and if that is not quite enough, I am attaching three documents.  The brief one just deals with the above steps.  The second explains these steps in some detail, but you get to the same end.  The third is a more detail-oriented journal of finding my way to that end.  I borrowed a lot from other posts on the subject, off this forum and from other sources, and cut out all personal references as to whom said or did what.  This was not to slight anybody, but to just try and get to the core of the matter.

Now here is what it boils down to:```

sudo apt-get update; sudo apt-get install gnome-tweak-tool unity-tweak-tool dconf-tool
dir /usr/share/icons/
CURSOR=DMZ-Black-Large; SIZE=48; SCALE=2
[COLOR="#FF0000"]sudo[/COLOR] gsettings set org.gnome.desktop.interface cursor-theme "$CURSOR"
[COLOR="#FF0000"]sudo[/COLOR] gsettings set org.gnome.desktop.interface cursor-size $SIZE
[COLOR="#FF0000"]sudo[/COLOR] gsettings set com.canonical.Unity.Interface cursor-scale-factor $SCALE
sudo update-alternatives --config x-cursor-theme

```
You have just one line to modify in order to select any cursor or any size.  That is the CURSOR= ; SIZE= ; SCALE= line.

[COLOR="#FF0000"]After this, you need to use dcont-editor, tweak-tool, and unity-tweak-tool in order to make your change happen everywhere[/COLOR].  Look at the 2nd attachment for detailed instructions for each of these tools.  There are a few helpful hints in there about doing this and more as well.

The last attachment shows you how it all finally came together, The other files are just extracts from the leading part of this one.  This one also gives you links to some interesting cursor themes that others like.  It also steers you to some of the posts or articles that I found very helpful.  Did you know there is a wiki devoted to the gnome cursor?  I provide the link.  Some of the other links provided are to other's posts that I felt were really on the mark, and I included them in case they work better for you as well.

The shortcoming is the unity-tweak-tool.  Thar's why you have to go to the command line mode.  It doesn't do enough as far as adding more cursor themes or getting the size right.  But with a few manual commands, you can steer around its limits.  Just to be sure though, it might be best to pick a cursor theme that
has been stripped down to one size.  This will be indicated in its name, like including Medium or Large.  You don't know what cursor choices you have?  Get the attachments.  Plenty of answers in there.  Including how to find what you have, and how to get and add others.

All the tweak tools do is change the dconf setting for the current user.
Your "**[COLOR="#FF0000"]sudo[/COLOR] gsettings**" commands are changing settings for the user **root**. 
If you remove "[COLOR="#FF0000"]sudo[/COLOR]" from your **gsettings** commands you don't need to use any of the tweak tools.
You can monitor what the tweak tools do by running...
```
dconf watch /
```
and then changing the cursor using a tweak tool.
[ATTACH=CONFIG]263191[/ATTACH]

It is also not necessary to change "**org.gnome.desktop.interface cursor-size**" in unity,
as "**com.canonical.Unity.Interface cursor-scale-factor**" does this for you and will override the dconf **cursor-size** setting.
ie
```
[COLOR="#006400"]**glen@Trusty:~$**[/COLOR] gsettings **get** org.gnome.desktop.interface cursor-size
24
[COLOR="#006400"]**glen@Trusty:~$**[/COLOR] gsettings **set** com.canonical.Unity.Interface cursor-scale-factor 2
[COLOR="#006400"]**glen@Trusty:~$**[/COLOR] gsettings **get** org.gnome.desktop.interface cursor-size
48

```
The default DMZ themes support different sizes.(24, 32, 48, 64)
For a consistent size, you must also create a **~/.Xresources** file with a line specifying a size the same as
your "org.gnome.desktop.interface cursor-size" setting.
eg
```
echo "Xcursor.size:**48**" > ~/.Xresources
```
Log out to complete the change.

As you said, alternatively you can use a cursor theme like **DMZ-Black-Large** which is made with just the one large pixel layer
so changing the dconf cursor-size setting or using a ~/.Xresources file is unnecessary.
Just need to also "sudo update-alternatives --config x-cursor-theme".
The benefit of using a cursor theme made with just the one size is you get this same size at the greeter.
You'll find DMZ-Black and DMZ-White themes of just one larger size [**_[COLOR="#B22222"]HERE[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=2048046&p=12735911#post12735911")

---

### Post by oldefoxx on 2015-07-14
Thanks lot for the rapid response, additions, and corrections.  I even made one myself, in that, the install is for dconf-tools, not dconf-tool.  As to the overuse of "sudo", I was drawing on a number of sources, and it does get overused.  Perhaps.  Anyway, a way to find  out is to try doing something without having "sudo", and then go back and stick "sudo" in front if the command is rejected. 

Going back is easy in terminal mode, as you can use the up- and down-arrows to bring back previously entered commands, and the left- and right-arrows allow you to position anywhere within the brought back command.  Then the Back and Del key lets you delete one character back or at the current character position, while the other keys let you insert new text starting at the current position.  Simple to learn, simple to use, and beats reintering a lot of exacting commands from scratch.

Now we have in just a few short posts the essence of what it takes to get a change made to the displayed mouse pointer.

As noted, but not directly stated, in the reply, "sudo" can make a change effect all users, and leaving it off can make it effect just one user.

In my case, I am the only user, so either way is fine.  But if you share a PC with a spouse, children, or whomever, you could give each one a mouse of preference.
 
Noted in my research, some like a red mouse cursor as it is most distinct against most backgrounds.  Others like green, blue, or something besides a simple arrow.  You can even find left-hand versions of some mouse cursor themes.  I find solid black is easier to track than a plain white cursor.  Ir's all a matter of personal choice now, as the means of making change has pretty much been brought together.

I'm going to reflag this thread as Solved, though I imagine others may want to add something to it going forward.  But when you are searching for answers, the sight of SOLVED on a thread tends to draw your interest.

---

### Post by CantankRus on 2015-07-14
> **oldefoxx said:**
> As noted, but not directly stated, in the reply, "sudo" can make a change effect all users, and leaving it off can make it effect just one user.

In my case, I am the only user, so either way is fine.  But if you share a PC with a spouse, children, or whomever, you could give each one a mouse of preference.
Hi oldefoxx, I believe the use of sudo with gsettings is not creating a system wide setting in this case... just altering root's dconf. (/root/.config/dconf/user) 
Individual users will still load with the settings stored in their own **~/.config/dconf/user** file.
I think this is why you still had to use the tweak tools to set your user settings.

Good work though, in attempting to sift through all the info out there and place in one location.

---

