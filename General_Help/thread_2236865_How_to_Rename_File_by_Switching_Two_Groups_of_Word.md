---
title: "How to Rename File by Switching Two Groups of Words in Its Filename?"
date: 2014-07-29
forum: General Help
---

### Post by GreenRaccoon on 2014-07-29
Say I'm trying to rename a bunch of songs in Terminal. In their filename, the [COLOR=#008000]track's name[/COLOR] comes first followed by the [COLOR=#0000ff]artist's name[/COLOR]. But I want to rename them so that the [COLOR=#0000ff]artist's name[/COLOR] comes first, followed by the [COLOR=#008000]track's name[/COLOR]. If I were to use the rename command in Terminal, how would I do this?

I know how to rename one group of words, but I don't know how to switch the order of two words. To rename one group would look like this:
```
rename 's/The Black Crows/Black Crows, The/g' *The Black*.mp3
```

I was hoping that I could do two things: 1) use a wildcard that includes everything else but the words I specify, and 2) turn this "wildcard" into a variable.

If it helps, the rename command uses perl.

---

### Post by tgalati4 on 2014-07-29
*easytag* has a naming tool that you can define in preferences.  I would use that to check the ID3 tags as well so that they match as you save each file.  If you have thousands of files that need changing, then this would be a tedious process.

If your names have a consistent field separator (say --) then you can define the field separator and use gawk or perl to rearrange the fields.  Your script will require a few iterations to get it right.  Perhaps post a small sample of a directory listing to have some data to work with.

A google search brings up a lot of ideas:  [https://www.google.com/search?q=linux+script+for+renaming+music+tracks&gws_rd=ssl](https://www.google.com/search?q=linux+script+for+renaming+music+tracks&gws_rd=ssl)

---

### Post by GreenRaccoon on 2014-07-29
> **tgalati4 said:**
> *easytag* has a naming tool that you can define in preferences.  I would use that to check the ID3 tags as well so that they match as you save each file.  If you have thousands of files that need changing, then this would be a tedious process.

If your names have a consistent field separator (say --) then you can define the field separator and use gawk or perl to rearrange the fields.  Your script will require a few iterations to get it right.  Perhaps post a small sample of a directory listing to have some data to work with.

A google search brings up a lot of ideas:  [https://www.google.com/search?q=linux+script+for+renaming+music+tracks&gws_rd=ssl](https://www.google.com/search?q=linux+script+for+renaming+music+tracks&gws_rd=ssl)
Awesome! Thanks!

I was hoping to see if I could do this beyond music files though. I'm actually trying to do this for ebook files, but I used music files as my example because it was a little easier for me to explain.

I didn't even think about googling specifically for ebook files. I'll try that and let you know if I find something.

-----EDIT-----

Aha! I found an answer here: [http://askubuntu.com/questions/348309/rename-file-from-title-author-to-author-title](http://askubuntu.com/questions/348309/rename-file-from-title-author-to-author-title).

So for me, it would be
```
rename 's/(.*)\s+[-]\s+(.*)\.(.{3,4})/$2 - $1.$3/' *Lewis.epub
```

Also, just for reference, if I want to rename titles to put "The" at the end, here's the command:
```
rename 's/(.*)\s+[-]\ The\s+(.*)\.(.{3,4})/$1 - $2, The.$3/g' *.epub
```

---

### Post by tgalati4 on 2014-07-29
You have become the master field manipulator.  Because *rename* uses PERL regular expressions, it is pretty powerful.  It has a learning curve, but the Agony Units of learning it are less than doing the conversions by hand, one-by-one.

---

### Post by GreenRaccoon on 2014-07-30
> **tgalati4 said:**
> You have become the master field manipulator.  Because *rename* uses PERL regular expressions, it is pretty powerful.  It has a learning curve, but the Agony Units of learning it are less than doing the conversions by hand, one-by-one.
Definitely. Haha I just noticed your picture. I guess you could call me the next Lone Starr. Maybe someday I'll be as good with the Linux side of the Schwartz as Yogurt.

---

### Post by tgalati4 on 2014-07-30
That's the business end (inside the afterburner flameholder) of an F16 fighter at an air show.  I thought it was a funny picture.  And it's the first thing I thought of when I discovered the speed and power of linux--ludicrous speed.

---

