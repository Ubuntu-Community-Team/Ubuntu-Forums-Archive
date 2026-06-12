---
title: "Extra /home in my ubuntu system"
date: 2013-02-22
forum: General Help
---

### Post by flnx on 2013-02-22
When I was getting acquainted with files and directories as a newbe, I mistakenly created a /Home directory. I also have the /home directory via ubuntu installation. So far it doesn't seem to effect/cause operational problems. How can I get rid of this other /Home directory without harming my Ubuntu 1204 OS. This is where it resides;

fff@asusslinux:~$ locate Home
/usr/share/applications/kde4/Home.desktop
/usr/share/unity-2d/shell/dash/Home.qml
/usr/share/unity-2d/shell/dash/HomeButton.qml
/usr/share/unity-2d/shell/dash/HomeButtonApplication.qml
/usr/share/unity-2d/shell/dash/HomeButtonDefaultApplication.qml

Here are the contents with in /Home,which is within /home
(If I delete /Home then I wipe out the following valid folders). Should I leave everything as is or what. Would surely appreciate your help on this and thanks;
 
/home/fff/craigs_sale 
/home/fff/Desktop
/home/fff/Documents
/home/fff/Downloads
/home/fff/Dropbox
/home/fff/efax-gtk-server
/home/fff/faxin
/home/fff/faxout
/home/fff/faxsent
/home/fff/Music
/home/fff/Pictures
/home/fff/Public
/home/fff/Templates
/home/fff/1211183840.efax.log
/home/fff/adapt
/home/fff/C:\nppdf32Log\debuglog.txt
/home/fff/dpwipe_new.zip
/home/fff/examples.desktop
/home/fff/google-earth-stable_current_i386.deb
/home/fff/scanModem.2011080803
/home/fff/ubuntu-12.04-desktop-i386.iso
/home/fff/wvtest

---

### Post by deadflowr on 2013-02-22
So you have /home/Home?
Why not simply move/copy the contents into your own userfolder?

---

### Post by ersatzsplatt on 2013-02-22
I don't really understand your problem or situation.
You say you created /Home  ... but I don't see /Home when you invoke locate.
You say you have /Home within /home  ... and from what you have listed I think I might have some inkling of what you are writing about there.
First, do not refer to a subdirectory with a leading /.  A leading / implies root ... not a subdirectory.

You should be able to get rid of that stuff by typing:
"sudo deluser fff"

If you want to save any of those files first, then copy them to the work area you intend to save before the command I showed you above.

... I think that is what you are looking for.

---

### Post by deadflowr on 2013-02-22
If I understand right, the OP has /home/Home/home/fff/bunch o folders and files. I least this is what i gather with the comment about the files within the /Home folder which is within the /home folder.
In which case copying the files into /home/fff would be enough. Afterward the OP can delete the /Home folder.

---

### Post by varunendra on 2013-02-23
> **deadflowr said:**
> In which case copying the files into /home/fff would be enough. Afterward the OP can delete the /Home folder.
Not an expert on this, but I think it is also important to take a look at fstab.

Although, unless they have manually created an abnormal entry there, it should be /home anyway. So I guess we are also interested in outputs of -
```
cat /etc/fstab
ls -d ~
```

Once confirmed that everything is normal, there should be no problem in following what deadflowr suggested.

---

