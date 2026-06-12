---
title: "DVD RW discs state &quot;Read only&quot;"
date: 2016-04-17
forum: General Help
---

### Post by Extreedoc on 2016-04-17
I want to burn an MP4 video to a DVD RW disc but it keeps telling me that the disc is "Read only". Anything I can do? I can't format the disc either, the "Format" option is greyed out.

---

### Post by ajgreeny on 2016-04-17
You don't "format" a DVD RW disk, though depending on whether it's a DVD-RW or DVD+RW, you may need to prepare it for writing before you can burn anything to it.  Also, if previously used for something and then finalised, you may have to unfinalise it and remove the old files from it before you can burn anything new to it.

---

### Post by Extreedoc on 2016-04-18
Thanks AJ, I can tell you it is a +RW disc and it has been used previously but not finalised. I no longer have a dedicated DVD player/writer, just my computer, can I carry out what I need to do with the computer?

---

### Post by mcduck on 2016-04-18
Re you trying to add fiels to the disc just by dropping things to it in the file manager? That'snot how file systems on optical media really work (even though there are some programs that let you do that kind of things and hide the actual disc writing stuff in the background...)

Anyway, try doing it using a CD/DVD burning software, like Brasero or K3B.

Also it's quite possible that you need to write full disk at a time, especially if you need to be sure the disc will work with every device correctly. While there are ways to write multiple session to discs, the most common standards only allow writing the whole disc at a time. This also explains why the disc appears as read-only, the filesystem used on the disc is read-only by design, even on RW disc, so you can't add content to the filesystem, However you can erase the flesystem and write a new one with the files you want. There are some packet writing tools around which allow writing things file at a time, although they sacrifice some space on the disc, and compatibility, to allow doing so.

---

### Post by Extreedoc on 2016-04-19
Thanks Mcduck, Yes, I was trying to drag and drop the file. 
I do have Brasero installed but there doesn't seem to be an option to remove existing files. How do I safely remove the contents of the DVD using the computer, I can't imagine it will suffice to delete the folders or their contents, or is it?

---

### Post by mcduck on 2016-04-19
It's been a while since I've done anything with optical media, but based on a quick google search there should be an option called "Blank" in the Tools menu. That will empty the disc for you.

---

### Post by Extreedoc on 2016-04-19
Hmm..., there is no "Tools" menu. If I right click the files or folders in the disc the option to "send to rubbish bin" is greyed out. It seems that the files are protected but I didn't do it, I used to have a DVD player/recorder, the discs contain tv programs that I recorded but I never finalised them. Sorry to be a pain but I have 20+ discs and I'd like to be able to use them, any other ideas?

---

### Post by howefield on 2016-04-19
> **Extreedoc said:**
> Hmm..., there is no "Tools" menu.

You don't have a Blank option in the tools menu as per the image ?

---

### Post by mcduck on 2016-04-19
I mean the "Tools" menu in Brasero, of course. Or it might be called "Disc" now. I can't check the exact name for you since I'm not at my Ubuntu machine right now and don't have any Linux machine around where I could install it).  And no, you can't delete the files from the disc in file manager either, read-only means you can't change anything on the filesystem, and removing a file would require changing things and writing the changed information back to the disc... And Brasero will only do whole flesystem at once. For example "erase disc and wipe everything from it" or "select a bunch of files and write all of them on one go to the disc (creating a new filesystem with those files in it).

Edit: Looks like it's still called "Tools": [https://www.linux.com/sites/lcom/files/joomla/images/stories/brasero_main.png](https://www.linux.com/sites/lcom/files/joomla/images/stories/brasero_main.png)

---

### Post by Extreedoc on 2016-04-19
If you read the post that was here before (before I deleted it that is), please disregard as it was total tosh. When I looked at the disc I thought I had emptied, it was still full. BUT, I have found that if I open Brasero and [I]then[I] insert the disc, I then get the menu bar and the "Tools" option. There is indeed a "Blank" option which does work. I couldn't get the file I wanted to burn to the disc from this point so I closed Brasero and then I tried dragging it to the DVD in "Places" and at this point it opened "CD and DVD creator" and gave me the option to burn it, which I did with complete success. If you are only half as confused as I am by this whole process you must be a genius! 

Thanks to all who offered help to me and my dumb questions, you gave me the clues I needed to solve this.

---

### Post by Extreedoc on 2016-04-19
> **howefield said:**
> You don't have a Blank option in the tools menu as per the image ?

Hi Howefield, no, there isn't even a menu bar, but I did suss it in the end.
Thanks for replying.

---

### Post by mcduck on 2016-04-19
> **Extreedoc said:**
> Well, thanks Mcduck, I have managed to get rid of the files in Brasero, you are right, it doesn't say "Tools" now, you have to drop the files you want to get rid of into Brasero and then select them and click a "Minus" figure... gone. 

All wasted effort as the file I wanted to burn has this message when I try: "Installing packages by files is not supported", it goes on to say: "This method hasn't yet been implemented". I'm assuming this means that the software I need doesn't exist yet...

Thanks again for your help, at least I learned how to empty the discs.

That's the difference I've been trying to explain.

Removing or adding individual files is called "packet writing", it's not the normal stanadard way how optical media works, and relies on separate software & might not work on all devices.

The usual way is to write (or erase) full disc at once. So to erase the disc you can't try to click the minus button to remove individual files, but instead use the Tools->Blank to erase the whole disc in one go. And then you can select all the files you wan to add, and write them all together on one go.

If you don't seer the Tools menu in the Brasero window itself, you are probably using Unity as your desktop? In Unity the window menus appear in the top panel when you have hover your mouse cursor over it. So you should find the Tools menu there.

---

### Post by Extreedoc on 2016-04-19
Thanks Mcduck, if you go back to the bottom of page one of this thread you will see that I have solved this problem. I couldn't have done it without your advice.

---

### Post by QLee on 2016-04-19
> **Extreedoc said:**
>  BUT, I have found that if I open Brasero and [I]then[I] insert the disc, I then get the menu bar and the "Tools" option. There is indeed a "Blank" option which does work. I couldn't get the file I wanted to burn to the disc from this point so I closed Brasero and then I tried dragging it to the DVD in "Places" and at this point it opened "CD and DVD creator" and gave me the option to burn it, which I did with complete success. If you are only half as confused as I am by this whole process you must be a genius! 

Well, you used a DVD/RW which had been formatted (an additional format) for UDF by a Windows or Apple computer so that it was able to be written to like a big floppy drive because that's what people were used to using back in the days when that "universal" format was developed originally for CDs. This is what mcduck meant about "packet writing".  When you "blanked" the disc it was back as a plain DVD/RW. Then you could use it as normal.

---

