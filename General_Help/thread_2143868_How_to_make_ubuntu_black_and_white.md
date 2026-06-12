---
title: "How to make ubuntu black and white?"
date: 2013-05-10
forum: General Help
---

### Post by Chelidze on 2013-05-10
This might be a somewhat strange question.

I had an argument with a windows person and I told him that linux is so much more customization then he told me to prove it and I told him .....
Now I need to make ubuntu black and white :D to prove linux is better 

I want to make ubuntus menus icons, folder icons etc... except the running apps black and white 

something like this ??

[IMG]http://i.imgur.com/rQanqVsl.jpg[/IMG]


[http://i.imgur.com/rQanqVs.jpg](http://i.imgur.com/rQanqVs.jpg)

And stock icons.

So can any one point me in a direction I need to go 


Thank you in advanced

---

### Post by zombifier25 on 2013-05-10
Sounds like you bit off more than you can chew there :P

First, install the packages "compizconfig-settings-manager" and "compiz-plugins-extra". Use this command:
```
sudo apt-get install  compiz-plugins-extra compizconfig-settings-manager
```
Then open the program ccsm (CompizConfig Settings Manager). It contains a plugin called "Opacity, Brightness and Saturation" which controls the opacity, brightness and saturation of windows.

[size=1]However, after experimenting for a while, it appears that this plugin cannot be applied to the Unity launcher and panel, since probably it's composited differently than the rest of the desktop (this problem also affects the zoom plugin). It means that this plugin can make any part of your screen (desktop background, windows, etc. etc.) black and white BUT the launcher and panel. So, unless someone knows something that I don't, what you're asking for is impossible.[/size]

If you are still curious as to how to make a window black and white, then: In ccsm, enable the plugin "Opacity, Brightness and Saturation". Wait a while for Compiz to sort itself out, then open it, go to the "Saturation" tab. On the **second** "Increase Saturation" entry, click it, choose "Ctrl", "Alt", and "Button4". Same for the **second** "Decrease Saturation" entry, but "Button5" instead of "Button4".

Now, hover your mouse on any windows, hold Ctrl + Alt and scroll down with the middle mouse button to make your window go black and white! To make it colorful again, Ctrl + Alt + Scroll up. This might be enough to amaze your friend.

---

### Post by Chelidze on 2013-05-10
> **zombifier25 said:**
> Sounds like you bit off more than you can chew there :P

First, install the packages "compizconfig-settings-manager" and "compiz-plugins-extra". Use this command:
```
sudo apt-get install  compiz-plugins-extra compizconfig-settings-manager
```
Then open the program ccsm (CompizConfig Settings Manager). It contains a plugin called "Opacity, Brightness and Saturation" which controls the opacity, brightness and saturation of windows.

[SIZE=1]However, after experimenting for a while, it appears that this plugin cannot be applied to the Unity launcher and panel, since probably it's composited differently than the rest of the desktop (this problem also affects the zoom plugin). It means that this plugin can make any part of your screen (desktop background, windows, etc. etc.) black and white BUT the launcher and panel. So, unless someone knows something that I don't, what you're asking for is impossible.[/SIZE]

If you are still curious as to how to make a window black and white, then: In ccsm, enable the plugin "Opacity, Brightness and Saturation". Wait a while for Compiz to sort itself out, then open it, go to the "Saturation" tab. On the **second** "Increase Saturation" entry, click it, choose "Ctrl", "Alt", and "Button4". Same for the **second** "Decrease Saturation" entry, but "Button5" instead of "Button4".

Now, hover your mouse on any windows, hold Ctrl + Alt and scroll down with the middle mouse button to make your window go black and white! To make it colorful again, Ctrl + Alt + Scroll up. This might be enough to amaze your friend.


Thank you so much for the reply and for such a detailed explanation 

If you do not mind I will reserve your solution because from my experience with compiz I can only associate it with plague breaks every thing 

what will happen if I batch convert

```
/usr/share/icons
```

will that work ??

---

### Post by arsenic23 on 2013-05-10
You might be better off going to gnome-look.org and downloading a black and white icon theme.  Then you can start picking at what isn't black and white one piece at a time.
Also you can totally do this in Windows as well with the correct software installed.

---

### Post by Chelidze on 2013-05-10
> **arsenic23 said:**
> You might be better off going to gnome-look.org and downloading a black and white icon theme.  Then you can start picking at what isn't black and white one piece at a time.
Also you can totally do this in Windows as well with the correct software installed.

 I tried installing icon pack did not worked too good for me first the icons it has is not to my liking and more then half of the software icons where missing 

I managed to convert an icon to black and white maybe if I do it to all the icons it will work :D
 god I am f!@#$%

[IMG]http://i.imgur.com/VqhqJOOl.png[/IMG]

[http://i.imgur.com/VqhqJOO.png](http://i.imgur.com/VqhqJOO.png)

---

### Post by whatthefunk on 2013-05-10
Icons:
[http://gnome-look.org/content/show.php/ALLGREY?content=76814](http://gnome-look.org/content/show.php/ALLGREY?content=76814)
[http://gnome-look.org/content/show.php/uniwhite-icons?content=147855](http://gnome-look.org/content/show.php/uniwhite-icons?content=147855)
[http://gnome-look.org/content/show.php/LaGaDesk-BlackWhite-III?content=124185](http://gnome-look.org/content/show.php/LaGaDesk-BlackWhite-III?content=124185)
[http://gnome-look.org/content/show.php/Faenza-Black?content=143852](http://gnome-look.org/content/show.php/Faenza-Black?content=143852)

Etc....

On a side note, trying to prove Linux customization ability with Unity is, well, kind of weird.  Unity is the least customizable interface Ive ever used.  You should give KDE a whirl.  You could greyscale it in a few minutes without installing all this ridiculous compiz plugin nonsense.

---

### Post by arsenic23 on 2013-05-10
You should more then likely look at a quick tutorial on packing icon themes (it's pretty easy - I maintain a patchy little one myself), then copy the theme you are using, convert the copy to black and white, rename and repack it.

---

### Post by whatthefunk on 2013-05-10
Another idea for icons:
[http://pobtott.deviantart.com/art/Any-Color-You-Like-175624910](http://pobtott.deviantart.com/art/Any-Color-You-Like-175624910)

---

### Post by Chelidze on 2013-05-10
> **whatthefunk said:**
> Icons:
[http://gnome-look.org/content/show.php/ALLGREY?content=76814](http://gnome-look.org/content/show.php/ALLGREY?content=76814)
[http://gnome-look.org/content/show.php/uniwhite-icons?content=147855](http://gnome-look.org/content/show.php/uniwhite-icons?content=147855)
[http://gnome-look.org/content/show.php/LaGaDesk-BlackWhite-III?content=124185](http://gnome-look.org/content/show.php/LaGaDesk-BlackWhite-III?content=124185)
[http://gnome-look.org/content/show.php/Faenza-Black?content=143852](http://gnome-look.org/content/show.php/Faenza-Black?content=143852)

Etc....

On a side note, trying to prove Linux customization ability with Unity is, well, kind of weird.  Unity is the least customizable interface Ive ever used.  You should give KDE a whirl.  You could greyscale it in a few minutes without installing all this ridiculous compiz plugin nonsense.
Thank you for the reply can you tell me how to make the screen black and white in kde ????


> **arsenic23 said:**
> You should more then likely look at a quick tutorial on packing icon themes (it's pretty easy - I maintain a patchy little one myself), then copy the theme you are using, convert the copy to black and white, rename and repack it.

can you link that tutorial to me ??? thank you

---

### Post by arsenic23 on 2013-05-10
> can you link that tutorial to me ??? thank you
Well...  no, sorry, I can't.  I just assumed there would be one on the first page if you googled it.  There isn't.  I just downloaded themes from gnomelook, unpacked them, and looked at how they were put together.
Sorry.

---

### Post by whatthefunk on 2013-05-10
> **Chelidze said:**
> Thank you for the reply can you tell me how to make the screen black and white in kde ????

-Install a black and white icon theme.
-Install a dark color theme.
-Tweak dark theme to exclude all colors.
-Install a dark style.
-Install dark window decorations.
-Drink beer.

The only problem I forsee is incomplete icon sets.  Fortunately, KDE makes it very easy to change icons for individual programs.  This is only a matter of finding the right dark themes.

---

### Post by Chelidze on 2013-05-10
Huge thanks 

**[COLOR=#000000][whatthefunk]("http://ubuntuforums.org/member.php?u=1202558") and[/COLOR] **[**[COLOR=#000000]arsenic23[/COLOR]**]("http://ubuntuforums.org/member.php?u=96218")
[COLOR=#000000][/COLOR]
SO I am going to combine and edit the stock them and one of the them that will best work for me 


Thank you
 
you are really nice people for sticking with me :) and helping me figure out my next move :)

---

### Post by Chelidze on 2013-05-11
Here is an black and white icon pack

[http://levan27.deviantart.com/art/Ater-370973051?ga_submit_new=10%253A1368280191&ga_type=edit&ga_changes=1&ga_recent=1](http://levan27.deviantart.com/art/Ater-370973051?ga_submit_new=10%253A1368280191&ga_type=edit&ga_changes=1&ga_recent=1)

[IMG]http://i.imgur.com/STMgnYtl.jpg[/IMG]

---

