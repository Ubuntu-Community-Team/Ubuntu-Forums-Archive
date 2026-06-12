---
title: "Uploading to Vimeo"
date: 2008-06-05
forum: General Help
---

### Post by Irony on 2008-06-05
I'm using Hardy Heron and cannot upload videos to [http://www.vimeo.com](http://www.vimeo.com) from terminal I get the message;

```
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
```

It doesn't matter whether it is Firefox, Opera or Epiphany - the problem doesn't occur in Windows XP or in Gutsy so it is something to do with Hardy.

Any suggestions as to how I might search out what the problem is? Note I can upload to youtube and veoh with no problem.

What happens is that with the standard Vimeo uploader firefox simply freezes (flash?) - with there simple uploader it simply times out but doesn't freeze.

---

### Post by ironcamel on 2008-06-23
I'm having trouble uploading as well.  My browser just crashes.  I'm running Hardy.  As a workaround, I upload using IE through wine.  And I can log in with firefox and edit the title, description, etc.  Hopefully this will be fixed soon.  I just found out about vimeo and it seems to be a great site.

---

### Post by Ralphie on 2008-06-23
Uploading through flash applications seems to be an issue in general, not only can I not upload to vimeo, but also the latest version of Wordpress, which I'm not sure if that is a flash uploader or what it is.

[https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/218635](https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/218635)
This is a bug report on the topic.

Also, a better work around is to upload from this link:
[http://vimeo.com/upload/video/basic](http://vimeo.com/upload/video/basic)

which does not use flash.

---

### Post by Ralphie on 2008-06-30
In my last post, I had a work around for uploading to Vimeo, and I just found another one for uploading to wordpress, that I thought I'd share just in case anyone needed help on that.

Download the attached plugin ( by [Dion Hulse]("http://dd32.id.au/") ), unzip it and put it in your wordpress plugins folder, then activate the plugin through the admin panel, you are now able to upload using the standard method. 
All this does is strips the flash upload element that crashes firefox.

---

### Post by deltateam2 on 2009-04-06
[vimeo.com/upload/video/basic]("vimeo.com/upload/video/basic") worked for me on Firefox 3.0.8 on Ubuntu 8.10 (Intrepid Ibex).

---

### Post by eyax on 2009-04-24
> **deltateam2 said:**
> [vimeo.com/upload/video/basic]("vimeo.com/upload/video/basic") worked for me on Firefox 3.0.8 on Ubuntu 8.10 (Intrepid Ibex).

Thank for tip
--
Lazzaro

---

### Post by BertieRooster on 2009-06-17
I've had this problem too, the simplest workaround I've found is just to use the windows version of firefox with WINE. Works fine.

---

