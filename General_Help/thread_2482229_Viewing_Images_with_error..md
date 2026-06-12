---
title: "Viewing Images with error."
date: 2022-12-25
forum: General Help
---

### Post by josephchrzempiec on 2022-12-25
Hello, I'm running ubuntu 20.04 LTS. I unzipped a folder with images in it and When I go to view an image I'm greeted with this error message Error interpreting JPEG image file (Not a JPEG file: starts with 0x00 0x00). I have never saw this message before. I looked online and So confused with a lot of people having this problem and Everything seen is confusing to try. I'm still kind of new to linux and I really need help. I'm fully switching from a windows system to a linux system but still learning. Please someone help me to figure this out and how I can fix the images in viewing?

Joseph

---

### Post by Holger_Gehrke on 2022-12-25
Not much you can do about it. The files are damaged and the viewer can't even identify them as jpegs (a jpeg file starts with a specific sequence of bytes which should be 0xFF 0xD8 - meaning Start of Image -  not 0x00 0x00). You could try running the 'file' command on the files to find out if they are some other type of image, but it's very probable they are just junk.

Holger

---

### Post by josephchrzempiec on 2022-12-25
That means all my images are damage? No image I can view. My family photo's do the same thing. No matter what photo I view does this. Yesturday All my photo's was working. Then after I did an update this is what happened.

---

### Post by Holger_Gehrke on 2022-12-25
> **josephchrzempiec said:**
> That means all my images are damage? No image I can view. My family photo's do the same thing. No matter what photo I view does this. Yesturday All my photo's was working. Then after I did an update this is what happened.

That admittedly sounds more like some component (libjpg ? some part of gtk ?) acting up than actual damage to the files. What viewer are you using ? Have you tried running 'file' from the command line on one of the files your viewer won't show ?

Holger

---

### Post by Impavidus on 2022-12-25
Usually when you get that error, it means that your files are damaged, either the jpeg files themselves or the archive in which they were stored. Broken hard drive or memory card, a fake drive that's actually smaller than advertised, damage in transmission over a network (without comparing hashes), careless command line use, buggy applications; there are many ways to damage files and all of them are uncommon. Having a lot of files damaged simultaneously is a bit suspect.

In the past 2 weeks I've received only a few updates and only one of the updates had anything to do with jpegs: python3-pil, which is a python library for reading, writing and manipulating several image formats. Not all image viewers use python3-pil, but some may. Have you tried using a different image viewer? Which image viewer have you tried? On my Xubuntu system I've got ristretto and gthumb, neither of which depend on python-pil.

You can check the image files on the command line.```
file /path/to/file.jpeg
```will tell you what file format the system thinks your image file has.```
hd -n 16 /path/to/file.jpeg
```will show the first 16 bytes. Instead of typing /path/to/file.jpeg, you can also drag and drop the file to the terminal.

---

