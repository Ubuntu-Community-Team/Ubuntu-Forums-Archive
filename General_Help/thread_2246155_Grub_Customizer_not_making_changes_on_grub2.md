---
title: "Grub Customizer not making changes on grub2"
date: 2014-09-28
forum: General Help
---

### Post by MetalPotatoHead on 2014-09-28
Hi, after making changes on the background and colors on Grub Customizer and saving the changes, the interface on grub2 is always the same, only the entries change.
I run the update-grub command after saving the changes, made the changes myself on "/boot/grub/grub.cfg" and nothing changed.
What could be the reason? I have ubuntu 14.04 64-bit, kernel 3.16.0-031600-generic.

Thanks.

---

### Post by Cavsfan on 2014-09-29
> **MetalPotatoHead said:**
> Hi, after making changes on the background and colors on Grub Customizer and saving the changes, the interface on grub2 is always the same, only the entries change.
I run the update-grub command after saving the changes, made the changes myself on "/boot/grub/grub.cfg" and nothing changed.
What could be the reason? I have ubuntu 14.04 64-bit, kernel 3.16.0-031600-generic.

Thanks.

It's my understanding that **/boot/grub/grub.cfg** cannot be edited as it is overwritten with update-grub command. 
You might give the custom grub wiki in my signature a go. It's pretty simple once you get a handle on it.

You can have a background and 3 different font colors: one outside the menu, one for the box and menu and one for the highlighted line in the menu.

This is my current menu on Mint 17:

[[IMG]http://www.zimagez.com/miniature/customgrub.jpg[/IMG]]("http://www.zimagez.com/zimage/customgrub.php")

---

### Post by Elfy on 2014-09-29
> It's my understanding that /boot/grub/grub.cfg cannot be edited as it is overwritten with update-grub command. You can edit it - the issue being you need to do so again and again ... :)

---

### Post by Cavsfan on 2014-09-29
> **Elfy said:**
> You can edit it - the issue being you need to do so again and again ... :)

LoL! I'm pretty sure you'd be wasting your time because the changes would never "stick". For that to happen you have to enter the update-grub command which replaces that file. :p

Like my 16 year old cat chasing his tale lol. You'd think he'd have learned by now that that thing is attached! :lol:

EDIT: BTW the op is talking about 14.04 so you might want to move this thread.

---

### Post by Elfy on 2014-09-29
I know - that is my point ;)

---

### Post by Elfy on 2014-09-29
*Thread moved to **General Help**.*

---

### Post by Cavsfan on 2014-09-29
> **Elfy said:**
> I know - that is my point ;)

Yeah that is why I was :lol: :lol: :lol: :lol: Loling. I figured I had better explain it though as not everyone knows that.

The OP said he was editing that file. Life is a learning experience.

---

### Post by nerdtron on 2014-09-29
> **MetalPotatoHead said:**
> Hi, after making changes on the background and colors on Grub Customizer and saving the changes, the interface on grub2 is always the same, only the entries change.
I run the update-grub command after saving the changes, made the changes myself on "/boot/grub/grub.cfg" and nothing changed.
What could be the reason? I have ubuntu 14.04 64-bit, kernel 3.16.0-031600-generic.

Thanks.

hhhmmm.. Just passing by...
Are you not dual booting with another Linux distro? Is grub currently controlled by Ubuntu?

And isn't the grub config now in /etc/grub.conf ?

---

### Post by MetalPotatoHead on 2014-09-29
Nope, I have only Ubuntu 14.04 and Windows 8.1

---

### Post by MetalPotatoHead on 2014-09-29
@Cavsfan I tried your way to change grub and didn't work
I followed the steps and the only things that changed were the font size and the number of entries. The background, the color of entries and the timeout (stopped working a while ago) didn't changed.

---

### Post by CantankRus on 2014-09-30
See [HERE]("https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen")

Relevant section of that page for font color...
> 
_Editing /etc/grub.d/05_debian_theme_

Only 2 lines for the font colors need to be added. 
Enter gksudo gedit /etc/grub.d/05_debian_theme 
For Ubuntu Precise Pangolin 12.04 using Grub version 1.99: 
At line 98 where you see the 1st line below add the two lines after that and save the file: 
**For Trusty Tahr 14.04** using Grub version 2.00: 
At line 118 where you see the 1st line below add only the two lines after that and save the file: 

Make sure you leave the one space before set in the 2 lines. 


echo "if background_image `make_system_path_relative_to_its_root "${1}"`; then"
echo " set color_normal=cyan/black"
echo " set color_highlight=light-cyan/black"
if [ -n "${2}" ]; then
eg my **/etc/grub.d/05_debian_theme** starting at line #117
[COLOR="#FF8C00"]Inserted lines[/COLOR].
```
echo "if background_image `make_system_path_relative_to_its_root "${1}"`; then"
        [COLOR="#FF8C00"]echo " set color_normal=cyan/black"
	echo " set color_highlight=yellow/black"[/COLOR]
	if [ -n "${2}" ]; then
```

After editing, run
```
sudo update-grub
```

---

### Post by Cavsfan on 2014-09-30
> **MetalPotatoHead said:**
> @Cavsfan I tried your way to change grub and didn't work
I followed the steps and the only things that changed were the font size and the number of entries. The background, the color of entries and the timeout (stopped working a while ago) didn't changed.

You must enter **sudo update-grub **for the changes to be made permanent. And you *must* run this command after you make *any* changes to grub.

Especially when you make changes to **/etc/default/grub** (default line, timeout, resolution and font) or any other changes.

To see what the effects of **update-grub** look like you can enter  **sudo grub-mkconfig > grub-text** - this will put a text file called grub-text in your home directory and you can view what is going on. And the text file name can be anything you want it doesn't have to be grub-text.

Did you put a picture the same size resolution as your monitor in **/boot/grub/** with this command **sudo cp picture-name /boot/grub/** ?
Not all pictures work for some reason. Sometimes you have to either edit it with gimp or try another picture. 

And did you put these 2 or 3 lines (red) in **/etc/grub.d/05_debian_theme** after line 117 (the top line is 117)

```
        echo "if background_image `make_system_path_relative_to_its_root "${1}"`; then"
	[COLOR="#FF0000"]echo " set menu_color_normal=white/black"
	echo " set menu_color_highlight=red/black"
        echo " set color_normal=cyan/black"[/COLOR]
```

This will make cyan the top and bottom color and the menu will be white with the highlighted line red like this:

[[img]http://www.zimagez.com/miniature/20140522151808.jpg[/img]](http://www.zimagez.com/zimage/20140522151808.php)

```
	echo "if background_image `make_system_path_relative_to_its_root "${1}"`; then"
	[COLOR="#FF0000"]echo " set color_highlight=light-cyan/black"
        echo " set color_normal=cyan/black"[/COLOR]
```

This will make cyan the normal color and light-cyan will be the highlight color  like this:

[[img]http://www.zimagez.com/miniature/20140501grub2.jpg[/img]](http://www.zimagez.com/zimage/20140501grub2.php)

Then **sudo update-grub**:

```
cavsfan@cavsfan-MS-7529:~$ sudo update-grub
[sudo] password for cavsfan: 
Generating grub configuration file ...
Found background image: road-to-know-where-1920_1200.jpg
Adding Precise Pangolin 12.04, Trusty Tahr 14.04, Utopic Unicorn 14.10, Utopic Unicorn 14.10 Mate, Mint 13 Nadia, Mint 17 Quina and Windows 7
done
```

The fact that there is a picture in **/boot/grub/** makes it use the font colors. But the fact that the picture displays as being found does not always mean the picture works.
As I said sometimes you have to try more than one picture.

---

### Post by Cavsfan on 2014-09-30
> **CantankRus said:**
> See [HERE]("https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen")

Relevant section of that page for font color...

eg my **/etc/grub.d/05_debian_theme** starting at line #117
[COLOR=#FF8C00]Inserted lines[/COLOR].
```
echo "if background_image `make_system_path_relative_to_its_root "${1}"`; then"
        [COLOR=#FF8C00]echo " set color_normal=cyan/black"
    echo " set color_highlight=yellow/black"[/COLOR]
    if [ -n "${2}" ]; then
```

After editing, run
```
sudo update-grub
```

I need to update that wiki. I posted in the last post or so of that thread that you could have 3 colors instead of just two.

Here is my Utopic Unicorn 14.10 grub after today's update to grub:
```
cavsfan@cavsfan-MS-7529:~$ apt-cache policy grub-pc
grub-pc:
  Installed: 2.02~beta2-14
  Candidate: 2.02~beta2-14
  Version table:
 *** 2.02~beta2-14 0
        500 http://us.archive.ubuntu.com/ubuntu/ utopic/main amd64 Packages
        100 /var/lib/dpkg/status
```


[[IMG]http://en.zimagez.com/miniature/20140930113614.jpg[/IMG]]("http://en.zimagez.com/zimage/20140930113614.php")

---

### Post by Cavsfan on 2014-09-30
> **CantankRus said:**
> See [HERE]("https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen")

Good deal that seems to be from the link in my signature. :p

---

### Post by Cavsfan on 2014-09-30
I had to try 3 pictures before I got this one to work. 
So, like I said the picture may say found in the output of update-grub command but that doesn't mean it will show up at boot time.
My grub on Mint 13:

[[IMG]http://en.zimagez.com/miniature/20140930171821.jpg[/IMG]]("http://en.zimagez.com/zimage/20140930171821.php")

---

### Post by DVD-R on 2014-10-02
Have you checked out this link?

[http://www.thegeekstuff.com/2012/10/grub-splash-image/](http://www.thegeekstuff.com/2012/10/grub-splash-image/)

---

### Post by Cavsfan on 2014-10-02
> **DVD-R said:**
> Have you checked out this link?

[http://www.thegeekstuff.com/2012/10/grub-splash-image/](http://www.thegeekstuff.com/2012/10/grub-splash-image/)

Why go with 2 colors when you can have 3? :p

This may well be my most gorgeous grub screen ever. The top and bottom color is magenta, the menu color is yellow and the highlighted menu color is red.
This picture doesn't really do the actual screen justice but it's not bad. ;)

[[IMG]http://en.zimagez.com/miniature/20141001122252.jpg[/IMG]]("http://en.zimagez.com/zimage/20141001122252.php")

---

