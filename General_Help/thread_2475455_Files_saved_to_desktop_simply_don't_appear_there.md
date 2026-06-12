---
title: "Files saved to desktop simply don't appear there"
date: 2022-05-27
forum: General Help
---

### Post by jonfisher on 2022-05-27
Ubuntu 22.04 lts

I have noticed that files saved to the desktop, from a webpage, such as jpg or pdf (and probably others) don't appear on the desktop when saved to the desktop from a Firefox/Chromium browser page (by right clicking to save it to desktop (by then choosing other locations ->computer->home->my name->desktop).

I invite others to attempt this & post here....

---

### Post by Dennis N on 2022-05-27
Look at this thread. It may be related to your problem:
[https://ubuntuforums.org/showthread.php?t=2475449](https://ubuntuforums.org/showthread.php?t=2475449)
You need "Extensions Manager" to view the extensions status (as in the screenshot there)

---

### Post by Dennis N on 2022-05-27
I saved an image from a web page to the Desktop and it works for me. The saved image appears in the lower _right_, so you may not notice the icon. 
I used the Firefox (snap) browser in Ubuntu 22.04.

---

### Post by jonfisher on 2022-05-27
I can drag a file from other folders to the desktop and they will appear  on the desktop.  I just saved a file from Gimp to the desktop and it  appears on desktop.    It seems that files saved from a web browser page  are the ones that won't.

Update:  I just attempted to save files from a browser page to the  desktop with my laptop, and the files DO appear on the desktop when  using it.  I wonder what the difference between my desktop and laptop  could be, as I did a fresh install of Ubuntu 22.04 lts on each machine  not long ago.   Hmmm.....

Also, the saved files don't appear in lower right....

This really isn't that big of a deal.  Just odd to me....  I wonder if there is a way to search the drive and see if the files are showing up somewhere....

---

### Post by Dennis N on 2022-05-27
> This really isn't that big of a deal. Just odd to me.... I wonder if there is a way to search the drive and see if the files are showing up somewhere.... 
In Firefox, the default save location is ~/Downloads. But you can change that in (Firefox) Settings > General > Files and Applications > Downloads.
To allow it to save to Desktop, I had to change the setting there to "Always ask you where to save files".

Other:
"Extensions Manager" is:
```
gnome-shell-extension-manager/jammy-updates 0.3.0-0ubuntu2.1 amd64
  Utility for managing GNOME Shell Extensions

```
if you don't have it already. This an essential application to have on your Ubuntu.

Unless the necessary extension somehow is turned OFF, you should be able to have icons on the Desktop. I can't think of other causes.

---

### Post by jonfisher on 2022-05-27
Where in settings is user installed extensions (please)

or do I install extensions manager to get to that

---

### Post by Dennis N on 2022-05-27
> **jonfisher said:**
> Where in settings is user installed extensions (please), or do I install extensions manager to get to that
You probably don't have any user installed extensions yet. Install the "Extensions Manager" and use it to search (click "Browse") for them and install. "Extensions Manager" is in Ubuntu Software. Install the top one, not the second. See attachment.

---

### Post by jonfisher on 2022-05-27
Desktops icons is turned on.  I suspected it was, as moving files to the desktop in other ways does make them appear there.

oh well.  It's not that big of a deal.  Files simply won't appear on desktop *only* when saving there from a open browser page....

---

### Post by Dennis N on 2022-05-27
Well, that's weird. You don't see the icon in the lower right corner of the Desktop when you save or copy something to the Desktop?

---

### Post by Dennis N on 2022-05-27
One other thing comes to mind that solves some problems related to display. On login, choose the 'Ubuntu on Xorg' session rather than 'Ubuntu' - use the gear icon in lower right to specify which session to start.

---

### Post by HermanAB on 2022-05-28
UNIX is case sensitive.  -/Desktop and -/desktop are not the same directory

---

### Post by mIk3_08 on 2022-05-28
> **jonfisher said:**
> Ubuntu 22.04 lts

I have noticed that files saved to the desktop, from a webpage, such as jpg or pdf (and probably others) don't appear on the desktop when saved to the desktop from a Firefox/Chromium browser page (by right clicking to save it to desktop (by then choosing other locations ->computer->home->my name->desktop).

I invite others to attempt this & post here....
You can try to create files to your desktop by running this command in your desktop. try this command below; Regards and cheers.
```
echo "This is a test" >~/Desktop/yourdesktoptextfile.txt
```

---

### Post by jonfisher on 2022-06-01
> **mIk3_08 said:**
> You can try to create files to your desktop by running this command in your desktop. try this command below; Regards and cheers.
```
echo "This is a test" >~/Desktop/yourdesktoptextfile.txt
```

Yes, that creates that file on my desktop.
Again, the only time a file doesn't get saved to desktop is when it is saved from Firefox browser....

Thanks...

---

### Post by Impavidus on 2022-06-02
"Save to desktop" is slightly ambiguous: there's placing something on the desktop, the part of the user interface, but there's also saving something to the ~/Desktop directory, a place in the filesystem. Normally, whatever is placed in the ~/Desktop directory show up on the desktop, unless your desktop environment is configured not to do so. In your case, it looks like the desktop environment properly shows the contents of ~/Desktop on your desktop, but the web browser fails to save to ~/Desktop. Is that right?

There are multiple ways to save some file in Firefox or other web browsers: right click on a link &#8594; save link (automatic for content that the browser can't display); click File &#8594; Save page; right click on a page or element &#8594; Save as; select &#8594; drag and drop to some target. Do none of these methods work or just some of them?

Personally, I find drag and drop a horrible interface, as it's far too easy to drop things in the wrong place. From a programmer's point of view it's by far the hardest. First the sending application has to notify the desktop manager that the user is dragging some element that the desktop manager can find at a particular stream, then the desktop manager has to tell the receiving application that some content can be dropped on mouse release, available at a particular stream. Both the sender and receiver must know how to interact with the particular desktop manager in use, and there are several of those.

Now it appears that Firefox (at least Firefox 100.0.2 on Xubuntu 21.10, deb version) chooses the temporary file /tmp/dnd_file*/* as the location where the dragged content can be found (dropping in the terminal results in dropping such a file name and indeed the files are there). My guess is that the snap version of Firefox may not be able to save files to /tmp/, so drag and drop doesn't work. Or it may be a desktop manager issue.

---

### Post by vanadium on 2022-06-02
> **Impavidus said:**
> My guess is that the snap version of Firefox may not be able to save files to /tmp/, so drag and drop doesn't work. Or it may be a desktop manager issue.
Could also be because of Wayland. Log in on an Xorg session and see if it works there.

---

### Post by mIk3_08 on 2022-06-02
> **jonfisher said:**
> Yes, that creates that file on my desktop.
Again, the only time a file doesn't get saved to desktop is when it is saved from Firefox browser....
Thanks...
Try to install other firefox via another package manager maybe it will now work. If snap version is the cause of the problem then try another version. If you love to use the snap version maybe their could be a bug update for that from snap we just have to wait. Regards and Cheers.

---

