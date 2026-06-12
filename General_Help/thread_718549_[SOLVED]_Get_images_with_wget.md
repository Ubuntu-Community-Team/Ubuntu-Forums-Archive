---
title: "[SOLVED] Get images with wget"
date: 2008-03-08
forum: General Help
---

### Post by engberg on 2008-03-08
):P
How do I rip images of my blog with wget? :confused:

If I do a:
wget -P Slides -A jpg,jpeg [http://kaspere.blogspot.com/](http://kaspere.blogspot.com/)

Then I get only an index-file :-k

Please help - I've been ](*,) for a long time with this problem..

---

### Post by xelapond on 2008-03-08
RIght click on the image and say  "Copy image location".  Then paste it into wget.

Hope that helps!

Alex

---

### Post by insineratehymn on 2008-03-08
> **xelapond said:**
> RIght click on the image and say  "Copy image location".  Then paste it into wget.

Hope that helps!

Alex

Indeed.
Are you sure you have the right folder and stuff?

Edit:

When I try the wget you posted, all I get is an index.html file.

---

### Post by engberg on 2008-03-08
oh... I'm sorry for not having been clear enough..

I want to rip my blog of images daily, in a part of a slideshow project I'm doing..

So I need to be able to rip the entire page of images, without knowing the excact image-link...

Doesn't matter if I get a lot of small images too - the can just be deleted afterwards.

---

### Post by insineratehymn on 2008-03-08
Ok. The problem that I am having when I try your exact posted wget is that I get NO images. At all.

And when I check the source on your page at [http://kaspere.blogspot.com/](http://kaspere.blogspot.com/) it doesn't say anything about Slides...

The problem may be with how blogsphere hosts images.

---

### Post by engberg on 2008-03-08
> **engberg said:**
> ):P
How do I rip images of my blog with wget? :confused:

If I do a:
wget -P Slides -A jpg,jpeg [http://kaspere.blogspot.com/](http://kaspere.blogspot.com/)

[COLOR="Red"]EDITED WITH HELP FROM insineratehymn, sorry I got it wrong the first time, I tried wget from another site.. I really don't know how to fix this problem..:[/COLOR]
Then I only get an index.html-file... :-k

Please help - I've been ](*,) for a long time with this problem..
 .

---

### Post by engberg on 2008-03-08
Oh.. the "Slides" is just the folder which I'd like to save the ripped images in..

---

### Post by insineratehymn on 2008-03-08
You know.... Everything tells me that what you are doing should work...
But it doen't and I don't know why.

Anyone else?

---

### Post by engberg on 2008-03-08
********.... :mad:

I really hope someone has a hint as to how I can make this work...

Perhaps there is an easy solution via a feed?
[http://kaspere.blogspot.com/feeds/posts/default](http://kaspere.blogspot.com/feeds/posts/default)

---

### Post by insineratehymn on 2008-03-08
If you can get the images into an RSS feed it shouldn't be hard to write a perl script to pull them out that way...

---

### Post by Sukarn on 2008-03-08
Here's something that should work.

```
wget -P Slides -r -nd -t5 -H --domains=.blogger.com,kaspere.blogpost.com http://kaspere.blogspot.com/ -A.jpg,.jpeg,.jpg.1,.jpeg.1 -erobots=off
```

**Edit:**
Script fixed.

---

### Post by insineratehymn on 2008-03-08
> **Sukarn said:**
> Here's something that should work.

```
wget -P Slides -r -nd -nc -H --domains=bp1.blogger.com,bp2.blogger.com,bp3.blogger.com,kaspere.blogpost.com http://kaspere.blogspot.com/ -A.jpg,.jpeg,.JPG,.JPEG -erobots=off
```

Or that would be easier. :guitar:

---

### Post by Sukarn on 2008-03-08
Script fixed.
Do not use the one that insineratehymn quoted.

---

### Post by Sukarn on 2008-03-08
If you want to run this as a script in a cron job, then you should add this commang to the script after the wget command so that it removes the useless small files after getting the real ones -

```

rm -f Slides/*.jpg
rm -f Slides/*.jpeg

```

This will not remove the real images as those are going to be saved with the ".1" extension.

---

### Post by engberg on 2008-03-08
You are a demi-god.... Thanx..

The problem is though, that it doesn't save the real images, only the thumbnails... which are the jpg.1 images

I tried deleting all the -a switch, and I can see that the real ones are the .jpg.6 images....
How do I get only those?

---

### Post by Sukarn on 2008-03-09
OK, found the problem.
It seems that blogger makes the thumbnailed links point to another html page with the extension of the actual image, which was giving us the original 396 bytes long .jpg files.
Add .jpg.2 and .jpeg.2 to the downloading list, and remove .jpg.1 and .jpeg.1 files after downloading them by adding them to the rm -f list.

The complete script should now be -

```

wget -P Slides -r -p -nd -t5 -H --domains=.blogger.com,kaspere.blogpost.com http://kaspere.blogspot.com/ -A.jpg,.jpeg,.jpg.1,.jpg.2,.jpeg.1,.jpeg.2 -erobots=off
rm -f Slides/*g
rm -f Slides/*g.1

```

---

### Post by engberg on 2008-03-11
I thank you both for spending time, making me wiser.
- with this last post - it works like a charm..!

If any of you have the time, then my photoframe project has presented another question about wget here:

[http://ubuntuforums.org/showthread.php?t=721569](http://ubuntuforums.org/showthread.php?t=721569)

---

### Post by Sukarn on 2008-03-11
I would help, but then your problem seems to have been solved already

---

