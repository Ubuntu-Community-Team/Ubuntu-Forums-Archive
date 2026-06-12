---
title: "Permission denied access"
date: 2015-02-23
forum: General Help
---

### Post by RobGoss on 2015-02-23
Hello everyone sorry if this post is in the wrong place this is my fist time posting here.

I'm new to Linux but have been wanting to learn it for some time now. I installed Ubuntu 14.10 and love it but I ran into a small problem

I wanted to change the login screen image to something else and I try to move the image to the following directory below.

/usr/share/backgrounds

The problem is when I try to move the file in this directory i get the follow message ( [COLOR=#ff0000]Error moving file: Permission denied [/COLOR])
Can you please tell me what I am doing wrong and how can I fit it so I can add different wall paper into this directory.

Thank you so much for any help on this matter. Rob

---

### Post by grahammechanical on 2015-02-23
I do not think that simply putting an image file in /usr/share/backgrounds/ will necessarily make that image available as a desktop wallpaper. On the other hand putting the image into the Pictures folder and then opening System Settings>Appearance and changing the panel on the left from "Wallpapers" to "Pictures Folder" will do it.

You are getting that error message because of the way that Ubuntu protects us from ourselves. We can access system folders but we cannot edit system files or even place files into system folders as a standard user. We need administrator privileges/permissions. In Linux this is called being "root."

To copy or move that image into /usr/share/backgrounds/ we need to open the File Manager (nautilus) with root or administrator privileges. I do that by running

```
sudo -H nautilus
```

I ignore the error messages. They are normal. But I am always careful because by using the file manager in this way I now have the power to break the OS.

Regards.

---

### Post by xxvirusxx on 2015-02-23
Completion

Or if image can`t be viewed by user when browse to **/usr/share/backgrounds/**, run in **Terminal** as **root** this command:

```
 chmod 755 /usr/share/backgrounds/your_image.jpg_or.png
```

And now you image is see in Appereance

---

### Post by RobGoss on 2015-02-24
Thank you both for the fast reply and taking the time to help me with this problem. I will try your suggestions in order to implement these changes.

I'm sure I will be back with more questions. Oh by the way which Linux OS you you say is the best in performance?

I'm currently using Ubuntu 14.10 and love it. Thank you so much.

---

### Post by xxvirusxx on 2015-02-24
> **robert159 said:**
> Oh by the way which Linux OS you you say is the best in performance?

Depend what hardware you have.

---

### Post by Ruben_van_Smirren on 2015-02-24
When you login to the server with your username/pwd make sure you start with the command "sudo -i" this actually might help for this issue but is also handy if it comes to managing the client/server. the -i option is like typing sudo in front of each command you give.

When you are just starting it might be handy to read a few online tutorials so you understand the commandline a bit more (it helped me out when i was starting Linux)

---

### Post by deadflowr on 2015-02-24
I've not had the chance to run normal Ubuntu 14.10(only kubuntu and ubuntu mate) so i can't say for certain that things haven't change, but from memory simply moving a picture into the /usr/share/backgrounds folder won't do anything but add a picture to the folder.
For the image to actually be shown in the Appearance section you need to add an entry for it in the .xml script /usr/share/gnome-background-properties/utopic-wallpapers.xml.
Or at least that is the way it has been for years. Like i say haven't ran normal/unity Ubuntu 14.10; but I doubt it changed that design.
(You'll run into the same permission problems as you do to move/copy the image, since /usr/share is root-owned, and not owned by you.)

Of course doing this would give all users the ability to use the image(s) you want to add (or you can even completely replace the default images with only your own, if you want).
The whole thing, while fun to learn, is ultimately a giant pain. (Lots of trials and errors, mainly with the fact the text editor by default save a backup and the Appearance page reads those backup so you end up with duplicate entries until you delete the backup file. Also, one missed character in some line in the xml file will/can leave you with a crippled selection of images to choose from in Appearances.)

This is probably over the top which is why:
Using the above mentioned approach of toggle the Appearance selection to Pictures Folder is an easier option, and more suitable if you're the only user on the machine, imo.
You simply need to make sure the image permission are readable by Other(?), I think; might be best to make the file readable by both group and other to be safe.

---

### Post by RobGoss on 2015-02-26
Thank you so much for the tips I'll try this to see how it goes.

Yes I've been reading up on Linux but there's so much info its overwhelming. But thanks for the help.

---

