---
title: "Thunderbird doesn't see old mail"
date: 2007-04-24
forum: General Help
---

### Post by infidel on 2007-04-24
Hello, all. I recently did a clean install of Feisty and decided that I wanted to try the latest Thunderbird. I installed 2.0.0.0 as described [here]("https://help.ubuntu.com/community/ThunderbirdNewVersion"). The installation went well, Thunderbird runs fine, but I'm not having any luck trying to import my mail from my older version of Thunderbird. As instructed by every how-to I can find, I've put my old Mail directory in ~/.thunderbird/<profile>; but when I launch Thunderbird there's no mail to be found.

Incidentally, it didn't work with the older version of Thunderbird available from the repositories, either (in this case, the directory was ~/.mozilla-thunderbird/<profile>.

Any guidance would be greatly appreciated, as I have a LOT of mail that I would like to keep. Thanks in advance.

---

### Post by zvacet on 2007-04-24
I don´t use Thunderbird but I belive ther is option **import from**.Point it where your mail is and it will import it (hopefully).

---

### Post by NJC on 2007-04-24
It does say the following in the Mozilla release notes but I wasn't able to get Tbird to see my old 1.5 mail folders either:

> Linux and Unix 
If Thunderbird is installed to a location with spaces in the path, it may not be able to set itself as default mail client and may keep prompting at startup. The work around is to install into a path without spaces. 


[http://www.mozilla.com/en-US/thunderbird/2.0.0.0/releasenotes/](http://www.mozilla.com/en-US/thunderbird/2.0.0.0/releasenotes/)

---

### Post by infidel on 2007-04-25
> **zvacet said:**
> I don´t use Thunderbird but I belive ther is option **import from**.Point it where your mail is and it will import it (hopefully).

It's there, but it's only for importing mail from other mail applications. Older versions of Thunderbird aren't included. Thanks for the suggestion, though.

TO NJC: spaces in the path aren't an issue in my case; but thanks for the information.

---

### Post by zvacet on 2007-04-25
I know it is stupid,but if you realy need your mail you can allways try this.Import your mail to some other mail cient and from it to thunderbird.Nothing else cross my mind.

---

### Post by aysiu on 2007-04-25
Try this:

1. Close Thunderbird
2. Paste these commands into the terminal: ```
mv ~/.thunderbird ~/.thunderbird.not.working
ln -s ~/.mozilla-thunderbird ~/.thunderbird
```
3. Launch Thunderbird again (the 2.0 one)

---

### Post by infidel on 2007-04-25
Huge thanks for everyone's input. Sadly, it doesn't look like I'm going to be able to make this happen. For whatever reason (and I should have looked before I posted), the Mail directory I copied from my old Edgy installation doesn't appear to actually contain any mail files. I saw a bunch of subdirectories in it corresponding to the mail accounts I had set up under Thunderbird 1.5 and assumed that everything I needed was inside. Turns out that I must have copied the wrong thing to begin with. So, quite literally, all is lost. :)

Luckily, I've used GMail almost exclusively for over two years, so anything I _really_ need should still be accessible.

Thanks again.

---

