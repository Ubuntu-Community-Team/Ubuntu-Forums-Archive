---
title: "Surplus Download Folders on Desktop"
date: 2021-02-04
forum: General Help
---

### Post by Daveski17 on 2021-02-04
Hello,

After downloading from Google Photos I am getting odd folders left on the desktop, and it requires a reboot to remove them.


[ATTACH=CONFIG]287907[/ATTACH]


This has been happening for a while in Vivaldi and now in Chrome (88.0.4324.150). I am running 16.04 LTS. Is this happening to anyone else?

Thanks,

Dave

---

### Post by deadflowr on 2021-02-04
Files showing on the desktop are located in the Desktop directory.
(two exceptions to this are external and network drives,
which will show as folders.
(But those must be set to show manually, normally)

I don't see this myself, but you could:
Check where the downloads are set to be placed. The default is Downloads, but that can be changed to anywhere.
And also check if somehow the Desktop folder is being linked to another location.

The odd part is that they disappear on reboot.
Seems weird but could mean that somehow a /tmp directory is linked to the Desktop Directory.
(/tmp directories are usually wiped on reboots)
 
Those are a couple things to look at.

Personally I would set the browser to always ask before downloading.
This allows you to 
1)always know when a download is about to take place,
2)allows you to set the download location every time a download is going to take place.

---

### Post by Daveski17 on 2021-02-05
> **deadflowr said:**
> Files showing on the desktop are located in the Desktop directory.
(two exceptions to this are external and network drives,
which will show as folders.
(But those must be set to show manually, normally)

I don't see this myself, but you could:
Check where the downloads are set to be placed. The default is Downloads, but that can be changed to anywhere.
And also check if somehow the Desktop folder is being linked to another location.

The odd part is that they disappear on reboot.
Seems weird but could mean that somehow a /tmp directory is linked to the Desktop Directory.
(/tmp directories are usually wiped on reboots)
 
Those are a couple things to look at.

Personally I would set the browser to always ask before downloading.
This allows you to 
1)always know when a download is about to take place,
2)allows you to set the download location every time a download is going to take place.


OK thanks. I've been getting this with Vivaldi for a while now, but it's new on Chrome. Admittedly I don't use Chrome much, but I suspect there is a connection (Blink?). It's never happened with Firefox. Oddly, on macOS Vivaldi did something similar recently. Although the surplus folders could be deleted without a reboot.

---

### Post by Daveski17 on 2021-02-05
I've selected to download to 'Downloads' (Chrome & Vivaldi).

[ATTACH=CONFIG]287909[/ATTACH]

Sometimes, but not always it does the same thing and a folder is left along with the picture file in 'Downloads'.

[ATTACH=CONFIG]287910[/ATTACH]

It seems to disappear on its own accord eventually though. It's weird.

---

### Post by deadflowr on 2021-02-05
crdownload is an in-progress download file.
It's chrome's designation that a file is being downloaded.
[https://www.howtogeek.com/210136/what-is-a-.crdownload-file-and-can-you-delete-it/#:~:text=crdownload%20file%20extension%20indicates%20a,file%20in%20your%20Downloads%20folder.]("https://www.howtogeek.com/210136/what-is-a-.crdownload-file-and-can-you-delete-it/#:~:text=crdownload%20file%20extension%20indicates%20a,file%20in%20your%20Downloads%20folder.")

---

### Post by Daveski17 on 2021-02-05
> **deadflowr said:**
> crdownload is an in-progress download file.
It's chrome's designation that a file is being downloaded.
[https://www.howtogeek.com/210136/what-is-a-.crdownload-file-and-can-you-delete-it/#:~:text=crdownload%20file%20extension%20indicates%20a,file%20in%20your%20Downloads%20folder.]("https://www.howtogeek.com/210136/what-is-a-.crdownload-file-and-can-you-delete-it/#:~:text=crdownload%20file%20extension%20indicates%20a,file%20in%20your%20Downloads%20folder.")

Thanks, that's interesting. For some reason if I download direct to desktop  sometimes these crdownload folders come with it, and it takes a reboot to remove them from the desktop. It appears that  when downloaded to Downloads the folders eventually disappear (so far). At least I can still download to desktop in Firefox.

---

### Post by CelticWarrior on 2021-02-05
Not a folder, it's a temporary file and it does disappear once the download is finished. 
And downloading to the Desktop has that issue - not updating the view -, among others. The Desktop is NOT for such usage, according to the Gnome design philosophy.
Firefox indeed works differently when downloading, it doesn't use the destination for the temporary incomplete files.

That said, nothing you're complaining of here is an actual problem.

---

### Post by Daveski17 on 2021-02-05
> **CelticWarrior said:**
> Not a folder, it's a temporary file and it does disappear once the download is finished. 
And downloading to the Desktop has that issue - not updating the view -, among others. The Desktop is NOT for such usage, according to the Gnome design philosophy.
Firefox indeed works differently when downloading, it doesn't use the destination for the temporary incomplete files.

That said, nothing you're complaining of here is an actual problem.

File/folder, either way I don't know why it won't delete from the desktop. It **doesn't** disappear from the desktop once the download is finished. I'm not up on Gnome design philosophy, although this seems more like *gremlin* design philosophy to me. Goblins, hobgoblins, kobolds, silkies, sprites and other assorted villainous fairies can study cohesive ontological  subjectivity to their malicious heart's content for all I care, it doesn't really solve my problem. 

This isn't a whinge, I'm genuinely puzzled and perplexed why these folders/files won't leave my desktop without a reboot. Which is a tad inconvenient (therefore it actually *_**is**_* a problem) for me, regardless of a variety of lawn ornament philosophies. 

Furthermore, it's only been happening for the past few weeks and I've been running Ubuntu for over a decade without this foray into Gnome man's land. As I stated earlier, this has also happened on macOS (with Vivaldi) at least once for me. So I'm just not sure what's happening at the Goblin University. 

I suspect this is some comparatively recent incompatibility bug with the Blink rendering engine and Unix platforms. 

I may have to send a strongly worded email to the goblins about this.

---

### Post by CelticWarrior on 2021-02-05
> [COLOR=#000000]File/folder, either way I don't know why it won't delete from the desktop. It [/COLOR]**doesn't disappear from the desktop once the download is finished.**
It actually does but the VIEW isn't updated. Desktop is a special folder. It used to be managed by the same file manager (Nautilus/Files), it no longer is. 
View can be easily refreshed without rebooting: [https://linuxconfig.org/how-to-restart-gui-on-ubuntu-20-04-focal-fossa](https://linuxconfig.org/how-to-restart-gui-on-ubuntu-20-04-focal-fossa)
But the best way to avoid that ridiculous non-problem that's causing you so much grieve is to NOT download stuff to the desktop, at least not with Chrome or any other Chromium based web browser (like Vivaldi).
Ansolutely NOT a problem and NOT a bug.

> [COLOR=#000000]I may have to send a strongly worded email to the goblins about this.[/COLOR]
Yeah, you do that... Keep us posted.

---

### Post by Daveski17 on 2021-02-05
> **CelticWarrior said:**
> It actually does but the VIEW isn't updated. Desktop is a special folder. It used to be managed by the same file manager (Nautilus/Files), it no longer is. 
View can be easily refreshed without rebooting: [https://linuxconfig.org/how-to-restart-gui-on-ubuntu-20-04-focal-fossa](https://linuxconfig.org/how-to-restart-gui-on-ubuntu-20-04-focal-fossa)
But the best way to avoid that ridiculous non-problem that's causing you so much grieve is to NOT download stuff to the desktop, at least not with Chrome or any other Chromium based web browser (like Vivaldi).

Yeah, I can manage the grieve by downloading elsewhere. It still actually gives me grief though.

> **CelticWarrior said:**
> Ansolutely NOT a problem and NOT a bug.

I disagree, it is a *new* problem and it definitely **bugs** me.

> **CelticWarrior said:**
> Yeah, you do that... Keep us posted.

[https://www.youtube.com/watch?v=1Oet1pKb0Vo](https://www.youtube.com/watch?v=1Oet1pKb0Vo)

They haven't got back to me yet. I know where I'm going to stick their little fishing rods.

---

