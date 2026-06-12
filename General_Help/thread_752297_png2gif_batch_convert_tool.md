---
title: "png2gif batch convert tool?"
date: 2008-04-11
forum: General Help
---

### Post by altonbr on 2008-04-11
I'm looking for a way to convert all my .png files to .gif in this folder for web development (damn IE6).

I found gif2png in the repos but I'm looking for png2gif. Is there anyway I can batch/automate this process?

---

### Post by SorryGoFish on 2008-04-13
Install imagemagick
```
sudo apt-get imagemagick
```

Then this oneliner should do it for you:
```
for file in *; do convert "$file" "$(basename file).png"; done
```

If you want to remove the old file too you can do
```
for file in *; do convert "$file" "$(basename file).png";** rm -f "$file";** done
```

---

### Post by SorryGoFish on 2008-04-13
Misread your post
```
for file in ***.png**; do convert "$file" "$(basename file)**.gif**"; done
```

---

### Post by altonbr on 2008-04-13
I fixed the code to look like this, but its still broken
```
for file in *.png; do convert "$file $(basename **$**file **.png**).gif"; done
```

It seems to return the ImageMagick/convert help file on every execuation.

I ran
```
for file in *.png; do echo "convert $file $(basename **$**file **.png**).gif"; done
```
to see what it would return and it produces valid:
> convert icon_xubuntu.png icon_xubuntu.gif

When I run the above quoted line manually, the quality between the .png and .gif is horrendous. Is there anyway to improve the conversation process?

Thank you for your time!

---

### Post by SorryGoFish on 2008-04-13
The quotes are supposed to be around each parameter, not the whole thing like that, so what's happening is that you're only passing one thing to imagemagick, which will make it output help. II put the quotes in case you have spaces in your names, if you don't you can ignore them.

```
for file in *.png; do convert "$file" "$(basename $file .png).gif"; done
```

As for the quality, be aware that GIF is not a pretty format. JPG would be a lot better for you, I think, but that's a different topic. Type "man convert" to see all the options you have for imagemagick.

---

### Post by altonbr on 2008-04-14
Ok, that worked perfectly, thank you!

I'll look into the quality issue on my own time, no need to waste yours.

---

