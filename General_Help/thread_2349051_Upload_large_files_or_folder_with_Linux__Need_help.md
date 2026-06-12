---
title: "Upload large files or folder with Linux ? Need help"
date: 2017-01-10
forum: General Help
---

### Post by autonenterprises on 2017-01-10
Hi,

I dual boot my work laptops with Unbuntu and windows 10. My windows 10 experience has been love/hate. For work I have to upload lots of xrays to Radiologists to read remotely.

On the Windows side, this is EASY. I can slide the folder into dropbox or let a desktop app for similar services zip the folder and send it to my recipients. I have problems with the wireless on my laptops with windows 10 so sometimes I cant connect to the internet.

I want to start uploading my xray folder ( typically 15- 90 MB) with my ubuntu installation because it ALWAYS connects to the internet with no problem. The difficulty is that I know of no desktop apps to make the process easy. I do know how to zip the folder to make a zip file myself, but after that I still don't know an easy way to upload that large zip file with ubuntu.

I would love tips.

B

---

### Post by howefield on 2017-01-10
You could use Dropbox in Ubuntu the same way you do in Windows.

---

### Post by autonenterprises on 2017-01-10
Thanks

Is there a dropbox application or are you referring to the dropbox webpage ? That ONLY works with chrome as do the hightail and dropsend websites. Any other browser is a real problem. I know I have tried. Qupzilla, midori, chromium, even FF. only the Commercial Chrome works like its windows counterpart in that drag and drop and searching directories for the file to upload work properly.

I hope there is another aption than dropbox at any rate as it is pretty clunky for what I do. i can't click "send" and forget about it as dropbox, only uploads to the dropbox, then I have to find the upload and choose "share" or something like that. I am usually doing all of this while driving so I avoid dropbox if possible. It is a pretty clunky operation.

Thanks again

---

### Post by wildmanne39 on 2017-01-10
Dropbox can be installed on ubuntu,it is in the repositories, but I recently read that dropbox is getting rid of the shared folder system and you will have to send a link to everyone that you want to access a certain file.

---

### Post by mc4man on 2017-01-10
You could install nautilus-dropbox package, then  run the setup using either new or  existing account. you'll get a dropbox folder in your home folder, ect.
```
sudo apt-get install nautilus-dropbox
```
After installing if using unity,  just open the Dash & type in dropbox, click on  to run the 1st time setup. You'll also get an app indicator in upper right panel.

DnD works as a copy when dropping into the dropbox folder

---

### Post by autonenterprises on 2017-01-11
Thanks All !

---

### Post by howefield on 2017-01-11
> **autonenterprises said:**
> Is there a dropbox application or are you referring to the dropbox webpage ?

As I said earlier (and others have above) it would work in the same way as it does in Windows, ie you would have an application independent of your web browser although of course you can manage dropbox files via your web browser of choice. Go to the dropbox website and download the relevant deb package depending on whether you need 32 or 64 bit, double click to start the install process.

If you are sending confidential information you may want to look at other options such as spideroak or simply encrypting the files. After all, when you put your files in the "cloud" you are trusting someone else to look after them.

---

