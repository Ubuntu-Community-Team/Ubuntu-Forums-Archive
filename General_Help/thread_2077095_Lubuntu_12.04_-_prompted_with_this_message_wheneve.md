---
title: "Lubuntu 12.04 - prompted with this message whenever I try to open eclipse"
date: 2012-10-27
forum: General Help
---

### Post by chickeneaterguy on 2012-10-27
As stated in the title, here is my screenshot:

[IMG]https://dl.dropbox.com/u/40864263/zmisc/captured/0053.jpg[/IMG]

While eclipse works fine, I just want to know if there's a way to get rid of this prompt each time I open it. 

I've tried chmod 777 to not avail and have only found results telling me to do

---

### Post by jerrrys on 2012-10-27
Right click on the folder and in "properties" check the box to make it executable.

---

### Post by chickeneaterguy on 2012-10-27
> **jerrrys said:**
> Right click on the folder and in "properties" check the box to make it executable.

This is all I'm provided with:
[IMG]https://dl.dropbox.com/u/40864263/zmisc/captured/0055.jpg[/IMG]
[IMG]https://dl.dropbox.com/u/40864263/zmisc/captured/0056.jpg[/IMG]

EDIT: I should add that I did the same for the folder, as you specified and was provided with no such option. :(

---

### Post by jerrrys on 2012-10-27
Ok, the only other way I know of to make it excutable is:

chmod +x eclipse.run

I suggest making a backup of that folder before trying as this is a untested suggestion.

---

### Post by chickeneaterguy on 2012-10-27
> **jerrrys said:**
> Ok, the only other way I know of to make it excutable is:

chmod +x eclipse.run

I suggest making a backup of that folder before trying as this is a untested suggestion.

No eclipse.run file :/

Thanks though.

---

### Post by jerrrys on 2012-10-27
Copy your eclipse file to /usr/bin and name it Eclipse.run

Then create an empty folder in your home folder and name it Eclipse and ..

chmod +x Eclipse.run

Thats my last idea, good luck

---

### Post by chickeneaterguy on 2012-10-27
> **jerrrys said:**
> Copy your eclipse file to /usr/bin and name it Eclipse.run

Then create an empty folder in your home folder and name it Eclipse and ..

chmod +x Eclipse.run

Thats my last idea, good luck

No luck. Thanks again though. I think this problem is specific to Lubuntu+eclipse?. I can't find anything on it elsewhere.

---

