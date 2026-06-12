---
title: "wich soft to  reframe a photo (Gimp seems awfull)"
date: 2013-06-04
forum: General Help
---

### Post by FroggySeven on 2013-06-04
I don't know if I missed a Gimp's feature, or if Gimp is not really made to reframe a photo
(in fact, that's THE point that explain why I still use Photoshop...).

But I just would like to choose a rectangular crop AND a rotation TOGETHER and visualise it "in continue" before  reframing.

HEEEEEEEEEEEEEEEEEEEEEEEEEEEELP !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

(and thank you for it!)

---

### Post by sudodus on 2013-06-04
There might be a learning curve, but I'm happy using gimp for such tasks. However, there are linux tools that are easier to use, for example gthumb.

See the discussion is this thread

[http://ubuntuforums.org/showthread.php?t=2149987](http://ubuntuforums.org/showthread.php?t=2149987)

---

### Post by plucky on 2013-06-04
Nautilus addons **nautilus-image-converter** as well. 
```
sudo apt-get install nautilus-image-converter
```
Good Luck

---

### Post by carl4926 on 2013-06-04
All the tools are there in Gimp

---

### Post by FroggySeven on 2013-06-04
Thank you all for your help !
>  carl4926 : All the tools are there in GimpOK you can crop a rectangle, OR rotate the picture... but is there really a tool that do it **AT THE SAME TIME** as in Photoshop ??? Which one ??????



sudodus/plucky  : thank you for the idea of nautilus &  gthumb I'll see that this evening :)

---

### Post by sudodus on 2013-06-04
Do you want to edit single pictures or do you want to do batch jobs and treat many pictures in the same way?

Anyway, cropping and rotation are two separate operations, that have to be done one after another in any software package. Usually cropping is done manually (to fit the particular picture). Rotation can sometimes be done automatically (depending on the information from the camera).

If you want to do batch jobs, imagemagick convert is a good choice (if you can run terminal window commands).

---

### Post by rewyllys on 2013-06-04
> **FroggySeven said:**
> Thank you all for your help !
OK you can crop a rectangle, OR rotate the picture... but is there really a tool that do it **AT THE SAME TIME** as in Photoshop ??? Which one ??????



sudodus/plucky  : thank you for the idea of nautilus &  gthumb I'll see that this evening :)
I'd like to reverse the question: Just what is the command in Photoshop that does simultaneous cropping and rotating?  I don't recall such a command (but I haven't used Photoshop for some years; perhaps it's a recently added command).

---

### Post by FroggySeven on 2013-06-04
Thanks a lot to really try to understand my problem

rewyllys : excellent idea. When you chose the reframe tool "1",  you can  both crop AND rotate when mouse cursor have the shape "2".

[[IMG]http://img194.imageshack.us/img194/6971/exemplerecadrage.jpg[/IMG]]("http://imageshack.us/photo/my-images/194/exemplerecadrage.jpg/")
( Noisette -nut- and Tigri -Tiger+grey- :wink: )

sudodus : I agree with you when there's some obvious horizontal or vertical line in the photo.
               But sometime there's no obligation at all to chose a line, or as in my exemple, to much lines.
               In those cases, choice of rotation depends directly of  the crop (narrow crop, large crop, line near the border or not, and so  on...)

              By the way, in my far youth, I used as all photographer  two set square to chose the reframing before using the cutter
              (it is what means the shape "1"), precisely to crop and rotate at the same time.

Moreover, the choice of the rotation depends sometime of the size of surface "3" you have to "rebuilt" after a rotation. 
Small crop, small rotation else too much work to do.        Big crop allowed big rotation.         Difficult to chose  -> we have to see that together.



So, does this tool exist somewhere in gimp ?

---

### Post by sudodus on 2013-06-04
To my knowledge, no, there is no such combined tool in Gimp. There is cropping, there is rotation, there is perspective (where you can stretch or shrink pulling corners), there is mirroring. But they are separate operations to be performed one after another.

---

### Post by FroggySeven on 2013-06-05
OK. So I won't waste my time looking for it, and rather test nautilus &  gthumb !

PS:  I wasn't talking about batch...( I wonder how automatic reframing could be done ;) )

---

### Post by sudodus on 2013-06-05
The nautilus plugin &  gthumb are very simple tools with very few bells and whistles. (Nautilus is the file browser.) I think you are searching for some professional tool.

Have a look at this link (it is a bit old, but you might get good tips ...)

[http://ubuntuforums.org/showthread.php?t=1882838](http://ubuntuforums.org/showthread.php?t=1882838)

---

### Post by Rebelli0us on 2013-06-05
If your favorite app is in Windows you can still use it in a virtual machine. Just install oracle virtual box.  Also try xnviewmp, mp stands for multi-platform, works in both windows & linux.

---

### Post by FroggySeven on 2013-06-05
sudodus : I tried gthumb, and you're right, it is too simple. There is quater-rotation only :) !
               I didn't succed in using nautilus... but if you say it's the same...
               But your link is very interesting. There talking for instance of darktable... I'll try this first.

Rebellious : That is a good idea... I haven't tought about ;)  But I am fan of Ubuntu of course, and I still hope there is some soft somewhere  to do the very basic work of a photographer : reframing ( Or we'll have to program it !!! )

---

### Post by Vaphell on 2013-06-05
well, everybody whines how gimp sucks for professional work and how it will never be on par with photoshop, so it's a bit of a self fulfilling prophecy. Less exposure, fewer programmers working on it, harder to keep up with the feature creep in the industry.

---

### Post by ahallubuntu on 2013-06-05
~

---

### Post by sudodus on 2013-06-06
Some people whine, but many people are happy with gimp. I use it and I like it :KS

---

### Post by Rebelli0us on 2013-06-06
> **FroggySeven said:**
> sudodus : I tried gthumb, and you're right, it is too simple. There is quater-rotation only :) !
               I didn't succed in using nautilus... but if you say it's the same...
               But your link is very interesting. There talking for instance of darktable... I'll try this first.

Rebellious : That is a good idea... I haven't tought about ;)  But I am fan of Ubuntu of course, and I still hope there is some soft somewhere  to do the very basic work of a photographer : reframing ( Or we'll have to program it !!! )

xnview has both Linux & Windows version. VMs let you run both OSes simultaneously so you can run your favorite apps without rebooting. Xnview has a "batch conversion" tool which includes crop, resize and rotate...

---

### Post by FroggySeven on 2013-06-06
I haven't tried darktable yet... waiting for it :

About Gimp and "self fulfilling prophecy" don't think to shut the curtain and to say tchoo tchoo will allow the train to start again ;)
More seriously, it's important to be fair about what we can do with ubuntu to seduce people instead of disgusting them.
I'm not like this, cause I feel Ubuntu is much more than something free, but lots of people will tried it only once. We have only one chance to seduce them.
If today someone asks me if ubuntu is fine for photos, I will say no, to keep the possibility I'll change his mind later.

To make positiv critics : how to able this sort of reframing in Gimp (that is dumb for a programmer) ? How to ask for it ? Can I help ?

ahallubuntu :  do you sometime have to 'reconstruct' part of the image after a rotation as the part "3" of my example (with the cats) ???

---

### Post by FroggySeven on 2013-06-09
bad new : darktable cuts much too much the borders of the photo during rotations...

good new : with Gimp, it's possible to move strait with the mouse the center of the rotation, that translates the photo (horizontal and vertical moves are just reversed).
                It's not so efficient than photoshop's interface, but allows quite good to tests what will do the rectangle-crop after the rotation.

                 (but I always wonder how to participate to gimp's developpement...)

---

### Post by sudodus on 2013-06-09
Test if you can establish cooperation with some guy via this page :-)

[http://www.gimp.org/develop/](http://www.gimp.org/develop/)

---

### Post by FroggySeven on 2013-06-10
thanks !

---

### Post by thotz on 2013-06-10
> **FroggySeven said:**
> bad new : darktable cuts much too much the borders of the photo during rotations...

good new : with Gimp, it's possible to move strait with the mouse the center of the rotation, that translates the photo (horizontal and vertical moves are just reversed).
                It's not so efficient than photoshop's interface, but allows quite good to tests what will do the rectangle-crop after the rotation.

                 (but I always wonder how to participate to gimp's developpement...)


If you want to combine your work with Ubuntu, you can for example look at the GIMP bugs in Ubuntu's bugtracker.
[https://launchpad.net/ubuntu/+source/gimp](https://launchpad.net/ubuntu/+source/gimp)

I sometimes compile versions from source into my system to test the bugs I have reported, if they are fixed on my system. On the other hand I like testing new features in early stage of development.

I'm not a GIMP developer, but I am a member of the Ubuntu Bugsquad team.

---

### Post by efflandt on 2013-06-12
Just curious what you mean by "automatic reframing"? When you crop an image to pick out a portion of it, how would any program know what part of the image you wanted (or how far to rotate it which way)? If you want certain pixel dimensions for a crop in gimp you can always drag a horizontal or vertical edge (dimensions show at the bottom) or move the area to be cropped once you drag the edges to a particular size. **Image** > **Scale Image** can resize either the original image or whatever you have cropped.  If I want to crop something that does not end up at the dimensions I want, I do the math so horizontal and vertical ratio will then scale to the size I want to end up at.

In gimp if you crop and rotate separately, you can always **Edit** > **Undo** multiple times before you save it, or **File** > **Revert** to completely reload the original image and start over.

---

### Post by Thee on 2013-06-12
Here is how you can do what you need (crop+rotate image) in GIMP:

1. Open the image.
2. Select **Rotate tool**, and then in the Rotate options panel, make sure **Clipping** is set to "**Crop with aspect**", and then go ahead and rotate the image the way you want.
3. After the image is rotated, go to **Image > Autocrop Image**.

Done.

---

