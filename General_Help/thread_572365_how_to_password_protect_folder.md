---
title: "how to password protect folder?"
date: 2007-10-10
forum: General Help
---

### Post by redss on 2007-10-10
I am running ubuntu fiesty and have a folder on my desktop called pictures, which contains private pictures.

My roomate uses the computer also and I dont want her to have access to that folder. 

Is there a way that I can make ubuntu require a password when attempting to open that destop folder?

I don't want to have to logoff and require her to login under a different account for her to use the computer.

---

### Post by zero-9376 on 2007-10-10
i too would be interested in such a feature, however if you cant find a solution using a better means you can always change ownership of the folder and its contents using sudo to disallow your account to read the files  and then reenable access when you need to.

the other thing you could so is use a zip file to store the pictures. you can create a a new zip archive using the archive manager, set a password using edit-password and then add the pictures to the archive. once again this is not the most elegant solution and you will need to open the zip file in the archive manager to add any new files but it will give you the password based protection you want

---

### Post by mocoloco on 2007-10-10
I know you mentioned this is not the solution you're looking for, but if I were in your situation I would just set up a second user.  If your roommate just needs access to all of your files, by default everything in your home folder is accessible to other users.  So basically you would just have to log in as you, right-click your pictures folder and under properties for permissions change access for others to "none".
You could even set up a bookmark to your home folder in your roommate's file browser, to make it easy to get to.

---

### Post by swisscow on 2007-10-10
I gutsy kubuntu you can right click on a folder and choose encrypt. Haven't tried it yet...

---

### Post by carnagex420x on 2007-10-10
if you use ccrypt, you can encrypt the whole CONTENTS of the folder but not the folder its self.

---

### Post by Tavathlon on 2007-10-22
Possibly Cryptonit? Found it in Synaptics, but I'm not sure how it works..  =P

Also hunting for the same thing..

---

### Post by Jofaba on 2007-10-27
It's not secure, but it sets up a barrier at least. It'll stop people from getting into the folder if they don't know how to use the terminal, and if its a trusted roomate who will respect your privacy then it'll stop her from accidentally going into the folder, but here ya go:

Open terminal, type "sudo nautilus" if you're using gnome, navigate to the folder and set full permissions as "root", and under "Others" set folder permission to none. 

As user, you'll get a wrong permissions box and nothing will display.  

In the end, we all know this is for hiding porn. Perv =P

Speaking of which,  you won't be able to save to this folder from a browser. You'll always have to log in using terminal to move stuff to that folder. Soooo, if you plan on being able to  save to it, you'll either have to change permissions before trying to save, or you'll have to save to an unprotected folder, then move the files while logged in as root, but then you have that whole file ranaming problem. 

It's a conundrum.

---

### Post by dayvy on 2007-10-27
Try the following. It works great.

[http://www.tomatarium.pwp.blueyonder.co.uk/cryptkeeper.html](http://www.tomatarium.pwp.blueyonder.co.uk/cryptkeeper.html)

d.

---

### Post by dayvy on 2007-10-27
I should mention that once you install encfs, fuse is usually added to /etc/modules automatically. Just make sure you're part of the fuse group.

d.

---

### Post by zero-9376 on 2007-10-27
following on from the idea of setting the permissions to root you can then install a nautilus extension that adds an open as administrator option to the right click menu which would make things more convinient although programs (photo management) still wont be able to access the folder
i cant remember the name now but you should be able to searh synaptic for nautilus and figure it out

---

### Post by ice60 on 2007-10-27
you can use the nautilus-script called encryption on this page -
[http://rob.pectol.com/component/option,com_wrapper/Itemid,30/](http://rob.pectol.com/component/option,com_wrapper/Itemid,30/)
there's an old thread about how to set it up. probably you make the script executable with chmod +x, then put it in ~/.gnome2/nautilus-scripts. then you can right-click a file and from the scripts menu select encrypt. 

you can use truecrypt too, but it's a little bit more difficult to setup because there's no GUI, however you can just follow iron-geeks setup guide for windows, the windows version has a GUI, but the setup steps are exactly the same.
[http://www.irongeek.com/i.php?page=videos/truecrypt1](http://www.irongeek.com/i.php?page=videos/truecrypt1)

when it's setup you mount the file with -
truecrypt file_name mount_point
to unmount - sudo truecrypt -d
list TC mounted partitions - sudo truecrypt -vl

---

### Post by wheredidrealitygo on 2007-10-27
I recommend Cryptkeeper, as suggested by Dayvy.

Link to .debs: [http://www.getdeb.net/app.php?name=Cryptkeeper]("http://www.getdeb.net/app.php?name=Cryptkeeper")

Very straightforward to set up, located in system tools after install (must restart). Click system tray icon once, hit "new encrypted folder", set location and password (with a gui), finished.

To encrypt, click icon once, and click the path. Folder disappears. To re-mount, click system tray icon, and click the path, requests password. Very nice.

---

