---
title: "Can't play video in WMV"
date: 2014-10-14
forum: General Help
---

### Post by F33435 on 2014-10-14
When I try to open a video the download box comes up with libre office. 
When I go to other the drop down box has no way I can get play video. 
Thanks ahead.

---

### Post by Ankush_Menat on 2014-10-14
> **F33435 said:**
> When I try to open a video the download box comes up with libre office. 
When I go to other the drop down box has no way I can get play video. 
Thanks ahead.

Please try to be more precise! Are you trying to play wmv video from browser? Do you have codecs for WMV?
Install all codecs - ```
sudo apt-get install ubuntu-restricted-extras
```
Have you tried VLC player? 
```
sudo apt-get install vlc browser-plugin-vlc
```

---

### Post by F33435 on 2014-10-15
The video is in a email. Thanks

---

### Post by SeijiSensei on 2014-10-16
As an email attachment?  If so, just save the video separately, then open the file.  Does that work?

It sounds like you have somehow managed to associate the .wmv extension with LibreOffice in your mail client.  If you're using Thunderbird, choose Edit > Preferences > Attachments and see what application is associated with the .wmv extension.  It's also possible that you have made this association at the operating system level.  If you open a file with a .wmv extension, does it try to launch LibreOffice?

If you don't have a WMV file to use for testing, download this: [https://archive.org/download/Windows7WildlifeSampleVideo/Wildlife.wmv](https://archive.org/download/Windows7WildlifeSampleVideo/Wildlife.wmv)

---

### Post by F33435 on 2014-10-16
Tried to download  archive .org this is what I get,  The item you have requested has a problem with one or more of the metadata files that describe it, which prevents us from displaying this page.   Yes, it tries to open in libre. Some other attachments open with no problem with WMV.  How can I save the video separate? Thanks

---

### Post by nerdtron on 2014-10-16
Open the email, on the lower part, there is an icon for attachment right?

From the mozilla site:
To save attachments for a single e-mail message, you can use any of these methods:  
 
[LIST]
[*] Right-click on the attachment name or icon in the "Attachments"  pane, at the bottom of the window, and choose "Save As..." (to save  only the selected attachment) or "Save All..." (to save all attachments  at once). In the dialog box that pops up, you can choose where on your  computer you would like to save the attachments.
[*] Using the "File" menu: look under "File -> Attachments" for the "Save As..." and "Save All..." options.
[*] Using your mouse, select an attachment in the Attachments pane and drag it to your Desktop.
[/LIST]

---

### Post by SeijiSensei on 2014-10-16
> **F33435 said:**
> Tried to download  archive .org this is what I get,  The item you have requested has a problem with one or more of the metadata files that describe it, which prevents us from displaying this page.   Yes, it tries to open in libre. Some other attachments open with no problem with WMV.  How can I save the video separate?
Most browsers offer a save file option when you right-click on the object.  With Firefox, right-clicking the link I gave you offers the "Save File As" option.

How you save an attachment to an email depends on the mail client you are using.

---

