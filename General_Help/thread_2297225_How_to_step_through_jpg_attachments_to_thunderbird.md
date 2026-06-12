---
title: "How to step through jpg attachments to thunderbird email"
date: 2015-10-01
forum: General Help
---

### Post by Ralph L on 2015-10-01
I run xubuntu 14.04 and Thunderbird email.  People send me emails with multiple .jpg attachments.  I would like to step though them with an image viewer (like Gnome Image Viewer) in a manner similar to stepping through images in a folder (just pushing page-up and page-down keys).  At present I accomplish this by clicking the "Save All" button (in the email to the right of the attachments) and saving the images to /tmp.  Then I double click one of the images to bring up Gnome Image Viewer and step through the images.  This is rather time consuming as I have to do the Save All, select the folder in which to save the images, bring up Thunar, select /tmp, and finally double click an image.  Is there an easier way to do this--maybe a T-bird extension or something.  I know that I can display pictures in-line in the email, but I prefer a full screen image like Gnome Image Viewer allows.

Any help appreciated....

---

### Post by claracc on 2015-10-02
I don't use thunderbird, but in other mail clients as evolution, you left click on the attached .jpg image and a menu is deployed where you can select "to open with other application", then you select your preferred program to open the .jpg image.

---

### Post by Habitual on 2015-10-02
View Menu> View attachments inline...
Check it.

All attachments should show up in the email below the  body of the email.

---

### Post by Ralph L on 2015-10-02
Habitual, claracc,
Thanks for the responses.  Yes, I understand that I can select different apps to view images, and yes I understand that I can display images in-line in the email.  However, I am trying to find a way to step through the images with a viewer app the way I can step through images in a folder.  Does anybody know of an extension or a script that might do this?  I would imagine that such and extension/script would copy all the images in the email to a temporary folder, launch the viewer, allow me to step through the images in the folder, and when I closed the app, delete the temporary folder.  Actually I could probably creates such a script myself, but I don't know how to add a toolbar button T-bird that would allow the user to activate it.

Edit:  I found the T-bird addon AttachmentExtractor 1.3.5.1 that does some of what I want.  If I use its Preferences and set the destination folder to /tmp, go to the window displaying the email from which I want to extract attachments, right-click on the attachments (e.g. 14 attachments 1.2 MB) at the bottom of page, and select AE Extract All, all the attachments will be copied to /tmp.  Then I display /tmp with Thunar, double-click the first image, and step through images with the default viewer (in my case Geeqie) using PageUp and PageDn keys.  When I am done viewing, I can either delete the images in /tmp or let the OS do it at the next boot.  This is not all that I want but better than anything I have now.  Maybe I will still write the script I described above, if I get time.

Ralph

---

