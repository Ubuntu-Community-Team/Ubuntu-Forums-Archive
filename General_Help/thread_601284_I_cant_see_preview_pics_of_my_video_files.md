---
title: "I cant see preview pics of my video files"
date: 2007-11-03
forum: General Help
---

### Post by jamison on 2007-11-03
Well, I have been at this all day and can't figure it out.  

I am running the newest version of Ubuntu and just would like to see a screen shot from a video file (wmv, mpg, etc.) instead of the standard film roll icon.

I tried a lot of things but nothing has given any results.  Is there an easy answer?  

Any advice would be greatly appreciated! 

Thank You!!

---

### Post by meg23 on 2007-11-04
Run these commands in terminal. 

rm -rf ~/.thumbnails/normal/*
rm -rf ~/.thumbnails/fail/*

I had the same problem and it fixed it.

---

