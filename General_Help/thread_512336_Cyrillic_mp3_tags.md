---
title: "Cyrillic mp3 tags"
date: 2007-07-29
forum: General Help
---

### Post by rpglover64 on 2007-07-29
When I ran windows, I used MP3BookHelper to convert tags like Áåëàÿ to normal Russian characters.  If I remember correctly, this is a conversion from ISO-8859-5 to cp1251, but I may be completely off.  I have looked for a native linux program which has can do what MP3BookHelper can, but none of the tag editors are nearly as powerful, and none can perform said conversion.  I tried to run it on wine, but it doesn't work properly.

If anyone knows of a way to get MP3BookHelper to work with wine, an editor that can replace it, or a way to convert encodings (in mp3 tags) manually via command line, I will be grateful to learn of it.

Thank you very much.

---

### Post by rpglover64 on 2007-07-29
After playing around with easytag, i found an option to read tags in from cp1251 and force write to unicode.

---

### Post by jim_p on 2007-07-30
Which music player are you using?

I had the same problem with Greek song titles in BMP.To correct it, you go to Preferences > Plugins.
Under the "Media" tab, click on the "MPEG sound addon" and click on "Preferences" to show its options.
Under the tab "Title" you can put your encoding to whatever Cyrilic uses, e.g. ISO-8859-7 is for Greek.
Save and exit.

---

