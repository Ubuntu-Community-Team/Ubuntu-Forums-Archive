---
title: "downloading images to webhost"
date: 2008-05-04
forum: General Help
---

### Post by Ruriko on 2008-05-04
How do I make my webhost to download a set of images from flickr?

---

### Post by iSplicer on 2008-05-04
You need to connect to your server through SSH and then use the wget command to download the files onto your server.

---

### Post by Ruriko on 2008-05-04
I never used wget before. What is the command to download a set of images on flickr?

---

### Post by karuptdata on 2008-05-05
Login to your server via ssh and issue the following command:

```
wget http://urdomainhere.com/filename.zip
```

Of course replace the url with the actual url of the file you are attempting to download.

---

### Post by Ruriko on 2008-05-05
That only downloads one file at a time. I want to grab all the images in a specific tag on flickr. For example I want to grab all the pics on this link [http://www.flickr.com/photos/tags/banana/](http://www.flickr.com/photos/tags/banana/) . I don't want the thumbnails but I want the full sized pictures

---

