---
title: "Import a folder of images with file names for captions?"
date: 2013-01-08
forum: General Help
---

### Post by Eric Boring on 2013-01-08
Hello,

I'm looking for a way to import all of the image files in a particular folder into a word-processable document. I don't really care whether this would be .odt or .doc(x) or .rtf or .html or whatever. But i don't want to import these into a PDF. 

I'm thinking there must be a handy-dandy command line tool that will do this for me. Any suggestions? 

Thanks in advance,

EB

---

### Post by leviteo on 2013-01-08
Hey,

I dont know if i really got your question but if you are trying to create a odt file based in the name of .jpg in some folder you may try this:

[http://linux.die.net/man/1/unoconv](http://linux.die.net/man/1/unoconv)

Leví

---

### Post by Eric Boring on 2013-01-08
Thanks for the response. 

I don't think that's quite what I'm after. 

I have a folder full of images, each with a file name. I want to have them all in a long document, each with the name of the file listed right below the image itself.  So if I start with 100 individual image files, I want them to all be in a single word processor file, and labeled with their file names when I'm done.

Any suggestions?

---

### Post by Impavidus on 2013-01-09
If the file format you want to produce is a kind of plain text (like html, xml based formats, you may want to zip them afterwards) you can write a simple script that writes the file for you and execute that script in the directory with the images:```

#!/bin/bash
echo "This is the header of your file" >output.whatever
echo "which may be several lines long" >>output.whatever

for file in *.jpg
do
    echo "BeginImage" >>output.whatever
    echo "    ImageFile=$file" >>output.whatever
    echo "    ImageCaption=$file" >>output.whatever
    echo "EndImage" >>output.whatever
    echo >>output.whatever
done

echo "This is the footer of your file" >>output.whatever
```This will link to your images, not include them in your document. If you want that you'll have to make this in a format that can somehow be compiled into something that includes the actual image data (like tex, that can be compiled into pdf, but you stated you didn't want pdf, so do whatever you like).

---

### Post by sudodus on 2013-01-09
> **Eric Boring said:**
> Thanks for the response. 

I don't think that's quite what I'm after. 

I have a folder full of images, each with a file name. I want to have them all in a long document, each with the name of the file listed right below the image itself.  So if I start with 100 individual image files, I want them to all be in a single word processor file, and labeled with their file names when I'm done.

Any suggestions?

If you tell us how you plan to use this big document or presentation file, we might come up with better suggestions.

---

### Post by Eric Boring on 2013-01-09
Thanks for the suggestions! 

Sudodus, we're going to take a bunch of screen grabs, put them into a long document and write up changes to the text in the screengrabs. It's essentially a copy editing project, but we need to have the images that need changes to be presented next to text describing those changes. 

Impavidus, thanks for the script sample. I will give that a try.

EB

---

### Post by sudodus on 2013-01-09
Then I think it would work with links to the images, as described by Impavidus. This would make it convenient to manage: a rather small file with links and text, and a directory [structure] with the images.

I'm thinking of a final touch of HTML to make it convenient for the reader.

---

