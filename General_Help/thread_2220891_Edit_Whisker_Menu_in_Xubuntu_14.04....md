---
title: "Edit Whisker Menu in Xubuntu 14.04...?"
date: 2014-04-29
forum: General Help
---

### Post by RallyDarkstrike on 2014-04-29
Hi all, I've tried using MenuLibre to alter the Whisker (and normal) Applications Menus in Xubuntu 14.04, however, none of my changes are showing up...it's as if there are two separate menu files...the one I am editing in MenuLibre, and the one that is displayed. Is there a way to fix this?

Cheers and thanks for any help!!!

---

### Post by taytaybongsong on 2014-04-30
I also use Xubuntu. Whisker menu generally follows the order that the standard XFCE applications menu does. The only exception to this is the favorites section in whisker menu, which can be arranged by drag and drop.

---

### Post by RallyDarkstrike on 2014-04-30
Thanks for the info taytaybongsong, but that doesn't really answer my question. I edited the panel to use the Application Menu, not Whisker, and I still have the same issue now...I can edit the menu in MenuLibre, but none of the changes appear to take? How can I edit the IN-USE menu in MenuLibre...?

[COLOR=#ff0000]EDIT - Ok, I've played around a bit with MenuLibre...it turns out that SOME of the things that I change DO take effect in the Menu. For example, I hid the 'Terminal' link near the 'Log Out' link and that DID disappear and stay hidden. However, for example, under the 'System' menu tree, the only thing I see is 'Task Manager' even though 'Shared Folders,' 'Time and Date' and a host of others are supposedly set to NOT be hidden...what is going on here...???[/COLOR]

---

### Post by taytaybongsong on 2014-04-30
Oh, I didn't notice your problem was with MenuLibre. I've always opted not to use any graphical menu editors because I've found them very buggy. On 13.10, Alacarte is the menu editor, and it's fine for adding new items, but editing them or attempting to remove one would always cause problems for me. On 14.04 it's MenuLibre, and that one is even worse (after any operation it prompts you to save your changes, and I found that after doing so, the menu would no longer remain alphabetized, and items I did not add at all would show up in places I did not want them to). So, I've learned to simply leave applications like Alacarte and MenuLibre alone, and if I need to manually add an item to the menu, I create a .desktop file for it in ~/.local/share/applications using a text editor. If I need to edit an item that I didn't add myself, I just find it in /usr/share/applications and make the desired changes to the launcher / .desktop file in a text editor as well. This way, my menus stay alphabetized, and if I need to move items from one category to another, I just edit the launcher / .desktop file itself. I find that applications like Alacarte and MenuLibre are extremely unpredictable, and at-least in the case of MenuLibre, mess with the global or system default menu settings (like xfce-applications.menu). I guess my advice is to do what I do and edit your launchers textually. Here's some decent info for that: [https://wiki.xfce.org/howto/customize-menu](https://wiki.xfce.org/howto/customize-menu)

---

### Post by RallyDarkstrike on 2014-04-30
Thanks! :)

I don't mind manually editing them at all...I basically just want to hide all the stuff I don't care about that is visible by default and UNHIDE the  hidden-by-default stuff that I use! ;)

---

### Post by taytaybongsong on 2014-04-30
No problemo. Check individual launchers / .desktop files in the locations I mentioned for parameters like "OnlyShowIn" and "NoDisplay" to hide or un-hide applications. If those don't make the menu obey your desires, also check for "Include" or "Exclude" tags surrounding the application you would like displayed or hidden, in ~/.config/menus/xfce-applications.menu, and the fallback one at /etc/xdg/menus/xfce-applications.menu (the last one you will have to edit as root). With the .menu files, be a lot more careful than you would with .desktop files. Editing the .menu files is absolutely a last resort, especially the the one in xdg.

---

### Post by RallyDarkstrike on 2014-04-30
Well....after unhiding an item in MenuLibre, I see what you mean....my entire menu is now invisible... 9_9

I click the Menu button to view my Applications Menu and all I get is a little white spec, despite the fact if I look at the .menu file or back in MenuLibre, everything is still listed there....is there a command to rebuild the Applications Menu to a default so I can fix this mess?

I wish the XFCE menu was more user-friendly for making changes...a lot of folks harp on Window$, but I have to say, the Start Menu in Win7 on my desktop is SO much easier to change :(

---

### Post by taytaybongsong on 2014-04-30
> **RallyDarkstrike said:**
> Well....after unhiding an item in MenuLibre, I see what you mean....my entire menu is now invisible... 9_9
I click the Menu button to view my Applications Menu and all I get is a little white spec, despite the fact if I look at the .menu file or back in MenuLibre, everything is still listed there....is there a command to rebuild the Applications Menu to a default so I can fix this mess?
Wow. If I remember correctly, you can delete  /home/YOUR_USER_NAME/.config/menus/xfce-applications.menu and it should be regenerated after logging out and logging in, then  things *should* look significantly more in order and you can make adjustments from there. I'd definitely make a  backup of that file just in-case anything goes wrong though.

Alternatively, if that doesn't work, restore the xfce-applications.menu you just made a backup of, log out and log back in, then you could zip up the following directories;
/home/YOUR_USER_NAME/.local/share/applications
/home/YOUR_USER_NAME/.config/menus
/usr/share/applications
/etc/xdg/menus
and  upload that to a file host of your choosing, then private message me a  link to the zip file, and I could look through them and see what the issue  is.

Definitely try the first option before that though.

P.S. You'd have to tell me what applications you are looking to hide and unhide if it comes down to the second option.
P.P.S. I agree. The available applications for editing the XFCE menu cause far more problems than they solve. Then again, I find XFCE to otherwise be the most sane and usable Desktop Environment.

---

### Post by RallyDarkstrike on 2014-04-30
I agree, XFCE is my preference as well, although I have 2 VMs with Mint 16 MATE and Mint 16 Cinnamon and they are both ok...I don't mind MATE at all. Can't STAND Unity whatsoever. I've used Puppy Linux in the past as well, and although it's also a bit clunky, ROX isn't too bad....Puppy had a no-fuss editor for editing it's Menu entries that always worked fine for me. I've even toyed around with MacPup running E17 on occasion and that wasn't too bad! :)

However, the machine I'm talking about in this thread is my spare desktop PC (my main desktop PC runs Windows 7) and my netbook runs Linux Mint 14 XFCE, so I've used XFCE on that for awhile now. I found a way to (relatively) easily edit the menus on Mint 14, but it was so long ago I can't remember how now, sadly :(

Think I'll not bother with editing the Menu for now...I've found a way to get to the settings/options, etc. for all of the things I usually use. However, I've run into another non-XFCE Menu-related problem now....I prefer Nautilus as my primary File Manager, however, if I try launching it on Xubuntu 14.04 (it came preinstalled?) I just get a warning message and the 'File Manager' file manager opens instead:

(nautilus:2945): Gtk-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

Any thoughts on that one? :) Thanks for being so kind in helping me, by the way! I appreciate it!

---

### Post by taytaybongsong on 2014-04-30
No problem again. I unfortunately can't really help you with the nautilus issue though, 'cause thunar is my preferred file manager and I've never attempted to have two coexist, or to use any other file manager than that under XFCE. Maybe check out preferences in your mime type editor and preferred applications though, and possibly reinstall nautilus. Not sure.

---

### Post by RallyDarkstrike on 2014-04-30
No worries, Thunar is my second choice anyway, but I dislike the way I can't seem to get it to remember view settings for individual folders (for example, Icon mode in a folder of photos and List mode everywhere else). I'll look into it! :)

---

### Post by a-you on 2014-07-17
This doesn't exactly answer your question about how to get nautilus working but maybe it's even better: I installed nemo and it's everything nautilus used to be and more. It's working fine for me. Just installed it with synaptic and I assume the installation process took care of all configuration needed to make it the default.

Re your menu issues: that's what led me to this thread; I'm trying to deal with this menu editing too. Frankly it's kinda screwed up imho. Alacarte is slow and lacks basic features while menulibre just crashes and fails to make the changes I try to make. Re your little white dot where the menu used to be problem: no doubt you've long ago figure this out but logging out/in fixes that for me. I don't know what causes it but it has occured a few times while I've been trying to edit the "Applications Menu".

---

### Post by Kirkx on 2014-07-17
Have you tried the latest Alacarte (v3.10.0-1ubuntu2)? I've run into problems with MenuLibre just two days ago and switching to Alacarte has resolved all the issues, like creating, renaming, sorting items and adding/removing them in the "top level" section. Here is the release log from 2014-Apr-10:

[http://i.imgur.com/61oaHmM.png](http://i.imgur.com/61oaHmM.png)

------------------------
Xubuntu 14.04 amd64

---

### Post by a-you on 2014-07-18
To Kirkx: thanks for the tip about the new alacarte.

---

