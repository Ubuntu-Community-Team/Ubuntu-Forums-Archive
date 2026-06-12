---
title: "Firefox doesn't know how to open downloaded files"
date: 2013-07-31
forum: General Help
---

### Post by FCNBYwP on 2013-07-31
Hi

I am using kubuntu 12.04.1 and when i download anything using firefox and double click on I am being asked to choose which app is supposed to open this file.
And if I do this once for anyfile like .jpg ! 
this action will be applied to all file formats like .deb, .zip etc...

Did anyone face this before??
I have faced the same problem on several machines.

regards,

---

### Post by speartip on 2013-07-31
Your file associations cannot be set up properly. This is not a Firefox issue.
What you need to do is right click the file you download, scroll down to open with & see what the default application is used to open that file.
If you need to change it click "other" find the application you want to open that file, then tick the box "remember application association...."
From now on everytime you double click that file type, the app you chose will automatically open that file.

---

### Post by FCNBYwP on 2013-07-31
Thank you for your reply but I don't have the "open with" option
please see the image below 
[IMG]http://eb.tl/qva71[/IMG]

---

### Post by speartip on 2013-07-31
That's because you are trying to open the file in your web browser & Firefox doesn't know the file type.
What you need to do is "open containing folder" & then double click on your download or follow #2.

---

### Post by Erik1984 on 2013-07-31
When the dialog pops up that lets you pick the application to open the file with point it to: /usr/bin/kde-open Then kde-open will determine which application needs to open that filetype. So images will be opened with Gwenview for example (if that's your default imageviewer).

---

### Post by FCNBYwP on 2013-08-01
Thnx a lot guys it works!
[**[COLOR=#000000]Euroman[/COLOR]**]("http://ubuntuforums.org/member.php?u=1332877") yeah what you said was right I have used this path"/usr/bin/kde-open" and now the problem is solved.

---

### Post by Erik1984 on 2013-08-01
Glad you found out :) It's hard to explain when you don't have Kubuntu + Firefox in front of you, plus once set you don't get the dialog again.

---

