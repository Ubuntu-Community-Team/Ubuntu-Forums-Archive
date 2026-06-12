---
title: "[SOLVED] Symbolic Links Question"
date: 2007-12-17
forum: General Help
---

### Post by ubuntu-freak on 2007-12-17
Is there a way to rename a folder containing multiple symbolic links without breaking them? A terminal command perhaps? Nautilus can't seem to do it. Thanks.

---

### Post by chippy99 on 2007-12-17
Well, this intrigued me because I've never tried it so I created a sub-directory called test and then created 2 symbolic links in it. I then renamed test to test1 and the links still worked so I cannot see what the problem is.

I id it all from a terminal though not in Nautilus.

---

### Post by chippy99 on 2007-12-17
To follow up, just did it in Nautilus and it worked Ok.

---

### Post by ubuntu-freak on 2007-12-17
Really? The link targets are in the folder I want to rename though. It's an icon theme folder. I made the theme in an unprofessional way I guess (copies of icons instead of symbolic links). Changing that now though as it's a waste of space. I used a test copy of my theme with a different folder name. Try it again with the targets in the same folder and you will see what I mean. Took a couple of hours to make the sym links so I'd love to find a way around this.

---

### Post by chippy99 on 2007-12-17
Oh sorry, I was looking at it the other way round. With the links in the directory you were renaming. I will shut up and have a think about it.

---

### Post by ubuntu-freak on 2007-12-17
Both the links and targets are in the folder. When I rename the folder the links break. Just seems odd seeing as they are all together still. Must be an alternative to deleting the links and starting over?

---

### Post by dagnabit dang doohickey on 2007-12-17
Usually links will break if the target is moved. But, if the link and target are located in the same directory there shouldn't be any breakage, unless the target was defined as an absolute path.

The link will break if *directory* is moved/renamed:
```
ln -s ~/directory/target ~/directory/link
```

The link will break if *directory* is moved/renamed:
```
cd ~/directory
ln -s ~/directory/target link

```

The link will not break if *directory* is moved/renamed:
```
cd ~/directory
ln -s target link

```

The link will not break if *directory* is moved/renamed:
```
cd ~/directory
ln -s target ~/directory/link

```

---

### Post by ubuntu-freak on 2007-12-17
Here is an example:

gnome-shutdown.svg and link named xfce-exit.svg 
 
I made the links using the context menu. Lots of them. So far I've done the actions, apps and catagories folders. I used a temporary folder name for my theme though cos it's in my home directory along with the original theme folder I'm working on. I didn't like sym links that's why the original is full of icon copies instead. I'm changing that now though cos it is a bit unprofessional and wastes space. At least you can move copies around without them breaking though.

---

### Post by dagnabit dang doohickey on 2007-12-17
```
ls -l xfce-exit.svg
```
should show xfce-exit.svg pointing directly to gnome-shutdown.svg (without a path preceding gnome-shutdown.svg), else breakage will occur.

---

### Post by ubuntu-freak on 2007-12-17
On my phone so can't type in the codes right now. What are you saying though? They break when the folder is named different to when I created the links. Despite the fact they are all next to each other in that said folder. I just wanna stop that. 
   
Has the context menu 'make link' created the wrong kind of link for my needs you're saying?

---

### Post by dagnabit dang doohickey on 2007-12-18
Other than firing up pcmanfm on rare occasions, I don't use a graphical file manager, so I'm not familiar with the contextual menu feature you're using. But, I'd imagine that it's default behavior would be to create links that have the full path to the target, since the majority of the time links are created to reside in a location that's different than the target location.

---

### Post by ubuntu-freak on 2007-12-18
I think you're right. I will start over with the command line instead. Thanks.

---

