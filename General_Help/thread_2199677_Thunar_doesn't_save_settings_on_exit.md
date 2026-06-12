---
title: "Thunar doesn't save settings on exit"
date: 2014-01-15
forum: General Help
---

### Post by kristal00 on 2014-01-15
Every time I reboot my system,  Thunar loses its settings for  view, window dimensions, column widths, etc, and reverts to its  installation defaults.

  I'm on Ubuntu 13.10 64bit, Thunar 1.6.3.

  Is there a way to make it remember its settings?

---

### Post by vasa1 on 2014-01-15
Thunar remembers its settings when I use it with the Xubuntu desktop. How did you install Thunar? Perhaps some dependencies are missing?

BTW, do you have these files:
~/.config/xfce4/xfconf/xfce-perchannel-xml/thunar.xml
~/.config/Thunar/accels.scm ?

The first seems to hold various settings:
```

<?xml version="1.0" encoding="UTF-8"?>

<channel name="thunar" version="1.0">
  <property name="misc-volume-management" type="empty"/>
  <property name="shortcuts-icon-size" type="empty"/>
  <property name="last-view" type="string" value="ThunarDetailsView"/>
  <property name="last-icon-view-zoom-level" type="string" value="THUNAR_ZOOM_LEVEL_NORMAL"/>
  <property name="last-show-hidden" type="bool" value="true"/>
  <property name="misc-single-click" type="bool" value="false"/>
  <property name="last-details-view-zoom-level" type="string" value="THUNAR_ZOOM_LEVEL_SMALLER"/>
  <property name="last-details-view-column-widths" type="string" value="50,758,50,50,232,50,50,76,67"/>
  <property name="last-window-width" type="int" value="683"/>
  <property name="last-window-height" type="int" value="721"/>
  <property name="last-window-maximized" type="bool" value="false"/>
  <property name="last-separator-position" type="int" value="183"/>
  <property name="last-location-bar" type="string" value="ThunarLocationButtons"/>
  <property name="last-sort-column" type="string" value="THUNAR_COLUMN_NAME"/>
  <property name="last-sort-order" type="string" value="GTK_SORT_ASCENDING"/>
  <property name="misc-date-style" type="string" value="THUNAR_DATE_STYLE_ISO"/>
  <property name="last-details-view-fixed-columns" type="bool" value="true"/>
  <property name="last-side-pane" type="string" value="ThunarShortcutsPane"/>
  <property name="misc-text-beside-icons" type="bool" value="false"/>
</channel>

```

---

### Post by ajgreeny on 2014-01-15
Are you making those changes on the fly or going into Edit -> Preferences.  Use the latter and the changes to the default view should stick.  Column width is a bit changeable on my system as well and seems dependent on column contents as far as I can find, so if you have any files or folders with long names the column will widen to show all the text.  Window size in may case is always exactly the same as the last time I closed thunar.

Have a good look through .config/xfce4/xfconf/xfce-perchannel-xml/thunar.xml to see if there is anything that seems wrong to you.

---

### Post by vasa1 on 2014-01-15
> **ajgreeny said:**
> ... if you have any files or folders with long names the column will widen to show all the text. ...
I don't know what I did but I don't have that happening. Instead longer filenames get truncated.

---

### Post by ajgreeny on 2014-01-15
Having checked thunar in my Xubuntu 12.04 I think I may have been wrong about that and I also find that columns are truncating long file names.

Perhaps that behaviour is from pcmnfm in Lubuntu which I have used on an older laptop in the past.

Obviously my memory is going fast!

---

### Post by kristal00 on 2014-01-16
I've just controlled the two file indicated and I found that I didn't have permissions to acces the folder ~/.config/xfce4/xfconf/xfce-perchannel-xml.
So I changed that permissions:
```
sudo chmod 777 ~/.config/xfce4/xfconf/xfce-perchannel-xml
```
and at the restart all work properly.

Thank you guys for the help :)

---

### Post by ajgreeny on 2014-01-16
> **kristal00 said:**
> I've just controlled the two file indicated and I found that I didn't have permissions to acces the folder ~/.config/xfce4/xfconf/xfce-perchannel-xml.
So I changed that permissions:
```
sudo chmod 777 ~/.config/xfce4/xfconf/xfce-perchannel-xml
```
and at the restart all work properly.

Thank you guys for the help :)That is a little worrying!

 I wonder why the folder was not given the correct permissions, which incidentally should not really be 777 but 755, or even 700 if you are paranoid on a multi-user machine.  Can you also tell us who is the owner of the folder, please, as it should be you as user, and as you did not have the usual permissions I am also wondering if it is owned by root for some inexplicable (at the moment) reason.

Have you made any changes to permissions on the folders or files in your home that might have given you this problem.

---

### Post by kristal00 on 2014-01-17
As I said in my first post, I'm on Ubuntu and not on Xubuntu.
Since nautilus annoying me with ever and ever refreshing the contents of those folder that contains many and many files (sometimes it also freezes during refreshing), I decided to change my default file manager (nautilus is always installed) and so I installed thunar.
At the beginning, I used sometimes one and sometimes the other, using thunar predominantly through the command ```
gksu thunar
```
Maybe on these occasions something must have gone wrong (I used thunar with root permission always to change repository and not for other purpose).

I think this is a necessary explanation.

Well, to answer your question I can tell you that the proprietary of the folder xfce-perchannel-xml is (I controlled the permission with thunar) "root" :-s and even for the father directory (xfconf) the proprietary is "root" as well as the xfce4 folder.

Do you need other infos?

---

### Post by ajgreeny on 2014-01-17
Your problem is that you are not the owner of those files and folders, and you should be owner of everything in your /home.  Using the chmod 777 means anyone can do anything with those files and folders,but still does not guarantee that they are owned by you, which they should be.

Also I don't understand why you used thunar as root to change repository; that does not make a lot of sense to me, but it may explain why some of the files or folders now belong to root and not to you.

As a general rule you should only ever use a file manager as root if you need to carry out specific file management operations that require root permissions, eg, copying a file to a system folder in, for example, /etc or /usr, and afterwards you should immediately close the manager; in all other cases open the file manager as user.

I think to try to sort out these problems that it is worth running the command ```
sudo chown -R kristal00:kristal00 /home/kristal00
```to make sure you are the owner of everything in your home, followed by ```
chmod -R 755 /home/kristal00
``` to ensure the files and folders have the correct permissions and not the current universal 777.
This assumes your computer username is kristal00; if not edit commands accordingly.

---

### Post by kristal00 on 2014-01-18
> **ajgreeny said:**
> Also I don't understand why you used thunar as root to change repository [...] As a general rule you should only ever use a file manager as root if you need to carry out specific file management operations that require root permissions, eg, copying a file to a system folder in, for example, /etc or /usr, and afterwards you should immediately close the manager; in all other cases open the file manager as user
I use thunar with root permission just to do that you describe, i.e. for deleting some repository that I don't need or for make some change on them, and once I finished to change the repository I close the file manager and I use it as user. I find this way more practical to do these operations.
As soon as I can, I'll executing the commands that you posted and after I'll let you know about the result.

Many thanks for the help so far proved :)

---

### Post by kristal00 on 2014-01-18
I've just executed your command and if I control the permissions of the folder .config/xfce4... now result that belong to me.
I think this is the end of the issue.


Thank you so much again :)

---

### Post by kristal00 on 2014-01-18
Argh! I declared victory too soon :confused:

Now if I try to copy a file to an external drive, like usb drive, thunar show to me this error:
```
[COLOR=#000000][FONT=Arial] Error setting extended attribute 'xdg.origin.url': Operation not supported[/FONT][/COLOR]
```
but the file seems  to be copied well.

With another file manager this doesn't happen.

Any idea?

---

### Post by ajgreeny on 2014-01-19
Looks like a bug that has already been reported in some other situations, though the copying procedure does seem to work in those as well as yours.
[https://bugs.launchpad.net/ubuntu/+source/evince/+bug/1159724](https://bugs.launchpad.net/ubuntu/+source/evince/+bug/1159724)

---

### Post by kristal00 on 2014-01-19
Ok, but before that I had executed your commands this error was not shown.

---

### Post by ajgreeny on 2014-01-19
Sorry, but I do not know anything more about that bug.  Just keep looking at the launchpad bug site I linked to, to see if any more info arrives as time goes by.

---

### Post by kristal00 on 2014-01-19
Ok I'll do as you say, at the end is not a problem.
Thanks again :)

---

