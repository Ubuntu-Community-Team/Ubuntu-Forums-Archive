---
title: "Can't Download JPEG Imagies With 7.10"
date: 2008-05-25
forum: General Help
---

### Post by Muchohombre57 on 2008-05-25
I am trying to download pictures taken in the JPEG format to my computer running Ubuntu 7.10. I have tried using both an SD card and a USB flash drive.

When I try I get this message:

"File format is unknown or unsupported."

"Eye of GNOME could not determine a supported writable file format based on the file name. Please try a different file extension. Like .PNG or JPEG."

I used to be able to download JPEG images without any problems. I must have accidentally changed a setting. I am hoping someone out there will be able to help me.

Thank you!

---

### Post by jrib on 2008-05-25
From your description, it seems like you copy the files to your system, but then they do not open correctly.  Is this accurate?

What does ```
file /path/to/image
``` return?

---

### Post by Muchohombre57 on 2008-05-25
First of all I apologize for the second post! I am having trouble with "FireFox."

After I plug in my flash drive I can open it up and see all of the pictures. I can even use one of the pictures on it for the backround on my desktop. Of course the next time I boot up the picture is gone.

Being new to Ubuntu I am not sure where to insert the file/path/to/image. If it is in the terminal how do I get the command to run? 

Once again my apologies and thank you!

---

### Post by FuturePilot on 2008-05-25
Yes, in a terminal.
Applications&#8594;Accessories&#8594;Terminal

Depending on where the file is located will determine what you need to enter in the terminal. So for example if it's on your desktop you would enter
```
file /home/<USER>/Desktop/some-file.JPEG
```
Replace <USER> with your username.

And note that Desktop is an uppercase D. Linux is case sensitive so Desktop is not the same as desktop or deskTop.

---

### Post by Muchohombre57 on 2008-05-25
The pictures (file) is located on a USB flash drive. So I am guessing I do not enter "Desktop." What would I enter? I am also guessing that after I enter the code in the terminal I press "Enter" on my keyboard.

When I click on "Disk" on my desktop the flash drive opens up and I can see the contents.

Thank you for your patience and help!

---

