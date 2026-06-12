---
title: "file manager that can handle invaild filenames better?"
date: 2019-02-25
forum: General Help
---

### Post by ardouronerous on 2019-02-25
[ATTACH=CONFIG]282648[/ATTACH]
I'm running PCManFM and Thunar on Lubuntu and when transferring files from my computer to my FAT32 formatted flash drive, this is the usual options I have when dealing with invalid filenames. I'm looking for a file manager that can give me the option to rename the file.

Thanks.

---

### Post by TheFu on 2019-02-25
I don't use GUIs much, so cannot help with that except to say that many Linux file managers have an addon right-click extension capability.  I've looked it up a few times, but always drop back to a shell script because I work on servers 95% of the time.

I've always just used a **rename** script and manually avoid creating filesystem objects that don't fit the filesystems I use.
If I didn't have control over the filenames - others get to name them whatever they like - then I'd make a comprehensive script to handle all the issues.

The top answer here: [https://serverfault.com/questions/242110/which-common-charecters-are-illegal-in-unix-and-windows-filesystems](https://serverfault.com/questions/242110/which-common-charecters-are-illegal-in-unix-and-windows-filesystems) has links to the limitation for each file system AND each OS.  Filesystems are much more permissive than OSes, it seems.

---

### Post by ardouronerous on 2019-02-25
I also try to avoid using these characters whenever I can: \ / : * ? " < > |
but there are times when I forget to do this and try to transfer files to my flash drive. So I'm looking for a file manager that can give me the option to rename the file during the transfer from computer to flash drive.

---

### Post by dragonfly41 on 2019-02-25
Krusader has a rename feature and is dual pane.
But so does Double Commander.

---

### Post by HermanAB on 2019-02-26
The best option is not to use FAT32 to begin with.  Reformat the drive with NTFS instead.  You won't be sorry.

---

### Post by oldfred on 2019-02-26
Always mount with windows_names parameter and you will  not have naming issues. I have used this with NTFS, not sure if valid for FAT32 also or not.

       Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20)  

You should only use FAT32 for small partition or where an external device requires it.
FAT32 does not have a journal, so repairs can be difficult or impossible. And it does not support file size over 4GB.

And only use Windows formats if dual booting with Windows. You cannot run chkdsk or defrag from Linux.

---

### Post by TheFu on 2019-02-26
> **ardouronerous said:**
> I also try to avoid using these characters whenever I can: \ / : * ? " < > |
but there are times when I forget to do this and try to transfer files to my flash drive. So I'm looking for a file manager that can give me the option to rename the file during the transfer from computer to flash drive.

And I'm suggesting that this is an addon that you can create using the customization available in most Linux file manager GUIs.  I think you'd need to recognize it BEFORE and do the rename using the right-click context menu. [https://manpages.debian.org/testing/caja-actions/caja-actions-config-tool.5.en.html](https://manpages.debian.org/testing/caja-actions/caja-actions-config-tool.5.en.html)  Others will have something similar.

For Thunar: [https://docs.xfce.org/xfce/thunar/custom-actions](https://docs.xfce.org/xfce/thunar/custom-actions)

I've seen bulk rename capabilities inside file managers too.


But if I'm copying a bunch of files, I'll be using rsync and if I'm using rsync, then it is 99% likely I'll have a tiny script. And if there is a tiny script, putting in a **rename** line to handle bad characters would have been one of the first things I did.  But that is me.  rsync feels much faster than other alternatives, but that i probably because it won't be using gvfs which is known to be terribly slow.  That and I'm not going to be watching the copy happen.

Sorry, I'm not any more help. Good luck.

---

### Post by Morbius1 on 2019-02-26
> **ardouronerous said:**
> I'm looking for a file manager that can give me the option to rename the file.

Erm .... maybe something happens to Thunar when installed in Lubuntu but the Rename option is available in Xubuntu by default:
[ATTACH=CONFIG]282651[/ATTACH]
Selecting Rename opens a dialogue box:
[ATTACH=CONFIG]282652[/ATTACH]
I don't have a Thunar Custom Action for this so me thinks it's just part of Thunar by default.

---

