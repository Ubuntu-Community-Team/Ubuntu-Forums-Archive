---
title: "Gimp and refocus issue"
date: 2007-10-28
forum: General Help
---

### Post by FerBatista on 2007-10-28
I'm having an issue with refocus plugin on gimp. When I run the plugin it does absolutely nothing, the progress bar appears moving on the bottom and it finishes without any errors, but with no effect at all on the image, also it doesn't appear on the undo history.
This is for regular sized images from my D70 or D50, if I use a websized image, at 700pix or similar and I open the refocus tool, increase the size of the palette so that it shows all of the image and then press the preview button, after this if I press OK refocus works as it should. But this limits me to use refocus on websized images only. 

All this is happening on my 32 bit install, on my 64 bit machine it works as it should I press OK and it works perfectly right away.

Any ideas of what could be wrong? I really love this plugin and I really want to be able to use it on both my installations. 


Thank you
Fernando

---

### Post by FerBatista on 2007-10-29
Anyone?

---

### Post by KittyChunk on 2007-10-31
Same problem here. Ubuntu Gutsy, GIMP 2.4.0-rc3. 

Doesn't seem to work with any size images on my laptop - looks like the plugin is failing silently before completion as the image is not marked as changed after using it, nor does it appear in the undo history as FerBatista pointed out.

---

### Post by MrGnu on 2007-10-31
Are you guy's trying to use the filter for Scanned Images or, Photo's from your digital camera ??

The Refocus Filter was designed for Scanned Images, And yes it workes perfectly.

---

### Post by FerBatista on 2007-10-31
I'm using it with photos from my cameras, I haven't tried with others. But I can't see why it would make a diference to be a camera image vs a scanned image.

Also, in the 64 bit version it works perfectly, JPGs, tiffs it doesn't matter it works as it should allways.

---

### Post by MickS on 2008-03-05
I have the same problem refocus goes through the motions but doesn't do anything.
The version in Digicam works fine:confused:


Mick

---

### Post by breaking on 2008-03-07
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/refocus/+bug/199508](https://bugs.launchpad.net/ubuntu/+source/refocus/+bug/199508) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				ditto here, I filed a bug:

[https://bugs.launchpad.net/ubuntu/+source/refocus/+bug/199508](https://bugs.launchpad.net/ubuntu/+source/refocus/+bug/199508)

---

### Post by fragos on 2008-03-07
Try the Filters-> Enhance-> Unsharp mask.  You might also try installing "gimo-refocus" which uses FIR Wiener filtering.

---

