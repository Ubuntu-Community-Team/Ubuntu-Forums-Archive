---
title: "Highlighted text icons on desktop"
date: 2013-05-24
forum: General Help
---

### Post by dxtr12 on 2013-05-24
Hello everybody
after installing a mac theme from [here]("http://www.noobslab.com/2013/05/mac-os-x-theme-for-ubuntu-1304-raring.html") , the icon's name on desktop are always highlighted :

[IMG]http://img15.hostingpics.net/pics/366110prlm.png[/IMG]

can you please help me fix it

---

### Post by Dennis N on 2013-05-24
To fix this, create a text file named **.gtkrc-2.0** in your home folder with the following contents. Note the period at the beginning of the name (which makes it a hidden file). You can copy and paste the following:

```
style "xfdesktop-icon-view" { 
XfdesktopIconView::label-alpha = 0 

fg[NORMAL] = "#ffffff" 
fg[SELECTED] = "#ffffff" 
fg[ACTIVE] = "#ffffff" 
} 


widget_class "*XfdesktopIconView*" style "xfdesktop-icon-view"

```

Now the icon text should have a transparent background.

---

### Post by dxtr12 on 2013-05-24
> **Dennis N said:**
> To fix this, create a text file named **.gtkrc-2.0** in your home folder with the following contents. Note the period at the beginning of the name (which makes it a hidden file). You can copy and paste the following:

```
style "xfdesktop-icon-view" { 
XfdesktopIconView::label-alpha = 0 

fg[NORMAL] = "#ffffff" 
fg[SELECTED] = "#ffffff" 
fg[ACTIVE] = "#ffffff" 
} 


widget_class "*XfdesktopIconView*" style "xfdesktop-icon-view"

```

Now the icon text should have a transparent background.

hey thnx for your reply
i did what you said but it didn't work : here is the set of command i did
touch **/home/.gtkrc-2.0**
mousepad [B]/home/.gtkrc-2.0
then i copied your code and save the file , but it didn't worked[/B]

---

### Post by Dennis N on 2013-05-24
You have to logout and login for the change to take effect.

---

### Post by dxtr12 on 2013-05-24
> **Dennis N said:**
> You have to logout and login for the change to take effect.

it didn't work even after i restarted it

---

### Post by Dennis N on 2013-05-24
What version of Xubuntu are you using? 
I am looking at the ppa - What is the full package name of the file you downloaded?

---

### Post by dxtr12 on 2013-05-24
> **Dennis N said:**
> What version of Xubuntu are you using? 
I am looking at the ppa - What is the full package name of the file you downloaded?
Xubuntu 13.04

---

### Post by Dennis N on 2013-05-24
@dxtr12

I suggest you test if the .gtkrc-2.0 file is working by testing with the preinstalled themes (there are only 6, under Settings Manager > Appearance > Style) and check if the icon text background is transparent. If transparent, then the file is working. When I tried a couple of the preinstalls **without** the added file, the text background was whitish as in you screenshot. Greybird (the default) was an exception. I wanted to install another  theme, Zukitwo, and it had this problem without the .gtkrc-2.0 file. It works fine with it.

If the file works with the preinstalled themes, and your theme does not change, then obviously something else is causing this in your new theme. 

I did not invent this code. I have used it in the past several releases to solve this problem. A source for this technique (there are several on the web) is:

[http://xubuntugeek.blogspot.com/2012/09/how-to-make-desktop-icons-text.html](http://xubuntugeek.blogspot.com/2012/09/how-to-make-desktop-icons-text.html)

---

### Post by vasa1 on 2013-05-24
@DennisN, this is not strictly related to the question, but Greybird has many of the settings you mention within /usr/share/themes/gtk-2.0/gtkrc (towards the end of the file). So, if one wants, the values can be tweaked there (or in the corresponding location on ~/.themes) instead of editing .gtkrc-2.0.

---

### Post by Dennis N on 2013-05-25
> **vasa1 said:**
> @DennisN, this is not strictly related to the question, but Greybird has many of the settings you mention within /usr/share/themes/gtk-2.0/gtkrc (towards the end of the file). So, if one wants, the values can be tweaked there (or in the corresponding location on ~/.themes) instead of editing .gtkrc-2.0.

I think Greybird was the only theme that had transparent desktop icon text background without using the extra .gtkrc-2.0, so I would guess the necessary code is added there to make it look good by default rather than relying on an external file. That would make sense. I will take a look when I next get on Xubuntu.

---

### Post by dxtr12 on 2013-05-25
I still have the same problem , this GTKRC file didn't do anything

---

### Post by vasa1 on 2013-05-25
> **dxtr12 said:**
> hey thnx for your reply
i did what you said but it didn't work : here is the set of command i did
touch **/home/.gtkrc-2.0**
mousepad [B]/home/.gtkrc-2.0
then i copied your code and save the file , but it didn't worked[/B]

It should be
touch /home/**xxxxx**/.gtkrc-2.0
and
mousepad /home/**xxxxx**/.gtkrc-2.0.

where **xxxx** is your username.

---

### Post by dxtr12 on 2013-05-25
> **vasa1 said:**
> It should be
touch /home/**xxxxx**/.gtkrc-2.0
and
mousepad /home/**xxxxx**/.gtkrc-2.0.

where **xxxx** is your username.

Thank you so much , it worked

---

### Post by vasa1 on 2013-05-27
> **dxtr12 said:**
> Thank you so much , it worked
You're welcome. And just remember that when people talk of your home folder they mostly mean /home/your_name and not just /home.
Plain /home will hold the home folders of each user. So, we can have
/home/user_1
/home/user_2
etc.

So even if you're just the only user, all your stuff will be in /home/dxtr12 (or whatever username you chose when installing your OS).

Also, please don't forget to mark threads **solved** when your question is answered to your satisfaction. You can look at this thread to know how to do so: [http://ubuntuforums.org/showthread.php?t=2121377](http://ubuntuforums.org/showthread.php?t=2121377)

---

### Post by Dennis N on 2013-05-27
@vasa1

Saw this thread pop up again. Good catch. I didn't see that mistake and should have.

---

### Post by vasa1 on 2013-05-28
> **Dennis N said:**
> I think Greybird was the only theme that had transparent desktop icon text background without using the extra .gtkrc-2.0, so I would guess the necessary code is added there to make it look good by default rather than relying on an external file. That would make sense. I will take a look when I next get on Xubuntu.

I got Greybird onto Lubuntu by installing shimmer-themes. Greybird is one of the themes in this package. I just checked the others. Albatross and Blackbird also have such a section in gtkrc. Bluebird doesn't seem to have such a section.

BTW, [http://git.xfce.org/xfce/xfdesktop/tree/README](http://git.xfce.org/xfce/xfdesktop/tree/README) refers to the use of ~/.gtkrc-2.0 while giving a nice explanation of most of the customization options.

---

