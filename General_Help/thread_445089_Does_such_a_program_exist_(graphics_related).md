---
title: "Does such a program exist? (graphics related)"
date: 2007-05-15
forum: General Help
---

### Post by petersjm on 2007-05-15
Hmmm, I know this is probably a long shot, but I thought I'd ask :D

I've got this poster that used to be on my wall of Yoda (Star Wars, as if I needed to specify!). It's actually a whole series of smaller images taken from the original movies and set side-by-side to make up the bigger picture of Yoda, using light and dark areas to make the image. It's hard to explain - up close, it looks like just a random smattering of photos, but when you step back you can see Yoda - does that mean anything to anyone?

I'm told there's a Windows program that can do this, but no one I've asked knows what it's called and Googling it doesn't throw up anything relevant (searching for things like "make large image from smaller images" just hits me with "Optimize your images for the web" sort of stuff!). Anyway, never mind the windows app, 'cos I don't use windows anymore, does anyone know if such a program exists for linux and, if so, where I'd get it?

Do yell and scream at me if I'm not making sense. Nobody ever understands me (queue the violins...) LOL

Thanks. Peter.

---

### Post by tkjacobsen on 2007-05-15
Look at the references from this wikipedia article [http://en.wikipedia.org/wiki/Photomosaic](http://en.wikipedia.org/wiki/Photomosaic)

Maybe you can use some of them


EDIT
Actually metapixel is in the repos.

---

### Post by Kobalt on 2007-05-15
It does make sense, I think I see what you mean :)
But unfortunately I'm not sure an application can do that properly... It's more of a creation thing I guess. You could try out to reproduce it with Gimp though it seems kind of hard.

---

### Post by lazyart on 2007-05-15
What you're talking about is a photo mosaic.  There used to be a GIMP plugin for this but it was pulled because the patent owner felt it was an infringement.

Doesn't mean it's not still out there somewhere, but you'll have to do some hunting for it.

There is also AndreaMosaic, which is a freeware Windows product.  Maybe it is wine-friendly?  As easy as it is to run a virtual machine inside Feisty, it's an option.

---

### Post by tkjacobsen on 2007-05-15
Metapixel is quite easy to use.

Open a terminal:
create a source dir for small pictures: here foo/. Assuming the pictures to use is in bar/ do
```
metapixel-prepare bar/ foo
```

Build the image from input.jpg and save to output.png;
```
 metapixel --metapixel input.jpg output.png --library foo/                 
```

---

### Post by prozacgod on 2007-05-15
Since everyone else helped you with this i figured I'd give you and answer to the exact opposite, I once had an image mosaic that was really low resolution like 16x16 per block, or 24x24 ..  I used the gimp to extract the images and then imageseek (I think thats right) to find the images in my collection of frames from the movie... and reconstructed the image at a much higher resolution :D  okay probably doesn't help you ... but might be fun.

-Prozacgod

---

### Post by petersjm on 2007-05-15
Wow, thanks everyone! I glad I made sense in the OP :D
TKJacobsen, I'll check out metapixel, thanks!

---

### Post by stooshbunutu on 2008-02-19
Hiya,

Front end for metapixel

I've created a webpage that gerneates the script based on input fields to be copy-and-pasted into terminal to run the command.

It is the attached file, just save the .txt file as a .html file, open it in firefox, and enjoy.

Let me know what you think, I am currently working on converting it into a program front end

Hope you like it :)

---

