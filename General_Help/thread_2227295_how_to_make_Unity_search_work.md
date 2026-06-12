---
title: "how to make Unity search work"
date: 2014-06-01
forum: General Help
---

### Post by LifeEnemy on 2014-06-01
Hi,

Unity search is terrible. It rarely finds the files I'm looking for unless I've already accessed them recently (making it useless for me). I found the "unity filesearch lens" ([link]("https://launchpad.net/~pydave/+archive/unity-lenses") [link]("http://www.webupd8.org/2011/05/real-files-folders-search-unity-lens.html")) in various places, but after a lot of tampering it seems that it no longer works for anything past 12.04. Certainly not 14.04 that I'm on.

Is there some way to make Unity search actually find files and folders in my computer, rather than just the ones I opened in the past few days? A lens or some kind of tweak?? It'd make my life far easier.

Thank you.

---

### Post by vanadium on 2014-06-01
For me, this is working quite well since several versions. 
- load dconf-editor (you may first need to install it)
- Navigate to "Desktop - unity - lenses - files"
- Check whether "Use locate" is checked (is by default as far as I am aware).

Eventually update the locate database: "sudo updatedb" (is automatically being done during startup).

This involves that the lens should find any file by name that is under your home folder, but not on removable media. It actually works quite powerfully, as the entire file path is searched. e.g, if you have a document "invitation birthday party.odt" in a folder "Documents/Letters/Grandma", then a search for "invitation birthday" will find any file with that string contained in the name, but a search "grandma invitation birthday" will retrieve only the one in the Grandma folder. The order is important:  "invitation birthday grandma" will not work.

---

### Post by philinux on 2014-06-01
sudo apt-get install --reinstall unity-lens-* unity-scope-home

Try this.

---

### Post by LifeEnemy on 2014-06-07
Neither of these suggestions worked, unfortunately. "Use locate" was checked, and I ran updatedb with no effect. Reinstalling the lenses didn't fix anything either.

I tried finding files that I used a few weeks ago, but the only things Unity showed me were completely unrelated. In fact, it seems to show me the same recently opened files no matter what I actually put into the search bar =/

---

### Post by LifeEnemy on 2014-06-23
Bump. Unity seems like it would be great if it worked.

I do have my documents/pictures/videos/etcc folders on a separate HDD from /home, but they're connected by symbolic links, so I don't think that would cause problems. Regardless, Unity rarely finds files located in my home folder proper anyway. Seemingly, unless I've accessed them that day they don't show up.

Suggestions?

---

### Post by vanadium on 2014-06-23
That might be the problem. Locate will find your files using their "true" paths, and I would not be surprised if Unity is designed to track only files under your home folder. You should probably mount bind the directories on your separate HDD to the respective folders in your home, instead of using a symbolic link. This involves adding statements to your /etc/fstab file like in:
```

/home/lifeenemy/Documents /media/drive/Documents none bind

```
This example assumes that your home directory is called /home/lifeenemy, and that your separate HDD is mounted on /media/drive. You would need to include similar statements to bind the other relevant folders in your home directory as well.

---

### Post by LifeEnemy on 2014-06-25
Symbolic links should behave like regular folders in most circumstance though, right?

And Unity still can't find files inside the home folder proper. I can sometimes find files on the secondary HDD, but they have to have been open that day. Possibly since the last boot, though I'm unsure.

---

### Post by LifeEnemy on 2014-10-30
I gave up for a long time, then tried using Unity again. It's still just as bad. This is infuriating! :mad: Every fix I look for on the net doesn't help.

I noticed that the "files & folders" lens doesn't update when I type into the search bar. Every other one works, F&F just shows Recent/Downloads/and Folders sections, but they never change at all when searching. Seriously, how can I fix this????


edit: Wow! I don't want to jinx it, but it seems one of the solutions I tried might have actually worked. Probably one of the ones from one of these pages

[http://askubuntu.com/questions/125843/dash-search-gives-no-result](http://askubuntu.com/questions/125843/dash-search-gives-no-result)

[http://askubuntu.com/questions/48994/unity-files-folders-lens-cant-find-anything](http://askubuntu.com/questions/48994/unity-files-folders-lens-cant-find-anything)

Now if only I could find a solution to the dozens of *other* problems with Ubuntu...

---

