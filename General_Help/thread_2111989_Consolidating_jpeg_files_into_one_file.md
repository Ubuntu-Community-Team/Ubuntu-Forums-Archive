---
title: "Consolidating jpeg files into one file"
date: 2013-02-03
forum: General Help
---

### Post by rmcellig on 2013-02-03
Is there a way to consolidate multiple jpeg files into one file? Maybe a pdf file or something similar? CLI and GUI options would be appreciated.

---

### Post by sudodus on 2013-02-03
- Manually - use LibreOffice Impress

- Automatically - use ImageMagick Convert

```
convert "*.jpg" output.pdf
```

I have used convert before, but not for this task until I tested it now to see that it works. I found it via this link

[[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=1480100[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1480100")

---

### Post by rmcellig on 2013-02-04
Excellent. Works great! One thing though. My jpgs have specific names. When they are converted and I open the pdf file, the jpg's are renamed 1,2,3,4 etc.... Is there a way to rename them or retain the original names of the jpg files?

---

### Post by sudodus on 2013-02-04
> **rmcellig said:**
> Excellent. Works great! One thing though. My jpgs have specific names. When they are converted and I open the pdf file, the jpg's are renamed 1,2,3,4 etc.... Is there a way to rename them or retain the original names of the jpg files?

I think you are referring to the page numbers. I don't know an easy way to keep the file names. You can do it manually, or you could let convert write the file names into the images before they are put into the pdf file.

- How many files are there?
- Why are you doing this?

---

### Post by sudodus on 2013-02-04
You can use 'Annotating Images' in ImageMagick (and for example store the images temporarily with a fixed frame size) and then merge them into a pdf file.

[http://www.imagemagick.org/Usage/annotating/]("http://www.imagemagick.org/Usage/annotating/")

Another way would be to make a ***tarball***. Then the jpeg files are stored with their names.

---

### Post by rmcellig on 2013-02-04
Maybe I am using the wrong tool and going about this the wrong way. Here is further clarification:

I host a weekly radio show. When I digitized some of my LP's, I also scanned in the notes on th back of the album jackets and saved them as seperate jpg files. When I get to the studio I find the only way I can view these files is to open them seperately in Firefox. What a pain. I have about 13 jpg files.

I have to find a way where I can open only one document and have the jpg's or notes there. I need to know what the jpg files refer to, so for example if I am playing something from an LP called Singers, I need to have the jpg file say Singers so I know what I am looking for. This works in Firefox because the names of the jpg files reflect the names of the albums. Make sense?

Let me know. Thanks!!

At the station they use XP Pro on their computer.

---

### Post by sudodus on 2013-02-04
There are several photo organizers in the linux world. So if you could use a linux system at the radio station, I would have suggested DigiKam or Shotwell to manage and view your jpeg files if there were hundreds or thousands of them.

Now it is only 13 jpeg files, which is few enough to manage manually. I would use the default picture viewer in linux and either the default picture viewer (for local pictures) in Windows, or if you are not happy with it, Irfanview (a free windows program). So keep the jpeg files on a USB pendrive, browse with the file brower (Nautilus in linux, Explorer in Windows), and use a picture viewer (these are better for this purpose than Firefox).

Another option is to make a slide-show with LibreOffice Impress, where you can add whatever texts and links you want at the pictures.

---

### Post by rmcellig on 2013-02-04
Unfortunately, I can't alter anything on the radio station computer. I tried the photo viewer that they use and it's awful! For me, I think if the files were in a pdf files and the images labelled properly, I would be OK.

---

### Post by sudodus on 2013-02-04
> **rmcellig said:**
> Unfortunately, I can't alter anything on the radio station computer. I tried the photo viewer that they use and it's awful! For me, I think if the files were in a pdf files and the images labelled properly, I would be OK.
I would regard it as a slide-show, and create it with pictures and text using LibreOffice Impress (and save it in the open document format). Then I would export it to a pdf file, that you can bring to the radio station.

---

### Post by Impavidus on 2013-02-04
There was a similar question three weeks ago: [http://ubuntuforums.org/showthread.php?t=2102856](http://ubuntuforums.org/showthread.php?t=2102856) Read post #4.

A simple script can generate a html file with the images and the filenames as captions. Keep the html file and the images in one directory on a usb stick and you can open it in a web browser.

Alternatively, you can print this to pdf or use a script to generate a tex file (if you've some experience with them) and turn that into a pdf. It's a bit overkill, but once you have it scripted it's quite convenient.

---

### Post by rmcellig on 2013-02-04
> **sudodus said:**
> I would regard it as a slide-show, and create it with pictures and text using LibreOffice Impress (and save it in the open document format). Then I would export it to a pdf file, that you can bring to the radio station.

Excellent idea!

I just tried it and it works great!! Thanks so much!

---

### Post by sudodus on 2013-02-04
You are welcome :-)

---

