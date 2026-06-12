---
title: "File Associations (.avi not detected as &quot;AVI video&quot;)"
date: 2007-11-19
forum: General Help
---

### Post by emwine on 2007-11-19
How do I edit file type associations?

I'm getting this exact [issue]("http://ubuntuforums.org/showthread.php?t=544150"), but I'm posting here because it isn't a multimedia problem-- it's some kind of association in nautilus that got borked somehow.

If I follow the instructions and rename the .avi, it works until I reboot.  If I use the open menu and select one of the players, it works fine.  But double-clicking brings up the annoying message from the link.  There's nothing wrong with the files, this happens to every one of them, and they have not changed.

I think this started when I had a permissions problem on one of my media directories and my fussing with things to fix that led to this issue.  But I don't know how to restore the default associations, getting rid of this "avi document" type that has apparently been added to nautilus associations.

I don't think this can be fixed by choosing Properties|Open With from the secondary click menu for a .avi file.  I've tried that-- I can't remove "Movie Player" or "VLC", nor can I add another instance of either.  The problem is more complex than this dialog is able to handle.

---

### Post by Spam Banjo on 2007-11-25
Bump.

I got different problems, well... annoyances to quash... but would like to edit file associations in Ubuntu 7.04 and Xubuntu 7.10.

---

### Post by pab10 on 2007-11-29
in nautilus file manager, right click properties, one of the tabs on that dialog has open with (associations) dialog.

Thats as much as I know and would be interested to know other ways to edit associations myself...

---

### Post by emwine on 2007-11-29
I was able to fix my problem by messing around in ~/.local/share/mime.  I'm not sure what step fixed it, and I'm unwilling to try to duplicate the problem.

On a related note, I wanted all my ".pgn" files to invoke a certain script I made when double-clicked and display a certain icon.  Getting the script invoked was easy enough using nautilus' dialogs.  But changing the icon only took effect on the specific .pgn file I was working on.  So, I followed the general plan [here]("http://adrianus.wordpress.com/2007/02/07/howto-add-new-mime-types-and-icon-for-visio-document-in-ubuntu/") to globally update the display icon for my pgn files.  [Note: pgn != png.  These pgn files are chess games, not images.]

---

### Post by berarma on 2007-12-02
Removing the .local/share/mime contents has fixed this problem for me. It must be some kind of problem with old configurations. The only drawback seems to be that all my customized associations are lost.

---

### Post by Spam Banjo on 2007-12-04
> **berarma said:**
> Removing the .local/share/mime contents has fixed this problem for me. It must be some kind of problem with old configurations. The only drawback seems to be that all my customized associations are lost.

Thanks for the reply... will probably take a look at modifying some code in the files in that location and see if I can't help you keep your old preferences if future. I'm sure someone on here will if I don't!

---

