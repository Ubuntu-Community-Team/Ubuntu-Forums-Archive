---
title: "How Do I create a config file under the /etc directory"
date: 2008-05-12
forum: General Help
---

### Post by Gndoab on 2008-05-12
I need to create a file called asound.conf in order to get my sound card working correctly ([http://ubuntuforums.org/showthread.php?t=104704&highlight=creative+live+external&page=2](http://ubuntuforums.org/showthread.php?t=104704&highlight=creative+live+external&page=2)). I was just wondering how I go about doing so, because using the x-server text editor, it won't allow me to save to the directory (I assume it's a console command I don't know about)

I'm Using GG with Gnome. Thanks for the help!

---

### Post by ruggersway on 2008-05-12
At the risk of this being something you already tried

Create the file
$ sudo touch /etc/asound.conf

Edit the file
$ sudo vi /etc/asound.conf

You can just skip touch and go to vi or gedit if you aren't good with vi.  I just like to touch the file before I work on it.

Hope that works for you.

---

### Post by Xgen on 2008-05-13
Perhaps try in terminal:

'asoundconf list' (for a list of installed sound cards)
'asoundconf set-default-card PARAMETER'   (substitute PARAMETER for a card in the list)
This will create a 'asoundrc.asoundconf' file in your home directory with the settings required.

---

