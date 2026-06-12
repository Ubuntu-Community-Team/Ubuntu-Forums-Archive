---
title: "Where is the ISO"
date: 2008-06-24
forum: General Help
---

### Post by elbow rub on 2008-06-24
hello,

I just downloaded v.8.04, and am curious. Why did it download as a rar file, which I can't burn as an ISO (can I)? I'm sure this is an obvious thing and I hope I posted in the correct area.

Thanks in advance

elbow rub :)

---

### Post by RATM_Owns on 2008-06-24
It probably is an ISO.
For WinRAR, ISOs look like .rar archives. 
Right click it and look in Properties to make sure it is an ISO before burning.

---

### Post by drs305 on 2008-06-24
It is possible the iso is within the RAR. For the normal, 32-bit version, you are looking for a file named "ubuntu-8.04-desktop-i386.iso".

---

### Post by jimv on 2008-06-24
Where did you download it from?  Does it say .rar on the end of the file?  Or is it blank?  Is this Windows or Ubuntu you're using?

Lotsa questions :D  <-- looks like that smiley has a mustache

---

### Post by elbow rub on 2008-06-24
I downloaded it from "Michigan tech linux users" mirror, it downloaded ad ubuntu-8.04-desktop-i386.iso, but for some reason it a WinRAR archive file, like it associated itself as a rar, properties even confirms that. When I used Breezy, this didn't happen so it was easy. I am on a M$ desktop, I wanted to dual boot. 

Thank you all for your response

elbow rub

---

### Post by msgmikeh on 2008-06-24
> **elbow rub said:**
> I downloaded it from "Michigan tech linux users" mirror, it downloaded ad ubuntu-8.04-desktop-i386.iso, but for some reason it a WinRAR archive file, like it associated itself as a rar, properties even confirms that. When I used Breezy, this didn't happen so it was easy. I am on a M$ desktop, I wanted to dual boot. 

Thank you all for your response

elbow rub

It most likely is an ISO file. If you are in need of a burning program try, InfraRecorder found here: 
[http://infrarecorder.sourceforge.net/]("http://infrarecorder.sourceforge.net/")

There is an Express version, like Nero Express which makes burning ISO files a breeze. Hope that helps. 

Mike

---

### Post by jimv on 2008-06-24
Ok.  Open My Computer.  Go to the Tools menu and click Folder Options.  Click on the View tab.  Scroll down the list and uncheck Hide Extensions for Known File Types.  Click Apply.  Now you should be able to see the file extension on hte file.  Is it .iso or .rar?  If it's .iso, you can go ahead and burn it to a disk.

---

### Post by elbow rub on 2008-06-24
jimv, I did as you said, it's definently a rar archive in properties, but with properties and the file itself, it's an iso. I attached a screenshot of what I mean.

mike, I downloaded it and it won't install, it says it can't find a copy of cygwin1.dll, but it's there.


Thank you both again

ER

---

### Post by geirha on 2008-06-24
That's an image-file allright. Winrar has just claimed iso-files as winrar-files.

Here's a video on how to burn the iso in Windows XP. [http://screencasts.ubuntu.com/Downloading_and_Burning_an_Ubuntu_ISO](http://screencasts.ubuntu.com/Downloading_and_Burning_an_Ubuntu_ISO) (for Ubuntu 6.06, but it applies for all Ubuntu releases.)

---

### Post by elbow rub on 2008-06-24
geriah,

thank you very much, that video gave good insight and led me to ImgBurn. Burning now


thank you

ER

---

### Post by msgmikeh on 2008-06-24
> **elbow rub said:**
> jimv, I did as you said, it's definently a rar archive in properties, but with properties and the file itself, it's an iso. I attached a screenshot of what I mean.

mike, I downloaded it and it won't install, it says it can't find a copy of cygwin1.dll, but it's there.


Thank you both again

ER

"cygwin1.dll" needs to be in this directory "C:\Program Files\InfraRecorder\cdrtools". Is the file in that directory?

Mike

---

### Post by elbow rub on 2008-06-24
I believe it was, however, I found success with ImgBurn. Now I'm trying to refresh my memory on partitioning this thing.


thanks for your time

ER

---

