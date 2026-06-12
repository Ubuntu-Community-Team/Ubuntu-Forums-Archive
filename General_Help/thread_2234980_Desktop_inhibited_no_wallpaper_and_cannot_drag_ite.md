---
title: "Desktop inhibited: no wallpaper and cannot drag items to the desktop"
date: 2014-07-18
forum: General Help
---

### Post by jevon2 on 2014-07-18
Hello,

I clean installed Ubuntu 14.04.

I did some fiddling to get vnc access (fiddling meaning blindly trying commands from google searching) - which now works.

However, when I log in using unity or gnome-metacity, my Desktop appears to be inactive:
1) No wallpaper. I get some redish/pinkish wallpaper with the ubuntu logo and ubuntu text bottom left corner. I DO see the wallpaper on the login screen.
2) Desktop folder contents not appearing on the actual desktop. I saved a document to the desktop and couldnt' see it, but found it when browsing the Desktop folder.
3) Can't drag documents/folders onto the desktop. When I release the mouse button the item bounces back to the source location.

I made some blind attempts at reinstalling the ubuntu-desktop, but no luck. 

The only other thing is if I switch to gnome-classic I will see the wallpaper, but the Desktop remains "inactive". 

Unity launch bar works; in gnome I can add icons to the top panel launcher; switch workspaces, etc. Eveything else appears OK. Just the actual desktop area appears dead.

Any ideas?

Thanks,
Jevon

---

### Post by grahammechanical on 2014-07-18
What I think you are seeing is normal behaviour for Ubuntu Unity 14.04. You seem to be describing the default background wallpaper. It is there at the login screen and there at the desktop after we login. We need to change desktop backgrounds in System Settings>Appearance to see something different. Have you set a different background wallpaper. You do not say so.

I have just created a new document on the desktop by right clicking the desktop and selecting New Document>Empty Document. And I got an empty document icon on the desktop. I then opened it with Gedit, typed some text and saved the document in Desktop. And there it is sitting on the desktop. What happens when I reboot I do not know. But there you go.

By design ubuntu is not meant to have documents and folders on the desktop. We have the Dash>Recent filter and the Dash Files scope for revealing previously opened documents and folders.

We do not install gnome-classic in Ubuntu Unity 14.04. We install gnome-session-flashback. Search the software centre for "gnome flashback." Gnome classic is a Gnome 3 shell extension. It is best used, in my opinion, with Gnome 3 shell. In Ubuntu Unity 14.04 with gnome-session-flashback installed we get two additional login options - Gnome Flashback (Compiz) and Gnome Flashback (Metacity)

Are you using Ubuntu Gnome? Then you do not have Unity. You have Gnome shell. Do not blindly attempt to do anything in Linux. We have the power to break things. Personally, I do not believe in alternative desktop environments. It messes things up. There will be conflicts with configuration files such as background settings.
 
If I want the look of Xubuntu, I install Xubuntu. Likewise with Ubuntu Gnome and the other flavours. And I have done this. Hard disks are large and all it needs is 15 - 20 GB partition sizes. It keeps things simple. My personal opinion.

Regards.

Edit: I have been experimenting with my 14.04 Unity, flaskback (compiz) and flashback (metacity) sessions. I have found that there is consistency between the sessions as regards background wallpapers. And in flashback (Metacity) I was able to drag the Calculator from the drop down menu to the desktop and a working Calculator icon appeared on the desktop. And it remains both on the desktop and working when I switched back into the Ubuntu (Unity) session.

I am not about to install Gnome Classic as that brings in Gnome 3 shell. And the last time I installed gnome-session-flashback on Ubuntu Gnome the sessions were broken. I like to keep things simple. Found that out from experience.

---

### Post by jevon2 on 2014-07-20
Thanks for your reply.

I installed Ubuntu 14.04 (default). I started with Unity. I changed the desktop wallpaper with success (one of the shipped wallpapers). The desktop behaved itself. I then went looking for a simpler desktop environment. Maybe that was my mistake.

After fiddling (my bad) things went pair shaped. I no longer see that wallpaper on my desktop. I DO see it when I'm at the login screen however.

My desktop area is totally inactive. I can't create a document directly on the desktop (by right-clicking) as in your example. I can't drag any items to the desktop.
Interestingly, the items that are in the Desktop folder don't show on the desktop.

My guess is that during my blind fiddling I did break something. Amongst other things I installed gnome-session-fallback to get gnome-metacity (what I'm using now).

My next question then: is there a way I could reset the desktop? I tried reinstalling gnome-session-fallback and compiz. Maybe there is some data I can clear?

Thanks,
Jevon

---

### Post by grumblebum2 on 2014-07-21
Is nautilus still drawing the desktop?
Terminal....
```
gsettings get org.gnome.desktop.background show-desktop-icons
```

Have you installed any other file browsers that may be interfering with nautilus drawing of the desktop?

---

### Post by jevon2 on 2014-07-21
> gsettings get org.gnome.desktop.background show-desktop-icons
false

I assume that's bad.

It's possible I installed another file browser without realising. I don't understand the ubuntu components very well, and could have copy+paste something I shouldn't have.

What's the next step?

Thanks,
Jevon

---

### Post by grumblebum2 on 2014-07-21
In the terminal run...
```
gsettings set org.gnome.desktop.background show-desktop-icons true
```

Can you now right click on the desktop?

---

### Post by jevon2 on 2014-07-21
And ... it's back!!!

Desktop wallpaper: YES
Icons for contents in Desktop folder: YES
Interactive desktop area: YES

Thank-you! :-)

Jevon

---

### Post by grumblebum2 on 2014-07-21
OK Good.
Be careful with what commands you run and instructions you follow.
Ubuntu is fairly stable but is also easy to mess up when you try to customize not really understanding what you are doing.
If unsure always use these forums for up to date advice.
What worked a few months ago may not apply now.

You may want to read about Desktop Environments.
This is a fairly basic explanation.
[http://www.howtogeek.com/163154/linux-users-have-a-choice-8-linux-desktop-environments/](http://www.howtogeek.com/163154/linux-users-have-a-choice-8-linux-desktop-environments/)

---

### Post by jevon2 on 2014-07-21
Thanks.

---

