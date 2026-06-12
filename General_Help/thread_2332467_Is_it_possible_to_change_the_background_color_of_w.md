---
title: "Is it possible to change the background color of windows in Ubuntu 16.04?"
date: 2016-07-31
forum: General Help
---

### Post by Deniii on 2016-07-31
Hi, everyone. New user here.

Trying to get used to Linux. So far, I've managed.
However, like topic tile says, is it possible to change the white background color windows have?
This white Ubuntu uses is on the verge of leaving me blind.
Windows 8 and 10 don't let you change color but I'm not surpised coming from microsoft.
What about Ubuntu? Is it possible?
I'm using Ubuntu 16.04.1 LTS.

Thanks.

---

### Post by CantankRus on 2016-08-01
Install a different theme and/or use redshift.
See [**_[COLOR="#B22222"]THIS[/COLOR]_**]("https://ubuntuforums.org/showthread.php?t=2330459&p=13516421#post13516421") post.

You can use unity-tweak-tool to select an installed theme.
```
sudo apt install unity-tweak-tool
```

---

### Post by Deniii on 2016-08-01
Thanks for the reply.
Yes, that's what I was looking for.

I see you have a lot of themes in your screenshot.
How do you download more themes?
I tried the link you posted but it only downloaded a few Arc themes.

---

### Post by CantankRus on 2016-08-02
You can find gtk3 themes on [**_[COLOR="#B22222"]gnomelook[/COLOR]_**]("https://www.gnome-look.org/browse/cat/135/ord/latest/")
Previously, you downloaded theme archives from here, extracted the theme folder and then placed in **~/.themes**. 
(The "~" symbol is a universal shortcut for the users home directory. eg for me it is **/home/glen** ...for you it may be **/home/Deniii**. 
A dot preceding a folder or file makes it hidden. ctrl+H to show hidden.
So **~/.themes** is a hidden folder in your home directory)

gnomelook now has an install button alternative which will auto install the theme to **~/.themes**
[ATTACH=CONFIG]270525[/ATTACH]
To use the install button you need to download and install [**_[COLOR="#B22222"]xdgurl[/COLOR]_**]("https://dl.opendesktop.org/api/files/download/id/1468612049/xdgurl_1.0.1-0ubuntu1_amd64.deb") <----direct download link.
Once you have downloaded xdgurl, go to the deb file in your file browser and click on it to install.

Now if you go to a [**_[COLOR="#B22222"]gtk3 theme @ gnomelook[/COLOR]_**]("https://www.gnome-look.org/browse/cat/135/ord/latest/")  and click on the install button you will see a "Launch Application" dialog...
[ATTACH=CONFIG]270526[/ATTACH]
Choose xdgurl and mark the box to remember choice.
You will then see a confirmation to install dialog (click yes to continue) and after a short period you will see an installation successful dialog.
[ATTACH=CONFIG]270527[/ATTACH] [ATTACH=CONFIG]270528[/ATTACH]

Theme should now be available to choose in unity-tweak-tool.

---

### Post by Deniii on 2016-08-02
Thanks CantankRus!
I tried that and it worked.

By the way, is there a key combination to enter the [B]~ symbol?
Like alt + some numbers keys or something.
I don't have that key in my keyboard.
[/B]

---

### Post by CantankRus on 2016-08-02
On my keyboard I use shift+grave(`).  key left of 1!
You could type tilde(~) with ctrl+shift+u, release all keys, then type 7e and hit Enter.

---

### Post by Deniii on 2016-08-03
Thanks!
I will try that.

---

### Post by vasa1 on 2016-08-03
@Denii, if your original question has been satisfactorily answered, please mark this thread [SOLVED] as described in 

[URL="https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads"]How to mark your thread as SOLVED
[/URL]

Also, I request you to start separate new threads for any other issues you face and to use descriptive titles for each such thread.

Clubbing different questions under one thread make not get the subsequent questions the attention they deserve. 

Thanks!

---

