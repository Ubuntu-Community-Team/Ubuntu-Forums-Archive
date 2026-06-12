---
title: "Archive Manager failure: 13.04"
date: 2013-09-05
forum: General Help
---

### Post by RodK on 2013-09-05
I use a Celeron laptop computer, and just began using 13.04 after a hard drive crash.

I downloaded several big zip files with photos but Archive Manager could not unzip any of them; after extracting, the individual pix in the zip were all still locked up and showed in the directory with a padlock icon, and the pix viewer failed to render them, leaving me an error message.

But it was not a failure of the zip file; there was no problem extracting the files with Windows on my desktop. 

Then I tried to extract downloaded .gz versions of those same zip files, and same result, all photos and other files still padlocked and inaccessible. (I didn't try decompressing the .gz files with Windows, didn't have to.)

I was then disappointed to find the absence of any other application in the repository that included a description saying it could unzip files. So there's no other obvious software choice within Ubuntu.

I plan to do this a lot, even if I am on the road. My laptop lost Windows and I don't plan to replace Windows in it, too much hassle. What are my options, generally excluding recommending some kind of terminal session, as I don't know and don't want to know a single command, having never been a programmer and having no desire to become one?

Thanks.

---

### Post by Impavidus on 2013-09-05
Maybe the owner was stored with the photos. .tar.gz can store owner and permissions in the archive, not sure about .zip. If you don't have the same user ID as the user who crated the archive it may cause issues. Try changing the owner or permission using your favorite file manager. You will probably need sudo to change them.

---

### Post by RodK on 2013-09-05
> **Impavidus said:**
> Maybe the owner was stored with the photos. .tar.gz can store owner and permissions in the archive, not sure about .zip. If you don't have the same user ID as the user who crated the archive it may cause issues. Try changing the owner or permission using your favorite file manager. You will probably need sudo to change them.

Thanks but I checked out some random files from that source and there did not seem to be any ownership or permissions limits, and there was no problem decompressing the zips with Windows without adjusting anything.

---

### Post by Impavidus on 2013-09-06
It seems that the archive manager (aka file-roller) didn't have any trouble unpacking the archive, as it didn't give you error messages and your file manager showed that the image files were present after unpacking. However, they were shown with padlock symbols and your image viewer refused to open them, which suggests you don't have permission to view the files. So, in your file manager (nautilus or whatever version you use), find the properties of those padlocked pictures (right click &#8594; properties). Check ownership and permissions and change them if you need.

Windows's permission system is very different from Linux's system, which may explain why Windows didn't have any problems with them.

---

