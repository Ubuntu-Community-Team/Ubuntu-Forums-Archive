---
title: "Gimp problem..."
date: 2013-05-14
forum: General Help
---

### Post by Nixarter on 2013-05-14
So I am trying to do autoadjusts in color/contrast, etc to improve an image.  BUT it keeps making the eft side of the image dark, while the right side stays bright like I want it.  It is a panorama.[ATTACH=CONFIG]242587[/ATTACH]

Open the attachment and you will see that the left side gets gradually darker.  esp th efishermen in the far left.  It just makes the eft not worth looking at lol.  I want it all like the right side up to the lifeguard truck.

---

### Post by Nixarter on 2013-06-30
anyone? please?

i think the problem is that it is a very, very large image.  well over 100 megapixels, and far wider than tall.  but i dont know how to correct for this in gIMP.

---

### Post by Maverick Meerkat on 2013-06-30
Do you have Gimp treating this as one big image?
If so, you might want to try breaking it into sections, and lightening the dark sections before putting it back together.
Just a guess.
Cool image by the way!

---

### Post by Thee on 2013-07-01
Because the picture is made up of many smaller pictures that were shot with different lens positions, GIMP wont be able to adjust the contrast equally in all of them so that they match as if it was one big picture, like you want.
So you will need to do this manually for each part of the picture that you are unhappy with.

To do this, I suggest trying it like this:

Select the Rectangle Select Tool and in the Tool Options Dialog, click on "Feather edges", then adjust the Radius of feather edges accordingly. Setting it from 70-100 should work good, but you may need to test it a few times until you get the right amount.
Now select the entire area of the picture that needs to be adjusted and then apply the effects you need (brightness, etc).

Now what this will do is allow the rectangle with feathered edges to soften the transition of the applied effect and make it blend good so it looks as if your picture was taken in one shot rather then multiple.

Hope this helps.

---

### Post by Nixarter on 2013-07-05
Thanks for the replies, they have given me some nice things to think about doing.  :)

After reading your replies I realized that I forgot a very important bit of info.  Before doing the autocontrast/etc adjustment(s), the image is actually of a uniform brightness overall, it just needs a bit of a brightness and contrast boost.  Somewhere along the way, Gimp darkend one side, and brightens the other.  Like a lopsided brightness gradient across the image. Maybe as it is counting pixels to calculate medium gray for the contrast it gets beyond some limit, assumes the rest as black, then adjusts the contrast on a gradient based on that?  I really do think at this point that it is some sort of bug in gimp related to the file's  size or dimensions.  I'd do it in photoshop but windows 7 (doubt it is photoshop) just simply cannot handle the file.  I tried it on a dedicated (professional) graphic design workstation with an i7 and loads of RAM and it just crashes every time (hence the gimp).

I'm afraid if I split the image into pieces and then adjust each one that there will be visible differences at the merge lines.

I could try modifying it before stiching it with hugin, but.... that would be a daunting task.  The stitch alone took ages, then I had to modify it for a while to get the crop right, touch things up, fill in empty areas.  ugh.

---

### Post by Buntu Bunny on 2013-07-06
Have you tried asking about this in the [Gimp forums]("http://www.gimpforums.com/")? There's usually a lot of good help to be found there.

---

