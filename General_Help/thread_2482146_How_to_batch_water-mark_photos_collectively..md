---
title: "How to batch water-mark photos collectively."
date: 2022-12-21
forum: General Help
---

### Post by satimis on 2022-12-21
Hi all,

Please advise how to batch water-mark photos collectively.

For example:- 

photo-01.jpg, photo-02.jpg, photo-03.jpg, photo-04.jpg, photo-05.jpg, etc

I need to water-mark a number on the left top corner of each photo
001, 002, 003, 004, 005

Thanks in advise.

Regards

---

### Post by ajgreeny on 2022-12-21
I have no personal experience of doing this but have a read through the thread at [https://askubuntu.com/questions/748698/software-to-add-watermark-to-photos-in-bulk](https://askubuntu.com/questions/748698/software-to-add-watermark-to-photos-in-bulk) which maay give you all you need.

---

### Post by satimis on 2022-12-22
> **ajgreeny said:**
> I have no personal experience of doing this but have a read through the thread at [https://askubuntu.com/questions/748698/software-to-add-watermark-to-photos-in-bulk](https://askubuntu.com/questions/748698/software-to-add-watermark-to-photos-in-bulk) which maay give you all you need.
Hi,

Thanks for your advice.

I found the solution on ImageMagick forum:-

To batch process the images I must write a script and besides;
All images must be in sequentially increasing order in the directory otherwise the script won't work

Therefore I have to adding the number to the images one-by-one as follow;
$ convert input_image_1.jpg -gravity northwest -font arial -pointsize 90 -fill red -annotate +100+100 "001" output_image_1.jpg 

$ convert input_image_2.jpg -gravity northwest -font arial -pointsize 90 -fill red -annotate +100+100 "002" output_image_2.jpg 

etc.

Done

Regards

---

### Post by dragonfly41 on 2022-12-22
> [COLOR=#000000]Therefore I have to adding the number to the images one-by-one as follow;[/COLOR][COLOR=#000000]

I am a bit busy on my own development tasks but I offer another  automation suggestion, since you have "100's of photos".

First consider using Scribus for open source desktop publications.

Then in Scribus > Script (toolbar) consider adding a plugin named "ScribusGenerator".
You will have to search for this and the YouTube tutorial on its use.

P.S. found it here.  [/COLOR]http://berteh.github.io/ScribusGenerator/[COLOR=#000000]

Basically you prepare an Excel spreadsheet containing all your  custom variables which might be

recipients (family)
images (100's ??)
watermarks
customised covers (perhaps addressed to individual family recipients).
 ... ...

Then prepare a Scribus template, perhaps one image frame (to import photo per page or multiple phots per page) and one or more text frames per page. But they are empty at this stage.

Your text can even "flow" around your photos in image frames.

Now after learning the ropes in using ScribusGenerator (originally developed for printing custom business cards in Scribus) you can import CSV from Excel sheet and embed VARS i(such as comments, watermarks) in your Scribus document.

You end up with a batch of documents (which can be PDF or ePub)  each customised to the recipient.

You can upload these "galleries" to be downloaded by recipients. Each download customised to the recipient.

[/COLOR]

---

### Post by satimis on 2022-12-23
Hi all,

Further to my late posting.

It is possible to perform batch processing eventhough the images not in sequentially increasing order in the directory.  It is not necessary adding number to the images one-by-one.

I found out the solution on ImageMagick forum with following script:
```

$ cd image_folder/
$ i=1
$ for img in *.jpg; do
> name=$(convert "$img" -format "%t" info:)
> convert "$img" -gravity northwest -font arial -pointsize 90 -fill red -annotate +100+100 "$ii" ${name}_annotate.jpg
> i=$((i+1))
> done

```

The script works seamlessly.

Regards

---

