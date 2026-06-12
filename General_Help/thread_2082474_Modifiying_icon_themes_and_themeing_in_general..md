---
title: "Modifiying icon themes and themeing in general."
date: 2012-11-09
forum: General Help
---

### Post by jerome1232 on 2012-11-09
Essentially I really like the elementary icon theme, but I don't like that it changes my system setting icon from Unities cog icon to a nice, but out of place looking monitor.

How can I modify individual icons in an icon theme?

On a second note, I'm trying to find a gtk3 theme similar to radiance but I want a different window look, maybe a little bit of transparency or darker, tending towards grey. I just can't seem to find good theme's well on deviant art and gnomelook, any suggestions?

---

### Post by vasa1 on 2012-11-09
> **jerome1232 said:**
> Essentially I really like the elementary icon theme, but I don't like that it changes my system setting icon from Unities cog icon to a nice, but out of place looking monitor.

How can I modify individual icons in an icon theme?
...

That's my latest interest. Are they svg files or png?
What I do is first copy the icons over to ~/.icons so I don't mess with the originals in /usr/share/icons.

I'm not using Unity but Lubuntu and so for me, (most of) the relevant icons are in /usr/share/icons/lubuntu.
I copy the lubuntu folder over to ~/.icons. But within the lubuntu folder, there's a file called index.theme. I had to edit that as well to get the new name "recognized".

The first part of index.theme goes like this:
```
[Icon Theme]
Name= My Lubuntu Box
Comment=Just an icon theme for Lubuntu
Inherits=elementary
Example=directory-x-normal

```
I changed the second line from Lubuntu Box to My Lubuntu Box.

Whether  you're now looking at the icons in ~/.icons or in /usr/share/icons, the folders have a similar content:
```
[11:35 PM] ~/.icons/lubuntu $ ls
actions  apps  devices  emblems  icon-theme.cache  index.theme  mimes  panel  places  status
[11:35 PM] ~/.icons/lubuntu $ 

```
You'll have to look at each folder to see if you recognize the icons you like and dislike. Then it maybe just a simple matter of replacing one with another.

The only catch is the format: if both are .png or .svg then it's simple. I'm not sure things will work if one is a .png and the replacement is a .svg.

The Lubuntu ones are largely svg so I installed Inkscape to fiddle a bit but (thanks to Vaphell) came to know about [svg-edit]("https://code.google.com/p/svg-edit/").

---

### Post by vasa1 on 2012-11-09
> **jerome1232 said:**
> ...
On a second note, I'm trying to find a gtk3 theme similar to radiance but I want a different window look, maybe a little bit of transparency or darker, tending towards grey. I just can't seem to find good theme's well on deviant art and gnomelook, any suggestions?
If you have the time, pick the theme that most closely fits your need and then fine-tune it by editing the .css files to your taste.

---

### Post by jerome1232 on 2012-11-09
That gives me a good starting place to look, I don't have time right at this moment but I'll try to give it a look and report back later today.

---

### Post by jerome1232 on 2012-11-10
I ended up useing the Faenza icon theme found here [http://tiheum.deviantart.com/art/Faenza-Icons-173323228](http://tiheum.deviantart.com/art/Faenza-Icons-173323228)

It has an installer script that allows you to change it up a bit, and by default uses all monochrome icons for the panel.

I will still take a look at editing elementary but I am really liking this icon theme.

---

