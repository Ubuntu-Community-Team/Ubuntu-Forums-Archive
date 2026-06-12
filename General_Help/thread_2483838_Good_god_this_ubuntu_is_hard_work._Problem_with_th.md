---
title: "Good god this ubuntu is hard work. Problem with the default file manager"
date: 2023-02-10
forum: General Help
---

### Post by gusgf on 2023-02-10
Originally I was trying to post a message with an attachment on this forum. When I select the file from my screenshots folder and click upload nothing happens. Then I noticed the file manager app (Files v42.2) is indicating an instance is open BUT it's doing this for all of my 7 workspaces even though it's actually only open in 1. If I happen to be in any of the other 6 workspaces and click on 'Files' nothing happens. Also if I right clik on it and try to exit, again nothing happens. I have to go the the actual workspace where it's open to view or exit it. God help me if 'Files' has been minimised because then it's a guessing game as to what workspace it's actually in.

Can anyone suggest a fix or a file manager that works please?

---

### Post by gusgf on 2023-02-10
I just wanted to add I still can't get the file upload to work for attaching a pic to a message. I select the file, click upload and nothing happens.

---

### Post by Tadaen_Sylvermane on 2023-02-10
What is this a picture of? Forums such as this generally prefer terminal output in code brackets. Pictures are helpful but you won't get near the exposure that text output will. It's also harder to make sense of pictures without guessing to much. If the picture isn't inserted into your post directly very few people will ever see it as many including myself don't just randomly download stuff for the hell of it.


As far as the file manager something is definitely off. Clicking it in the dock should take you straight to it. Things can get stuck very rarely. No system is perfect. To be fair though if you've gone real far off the reservation with modifications and packages that aren't from the repositories or sandboxed in some way (flatpak, snaps) they could be the problem. Is why repos is the number 1 preferred place to get stuff. For me snaps and flatpaks are the next step. PPA's last.

---

### Post by monkeybrain20122 on 2023-02-10
> **gusgf said:**
> I just wanted to add I still can't get the file upload to work for attaching a pic to a message. I select the file, click upload and nothing happens.

What browser? Probably because Firefox is a snap.

---

### Post by DuckHook on 2023-02-10
Ubuntu is powerful, but it does have its learning curve. No question about that.

Answering your questions in no particular order:

[LIST=1]
[*]You can use whichever file manager you like. Linux power users will substitute something else for the default file manager at their convenience. You can also have two of them installed together. That means that you can install, say, Nemo alongside Nautilus without having to delete it. They will both work for you.
[*]I've found that a useful trick is to use the <Alt>+<Tab>&#8594;<Tab>… combo. This will cycle through all of your open apps. By releasing the <Alt> key when the wanted app is highlighted, I am taken right to the Workspace on which the app is resident. If the app is minimized, it will get restored to its open window state.
[*]Do you really need 7 workspaces? I have multiple apps up and running concurrently and like to think that I can multi&#8209;task, but 7 workspaces would be unmanageable to me. What's true in life is also true in tech: you reduce unnecessary problems by reducing unnecessary complexity.
[/LIST]
What I say next is based on the assumption that you are a Windows or Apple user trying to migrate to Ubuntu:

There is a tendency with Windows migrants to start off right away by customizing the Ubuntu desktop and loading all sorts of apps, utilities and tweaks. This is a (bad) Windows habit and almost invariably unwise. Such customizations more often than not cause all sorts of untraceable incompatibilities, glitches and breakages. Stick with the default setup until you are thoroughly comfortable and familiar with your new environment. If you make changes, carefully record what you did (I keep a simple text file on my desktop for this) so that you can reverse the changes if it leads to trouble. If you are ambitious, you can format your initial install using LVM or ZFS which allows you to snapshot your OS at a given moment for easy restores should you screw something up. But LVM/ZFS adds initial complexity, so it actually breaks my keep&#8209;it&#8209;simple rule and I don't really recommend it for new users.

---

### Post by gusgf on 2023-02-11
Thanks for all the replies lovely people, very supportive :)

My Ubuntu installation is pretty much stock and am using the default file manager...'Files'

I use 7 workspaces but not all have open stuff. I guess about 5 are consistently used and I like to keeps my different areas of work separate. I could use Clonezilla (on a USB) I suppose for periodic image backups, something I've used before. Yes Alt-Tab is very hand esp with this weird taskbar scenario, in W10 it was just a case of one click to get to the browser window I wanted now it's two or Alt-Tab*n.

The picture is simply for illustration purposes to help with a solution I've got for a post I posted regarding a problem I had. It doesn't contain any code.

It was suggested to post the picture directly, well I've tried that and when I use Amazon Photos as the host and post the link in the box, nothing, nada, niets happens. The link box disappears and no image appears within the post. I've tried dragging the image file onto the post but all that does is open a another tab in my browser containing the image. If someone can tell me how I embed an image directly.

---

### Post by ajgreeny on 2023-02-11
I suspect your problems are much more related to the version of Ubuntu that you are using which I assume is the default Ubuntu with gnome desktop environment than specifically your file-manager, though I also find the files application a bit unusual and difficult to use.

I think you may find one of the alternative DE versions much more like the standard desktop type that you will be used to using having come from Windows.
You will see from my information that I use Xubuntu with the Xfce4 DE in place of gnome which I admit that I find almost unusable, but then I'm an old user, both in age and also the number of years I have been using Ubuntu. Xubuntu has a much more normal looking desktop with a standard menu system and the equivalent of a Start button which can be placed anywhere you wish in the panel.

Using images in your posts is more adding an attachment than dropping an inline image into your text.
To do this you need to do the following.
[LIST=1]
[*]Create eg by using the PrintScreen key and saving it to your hard disk, or choose an existing image in your /home to attach.
[*]Go the Reply To Thread window, not the Quick Reply box, click on the paperclip icon in the toolbar and a dialogue appears
[*]Go to Add Files, then click Browse to navigate to the image and double-click it.
[*]Click the Upload button to add a small thumbnail which will show in the Attachments pane at the bottom of the dialog.
[*]That thumbnail will also show your post and when clicked by readers the thumbnail will open a large version of the image.
[/LIST]


See my uploaded image added in this way which I think should be now be clear to you.

See also the thread at [https://ubuntuforums.org/showthread.php?t=2415676](https://ubuntuforums.org/showthread.php?t=2415676) which gives more details of the available DE versions.

---

### Post by xanizen on 2023-02-11
The File Picker has been a controversial issue as it doesn't permit thumbnails. An 'improvisation' is to open a 2nd window with file explorer (aka nautilus), and then drag the file you wish to open onto the file picker.
[https://askubuntu.com/questions/1150404/kubuntu-18-10-how-do-i-change-this-file-picker](https://askubuntu.com/questions/1150404/kubuntu-18-10-how-do-i-change-this-file-picker)

The latest version of Gnome has thumbnails in the file picker, but many apps still rely on previous version of GTK.

You may need to relocate the file from the location of wherever its located onto your /home/ (aka ~) directory first. Then from there you may deduct there's a 'permission restriction' due to Snap 'enclosure'/sandbox.
[https://ubuntuforums.org/showthread.php?t=2483829](https://ubuntuforums.org/showthread.php?t=2483829)

---

### Post by lucant on 2023-02-12
Thank you for the explanation, [COLOR=#000000]ajgreeny!

[/COLOR]Using Ubuntu with gnome here.

---

### Post by ajgreeny on 2023-02-12
Great news, and I am very happy to have helped you sort out how to add thumbnails of images to your posts!

If you are now happy that your difficulty has been overcome, please mark as SOLVED from the Thread Tools menu up-top as it is a great help to other users searching the forum.

---

