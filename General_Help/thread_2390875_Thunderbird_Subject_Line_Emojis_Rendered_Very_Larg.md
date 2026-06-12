---
title: "Thunderbird Subject Line Emojis Rendered Very Large"
date: 2018-05-03
forum: General Help
---

### Post by tydfil2 on 2018-05-03
I have an annoying problem with font scaling in Ubuntu 18.04 in Thunderbird.  Subject line emojis rendered very large and obscure surrounding subjects.  
Have googled this and can find nothing that helps on Thunderbird/Mozilla threads.
Have turned off "Display emmoticons as graphics" in Thunderbird Preferences and removed the font EmojiOneMozilla.ttf,  cleared the cache to no avail. 
Every time I start the PC and check mail I can't see headers of nearby mail. 
I read that removing "<edit name="scalable" mode="assign"><bool>true</bool></edit>" from the font config would work but I cannot find it anywhere using grep -r. 
I haven't noticed the problem in other applications. Any ideas?

attached an image.

Thanks in advance for looking and advice.

---

### Post by PaulW2U on 2018-05-03
I think [Emojis in email headers are shown MUCH too large]("https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/1767415") is the bug report you might want keep watching.

Report doesn't mention a workaround though.

---

### Post by tydfil2 on 2018-05-03
Thanks a lot for that @ PaulW2U, at least I know it is being addressed.

---

### Post by habana on 2018-05-03
@tydfil2. If you look at the bug report, it is currently _not_ being addressed. Can I suggest you add your name to the list of those affected? More chance of it being fixed. 

Cheers
Bill

---

### Post by habana on 2018-05-05
A fix is now added to the bug report.

```
sudo apt-get install fonts-symbola
```

It worked for me

---

### Post by cds60601 on 2018-05-05
> **habana said:**
> A fix is now added to the bug report.

```
sudo apt-get install fonts-symbola
```

It worked for me

Ditto here.

---

### Post by strixtux on 2018-05-08
For me as well. Thank you all!

---

### Post by bleakwizard on 2018-05-14
sudo apt-get install fonts-symbola

who ever sorted out this remedy and those spreading it: thanks. works perfectly. Simple and effective

---

### Post by n4113032 on 2018-05-26
The [fix]("https://askubuntu.com/questions/1030609/18-04-fresh-install-thunderbird-inbox-invaded-by-large-icons/1030634#1030634") has been improved to include colour icons.

---

