---
title: "Unable to open image file"
date: 2020-07-26
forum: General Help
---

### Post by satimis on 2020-07-26
Hi all,

I have images files running on WordPress site.  They have been working for long time without problem.  Just found that they can't be browsed, not working.

I have download one of them to local PC.  Opening it with "Image Viewer" following warning popup;```

Could not load image “gadily.jpeg”.
Error interpreting JPEG image file (Invalid JPEG file structure: SOS before SOF)

```

Please advise how to fix the problem.

Thanks

Regards

---

### Post by TheFu on 2020-07-26
A corrupted image is a corrupted image.  Try opening it in any of the 50+ image editors. If one does open it, do a **Save As....**.  If none open it, use your backups.  Heck, I'd use a backup first.  There may be jpeg repair software. Have you searched?

The **convert** and **mogrify** tools in ImageMagick can handle things sometimes too. Try those.

---

### Post by mIk3_08 on 2020-07-26
If it is corrupted and feeling don't have any chances, then try to use hex editor a tool that is used to display raw data of the image file. This hex editor can help to get rid of image corruption. If some of the data is missing, then there can be difficulty in repairing the file. Some of the most common hex editor tools are Xxd Hex Editor, HxD,Cygnus and etc. It can be more tricky and complicated but it will help if the image so important. As TheFu has mentioned ImageMagick It also can help you a lot. And try to export it to any image format .png .tiff .eps.

---

### Post by satimis on 2020-07-26
> **TheFu said:**
> A corrupted image is a corrupted image.  Try opening it in any of the 50+ image editors. If one does open it, do a **Save As....**.  If none open it, use your backups.  Heck, I'd use a backup first.  

Hi,

Thanks for your advice.

The website was created on about 2013. It seems to me that all photo/images upload are corrupted.  Also I think it would be difficult for me to search their backups.

Whether you meant "Photoflare Image Editor"?

Install The Latest Photoflare Image Editor in Ubuntu 18.04, 19.10
[http://ubuntuhandbook.org/index.php/2020/01/install-latest-photoflare-ubuntu-18-04-19-10/](http://ubuntuhandbook.org/index.php/2020/01/install-latest-photoflare-ubuntu-18-04-19-10/)

Regards

---

### Post by TheFu on 2020-07-26
> **satimis said:**
>  Also I think it would be difficult for me to search their backups. 

Well, if the files are all corrupted and they don't have backups, then that's terrible news to give them, but it may be the best you can do. If they were a friend or client, I'd start managing expectations towards total loss.

But it could just be they used crappy software to create the images which didn't follow standards.  Something like convert could be scripted to read the bogus files --> write current standard files. Should take just a second for each file.

---

### Post by ajgreeny on 2020-07-26
I have occasionally managed to open using gimp a jpeg file that my image viewer application could not; no idea why and I could not be bothered to investigate in detail.

Which "image viewer" is failing for you?  Have you already tried any other image viewing applications?

---

### Post by satimis on 2020-07-26
> **ajgreeny said:**
> I have occasionally managed to open using gimp a jpeg file that my image viewer application could not; no idea why and I could not be bothered to investigate in detail.
Tired GIMP and also failed.

Pls see attached screenshot

> 
Which "image viewer" is failing for you?  Have you already tried any other image viewing applications?
Default "image viewer"

Tried other image viewer such as "fim" or "viewnoir" ?

Regards

Edit
===
Email advice seems not working !!!

---

### Post by satimis on 2020-07-26
> **TheFu said:**
> Well, if the files are all corrupted and they don't have backups, then that's terrible news to give them, but it may be the best you can do. If they were a friend or client, I'd start managing expectations towards total loss.

I do hope that I can find the VM on which the website in question was running on it.  The website is hoisted on Godaddy server.  It is running without problem but with only some images disappeared.  I recalled that the problem was caused by upgrading WordPress 2.4 version.  

> 
But it could just be they used crappy software to create the images which didn't follow standards.  Something like convert could be scripted to read the bogus files --> write current standard files. Should take just a second for each file.
Could you please explain in more detail?

Thanks

---

### Post by satimis on 2020-07-26
> **mIk3_08 said:**
> If it is corrupted and feeling don't have any chances, then try to use hex editor a tool that is used to display raw data of the image file. This hex editor can help to get rid of image corruption. If some of the data is missing, then there can be difficulty in repairing the file. Some of the most common hex editor tools are Xxd Hex Editor, HxD,Cygnus and etc. It can be more tricky and complicated but it will help if the image so important. As TheFu has mentioned ImageMagick It also can help you a lot. And try to export it to any image format .png .tiff .eps.
Thanks for your advice.

hex editor ?

such as;
Hex Editors on Linux
[https://linuxhint.com/hex_editor_linux/](https://linuxhint.com/hex_editor_linux/)

Regards

---

### Post by TheFu on 2020-07-26
> **satimis said:**
> 
> But it could just be they used crappy software to create the images which didn't follow standards. Something like convert could be scripted to read the bogus files --> write current standard files. Should take just a second for each file.
Could you please explain in more detail?


Could you please explain in more detail?

Crappy software is poorly coded software that usually works, but doesn't make files that are exactly compliant.  This was common for many decades. It is especially common when a proprietary piece of software is involved.

"convert" is a program included with Imagemagick.  Anyone doing any sort of image processing should be aware of that package and the XX tools it provides.  They are mostly CLI programs, but there is a bonehead GUI written in the 1990 X/Windows style to access a few of them.  There's no way around reading the manpage for the different Imagemagick tools. That's the only way, but in general, they work with 
```
$  command  [--long-option=value1] .... ... .... ... input-file  output-file
```

This means that a trivial looping bash script can be used to process each of the files, once you determine the correct settings.  For example, I have a little script that "optimizes" images from the source to what a website would rather use. It drastically reduces the file size, but for simple viewing by eye on a screen, it is good enough.
```
$ more img-opt
#!/bin/bash
QUAL=40

for img in "$@"; do
  NEW=${img/%.???/-opt.jpg}
  echo " Working on $img ..."
   convert -quality $QUAL  "$img"  "$NEW"
done
echo "rename 's/-opt.jpg/.jpg/g' "
```

No filenames can have spaces or any bash-interpreted punctuation. Run as 
```
$ img-opt  *jpg
```
It is non-destructive.  A QUAL over 90 would barely change anything. You might try that.

---

### Post by monkeybrain20122 on 2020-07-26
I have some pictures which have extension .png and ImageViewer threw an error, but changing it to jpg it works.

---

### Post by GhX6GZMB on 2020-07-26
How do you even know they are JPEGs? Never just trust a file extension. Best thing to do is open the file as hex and look at the header.

---

### Post by TheFu on 2020-07-26
> **ml9104 said:**
> How do you even know they are JPEGs? Never just trust a file extension. Best thing to do is open the file as hex and look at the header.

+1. Extensions are for humans. Linux doesn't care.

```
$ file star-wars-backgrounds-06-n.jpg
star-wars-backgrounds-06-n.jpg: JPEG image data, JFIF standard 1.01, aspect ratio, density 1x1, segment length 16, 
Exif Standard: [TIFF image data, little-endian, direntries=0], baseline, precision 8, 1920x1080, frames 3

$ file star-wars-backgrounds-20.jpg
star-wars-backgrounds-20.jpg: JPEG image data, Exif standard: [TIFF image data, little-endian, direntries=0], baseline, 
precision 8, 1920x1080, frames 3


```

---

### Post by monkeybrain20122 on 2020-07-26
> **ml9104 said:**
> How do you even know they are JPEGs? Never just trust a file extension. Best thing to do is open the file as hex and look at the header.

I didn't know, just a guess and it worked.

---

### Post by satimis on 2020-07-27
Hi all,

Lot of thanks for your advice.

Performed follows on Terminal;
$ convert gadily.jpeg gadily.png```

convert-im6.q16: Corrupt JPEG data: 18 extraneous bytes before marker 0xc4 `gadily.jpeg' @ warning/jpeg.c/JPEGWarningHandler/352.
convert-im6.q16: Invalid JPEG file structure: SOS before SOF `gadily.jpeg' @ error/jpeg.c/JPEGErrorHandler/322.
convert-im6.q16: no images defined `gadily.png' @ error/convert.c/ConvertImageCommand/3258.

```

Also;
$ convert gadily.jpeg gadily.jpg```

convert-im6.q16: Corrupt JPEG data: 18 extraneous bytes before marker 0xc4 `gadily.jpeg' @ warning/jpeg.c/JPEGWarningHandler/352.
convert-im6.q16: Invalid JPEG file structure: SOS before SOF `gadily.jpeg' @ error/jpeg.c/JPEGErrorHandler/322.
convert-im6.q16: no images defined `gadily.jpg' @ error/convert.c/ConvertImageCommand/3258.

```
The same.

On Internet I found following article;
A Complete List of JPEG Errors & Their Solutions
[https://www.stellarinfo.com/blog/a-complete-list-of-jpeg-errors-their-solutions/](https://www.stellarinfo.com/blog/a-complete-list-of-jpeg-errors-their-solutions/)

I have at least >20 image files corrupted.  Even if I found a solution it would take long time to fix the problem.

On WordPress websites
-> Add Media -> Media Library
Only 2 image files there which were just added by me lately.  

Others are square boxes.  Pls refers to attached screenshot.

I'll post on WordPress forum to see whether they can help?  I'll come back.

Regards

---

### Post by satimis on 2020-07-27
> **monkeybrain20122 said:**
> I have some pictures which have extension .png and ImageViewer threw an error, but changing it to jpg it works.

Hi,

I have tried your version.

Renamed gadily.jpeg as gadily.jpg.  Still the same error, unable to view it.

Regards

---

### Post by GhX6GZMB on 2020-07-27
@satimis, apparently you didn't 100% understand my comment about file extensions.

Do as TheFu suggested and use the "file" command from a terminal.

Otherwise, here's another command to run in a terminal:
```
$ xxd -l 60 -c 12 $HOME/Documents/.face.jpg
00000000: ffd8 ffe0 0010 4a46 4946 0001  ......JFIF..
0000000c: 0101 00c8 00c8 0000 ffdb 0043  ...........C
00000018: 0008 0606 0706 0508 0707 0709  ............
00000024: 0908 0a0c 140d 0c0b 0b0c 1912  ............
00000030: 130f 141d 1a1f 1e1d 1a1c 1c20  ........... 

```
The file is just some JPG I had lying around.
The first line of the hex dump is the interesting part.
If your files have the "JFIF", they're JPEG files. And if they have and then don't open/display, then they're corrupted.
But if you have something else in that line, they're not JPEG files.

If it looks like this, they're PNG files:
```
$ xxd -l 60 -c 12 /home/abguest/.face.icon
00000000: 8950 4e47 0d0a 1a0a 0000 000d  .PNG........
0000000c: 4948 4452 0000 0100 0000 0100  IHDR........
00000018: 0806 0000 005c 72a8 6600 0000  .....\r.f...
00000024: 0970 4859 7300 001e c200 001e  .pHYs.......
00000030: c201 6ed0 753e 0000 2000 4944  ..n.u>.. .ID

```
And so on. I'm not going to make examples for every kind of graphic file around...

Cheers.

---

### Post by Holger_Gehrke on 2020-07-27
Wouldn't using the command 'file' be simpler than looking at a hex-dump ? Or - in this specific case - 'identify' from ImageMagick ? Both look at the 'magic number' in a file by which you can tell what kind of file this is.

Holger

---

### Post by satimis on 2020-07-28
> **ml9104 said:**
> @satimis, apparently you didn't 100% understand my comment about file extensions.....
....
$ file -i gadily.jpeg ```

gadily.jpeg: image/jpeg; charset=binary

```

$ file gadily.jpeg ```

gadily.jpeg: JPEG image data, JFIF standard 1.01, aspect ratio, density 1x1, segment length 16

```

The output shows it is .jpeg file

regards

---

### Post by sdsurfer on 2020-07-28
> **TheFu said:**
> +1. Extensions are for humans. Linux doesn't care.

But if something is changed in the server config that does not include the jpeg extension, these files would fail to be output in a request, correct?

No matter, from the offline examination of the files, and the fact that they were displaying correctly at one point, it's clear the files are broken, either through server disk corruption or something else. Have you reported this to the hosting service to see if there was a way to recover them? Most services don't offer backups for free, but there is an off chance that the corruption may be due to something in their hardware and they **may** be able to recover old versions. Fixing images for an entire website one by one would be an exercise in insanity.

There is another option, not a good one, as it would be almost the same thing, recovering the files one by one. See if the site is in the WayBack Machine. You may be able to recover files from there, but it will still be tedious.

[https://archive.org/web/](https://archive.org/web/)

---

### Post by satimis on 2020-07-30
Hi all,

No solution to my posting on WordPress.org

This website was built on about 2013 for sharing information amongst friends but not for business.  It is only occasionally updating its information.

Problem was solved as follows;

I found an export file of "All in One Migration" plugin on my database.  It was created and download to local PC on about Nov. 2019.

Steps performed;
==========

1.  Created an VirtualBox VM on local PC and installed WordPress on it including all necessary software and plugins.

2.  Imported the export file - "string.satimis.com-20191116-100609-508.wpress" on VM WordPress

3.  The website was found running without problem with all upload images working.

3.  Updated the website including touching it.

4.  Exported the website with "All in One Migration" plugin and download the file "192.168.0.197-20200728-155351-uysxe2.wpress" to local PC.

5.  Created a new WordPress website - strings.reynoldstocks.com on Godaddy Server

6.  Imported "192.168.0.197-20200728-155351-uysxe2.wpress" to the new website.

Now strings.reynoldstocks.com is working, all uploaded images being there.

I suppose uploading the wp-contents/uploads/ folder including all images to the old website "string.satimis.com" can also work?

One minor issue: This website when browsed on Firefox it leaves a big margin on both sides.  However there is no problem browsed on Chrome.  Please see attached screenshots

New website;
[http://strings.reynoldstocks.com](http://strings.reynoldstocks.com)

Any suggestion to solve this problem.  Thanks in advance.

Regards

---

### Post by ajgreeny on 2020-07-30
Great news if it's really solved!

With reference to the margin problem is this perhaps simply a zoom factor which I often find varies between firefox and chromium.  Try the usual Ctrl+ to zoom in as usual and see if that does the trick.

If it does, please mark as SOLVED from the Thread Tools menu up-top, if this is now solved to your satisfaction. It is a great help to other users searching the forum.

---

### Post by sdsurfer on 2020-07-30
> I suppose uploading the wp-contents/uploads/ folder including all images to the old website "string.satimis.com" can also work?


So you:
- created a worpress backup
- unpacked the backup in a different hosting environment (a VM on your local computer)
- in that environment everything works

Correct?

I still return to a server issue in the original location, but sure, now that you have confirmed the images display this may be a really good way to prove or disprove that idea.

---

### Post by satimis on 2020-07-30
> **ajgreeny said:**
> Great news if it's really solved!

With reference to the margin problem is this perhaps simply a zoom factor which I often find varies between firefox and chromium.  Try the usual Ctrl+ to zoom in as usual and see if that does the trick.
Hi,

Yes, your advice works.  Zoom factor solves my problem.

Thanks

Remark:  Please check the notification system of your server.  No advice of reply received.  I have to check the forum website.  This problem happens many times in the past.  Thanks

Regards

---

### Post by satimis on 2020-07-30
> **sdsurfer said:**
> So you:
- created a worpress backup
- unpacked the backup in a different hosting environment (a VM on your local computer)
- in that environment everything works

Correct?
I haven't checked it yet.  I'm now updating the new website and after confirming it working without problem then I will copy its /wp-contents/uploads folder including all images and paste the same to the problematic old website.  I'll come back then.

> 
I still return to a server issue in the original location, but sure, now that you have confirmed the images display this may be a really good way to prove or disprove that idea.
I can't really find out what was the real cause of making all images on the old website corrupted.  I'm confident that it was due to updating WordPress version to 2.4 in the past.  It caused many problems to my other websites as well.  Up-to-now the "Preview" function is still NOT working on all my websites.

Regards

---

### Post by sdsurfer on 2020-07-31
> I'm confident that it was due to updating WordPress version to 2.4 in  the past.

Worpress updates modify PHP code, they don't touch images.

> Up-to-now the "Preview" function is still NOT working on all my  websites.

Do you mean preview from admin when you are going through images? And what do you mean by "doesn't work?" 404 not found, blank image box with little X in it, or just no display?
For not found or "empty image holder" this is a wordpress configuration issue. You can inspect the image element and see where wordpress thinks the image is supposed to be and confirm that is the actual location.
For no display, that would take a bit more hands-on investigation.

---

### Post by ActionParsnip on 2020-07-31
Lesson learned here: backup your data well. Saves all this effort

---

### Post by satimis on 2020-07-31
> **sdsurfer said:**
>  -snip-
Do you mean preview from admin when you are going through images? And what do you mean by "doesn't work?" 404 not found, blank image box with little X in it, or just no display?
For not found or "empty image holder" this is a wordpress configuration issue. You can inspect the image element and see where wordpress thinks the image is supposed to be and confirm that is the actual location.
For no display, that would take a bit more hands-on investigation.
After editing a webpage I'll click "preview" to check whether the change is up to my satisfaction.  If satisfied than I'll click "update".  I did this steps for prolonged time.

Now I must click "update" first before clicking "preview".  Otherwise the latter won't work.  In doing so I can't go back to the original page if not satisfying with the editing.

Another strange thing is;
On editing a webpage, after login and place the mouse cursor in the location where I expect to edit.  On clicking "Enter" it popup to another place.  I have to move up/down on the webpage to find the mouse cursor.  This problem only happens on the first time.  On continue editing the same webpage it won't happen again.

Regards.

---

### Post by satimis on 2020-07-31
> **ActionParsnip said:**
> Lesson learned here: backup your data well. Saves all this effort
I have "backup" created with "All in One Migration" plugin.  It just came to my notice that I can't use it without paying.  I will change "All in One Migration" plugin to Duplicator plugin.

I have more than 30 websites running on Godaddy server.  It would be difficult keeping all backup data.

I have cloned websites running on VMs of local PC.  Should the website on Godaddy server encountering serious problem, which never happened before, I just dump the website on local pc to replace the problematic website on Godaddy server.

I'm now building share hosting on VM running on local PC.  I use Duplicator plugin dumping the websites from Godaddy server onto the VM.  It works for me without problem.  Now I have a VM running 10 websites.  I'm prepared increasing to 20 websites.  If successful then I'll install 30 websites on it, ONE VM.  It is a very interesting setup.

Regards

---

### Post by satimis on 2020-08-03
Hi all,

After having fine tuned the new website;
[http://strings.reynoldstocks.com](http://strings.reynoldstocks.com)

On "File Manager Advanced" plugin, Download /wp-content/uploads folder to local PC and extract it.

There are 5 folders namely;
2013
2014
2018
2020
et_temp   #an empty folder

Started the problematic website;
[http://string.satimis.com](http://string.satimis.com)

Ran "File Manager Advanced" plugin
on /wp-content/uploads folder
There are 6 folders on;
2013
2014
2018
2019
2020
et_temp   #an empty folder also

Renamed them as
2013.old
2014.old
2018.old
2019    # no change
2020.old

Upload folders 2013,2014,2018 and 2020 from local PC

Now all images come back and working.

I'll delete this website later, including its subdomain;
[http://string.satimis.com](http://string.satimis.com)

Regards

---

