---
title: "How to download files on Gallery of Samsung S9+ mobile phone"
date: 2023-06-13
forum: General Help
---

### Post by satimis on 2023-06-13
Hi all,

Ubuntu 22.04 desktop PC
Samsung Galaxy S9+ mobile phone.

I have no problem download video and photo files captured by the mobile phone to desktop PC via USB cable .  But I have problem to download files which were download on the Gallery folder of the mobile phone.  I couldn't find the Gallery folder of the mobile phone.

Please help.  Thanks in advance.

Regards

---

### Post by MAFoElffen on 2023-06-13
It should be the DCIM folder... Which in most phones is /storage/emulated/0/DCIM for the internal storage path to Pictures.

---

### Post by satimis on 2023-06-13
> **MAFoElffen said:**
> It should be the DCIM folder... Which in most phones is /storage/emulated/0/DCIM for the internal storage path to Pictures.Thanks for your advice.

You're correct.  But I only found the media (video and photos) captured by the phone, not download on the phone from emails.  It is very strange to me.

After mounting the phone
SAMSUNG Android/phone/DCIM
(please refers to screenshot)

All folders are empty except the Camera folder but I couldn't find the download video and photos

Regards

[B][COLOR="#FF0000"]Edit
====[/COLOR][/B]
Those download video and photos can be found on the phone Gallery.  The only way, which I just found, to download them to desktop PC is using Link share.  Send the link (url) via Yahoo Mail and download them from the mail.

---

### Post by MAFoElffen on 2023-06-14
For emails and Multimedia MMS messages you would have had to "save" the photos to the phone, then I would imagine that they would be saved to a download folder... My old Motorola phones had special folders for MMS, Facebook Messenger, screenshots and such, but Samsung always seemed to save things in basic folders.

---

### Post by satimis on 2023-06-14
> **MAFoElffen said:**
> For emails and Multimedia MMS messages you would have had to "save" the photos to the phone, then I would imagine that they would be saved to a download folder... My old Motorola phones had special folders for MMS, Facebook Messenger, screenshots and such, but Samsung always seemed to save things in basic folders.
When I receive emails with media attached, the media will be automatically download to Gallery folder.  I can browse them on phone but I could not find them on File Manager of Ubuntu 22.04.  Photos and video captured by phone camera are also saved on Gallery folder but the File Manager can find them.

Regards

---

### Post by MAFoElffen on 2023-06-14
Sorry. There is no folder on a Samsung Phone specifically named "Gallery". Samsung does use the Android "Gallery" Application to manage and view photos and videos.

If you go to the file manager application on Samsung, which they refer to as 'My Files', and select category "Images", it will show you media files of type photos and where they are physically located. I had to look at my wife's old Samsung phone to confirm that... And double checked Samsung's doc's.

Is that what you are referring to?

---

### Post by satimis on 2023-06-14
> **MAFoElffen said:**
> For emails and Multimedia MMS messages you would have had to "save" the photos to the phone, then I would imagine that they would be saved to a download folder... My old Motorola phones had special folders for MMS, Facebook Messenger, screenshots and such, but Samsung always seemed to save things in basic folders.
Actually without saving those attached media, I can find all of them on Phone Gallery, including WhatsApp.  "Quick Share" is a robust App I can download all media files on Gallery folder to PC at the same time avoiding clicking around on the PC screen.

Also I have made another test using an USB external SSD connected to the Phone, I can copy all files to SSD in following way;
On Phone
Settings -> Tools -> My Files
Copy files from "Internal Storage" to "USB Storage"

Then I can connect the USB external SSD to PC.  It is very convenient.

Regards

---

