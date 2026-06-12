---
title: "Looking for website downloading program"
date: 2007-06-16
forum: General Help
---

### Post by Error47 on 2007-06-16
Linux or windows, I am looking for a program to download content off of a website. The website has a main page, then if you click on a link it takes you to where all the files are, I don't want to click and save all 600 files scattered throughout the website, it is free and not copyrighted. How can I download all audio and video from the entire website?

---

### Post by 5-HT on 2007-06-16
httrack or wget would do the job. Webhttrack is a gui-frontend to httrack if you'd prefer that.

---

### Post by Error47 on 2007-06-16
I need something that would download only video and audio files, I do not need all the html files that would come with it. LIke I would like to specify the file extentions to download. And it should be easy to use too.

---

### Post by cookies on 2007-06-16
There is a Firefox extension that does this:
[https://addons.mozilla.org/en-US/firefox/addon/1468](https://addons.mozilla.org/en-US/firefox/addon/1468)

---

### Post by cwaldbieser on 2007-06-16
> **Error47 said:**
> I need something that would download only video and audio files, I do not need all the html files that would come with it. LIke I would like to specify the file extentions to download. And it should be easy to use too.

The -A option of wget should let you specify a particular pattern:
```

$ wget -r -nd -l3 --no-parent -A '*.gif' http://www.example.com

```
This pulls the files ending in ".gif" from [www.example.com](www.example.com).
The "-l3" means it only goes 3 levels deep.  If the site has a robots.txt file, this seems to be pulled, too.

---

### Post by Znupi on 2007-06-16
[FlashGot extension for Firefox.](https://addons.mozilla.org/en-US/firefox/addon/220)

---

### Post by 5-HT on 2007-06-16
> **Error47 said:**
> I need something that would download only video and audio files, I do not need all the html files that would come with it. LIke I would like to specify the file extentions to download. And it should be easy to use too.

You can do that with {web}httrack as well as wget (as cwaldbieser mentioned).

---

