---
title: "[SOLVED] Please help me remove the Opera tray icon in Xubu!"
date: 2008-06-28
forum: General Help
---

### Post by shebuwa on 2008-06-28
I use Xubuntu, with Xfce instead of gnome or kde. So I can't select properties, on the Opera tray icon, to add the known fix for this "issue".

How then do I remove the Opera system tray icon in Xubuntu?

How do I also STOP Opera from loading at boot-up?

What was the Opera devel team thinking? :mad:

---

### Post by dizee on 2008-06-28
```
opera -notrayicon
``` works for me.

as for opera loading on login, try closing all programs and then when you logout make sure the box "Save session for future logins" is ticked.

that might solve it.

edit - haven't figured out a way to get the no tray icon from the menu entry, but it should work if you use an application launcher with that command.

---

### Post by shebuwa on 2008-06-28
Thanks dizee. I will give that a try.

---

### Post by shebuwa on 2008-06-28
Dizze! ):P

Closing all programs, then ticking 'save session for future logins' at logout, worked great. Thanks so much! :)

Of course the tray icon still returns at Opera startup. I can just close it as usual though.



Thanks again Dizze. That's a good temporary fix. I don't think I should mark this thread solved quite yet though.

---

### Post by Elfy on 2008-06-29
You just need to edit the launcher - I'm not sure how to do so in Xubuntu, but try right clicking the launcher you use and adding -notrayicon to the end of the command it will stop it.

I am not sure how the menu works in Xubuntu - look for something which says 'Edit menu' or similar - gnome you right click the menu and get an option to edit menus - see if it's the same.

---

### Post by shebuwa on 2008-06-29
Thanks for trying forestpixie. :) Like I said, in the OP, I have already tried that. I bet you were just giving me a bump though. Thanks hon. :D

I haven't found out how to edit 'icon launch commands'(?) in Xubuntu, I guess that is how you say it, by searching on Google either. 

That is why I am asking here.

---

### Post by Elfy on 2008-06-29
It appears that editing the menu in xubuntu is not as easy as ubuntu - you need to edit files apparently.

[http://ubuntuforums.org/showpost.php?p=1409812&postcount=8](http://ubuntuforums.org/showpost.php?p=1409812&postcount=8)

This suggests to me that if you navigate to /usr/share/applications/ you should find a opera.desktop file - this needs to be edited it seems

Find the line that looks like

> Exec=cream %F

except you're looking for opera, then add the -notrayicon to the end

> Exec=cream %F [COLOR="Red"]-notrayicon[/COLOR]


So if the file actually was called opera.desktop you would need to run this to edit it.

```
gksudo mousepad /usr/share/applications/opera.desktop
```




Try that - it can only not work I'd imagine, if you want to backup the file prior to editing

```
sudo cp /whole/path/tofile /whole/path/tofile.bak
```

to replace edited file with backed up one

```
sudo mv /whole/path/tofile.bak /whole/path/tofile
```

---

### Post by shebuwa on 2008-06-29
Thanks forestpixie. I don't feel comfy trying that right now though. :D

---

### Post by Elfy on 2008-06-30
No neither would I if I'd only just begun :)

Still - you know what the answer is now anyway

Good luck.

---

### Post by Elfy on 2008-06-30
Yea - that works without a doubt - I installed xubuntu in a virtual machine and edited the fiel - opened opera and no tray icon appeared.

---

### Post by shebuwa on 2008-07-02
It worked! Thanks forestpixie. :) 

**It was so nice of you to go to all that trouble!** 

You are now officially my hero. =D>

---

### Post by Elfy on 2008-07-02
Welcome - glad you're sorted :)

> It was so nice of you to go to all that trouble!I learnt as well with that.

---

### Post by shebuwa on 2008-07-02
Thanks again forestpixie. 

I am beginning to get a feel for Xubuntu with Xfce desktop. I have, so far, managed to get GKrellM for i8k fan control, up and running smoothly, on my old Dell Latitude C610, and I also downloaded and installed the Slickness-black desktop and XUbuntuStudio icon themes, just the other day. 

I have the SunJava package supporting Opera 9.50 with Adobe Flash operating perfectly, and as well I have Totem Movie Player 2.22.1 with Xine, which works just great for DVD playback. I also have VLC for streaming video, but I have yet to test it out. I first must figure out how to get Totem Xine to auto-play my DVDs. It works great when I select the DVD from the menu though. It is very smooth, offering good features, all with a small gnome footprint. 

System Monitor, shows that memory usage stays below 32% on average, leaving me with 503.4 mb ram, which should well cover my future needs for quite a while. 

This laptop is now both quick and stable on Xubuntu, having all the extras I ever needed on XP professional. This OS, not only looks terrific visually now, it operates with far more stability and security than windoze XP ever could. No more defragging the hard drive, and no more viruses or spyware to fret about and buy security software for. 

These things alone, have made my beginning, Linux journey, very well worth it. I even have, over 30 Gigs of HD left, to populate with carefully chosen programs and files. All of this at no cost, other than the joy of taking a little personal responsibility and learning, along with the satisfying prospect of soon becoming able to help others like myself. Such bargains are rare indeed!

I am just going to take my time, by continuing to read and study about Linux Ubuntu, so I can make full use of this fabulous operating system.

It is all because of wonderful people, like you forestpixie, and that super smart guy here, who maintains the [**Tips for beginners with Ubuntu 8.04**]("http://ubuntutip.googlepages.com/home") webpage, and a few others here whom I just can't remember right now.

**[SIZE="4"]Thanks to all of you![/SIZE]** 

I so admire the open source non commercial philosophy behind Ubuntu, and hopefully, someday, I may even become knowledgeable enough to contribute.


with gratitude


Lynn

---

### Post by Elfy on 2008-07-02
Nice - carry on with the good work and enjoy it

---

