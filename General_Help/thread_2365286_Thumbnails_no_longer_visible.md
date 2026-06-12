---
title: "Thumbnails no longer visible"
date: 2017-07-04
forum: General Help
---

### Post by joseph123321123 on 2017-07-04
Hi there,

When browsing files in nautilus some files types such as .pdf weren't showing thumbnails whilst others, such as .odt and .jpeg were. I looked online to see if there was an easy fix, but couldn't really find anything. I had tried changing the file size to display from 10mb to 100mb in nautilus preferences but that didn't have any effect.

So I found something suggesting that I delete the thumbnails folder and then make a new one. And possibly quite foolishly I tried that.

I did: [COLOR=#111111][FONT=Consolas]sudo rm ~/.cache/thumbnails

[/FONT][/COLOR]However terminal gave a message about it being a directory.

 So I deleted the folder in nautilus and then did: [COLOR=#111111][FONT=Consolas]sudo mkdir ~/.cache/thumbnails[/FONT][/COLOR]

I rebooted and now all the thumbnails are gone. 

 Is there an easy way to get nautilus to display the thumbnails again?

Any ideas?

Thanks.[COLOR=#111111][FONT=Consolas]
[/FONT][/COLOR]

---

### Post by CatKiller on 2017-07-04
Why did you delete and create the folders as root? They're in your Home folder.

Delete the directory that you created that your user account now cannot write to. The folder will be recreated and populated with thumbnails automatically.

Seriously, don't do things as root unless you really really have to.

With regards to your initial problem, I believe the control for which filetypes generate thumbnails is the org.gnome.desktop.thumbnailers dconf key. More information [here]("https://developer.gnome.org/gnome-desktop3/stable/GnomeDesktopThumbnailFactory.html").

---

### Post by joseph123321123 on 2017-07-04
Thanks for your reply.

I wasn't aware that it would be in the root directory.

The thumbnails are now as they were before so that's a relief anyway.

Some filetypes such as .pdf and some video files, .avi and .mov still don't have thumbnails though.

Do you have any ideas about that?

Cheers

---

### Post by CatKiller on 2017-07-04
> **joseph123321123 said:**
> I wasn't aware that it would be in the root directory. Now that I think about it I guess that's what the ~ symbol means?

They were in your Home directory. The Home directory of the current user is what the ~ represents.

You never need to be anything other than your user to change anything in your Home folder. In almost all cases, you can't change anything outside of your Home folder without being the *root* user, the system user that has all privileges. If you think about it for a moment, you will see why that is sensible. Becoming the *root* user is something that you should never do unless you really really need to. That is what you did when you used the *sudo* command: you temporarily elevated your privileges to those of the absolute most-trusted user. If you misuse it, you cause yourself problems, which is exactly what happened here.

There is more information on [this page]("https://help.ubuntu.com/community/RootSudo").

> **joseph123321123 said:**
> Some filetypes such as .pdf and some  video files, .avi and .mov still don't have thumbnails though.

Do you have any ideas about that?

I included that information in my first post, but you might not have seen it since it was in an edit. You can use dconf-editor to see if the thumbnailer has been disabled for those filetypes by checking the key listed in that post. How thumbnailers work is detailed in the link I gave you. AIUI, if you have something that can display those filetypes then you probably also already have a thumbnailer for those filetypes, but it's possible that you'd need to tweak it in some way to make uncommon formats work.

---

### Post by joseph123321123 on 2017-07-04
Ok thanks. 

The thumbnailer isn't disabled

[https://ibb.co/fJbWja](https://ibb.co/fJbWja)

> [COLOR=#000000]AIUI, if you have something that can display those filetypes then you probably also already have a thumbnailer for those filetypes[/COLOR]

Yeah, was thinking similar.

Okular and VLC would be that. 

How would such tweaking be made?

Haven't done anything with dconf before :?

---

### Post by joseph123321123 on 2017-07-04
Solved

Evince and Totem were necessary. Downloaded 'em now 's all good!

:)

---

### Post by CatKiller on 2017-07-04
Awesome, glad to hear it! And you already knew to mark the thread as solved when it was solved. You can come again :)

---

