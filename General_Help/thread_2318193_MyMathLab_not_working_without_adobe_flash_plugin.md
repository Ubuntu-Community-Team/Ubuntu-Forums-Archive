---
title: "MyMathLab not working without adobe flash plugin"
date: 2016-03-23
forum: General Help
---

### Post by haplorrhine on 2016-03-23
I just did a reinstall at the library and now this is all I see when I try to work on my MyMathLab assignments.  This wasn't a problem before.   > You do not have the most recent version of the Adobe® Flash® Player, which is required to view the content in this course.  Run Browser Check now to install Flash® and check for other components required for this course. [https://www.mathxl.com/Service/PlayerCheckNG.aspx?player=nextgen_math&dest=%2fStudent%2fPlayerHomework.aspx%3fhomeworkId%3d348393838%26questionId%3d9%26flushed%3dfalse%26cId%3d3813439%26centerwin%3dyes&bookId=94202&usewizard=yes](https://www.mathxl.com/Service/PlayerCheckNG.aspx?player=nextgen_math&dest=%2fStudent%2fPlayerHomework.aspx%3fhomeworkId%3d348393838%26questionId%3d9%26flushed%3dfalse%26cId%3d3813439%26centerwin%3dyes&bookId=94202&usewizard=yes)  When I follow the hyperlink titled "Run Browser Check", nothing happens.  I tried installing the adobe flash plugin, allowing scripts globally, creating a fresh firefox profile, unconfining firefox via apparmor, and attempting it from unconfined chromium-browser.  I can't change the URL (to http).  Any clue what the problem could be?

---

### Post by haplorrhine on 2016-03-24
This was helpful.  [https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash)  I installed mozilla-plugin-gnash and it works.  ```
sudo add-apt-repository "deb http://archive.ubuntu.com/ubuntu $(lsb_release -sc) universe"
``` ```
sudo apt-get install mozilla-plugin-gnash
```

---

