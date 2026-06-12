---
title: "How to preserve image description when uploading to Facebook"
date: 2013-01-18
forum: General Help
---

### Post by mcdragon on 2013-01-18
I came upon this problem when I wanted to edit/apply an exif image description and have that recognized by Facebook.
As it has been mentioned FB does [strip some exif data]("http://www.windowsitpro.com/blog/security-blog-12/socialmedia/facebook-handles-image-exif-data-141543#/0").
I used to use the linux version of Google Picasa and the image description would be preserved upon FB upload. However as [Picasa on linux has finished]("http://www.omgubuntu.co.uk/2012/04/google-officially-drop-picasa-for-linux").
I have now used [Phatch]("http://photobatch.stani.be") to do more advanced exif editing and writing. However its quite advanced and will not tell you what exif tag to write so it gets preserved for FB.
I found at least two tags that would possibly apply. One is an [exif]("http://en.wikipedia.org/wiki/Exchangeable_image_file_format") tag ```
<Exif_Image_ImageDescription>
``` and another tag whitch is actually an [IPTC]("http://en.wikipedia.org/wiki/IPTC_Information_Interchange_Model") tag ```
<Iptc_Application2_Caption>
```
It turns out that only the <Iptc_Application2_Caption> tag was recognized and actually ended up in the Facebook image description.

This is my small contribution on the matter in case somebody has the same problem. I do understand the matter is more extensive and I would even dream about claiming to know the whole story.

---

